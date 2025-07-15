```markdown
# Playbooks de Resposta a Incidentes
##Desafio:

- Criar um playbook real baseado nesse modelo
- Adaptar scripts com argumentos dinâmicos
- Rodar os scripts localmente ou via orquestrador simulado
- Apresentar o caso + log + evidência
- Diagrama Visual (Fluxo Playbook)

---

## Mesa 1

**Membros:**
- Gabriel Braga
- Helena Albano
- João Pedro
- Lucas Silva
- Júlio Onofre
- Marcos Paulo
- Victor Cássio

### 🎯 **Playbook 4: Resposta a Advanced Persistent Threat (APT) Multi-Stage**

| Campo | Valor |
|-------|-------|
| **Nome do Playbook** | Caça e Erradicação de APT com C2 Encryption |
| **MITRE ID** | T1071.001 (Web Protocols) + T1573 (Encrypted Channel) |
| **Tática** | Command and Control + Persistence |
| **Vetor de Entrada** | Backdoor persistente com comunicação HTTPS |
| **Ferramentas** | Network Analysis, SSL/TLS Inspection, Memory Forensics, Timeline Analysis |

**Por que é complexo:** Requer análise de tráfego criptografado, correlação temporal, threat hunting proativo e erradicação completa sem alertar o atacante.

---

## Mesa 2

**Membros:**
- Jéssica
- Ana Emylli
- Gabriel Souza
- Maria Eduarda
- Marcos Antônio
- Lorena Lobo
- Sofia

### 🎯 **Playbook 2: Resposta a Lateral Movement via Kerberoasting**

| Campo | Valor |
|-------|-------|
| **Nome do Playbook** | Detecção e Mitigação de Kerberoasting em Active Directory |
| **MITRE ID** | T1558.003 (Kerberoasting) |
| **Tática** | Credential Access + Lateral Movement |
| **Vetor de Entrada** | Conta comprometida solicitando TGS para SPNs |
| **Ferramentas** | Windows Event Log, PowerShell, LDAP Query, Group Policy |

**Por que é complexo:** Requer conhecimento profundo de Kerberos, análise de logs do AD, correlação de eventos de autenticação e remediação sem impactar serviços.

---

## Mesa 3

**Membros:**
- Mirellen
- Viviane 
- Erica
- Mariana
- Lucas
- Jonh (talvez)
- Gabriele (talvez)
- Aline

### 🎯 **Playbook 1: Resposta a Ataque Living-off-the-Land com PowerShell**

| Campo | Valor |
|-------|-------|
| **Nome do Playbook** | Detecção e Resposta a PowerShell Malicioso Fileless |
| **MITRE ID** | T1059.001 (PowerShell) + T1055 (Process Injection) |
| **Tática** | Execution + Defense Evasion |
| **Vetor de Entrada** | PowerShell obfuscado via macro do Office |
| **Ferramentas** | EDR, SIEM, PowerShell ISE, Sysmon, VirusTotal, Memory Dump |

**Por que é complexo:** Ataques fileless são difíceis de detectar, exigem análise de comportamento, desobfuscação de código e correlação temporal de eventos.

---

## Mesa 4

**Membros:**
- Cássio Costa
- Ian Lima
- Júlia Andrade
- Raphael Tavares
- Maria Júlia Pina
- Yasmin Athougia
- Vitor Vernec

---

## 📚 Recursos Adicionais

### Github de Playbooks:
- [Phantom Cyber Playbooks](https://github.com/phantomcyber/playbooks/tree/6.4)
- [The IR Gurus Playbooks](https://github.com/TheIRGurus/Playbooks)
```
