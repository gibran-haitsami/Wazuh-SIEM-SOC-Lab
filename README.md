# 🛡️ Wazuh SIEM & SOC Automation Lab Implementation

## 📝 Project Overview
Proyek ini mendemonstrasikan implementasi **Wazuh SIEM** tingkat enterprise untuk monitoring keamanan terpusat. Fokus utama lab ini adalah mengoptimalkan kinerja SIEM pada perangkat dengan *low-resource* serta memvalidasi deteksi ancaman nyata menggunakan kerangka kerja **MITRE ATT&CK**.

---

## 🏗️ Lab Environment & Infrastructure
Lingkungan lab dibangun menggunakan virtualisasi terisolasi untuk simulasi serangan yang aman:

| Component | Operating System | Role | Specifications |
| :--- | :--- | :--- | :--- |
| **SIEM Manager** | Ubuntu Server 22.04 LTS | Central Log Analysis | RAM 2GB + 5GB Swap |
| **Endpoint Client** | Windows 11 Pro | Victim Machine | Wazuh Agent Installed |
| **Attacker Node** | Kali Linux 2024.1 | Threat Actor | Hydra, Nmap, Metasploit |

---

## 🛠️ Implementation Steps

### 1. Wazuh Manager Deployment (Server Side)
Langkah awal adalah instalasi manager. Karena keterbatasan RAM, dilakukan optimasi melalui bypass hardware check:

**Command Instalasi:**
```bash
curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh && sudo bash wazuh-install.sh -a -i
