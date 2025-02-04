# Windows10Scripts
Usefull Windows 10 Scripts

/////////////////////////////////

# Disable Sharing and Data Collection in Windows 10

This PowerShell script disables various Windows 10 features that share data, sync settings, or allow network-based sharing.

# What Does This Script Do?
- Disables Telemetry: Prevents Windows 10 from sending system usage data to Microsoft.
- Disables Sync Settings: Stops syncing user preferences, passwords, and settings across devices.
- Disables Network File Sharing: Blocks file and printer sharing over the local network.
- Disables Bluetooth Sharing: Prevents file sharing via Bluetooth.
- Disables Automatic File Sharing: Stops Windows from automatically sharing files and printers over the network.
- Disables App & Store Sync: Prevents app and web data synchronization across devices.
- This script helps minimize data sharing on Windows 10 but may affect certain services or apps that rely on these features. Let me know if you need further modifications! 🚀

## Features Disabled:
- **Telemetry & Data Collection**: Prevents Windows from sending usage data to Microsoft.
- **Sync Settings**: Stops syncing user preferences, passwords, and configurations across devices.
- **File and Printer Sharing**: Blocks file and printer sharing over the network.
- **Bluetooth Sharing**: Disables Bluetooth file sharing.
- **Auto Network Sharing**: Prevents Windows from automatically sharing files and printers.
- **Windows Store & App Sync**: Disables Windows Store automatic downloads and app sync.

## 🚀 How to Use
1. **Open PowerShell as Administrator**:
   - Right-click the Start button and select **"Windows PowerShell (Admin)"**.

2. **Run the Script**:
   - Copy and paste the script into PowerShell and press **Enter**.

## 📜 PowerShell Script

```powershell
# Disable Telemetry and Data Collection
Set-ItemProperty -Path "HKLM:\Software\Policies\Microsoft\Windows\DataCollection" -Name "AllowTelemetry" -Value 0 -Force

# Disable Sync Settings with Microsoft Account
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\SettingSync\" -Name "AllowSync" -Value 0

# Disable File and Printer Sharing over Network
Set-NetFirewallRule -DisplayGroup "File and Printer Sharing" -Enabled False

# Disable Windows Password and Settings Sync
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\CloudStore" -Name "Enabled" -Value 0

# Disable Bluetooth File Sharing
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Bluetooth" -Name "AllowSharing" -Value 0

# Disable Network Sharing
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters" -Name "AutoShareServer" -Value 0
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters" -Name "AutoShareWks" -Value 0

# Disable Windows Store Auto Download (if enabled)
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\WindowsStore" -Name "AutoDownload" -Value 0

# Disable App and Web Sync
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\SettingSync" -Name "AllowAppSync" -Value 0
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\SettingSync" -Name "AllowWebSync" -Value 0

/////////////////////////////////////

⚠️ Important Notes
This script modifies system settings that may affect Windows functionality.
Some applications or network services may require these features to work correctly.
Always create a System Restore Point before making changes.

📝 License
This script is provided under the MIT License. Feel free to modify and share it. 🚀
