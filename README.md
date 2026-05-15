# Feed de Threat Intelligence

![Status](https://img.shields.io/badge/status-ativo-success?style=flat-square)
![Licença](https://img.shields.io/badge/license-MIT-blue?style=flat-square)
![FortiGate](https://img.shields.io/badge/FortiGate-compativel-red?style=flat-square)
![Threat-Intel](https://img.shields.io/badge/threat%20intel-feeds-orange?style=flat-square)

---

## 📌 Visão Geral

Este repositório fornece um **Feed de Threat Intelligence (IoCs)** voltado exclusivamente para integração com soluções **Fortinet FortiGate**.

O objetivo é permitir o bloqueio automático de ameaças conhecidas através de indicadores como:

* 🧬 Hashes de arquivos maliciosos (SHA256)
* 🌐 Endereços IP maliciosos
* 🔗 Domínios maliciosos e infraestrutura C2
* 🖧 Endereços MAC suspeitos
* 📦 Feed unificado (todos os indicadores)

---

## 📂 Estrutura dos Feeds

Os indicadores são separados por tipo para facilitar a integração no FortiGate:

| Arquivo             | Descrição                                        |
| ------------------- | ------------------------------------------------ |
| `hashs-sha256.txt` | Hashes SHA256 de arquivos maliciosos             |
| `ips.txt`           | Endereços IP maliciosos                          |
| `domains.txt`       | Domínios de comando e controle (C2) e maliciosos |
| `macs.txt`          | Endereços MAC suspeitos ou comprometidos         |

Cada linha contém apenas um indicador.

---

## 🔗 URLs dos Feeds (Raw)

Utilize as URLs abaixo diretamente no FortiGate:

```
https://raw.githubusercontent.com/giaosoissomsm/malicious-hash/main/files/hashs-sha256.txt
https://raw.githubusercontent.com/giaosoissomsm/malicious-hash/main/files/ips.txt
https://raw.githubusercontent.com/giaosoissomsm/malicious-hash/main/files/domains.txt
https://raw.githubusercontent.com/giaosoissomsm/malicious-hash/main/files/macs.txt
```

---

## 🛡️ Integração com FortiGate

Os feeds podem ser utilizados como **External Threat Feeds** para bloqueio automático de ameaças em tempo real.

### 🔧 Configuração

1. Acesse o FortiGate

2. Vá em **Security Fabric > External Connectors**

3. Clique em **Create New**

4. Selecione o tipo de feed:

   * Malware Hash Feed → `hashs-sha256.txt`
   * IP Address Feed → `ips.txt`
   * Domain Name Feed → `domains.txt`

5. Configure:

   * **Nome:** `Threat-Intel-Feed`
   * **URI:** Cole a URL raw do GitHub
   * **Intervalo de atualização:** recomendado 5 a 15 minutos

6. Salve a configuração

---

## 🏷️ Categorias Personalizadas

Os feeds podem ser organizados em categorias personalizadas no FortiGate:

* `malware_hashes`
* `c2_infrastructure`
* `botnet_ips`
* `dominios_maliciosos`
* `indicadores_endpoint`

Essas categorias podem ser aplicadas em:

* Políticas de Firewall
* Web Filter
* DNS Filter
* Perfis de AntiVirus
* Regras de Threat Intelligence

---

## 🔥 Exemplo de Uso

Após a integração, o FortiGate poderá:

* Bloquear downloads de arquivos maliciosos por hash
* Impedir acesso a domínios C2 conhecidos
* Bloquear conexões com IPs maliciosos
* Detectar comunicação com infraestrutura de ataque

---

## ⚙️ Atualização e Automação

* Os feeds são atualizados continuamente
* Intervalo recomendado: 15 a 60 minutos
* Compatível com automação via API do FortiGate

---

## 📄 Licença

Este projeto está licenciado sob a licença MIT.
