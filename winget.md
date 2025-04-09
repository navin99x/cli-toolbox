# winget — Windows Package Manager

> 🧰 Microsoft's official command-line package manager for Windows to **install**, **upgrade**, and **manage** applications quickly and efficiently.

---

## Installation

✅ It comes pre-insatlled on Windows 10 (version 1809+) and Windows 11.  

**To check if you have it:**

```bash
winget --version
```

❌ If it is not installed, then simply install [App Installer](https://apps.microsoft.com/detail/9nblggh4nns1) from the Microsoft Store.


## Basic Usages

```powershell
winget  [<command>] [<options>]
```

## Searching application

```powershell
# Search for an application
winget search chrome

# Get detailed info about package
winget show Google.Chrome
```

## Filter search

```powershell
# Search by name
winget search --name chrome

# Search by id
winget search --id Google.Chrome

# Search by alias/nickname
winget search --moniker browser

# Limit search results
winget search chrome -n 3
```

## Basic Installation

```powershell
winget install -id=Google.Chrome -e
```
> `-e` flags ensure app with exact id is installed. 

## Installation options

```powershell
--interactive               # Manual configuration during install
--silent                    # No UI, no prompts
--version <version>         # Install a specific version
--scope user|machine        # Install for current user or all users
--location D:\Programs      # Custom installation path
--accept-package-agreements # Skip license prompt
--force                     # Reinstall even if already installed
```

**Example:**
```powershell
winget install Git.Git --scope machine --silent --accept-package-agreements
```

## 🔄Managing Application

```powershell
# List installed applications
winget list

# List applications managed by winget
winget list --source winget

# Upgrade a specific application
winget upgrade Microsoft.PowerToys

# Upgrade all applications
winget upgrade --all

# Reset an application
winget reset Microsoft.PowerToys

# Uninstall an application
winget uninstall Microsoft.PowerToys
```

## 🔁Export/Import Configurations

```powershell
# Export installed application
winget export -o apps.json

# Check if import config is valid
winget validate apps.json

# Install application from JSON file
winget import -i apps.json
```

## ⚙️ Configuring winget

```powershell
# View current settings
winget settings

# Open settings file to edit
winget settings --open
```

## 💡 My Use Cases

- 🧼 Quickly clean-install essential dev tools after a format.
- 🚀 Install VS Code, Git, Python, Edge in seconds.
- 🔄 Keep apps up-to-date with one command: `winget upgrade --all`

## 📚 Resources
- 📘[winget GitHub](https://github.com/microsoft/winget-cli)
- 📖[Microsoft Docs](https://learn.microsoft.com/en-us/windows/package-manager/winget/)
- [CommandMasters Guide](https://commandmasters.com/commands/winget-windows/)
- 📦[Package Search](https://winstall.app/) - unofficial but awesome web interface for winget
