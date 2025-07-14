# Plataforma Acadêmica de Resposta a Incidentes Baseada em SOAR

## Visão Geral

Os alunos irão:

- Modelar ataques com MITRE ATT&CK
- Desenvolver Playbooks com etapas bem definidas
- Acoplar Scripts Automatizados em cada fase
- Orquestrar ações como um verdadeiro SOAR faria

## O que é um SOAR?

SOAR (Security Orchestration, Automation and Response) é uma plataforma que:

- Orquestra diferentes ferramentas de segurança
- Automatiza respostas (execução de scripts, bloqueios, notificações)
- Apresenta fluxos de trabalho (playbooks visuais)
- Gera logs, relatórios e auditoria de todas as ações

### Ferramentas SOAR reais:

- Cortex XSOAR (Palo Alto)
- IBM Resilient
- TheHive + Cortex (open source)
- Splunk SOAR
- Shuffle (open source e ideal para laboratório)

## Estrutura Completa do Projeto

### 1. Banco de Playbooks (Baseado em MITRE)

Cada playbook conterá:

- MITRE ID (ex: T1059.001)
- Descrição do ataque
- Vetor de entrada
- Diagrama de fluxo do ataque
- Etapas do Playbook
- Scripts automatizáveis por etapa
- Ferramentas integráveis (SIEM, EDR, Email, Firewall)
- Outputs esperados

**Formato:**
- Markdown (.md),PDF,WORD.... 
- Com links para scripts e artefatos

### 2. Modelo de Playbook Estilo SOAR

```yaml
playbook_id: PB-001
nome: "Resposta a Phishing com Anexo"
mitre_id: T1204.002
vetor: Email
etapas:
  - nome: "Analisar cabeçalhos de e-mail"
    ação: "Executar script"
    script: scripts/analisa_headers.py
    entrada: email_id
    saída: header_info
  - nome: "Consultar IOC"
    ação: "API para VirusTotal"
    script: scripts/consultar_vt.py
    entrada: hash_do_anexo
    saída: reputação
  - nome: "Bloquear IP"
    ação: "Enviar comando ao firewall"
    script: scripts/firewall_block.sh
    entrada: ip
    saída: confirmação
  - nome: "Notificar usuários"
    ação: "Envio de e-mail"
    script: scripts/notifica_usuarios.sh
```

### 3. Repositório de Scripts (Automação)

Organizado por função e linguagem:

```
/scripts/
├── rede/
│   └── firewall_block.sh
├── email/
│   └── analisa_headers.py
├── edr/
│   └── isola_maquina.ps1
├── notificacoes/
│   └── notifica_usuarios.sh
```

**Scripts devem:**
- Ser reutilizáveis
- Ter logs de execução
- Ser comentados
- Receber parâmetros via linha de comando ou JSON

### 4. Orquestração dos Fluxos (SOAR Open Source)

Para praticar orquestração real:

#### Opção Open Source:
- **Shuffle** — Ferramenta visual, com nodes tipo Node-RED, ideal para simular playbooks SOAR com APIs e scripts
- **TheHive + Cortex** — Plataforma de investigação + automação real, com casos, alertas, tarefas e ações automatizadas

#### Como usar:
- Criar cada etapa do playbook como um "nó"
- Conectar os nós (condições, saídas, logs)
- Integrar com APIs reais ou simuladas (Ex: VT, AbuseIPDB, E-mail)
- Monitorar a execução automatizada do início ao fim

### 5. Matriz de Correlação (MITRE → Fase SOAR)

| MITRE Tática | Técnica (ID) | Evento Detectado | Ação SOAR | Script | Ferramenta |
|--------------|--------------|------------------|-----------|---------|------------|
| Execution | T1059.001 | Powershell suspeito via EDR | Isolar máquina | isola_maquina.ps1 | EDR API (CrowdStrike) |
| Defense Evasion | T1070.004 | Limpando logs | Ativar monitoramento de logs | reativa_logs.ps1 | Sysmon |
| Impact | T1486 | Criptografia de arquivos | Interromper processo + isolar | mata_processo.py | SIEM + EDR |

## Fluxo Geral da Aula / Atividade Prática

## 1: Escolha de um ataque
- Cada grupo escolhe um tipo de ataque
- Mapeia com MITRE
- Cria um playbook (etapas + ações)

### 2: Automação
- Desenvolvimento ou ajuste dos scripts
- Integração com fluxo (Shuffle ou simulado)

### 3: Execução + Documentação
- Rodar os playbooks
- Gerar relatório de resposta
- Apresentar (fase por fase) com justificativa

## Entregas dos Alunos

- ✅ Playbook .md,pdf,word com todas as etapas
- ✅ Scripts funcionais e comentados
- ✅ Diagrama de fluxo (pode ser em Draw.io, Lucidchart, ou Shuffle)
- ✅ Relatório de execução (JSON ou PDF)
