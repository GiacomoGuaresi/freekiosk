<div align="center">

# 🧭 FreeKiosk Features and Modes

**A quick map of how FreeKiosk can run, lock, and present content on Android tablets**

<p>
  <a href="README.md">📚 Docs Home</a> •
  <a href="installation.md">🔧 Installation</a> •
  <a href="INTEGRATIONS.md">🔗 Integrations</a>
</p>

</div>

> [!TIP]
> Use this page to choose your operational mode first, then jump to setup and automation guides.

## 🎛️ Core Features

<div align="center">

| ✅ Feature | 📋 Description |
|---|---|
| **🌐 Kiosk Browser Mode** | WebView-based web content display |
| **📱 External App Mode** | Lock to a specific Android application |
| **🏢 Device Owner Support** | Enterprise-grade full device lockdown |
| **🔐 PIN Protection** | Secure settings access with authentication |
| **📌 Screen Pinning** | Optional task locking policies |

</div>

## 🖥️ Display Modes

### 🌐 WebView Mode

<div align="center">

**Perfect for dashboards, web apps, and websites**

| ⚡ Capability | 📋 Details |
|---|---|
| **🔗 URL Display** | Any HTTPS/HTTP website or dashboard |
| **🔒 SSL Support** | Including self-signed certificates |
| **📱 Immersive** | Fullscreen kiosk experience |
| **🏠 Home Assistant** | Native integration with HA dashboards |

</div>

**Best for:**
- Home Assistant dashboards
- Information displays
- Web-based applications
- Digital signage

### 📱 External App Mode

<div align="center">

**Lock device to a specific Android application**

| ⚡ Capability | 📋 Details |
|---|---|
| **🎯 App Locking** | Lock to any installed Android app |
| **🔄 Auto-relaunch** | Automatic app restart on exit/crash |
| **🧪 Test Mode** | Safe deployment with back button access |
| **🔐 Secure Access** | 5-tap gesture + PIN for settings |

</div>

**Best for:**
- Cloud gaming (Steam Link, Xbox Cloud Gaming)
- Digital signage apps
- Corporate applications
- Media players

### 📊 Dashboard Mode

<div align="center">

**Multi-URL tile grid for quick navigation**

| ⚡ Capability | 📋 Details |
|---|---|
| **🔷 Tile Grid** | Multiple configurable URL tiles |
| **👆 One-tap Navigation** | Quick access to different resources |
| **⏰ Inactivity Return** | Auto-return to dashboard after timeout |
| **🎨 Customizable** | Custom names and URLs for each tile |

</div>

**Best for:**
- Multi-dashboard environments
- Resource collections
- Quick access portals
- Control centers

### 🎬 Media / Multi-App Enhancements

<div align="center">

**Advanced features for media and multi-app deployments**

Recent versions include significant improvements for:

- **🎥 Media Player Integration** - Enhanced video and audio playback
- **📱 Multi-App Support** - Switch between multiple applications
- **🎯 Advanced Scheduling** - Time-based content switching
- **📊 Performance Monitoring** - Resource usage tracking

</div>

> [!NOTE]
> For detailed release information, see [Roadmap and Changelog](Roadmap-and-Changelog).

## 🔐 Security and Control

<div align="center">

| 🛡️ Security Feature | 📋 Protection Level |
|---|---|
| **🏢 Device Owner** | Complete device control and lockdown |
| **🚫 Navigation Blocking** | Disable home, recent, settings access |
| **📱 Overlay Prevention** | Block system dialogs and notifications |
| **🐕 Watchdog Service** | Automatic kiosk recovery and monitoring |

</div>

### 🔒 Lockdown Levels

<div align="center">

| 🔒 Level | 📋 Description | 🎯 Use Case |
|---|---|---|
| **Basic** | WebView kiosk with minimal restrictions | Simple displays |
| **Standard** | External app with navigation blocking | Single-app deployments |
| **Enterprise** | Device Owner full lockdown | Corporate/public kiosks |

</div>

## ⚙️ Provisioning and Operations

<div align="center">

| 🚀 Operational Feature | 📋 Capability |
|---|---|
| **⌨️ ADB Provisioning** | Headless scripted deployment |
| **💾 Configuration Backup** | Save/restore complete settings |
| **🚀 Auto-launch** | Boot-time automatic startup |
| **🔄 Keep-alive** | Continuous monitoring and recovery |
| **📡 Remote Control** | REST API and MQTT automation |

</div>

### 🎯 Deployment Methods

<div align="center">

| 📋 Method | 🛠️ Tools | 📏 Scale |
|---|---|---|
| **Manual** | Touch interface | Single device |
| **ADB Script** | Command line | Small batches |
| **MDM Integration** | Enterprise tools | Large fleets |

</div>

---

## 🎯 Choosing Your Mode

<div align="center">

| 🎭 Use Case | 🎯 Recommended Mode | 🔧 Setup Guide |
|---|---|---|
| **🏠 Home Dashboard** | WebView Mode | [Installation](Installation) |
| **🎮 Cloud Gaming** | External App + Device Owner | [ADB Configuration](ADB-Configuration) |
| **🏢 Corporate Kiosk** | External App + Enterprise Lock | [Installation Guide](Installation) |
| **📊 Multi-Dashboard** | Dashboard Mode | [Installation](Installation) |
| **🎬 Media Display** | Media Mode | [Roadmap](Roadmap-and-Changelog) |

</div>

---

<div align="center">

**Made with ❤️ by [FreeKiosk Team](https://freekiosk.app)**

</div>
