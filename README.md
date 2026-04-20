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

```bash
curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh
sudo bash wazuh-install.sh -a -i
```
---

### Installation Result

![Wazuh Installation](Wazuh_install.png)`

## 2. Endpoint Configuration (Windows Agent Connection)

Setelah **Wazuh Manager** berhasil diinstal, langkah berikutnya adalah menghubungkan endpoint Windows ke server agar log keamanan dapat dikirim dan dianalisis oleh Wazuh SIEM.

### Installation Process

1. Unduh **Wazuh Agent installer (.msi)** dari dashboard Wazuh.
2. Jalankan installer tersebut pada mesin Windows.
3. Masukkan IP Address dari **Wazuh Manager** berikut:

```bash
192.168.100.10
Selesaikan proses instalasi hingga agent berhasil terpasang.
Start Wazuh Agent Service

Buka PowerShell sebagai Administrator, kemudian jalankan perintah berikut untuk mengaktifkan service Wazuh Agent.
```bash
NET START Wazuh
```
Perintah ini akan memulai service agent sehingga endpoint Windows mulai mengirimkan log keamanan ke server Wazuh.

Verification Result

Setelah agent aktif, buka Dashboard Wazuh → Agents untuk memastikan endpoint telah berhasil terhubung.

Indikator keberhasilan:

Nama komputer Windows muncul pada daftar agent
Status agent menunjukkan Active (warna hijau)

Screenshot hasil koneksi agent:
![agent](agent_activet.png)`
