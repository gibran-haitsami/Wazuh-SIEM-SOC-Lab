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
Troubleshooting: Mengatasi konflik port 443 dengan menonaktifkan layanan web server apache2 agar dashboard bisa diakses.

2. Endpoint Configuration (Windows Agent)
Deployment agen pada Windows dilakukan melalui langkah berikut:

Mendaftarkan agen ke IP Manager 192.168.100.10.

Menjalankan perintah PowerShell (Administrator) untuk instalasi agent.

Memastikan service Wazuh berjalan dengan perintah NET START Wazuh.

⚔️ Security Simulation & Analysis
A. Brute Force Attack (SSH)
Simulasi serangan menebak kata sandi menggunakan tool Hydra dari Kali Linux untuk menguji respon SIEM.

Command: hydra -l gibranee -p 123456 ssh://192.168.100.10 -t 4

Detection: Wazuh berhasil mendeteksi kegagalan otentikasi berulang (Rule 5760) dan memetakannya ke taktik Credential Access pada framework MITRE ATT&CK.

B. Malware Detection Test (EICAR)
Pengujian fitur EDR (Endpoint Detection and Response) menggunakan standar file EICAR.

Hasil: Wazuh mencatat aktivitas pembuatan file mencurigakan melalui modul File Integrity Monitoring (FIM) dan memberikan alert level tinggi secara instan.
📊 Detection Results & Log AnalysisTabel di bawah ini menunjukkan log asli yang berhasil ditangkap oleh Wazuh Manager selama simulasi:TimeEvent DescriptionLevelRule IDTactic (MITRE ATT&CK)Apr 20, 03:38Windows Application Error960602-Apr 20, 03:25sshd: authentication failed55760Credential AccessApr 20, 03:17SCA: Windows Benchmark < 50%719004HardeningApr 20, 03:16Windows Logon Success360106

Siap, Bro! Saya mengerti sepenuhnya. Saya sudah mengganti nama file gambarnya di dalam kode agar terlihat lebih profesional (bukan sekadar angka 1 atau 2).1. Instruksi Penting (Ubah Nama File Foto)Sebelum kamu upload, ubah dulu nama file screenshot di komputermu menjadi:Gambar Dashboard utama: wazuh-dashboard-overview.pngGambar Tabel Log/Alerts: wazuh-security-alerts.png(Pastikan ekstensinya .png. Kalau filemu .jpg, ganti tulisan .png di bawah menjadi .jpg).2. Kode Final (Copy Semua Dalam Kotak Ini)Silakan Copy semua teks di bawah ini dan Paste ke Notepad++. Jangan ada yang tertinggal dari baris pertama sampai terakhir.Markdown# 🛡️ Wazuh SIEM & SOC Automation Lab

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
Troubleshooting: Mengatasi konflik port 443 dengan menonaktifkan layanan web server apache2 agar dashboard bisa diakses.2. Endpoint Configuration (Windows Agent)Deployment agen pada Windows dilakukan melalui langkah berikut:Mendaftarkan agen ke IP Manager 192.168.100.10.Menjalankan perintah PowerShell (Administrator) untuk instalasi agent.Memastikan service Wazuh berjalan dengan perintah NET START Wazuh.⚔️ Security Simulation & AnalysisA. Brute Force Attack (SSH)Simulasi serangan menebak kata sandi menggunakan tool Hydra dari Kali Linux untuk menguji respon SIEM.Command: hydra -l gibranee -p 123456 ssh://192.168.100.10 -t 4Detection: Wazuh berhasil mendeteksi kegagalan otentikasi berulang (Rule 5760) dan memetakannya ke taktik Credential Access pada framework MITRE ATT&CK.B. Malware Detection Test (EICAR)Pengujian fitur EDR (Endpoint Detection and Response) menggunakan standar file EICAR.Hasil: Wazuh mencatat aktivitas pembuatan file mencurigakan melalui modul File Integrity Monitoring (FIM) dan memberikan alert level tinggi secara instan.📊 Detection Results & Log AnalysisTabel di bawah ini menunjukkan log asli yang berhasil ditangkap oleh Wazuh Manager selama simulasi:TimeEvent DescriptionLevelRule IDTactic (MITRE ATT&CK)Apr 20, 03:38Windows Application Error960602-Apr 20, 03:25sshd: authentication failed55760Credential AccessApr 20, 03:17SCA: Windows Benchmark < 50%719004HardeningApr 20, 03:16Windows Logon Success360106Initial Access🖼️ Proof of Concept (Screenshots)1. Wazuh Security Dashboard OverviewMenunjukkan ringkasan aktivitas keamanan, statistik alert, dan grafik integrasi MITRE ATT&CK yang terpantau pada dashboard utama.2. Security Alerts & Attack Detection DetailDokumentasi log saat sistem mendeteksi kegagalan otentikasi (Brute Force). Terlihat Rule ID 5760 (SSH Auth Failed) yang dipicu oleh simulasi serangan.

.

🚀 Conclusion
Optimization: Berhasil menjalankan SIEM Enterprise pada perangkat RAM 2GB dengan teknik Swap Memory.

Real-time Monitoring: Wazuh terbukti efektif menangkap aktivitas mencurigakan (Brute Force & Malware) secara instan.

Security Hardening: Modul SCA memberikan visibilitas terhadap konfigurasi OS yang lemah untuk diperbaiki lebih lanjut sesuai standar CIS.

Author: [Gibran Hait Sami]

Date: April 2026

Tools Used: Wazuh SIEM, VirtualBox, Kali Linux, PowerShell, Hydra.