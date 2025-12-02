# PDF Preview Fix for Windows

![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=for-the-badge&logo=powershell&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active-success?style=for-the-badge)

## Overview

Fix Windows file preview issues where PDFs show the warning: *"The file you are trying to preview could harm your computer. If you trust the file and its origin, you can open it to view the content."*

This solution unlocks blocked PDF files in bulk using PowerShell, enabling instant preview without manually unblocking each file.

---

## Prerequisites

![PowerShell Version](https://img.shields.io/badge/PowerShell-5.1%2B-blue?style=flat-square)
![Admin Rights](https://img.shields.io/badge/Admin%20Rights-Required-red?style=flat-square)

- Windows 10/11
- PowerShell 5.1 or higher
- Administrator privileges

---

## Quick Start

### Step 1: Open PowerShell

> [!CAUTION]
> **Run PowerShell in Administrator Mode**
> 
> Press `Windows + X` and select **"Windows PowerShell (Admin)"** or **"Terminal (Admin)"**

### Step 2: Navigate to Target Folder

Navigate to the folder where your PDFs are located:

```powershell
cd "C:\path\to\your\folder"
```

**Example:**
```powershell
cd "C:\Users\YourName\Documents\PDFs"
```

### Step 3: Unblock All PDFs

Run this command to unlock all PDFs recursively:

```powershell
Get-ChildItem -Path . -Recurse -Filter *.pdf | Unblock-File
```

### Step 4: Refresh File Explorer

Close and reopen File Explorer to see the changes take effect.

---

## Alternative Commands

### Unblock All Files (Not Just PDFs)

```powershell
Get-ChildItem -Path . -Recurse | Unblock-File
```

### Unblock Files in Specific Directory Only (Non-Recursive)

```powershell
Get-ChildItem -Path . -Filter *.pdf | Unblock-File
```

### Unblock a Single File

```powershell
Unblock-File -Path "C:\path\to\file.pdf"
```

---

## Permanent Solution

To prevent Windows from blocking downloaded files in the future:

1. Open **Registry Editor** (`regedit`)
2. Navigate to:
   ```
   HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Attachments
   ```
3. Create a new **DWORD (32-bit) Value**:
   - Name: `SaveZoneInformation`
   - Value: `1`
4. Restart File Explorer

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| **"Access Denied"** | Ensure PowerShell is running as Administrator |
| **Command not found** | Verify PowerShell version is 5.1+ with `$PSVersionTable` |
| **Preview still blocked** | Restart File Explorer or reboot the system |
| **Registry key missing** | Create the `Attachments` key manually under `Policies` |

---

## License

![MIT License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)

This project is licensed under the MIT License - feel free to use and modify as needed.

---

## Acknowledgments

Thanks to the Windows community for discovering these registry tweaks and PowerShell solutions!

---

<div align="center">

<img src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExYmkwcTA1bzNlMTc2bmNkb3NzYWZ0bDB6dG14YjdsbWo0bzJmbXg1ZiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xWMPYx55WNhX136T0V/giphy.gif" width="600">

**Happy Previewing!**

</div>
