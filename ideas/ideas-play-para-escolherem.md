



## 🎯 **Playbook 1: Resposta a Ataque Living-off-the-Land com PowerShell**

| Campo | Valor |
|-------|-------|
| **Nome do Playbook** | Detecção e Resposta a PowerShell Malicioso Fileless |
| **MITRE ID** | T1059.001 (PowerShell) + T1055 (Process Injection) |
| **Tática** | Execution + Defense Evasion |
| **Vetor de Entrada** | PowerShell obfuscado via macro do Office |
| **Ferramentas** | EDR, SIEM, PowerShell ISE, Sysmon, VirusTotal, Memory Dump |


**Por que é complexo:** Ataques fileless são difíceis de detectar, exigem análise de comportamento, desobfuscação de código e correlação temporal de eventos.

---

## 🎯 **Playbook 2: Resposta a Lateral Movement via Kerberoasting**

| Campo | Valor |
|-------|-------|
| **Nome do Playbook** | Detecção e Mitigação de Kerberoasting em Active Directory |
| **MITRE ID** | T1558.003 (Kerberoasting) |
| **Tática** | Credential Access + Lateral Movement |
| **Vetor de Entrada** | Conta comprometida solicitando TGS para SPNs |
| **Ferramentas** | Windows Event Log, PowerShell, LDAP Query, Group Policy |

**Por que é complexo:** Requer conhecimento profundo de Kerberos, análise de logs do AD, correlação de eventos de autenticação e remediação sem impactar serviços.

---

## 🎯 **Playbook 3: Resposta a Supply Chain Attack via Package Malicioso**

| Campo | Valor |
|-------|-------|
| **Nome do Playbook** | Detecção de Dependency Confusion e Typosquatting |
| **MITRE ID** | T1195.002 (Compromise Software Supply Chain) |
| **Tática** | Initial Access |
| **Vetor de Entrada** | Package malicioso em repositório público (npm/pip) |
| **Ferramentas** | SBOM Scanner, Package Registry API, Git Analysis, CI/CD Logs |

**Por que é complexo:** Envolve análise de dependências, versionamento, análise estática de código e impacto em toda a pipeline de desenvolvimento.

---

## 🎯 **Playbook 4: Resposta a Advanced Persistent Threat (APT) Multi-Stage**

| Campo | Valor |
|-------|-------|
| **Nome do Playbook** | Caça e Erradicação de APT com C2 Encryption |
| **MITRE ID** | T1071.001 (Web Protocols) + T1573 (Encrypted Channel) |
| **Tática** | Command and Control + Persistence |
| **Vetor de Entrada** | Backdoor persistente com comunicação HTTPS |
| **Ferramentas** | Network Analysis, SSL/TLS Inspection, Memory Forensics, Timeline Analysis |

**Por que é complexo:** Requer análise de tráfego criptografado, correlação temporal, threat hunting proativo e erradicação completa sem alertar o atacante.

---

## 🎯 **Playbook 5: Resposta a Container Escape e Privilege Escalation**

| Campo | Valor |
|-------|-------|
| **Nome do Playbook** | Detecção de Container Breakout em Kubernetes |
| **MITRE ID** | T1611 (Escape to Host) + T1068 (Exploitation for Privilege Escalation) |
| **Tática** | Privilege Escalation + Defense Evasion |
| **Vetor de Entrada** | Container comprometido explorando vulnerabilidade do kernel |
| **Ferramentas** | Falco, kubectl, Docker API, Syscall Monitoring, Runtime Security |

**Por que é complexo:** Ambiente cloud-native, análise de syscalls, conhecimento de Kubernetes security e orquestração de resposta em cluster distribuído.

---


**Scripts envolvidos seriam:**
- Análise de certificados SSL suspeitos
- Correlação temporal de eventos multi-fonte
- Detecção de beaconing patterns
- Memory dump analysis
- Network traffic decryption
- IOC generation automático
- Threat intelligence correlation

