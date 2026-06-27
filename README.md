# Windows System Info Extractor ⚡

![OS](https://img.shields.io/badge/OS-Windows-blue)
![Script](https://img.shields.io/badge/Script-Batch%20%2F%20PowerShell-green)
![Dependencies](https://img.shields.io/badge/Dependencies-None-success)

A lightning-fast, zero-dependency Batch script that instantly generates a comprehensive hardware and system information report. 

This tool is designed for quick system audits, IT troubleshooting, and network management without requiring administrative installations or heavy third-party software.

## ✨ Features

* **Instant Execution:** Optimized to bypass heavy WMI queries (like Windows Activation checks) to ensure the script runs in under a second.
* **Hybrid Execution:** Uses a standard `.bat` entry point for simple "double-click" execution while leveraging PowerShell under the hood for accurate hardware querying.
* **Clean Output:** Generates a clearly formatted `.txt` file named dynamically after the host machine (`PC_Info_COMPUTERNAME.txt`).

## 📊 What It Captures

The script extracts the following data points:
* **System:** Computer Name, Logged-in User, System Uptime, IP Address (IPv4)
* **Hardware:** Device Model, BIOS Serial Number, BIOS Version
* **Compute:** CPU Model, Total RAM (Rounded to GB), GPU(s)
* **Storage:** Physical Disk mapping (Name, Type [SSD/HDD/NVMe], and Size in GB)
* **OS:** Windows Version and Edition

## 🚀 Usage

1. Download or clone this repository.
2. Double-click the `Get_PC_Info.bat` file.
3. A command prompt will flash briefly.
4. A new file named `PC_Info_[Your-Computer-Name].txt` will be generated in the same directory.

## 🛠️ Under the Hood

Older batch commands (`wmic`) are deprecated and often struggle to accurately identify modern hardware like NVMe drives or distinguish between integrated and dedicated GPUs. 

This script solves that by wrapping a PowerShell command (`Get-CimInstance` and `Get-PhysicalDisk`) inside a standard batch executable. It automatically bypasses local execution policies (`-ExecutionPolicy Bypass`) temporarily for the script's run, ensuring it works on locked-down enterprise machines without throwing permission errors.
