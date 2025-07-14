# Playbook: Resposta a Phishing com Execução de Anexo Malicioso

## 🆔 Identificação Geral

| Campo | Valor |
|-------|-------|
| **Nome do Playbook** | Resposta a Phishing com Execução de Payload |
| **MITRE ID** | T1204.002 (Malicious File) |
| **Tática** | Execution |
| **Vetor de Entrada** | E-mail com anexo executável (.exe/.scr) |
| **Ferramentas** | Email Gateway, SIEM, VirusTotal, EDR, Firewall, PowerShell |

## 📑 Fases do Playbook

| Etapa | Ação | Tipo | Script / Ferramenta | Entrada Esperada | Saída / Evidência |
|-------|------|------|-------------------|-----------------|-------------------|
| 1 | Coletar cabeçalhos do e-mail suspeito | Automatizada | `scripts/email/extrair_headers.py` | ID do e-mail | Arquivo JSON com cabeçalhos |
| 2 | Analisar reputação do hash do anexo | Automatizada | `scripts/analise/hash_virustotal.py` | Hash extraído do anexo | Score e reputação |
| 3 | Bloquear IP/domínio no firewall | Automatizada | `scripts/firewall/bloquear_ip.sh` | IP/domínio extraído dos headers | Confirmação via log |
| 4 | Notificar usuários afetados | Automatizada | `scripts/notificacao/enviar_email.sh` | Lista de usuários afetados | E-mail enviado com instruções |
| 5 | Atualizar incident ticket e registrar ações | Manual | SIEM / Plataforma SOAR | Logs dos passos anteriores | Incidente fechado com log completo |

## 🔄 Diagrama Visual (Fluxo SOAR)

```
[ DETECÇÃO ]
     ↓
[ Extrair headers e IOC ]
     ↓
[ Verificar reputação IOC ]
     ↓
┌───────────────┐
     ↓         ↓
[ IOC confiável ] [ IOC malicioso ]
     ↓         ↓
[ Encerrar ]  [ Bloquear IP ]
              ↓
         [ Notificar usuários ]
              ↓
         [ Registrar no SIEM ]
```

## ⚙️ Scripts (Exemplos)

### 🔹 `extrair_headers.py`

```python
import email
from email import policy
from sys import argv

with open(argv[1], 'rb') as f:
    msg = email.message_from_binary_file(f, policy=policy.default)

print("From:", msg['From'])
print("To:", msg['To'])
print("Subject:", msg['Subject'])
print("Received headers:", msg.get_all('Received'))
```

### 🔹 `hash_virustotal.py`

```python
import requests, sys

API_KEY = 'SUA_API_KEY'
file_hash = sys.argv[1]

url = f"https://www.virustotal.com/api/v3/files/{file_hash}"
headers = {"x-apikey": API_KEY}

r = requests.get(url, headers=headers)
data = r.json()

print("Reputação:", data['data']['attributes']['reputation'])
```

### 🔹 `bloquear_ip.sh`

```bash
#!/bin/bash
IP=$1

echo "Bloqueando IP: $IP"
iptables -A INPUT -s $IP -j DROP
logger "IP $IP bloqueado automaticamente por playbook"
```

### 🔹 `enviar_email.sh`

```bash
#!/bin/bash
USUARIO=$1
ASSUNTO="Alerta de Segurança: Phishing Detectado"
MENSAGEM="Você recebeu um e-mail malicioso. Não clique no anexo."

echo "$MENSAGEM" | mail -s "$ASSUNTO" "$USUARIO"
```

## 📦 Artefatos e Outputs

- Log de execução dos scripts
- IOC extraído: IP, domínio, hash
- JSON com reputação
- Confirmação de bloqueio no firewall
- Registro no SIEM

## 📘 Finalização e Auditoria

- Incidente fechado com status: **Mitigado**
- Scripts executados registrados no log
- Evidência capturada anexada ao ticket
- Possível ação corretiva: reforçar filtros no gateway

## ✅ Pronto para integrar com um SOAR como:

| Plataforma | Integração via |
|------------|----------------|
| Shuffle | API + Python |
| TheHive + Cortex | Analyzer |
| IBM Resilient | Script Node |
| XSOAR | Task e Integration |

**Desafio:**
- Criar um playbook real baseado nesse modelo
- Adaptar scripts com argumentos dinâmicos
- Rodar os scripts localmente ou via orquestrador simulado
- Apresentar o caso + log + evidência