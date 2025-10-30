# ADB Commands Reference Guide

## Device Connection & Management

```bash
# List all connected devices
adb devices

# Switch device to TCP/IP mode on port 5555 (for wireless debugging)
adb tcpip 5555

# Switch device back to USB mode
adb usb

# Connect to device over network
adb connect ip:port

# Disconnect from network device
adb disconnect
```

## Server Management

```bash
# Start ADB server on host computer
adb start-server

# Stop ADB server on host computer
adb kill-server
```

## Device Control

```bash
# Restart device normally
adb reboot

# Restart device into bootloader/fastboot mode
adb reboot bootloader

# Restart device into recovery mode
adb reboot recovery

# Shutdown device (power off)
adb shell reboot -p
```

## Shell Access

```bash
# Open interactive shell on device
adb shell
```

## App Installation & Management

```bash
# Install APK file to device
adb install app.apk

# Reinstall APK (replace existing app)
adb install -r app.apk

# Uninstall user-installed app by package name
adb uninstall com.package.name

# Uninstall user-installed app but keep data and cache
adb uninstall -k com.package.name

# Uninstall system app
adb shell pm uninstall --user 0 com.package.name

# Uninstall system app but keep data and cache
adb shell pm uninstall -k --user 0 com.package.name

# Clear app data and cache
adb shell pm clear com.package.name

# Disable system package
adb shell pm disable-user --user 0 com.package.name

# Enable disabled package
adb shell pm enable com.package.name

# Uninstall all disabled apps
adb shell 'pm list packages -d' | grep 'package:' | cut -c9- | tr -d '\r' | xargs -n1 -t adb shell pm uninstall --user 0

# Re-install removed system packages
adb shell cmd package install-existing com.package.name
```

## Package Information

```bash
# List all installed packages
adb shell pm list packages

# List package that contains given name
adb shell pm list packages chrome

# List only system packages
adb shell pm list packages -s

# List only third-party packages
adb shell pm list packages -3

# List disable apps
adb shell pm list packages -d

# Show installation path of specific package
adb shell pm path com.package.name
```

## APPOPS

```bash
# View app permission
adb shell cmd appops get com.package.name

# Restrict specific permission
adb shell cmd appops set com.package.name PERMISSION_NAME ignore | deny | default

# Example: Restrict facebook from running on background
adb shell cmd appops set com.facebook.katana RUN_IN_BACKGROUND ignore
 
> Note: `deny` is aggressive and throws exception which might crash app
> `ignore` just drop the request silenetly

```

## App State Management

```bash
# Disable app for current user
adb shell pm disable-user com.package.name

# Enable previously disabled app
adb shell pm enable com.package.name
```
