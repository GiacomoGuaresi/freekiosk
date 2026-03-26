<div align="center">

# 🚀 FreeKiosk Installation Guide

**Complete path from first install to full Device Owner lockdown**

<p>
  <a href="README.md">📚 Docs Home</a> •
  <a href="features-and-modes.md">🎛️ Modes</a> •
  <a href="adb-configuration.md">⌨️ ADB Configuration</a>
</p>

</div>

> [!TIP]
> If you are deploying public-facing tablets, skip directly to Device Owner mode.

---

## 📋 Table of Contents

<div align="center">

| 📖 Section | 🎯 Focus |
|---|---|
| **🚀 Quick Install** | Basic mode setup without PC |
| **🏢 Advanced Install** | Device Owner full lockdown |
| **🚨 Troubleshooting** | Common issues and solutions |
| **🔧 Remove Device Owner** | How to uninstall properly |

</div>

---

## 🚀 Quick Install (Basic Mode)

Perfect for testing, personal use, or when you don't have a PC available.

### 📋 Requirements

<div align="center">

| ⚙️ Requirement | 📋 Details |
|---|---|
| **📱 Android Tablet** | Version 8.0+ (API 26+) |
| **📥 APK File** | Download from [Releases](https://github.com/rushb-fr/freekiosk/releases) |
| **🔐 PIN Code** | Choose 4-6 digits for security |

</div>

### 🔧 Installation Steps

<div align="center">

| 📋 Step | 🎯 Action | 📝 Details |
|---|---|---|
| **1️⃣ Download** | Get the APK | From [GitHub Releases](https://github.com/rushb-fr/freekiosk/releases) |
| **2️⃣ Install** | Transfer & Install | USB, email, or direct download |
| **3️⃣ Configure** | Set URL & PIN | 5-tap secret button (bottom-right) |
| **4️⃣ Launch** | Start Kiosk | Tap "Start Kiosk Mode" |

</div>

### 📱 Detailed Instructions

**Step 1: Download APK**
1. Go to [Releases](https://github.com/rushb-fr/freekiosk/releases)
2. Download the latest `FreeKiosk-vX.X.X.apk`
3. Transfer to tablet via USB, email, or direct download

**Step 2: Install**
1. Open the APK file on tablet
2. Allow "Install from unknown sources" if prompted
3. Complete installation

**Step 3: Configure**
1. Open FreeKiosk app
2. Tap 5 times on secret button (default: bottom-right corner)
3. Enter settings with your PIN
4. Set your target URL
5. Configure additional settings as needed

**Step 4: Start Kiosk**
1. Tap "Start Kiosk Mode"
2. Your tablet is now in basic kiosk mode!

> [!WARNING]
> Basic mode allows some system interactions (notifications, back button access in some cases). For complete lockdown, use Device Owner mode.

---

## 🏢 Advanced Install (Device Owner Mode)

For **complete lockdown** with no system interruptions. Perfect for public displays, corporate kiosks, and secure deployments.

### 📋 Requirements

<div align="center">

| ⚙️ Requirement | 📋 Details |
|---|---|
| **📱 Android Tablet** | Version 8.0+ (API 26+) |
| **💻 Computer** | Windows, Mac, or Linux |
| **🔌 USB Cable** | For tablet connection |
| **🛠️ ADB Tool** | Android Debug Bridge (15 MB) |

</div>

### 📥 Step 1: Install ADB

Choose your operating system:

#### 🪟 Windows

<div align="center">

1. Download [SDK Platform Tools](https://dl.google.com/android/repository/platform-tools-latest-windows.zip) (15 MB)
2. Extract to `C:\platform-tools\`
3. Open Command Prompt and navigate to the directory

</div>

#### 🍎 Mac

<div align="center">

**Option A: Homebrew** (recommended)
```bash
brew install android-platform-tools
```

**Option B: Manual**
1. Download [SDK Platform Tools](https://dl.google.com/android/repository/platform-tools-latest-darwin.zip)
2. Extract and add to PATH

</div>

#### 🐧 Linux

<div align="center">

**Ubuntu/Debian:**
```bash
sudo apt install adb
```

**Fedora:**
```bash
sudo dnf install android-tools
```

</div>

### 📱 Step 2: Prepare Tablet

#### 🔐 1. Remove All Accounts

Device Owner requires that **no user accounts** are active on the device. A factory reset is **not** required.

<div align="center">

| 📋 Action | 🎯 Purpose |
|---|---|
| **🗑️ Remove Google Accounts** | Settings → Accounts → Google → Remove |
| **🗑️ Remove Samsung Accounts** | Settings → Accounts → Samsung → Remove |
| **🗑️ Remove Microsoft 365** | Settings → Accounts → Work → Remove |
| **📱 Remove/Disable SIM** | Remove SIM card or disable SIM profile |
| **✅ Verify** | Settings → Accounts should show "No accounts" |

</div>

> [!IMPORTANT]
> You can sign back into all your accounts **after** Device Owner is activated.

> [!NOTE]
> **Fallback**: If the `dpm` command still fails after removing accounts (some devices retain hidden accounts), perform a factory reset: Settings → System → Reset → Factory data reset. After reset, do **not** add any account before activating Device Owner.

#### 🔧 2. Enable USB Debugging

<div align="center">

| 📋 Step | 🎯 Action |
|---|---|
| **1️⃣ Developer Mode** | Settings → About tablet → Tap "Build number" 7 times |
| **2️⃣ USB Debugging** | Settings → System → Developer options → Enable "USB debugging" |

</div>

#### 📥 3. Install FreeKiosk

1. Transfer APK to tablet
2. Install the APK
3. **Do NOT open yet** - wait for Device Owner activation

### 🎯 Step 3: Activate Device Owner

#### 🔌 1. Connect Tablet to PC

<div align="center">

| 📋 Action | 🎯 Details |
|---|---|
| **🔌 Connect USB** | Use USB cable to connect tablet to PC |
| **📱 Allow Debugging** | Check "Always allow from this computer" |
| **✅ Tap Allow** | Accept the USB debugging popup |

</div>

#### 🔍 2. Verify Connection

<div align="center">

**Windows:**
```bash
cd C:\platform-tools
adb devices
```

**Mac/Linux:**
```bash
adb devices
```

**Expected output:**
```
List of devices attached
ABC123XYZ device
```

If you see "unauthorized" → Check tablet screen for popup

</div>

#### 🏢 3. Set Device Owner

<div align="center">

**Run this command:**
```bash
adb shell dpm set-device-owner com.freekiosk/.DeviceAdminReceiver
```

**Expected output:**
```
Success: Device owner set to package com.freekiosk
Active admin set to component {com.freekiosk/com.freekiosk.DeviceAdminReceiver}
```

✅ **Success!** Your tablet is now in Device Owner mode.

</div>

#### 🔄 4. Reboot (Optional)

```bash
adb reboot
```

### 🚀 Step 4: Launch FreeKiosk

<div align="center">

| 📋 Step | 🎯 Action |
|---|---|
| **1️⃣ Open App** | Launch FreeKiosk from app drawer |
| **2️⃣ Configure** | Set URL and PIN in settings |
| **3️⃣ Start Kiosk** | Tap "Start Kiosk Mode" |
| **4️⃣ Complete** | Full lockdown is now active! |

</div>

---

## ⚖️ What's the Difference?

<div align="center">

| 🔒 Feature | 🟢 Basic Mode | 🔴 Device Owner Mode |
|---|---|---|
| **🚪 Kiosk Lockdown** | Partial | Complete |
| **🔔 System Notifications** | Visible | Blocked |
| **📊 Status Bar** | May appear | Hidden |
| **⬅️ Navigation Buttons** | Accessible | Disabled |
| **🏠 Home Button** | May work | Disabled |
| **📱 Recent Apps** | Accessible | Disabled |
| **📱 Samsung Popups** | Can appear | Blocked |
| **🚪 Exit Without PIN** | Possible (long press) | Impossible |
| **🚀 Auto-start on Boot** | Yes | Yes |
| **🎯 Recommended For** | Testing, personal use | Production, public displays |

</div>

---

## 🚨 Troubleshooting

### ❌ "adb: command not found" (Windows)

<div align="center">

| 🔍 Cause | ✅ Solution |
|---|---|
| **Not in platform-tools directory** | `cd C:\platform-tools` then `adb devices` |

</div>

### 🚫 "Not allowed to set the device owner"

<div align="center">

| 🔍 Cause | ✅ Solution |
|---|---|
| **User accounts exist** | Remove ALL accounts (Google, Samsung, Microsoft, SIM) |
| **Hidden SIM account** | Remove SIM card or disable SIM profile |
| **Device-specific accounts** | Factory reset and try again (no accounts added) |

</div>

### 🔌 "No devices/emulators found"

<div align="center">

| 🔍 Cause | ✅ Solution |
|---|---|
| **USB not connected** | Check USB cable connection |
| **USB debugging disabled** | Enable in Developer Options |
| **Driver issues (Windows)** | Install [USB drivers](https://developer.android.com/studio/run/oem-usb) |
| **Popup not accepted** | Check tablet screen for "Allow USB debugging" popup |

</div>

### 📱 Tablet not recognized (Windows)

<div align="center">

**Install manufacturer USB drivers:**

| 🏭 Brand | 🔗 Driver Link |
|---|---|
| **Samsung** | [Samsung USB Driver](https://developer.samsung.com/android-usb-driver) |
| **Other Brands** | Search "[Brand] USB driver for Windows" |

</div>

### 🔒 "Error: Not enough permissions" (Linux)

<div align="center">

**Quick fix:**
```bash
sudo adb kill-server
sudo adb start-server
adb devices
```

**Permanent fix (udev rules):**
```bash
sudo nano /etc/udev/rules.d/51-android.rules
```
Add: `SUBSYSTEM=="usb", ATTR{idVendor}=="[vendor_id]", MODE="0666", GROUP="plugdev"`
```bash
sudo udevadm control --reload-rules
```

</div>

### 🔐 Device Owner set but kiosk doesn't lock completely

<div align="center">

| 📋 Step | 🎯 Action |
|---|---|
| **1️⃣ Reboot** | Restart the tablet |
| **2️⃣ Restart Kiosk** | Exit and start kiosk mode again |
| **3️⃣ Check Settings** | Verify Device Owner is active |

</div>

---

## 🔧 Remove Device Owner

### 📱 Option 1: Via FreeKiosk App

<div align="center">

| 📋 Step | 🎯 Action |
|---|---|
| **1️⃣ Access Settings** | Tap 5 times on secret button (bottom-right) |
| **2️⃣ Enter PIN** | Authenticate with your PIN code |
| **3️⃣ Remove Device Owner** | Tap "⚠️ Remove Device Owner" button |
| **4️⃣ Confirm** | Confirm the action in the dialog |
| **5️⃣ Complete** | Device Owner removed and settings reset |

</div>

> [!WARNING]
> "Exit Kiosk Mode" only closes the app but keeps Device Owner active. Use "Remove Device Owner" to completely disable.

### ⌨️ Option 2: Via ADB

<div align="center">

```bash
adb shell dpm remove-active-admin com.freekiosk/.DeviceAdminReceiver
```

</div>
---

## 🗑️ Uninstall

### 🏢 If Device Owner is Active

<div align="center">

| 📋 Step | 🎯 Action |
|---|---|
| **1️⃣ Remove Device Owner** | Follow steps above |
| **2️⃣ Uninstall App** | Standard uninstall procedure |

</div>

### 📱 Standard Uninstall

<div align="center">

Settings → Apps → FreeKiosk → Uninstall

</div>

---

## ❓ FAQ

<div align="center">

| ❓ Question | ✅ Answer |
|---|---|
| **🔓 Do I need to root my tablet?** | No! FreeKiosk uses Android's official Device Owner API (no root required). |
| **🟢 Can I use FreeKiosk without Device Owner?** | Yes! Basic mode works without Device Owner, but lockdown is not complete. |
| **🛡️ Does Device Owner void my warranty?** | No. Device Owner is an official Android feature. No modifications are made to the system. |
| **📱 Can I have multiple apps in Device Owner mode?** | No. Android allows only ONE Device Owner per device. FreeKiosk must be the only one. |
| **🔄 Can I still use my tablet normally after removing Device Owner?** | Yes! Just exit kiosk mode and uninstall. Your tablet returns to normal state. |
| **🔥 Does it work on Fire tablets (Amazon)?** | Should work, but not officially tested. Device Owner setup may differ. |

</div>

---

## 🎥 Video Tutorial

<div align="center">

🎥 Coming soon! Subscribe to [Rushb YouTube](https://youtube.com/@rushb) for updates.

</div>

---

## 🆘 Need Help?

<div align="center">

| � Resource | 🔗 Link |
|---|---|
| **📖 FAQ** | [FAQ](FAQ) |
| **💬 Discussions** | [GitHub Discussions](https://github.com/rushb-fr/freekiosk/discussions) |
| **🐛 Bug Reports** | [GitHub Issues](https://github.com/rushb-fr/freekiosk/issues) |
| **📧 Email Support** | support@freekiosk.app |

</div>

---

<div align="center">

**Made with ❤️ by [FreeKiosk Team](https://freekiosk.app)**

</div>