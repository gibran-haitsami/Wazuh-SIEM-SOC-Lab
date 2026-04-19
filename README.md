# 🛡️ Wazuh SIEM & SOC Automation Lab

## 📌 Project Overview
Proyek ini mendemonstrasikan implementasi **Wazuh SIEM** untuk monitoring keamanan terpusat. Lab ini mencakup instalasi manager pada infrastruktur dengan sumber daya terbatas (RAM 2GB), integrasi endpoint Windows, serta simulasi serangan nyata untuk memvalidasi kemampuan deteksi ancaman secara real-time.

---

## 🏗️ Infrastructure & Topology
* **SIEM Manager:** Ubuntu Server 22.04 (IP: 192.168.100.10)
  * *Resource Optimization:* Menggunakan Swap 5GB untuk mendukung kestabilan servis Wazuh pada RAM 2GB.
* **Endpoint (Victim):** Windows 11 (Wazuh Agent)
* **Attacker Machine:** Kali Linux (Penetration Testing Tools)

---

## 🛠️ Implementation Steps

### 1. Wazuh Manager Deployment
Instalasi dilakukan menggunakan skrip otomasi Wazuh dengan modifikasi untuk melewati pengecekan hardware karena keterbatasan resource:
```bash
# Bypass RAM check and Install
curl -sO [https://packages.wazuh.com/4.7/wazuh-install.sh](https://packages.wazuh.com/4.7/wazuh-install.sh)
sudo bash wazuh-install.sh -a -i