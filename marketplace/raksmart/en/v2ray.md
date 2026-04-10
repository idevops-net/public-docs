# V2Ray Usage Guide

## 1\. Quick Start (Copy Link & One-Click Import)

You can obtain your connection credentials by executing the following command after logging into your server via console or SSH:

```bash
cat /opt/cloud/v2ray/credentials.txt
```

Follow these steps to complete the import:

**Step 1: Copy the Share Link**

In the console output, select and copy the entire long link string. Ensure you copy from the beginning (e.g., `vless://` or other generated protocols) to the very end (e.g., until identifiers like `#V2Ray-Reality`).

**Step 2: One-Click Import**

Follow the instructions for your specific operating system to import the copied link into your client:

- **Windows (v2rayN)** Open the application and press `Ctrl + V` on your keyboard, or click the **"Servers"** menu at the top and select **"Import bulk URL from clipboard"**.

- **macOS (V2RayX / V2Free / Clash)** Click the application icon in the top menu bar and select **"Import config from clipboard"** or **"Add from clipboard"**.

_(For detailed steps on mobile and other platforms, please refer to Section [4. Client Configuration](https://www.google.com/search?q=%234-client-configuration) below.)_

If your specific scenario requires raw underlying parameters:

```bash
cat /opt/cloud/v2ray/config/config.json
```

---

## 2\. Key Directories

| Directory/File                        | Description                                                       |
| :------------------------------------ | :---------------------------------------------------------------- |
| `/opt/cloud/v2ray/config/config.json` | Core V2Ray configuration file (includes Inbound/Outbound rules).  |
| `/opt/cloud/v2ray/credentials.txt`    | Credentials file containing node login and plaintext share links. |
| `/var/log/v2ray/`                     | Directory for V2Ray access and error logs.                        |

---

## 3\. Common Operations

Navigate to the `/opt/cloud/v2ray` directory. You can use the following built-in management scripts (depending on your deployment method, you may also use `docker` commands):

| Operation       | Command                                               |
| :-------------- | :---------------------------------------------------- |
| Start Service   | `/opt/cloud/v2ray/start.sh`                           |
| Stop Service    | `/opt/cloud/v2ray/stop.sh`                            |
| Restart Service | `/opt/cloud/v2ray/restart.sh`                         |
| Check Status    | `/opt/cloud/v2ray/status.sh`                          |
| View Logs       | `/opt/cloud/v2ray/logs.sh` or `docker logs v2ray-app` |

---

## 4\. Client Configuration

We recommend the following clients for various operating systems to ensure the best experience.

### 💻 Windows: v2rayN

**v2rayN** is currently the most stable and feature-rich graphical client for Windows.

- **Download**: [GitHub Releases - 2dust/v2rayN](https://github.com/2dust/v2rayN/releases)
  - _Note: Beginners are advised to download `v2rayN-With-Core.zip`, which includes the core engine and works out of the box._
- **Installation**:
  1.  Extract the downloaded ZIP file to a non-system drive folder.
  2.  Double-click `v2rayN.exe` (if prompted for .NET Desktop Runtime, follow the pop-up instructions to install).
- **Quick Setup**:
  1.  **Copy Link**: Copy the node share link from the console (starting with `vless://`).
  2.  **Import**: Open the v2rayN main interface, press `Ctrl + V`, or use the **"Servers"** menu -\> **"Import bulk URL from clipboard"**.
  3.  **Select Node**: Press `Enter` on the node or right-click to set it as the **Active Server**.
  4.  **Start Proxy**: Right-click the system tray icon (bottom right), select **System Proxy** -\> **Automatic Configuration**. The icon turning purple indicates success.

### 📱 Android: v2rayNG

**v2rayNG** is the preferred choice for Android, maintaining the ease of use found in v2rayN.

- **Download**: [GitHub Releases - 2dust/v2rayNG](https://github.com/2dust/v2rayNG/releases) or Google Play Store.
- **Quick Setup**:
  1.  **Import**: Copy the link, open v2rayNG, and tap the **"+"** icon in the top right.
  2.  **Add from Clipboard**: Select **"Import config from clipboard"**; the app will automatically recognize the node.
  3.  **Connect**: Tap the imported node, then tap the **circular "V" icon** at the bottom right. Grant VPN permissions if prompted.

### 🍎 macOS: V2Box / V2rayU

For macOS, we recommend clients that natively support one-click clipboard imports:

- **Recommended Downloads**:
  - **V2Box**: Search and download for free on the Mac App Store (Native support for Apple Silicon and Intel).
  - **V2rayU**: A classic open-source client available via [GitHub Releases](https://github.com/yanue/V2rayU/releases).
- **Quick Setup (V2Box)**:
  1.  **Import**: Copy the link, open V2Box, go to **"Configs"** at the bottom, click **"+"**, and select **"Import from clipboard"**.
  2.  **Connect**: Go to the **"Home"** tab and tap the large center button or slide the toggle.
- **Quick Setup (V2rayU)**:
  1.  **Import**: Click the `V2rayU` icon in the top menu bar and select **"Import from Clipboard"**.
  2.  **Connect**: Select **"Turn V2ray-Core On"** and choose **Global Mode** or **PAC Mode**.

### 🍏 iOS: V2Box

For iOS, **V2Box** is recommended as it is free, supports multiple protocols, and is very user-friendly.

- **Download**: Search for `V2Box` in the App Store.
  - _Note: If not available in your local App Store, you may need an Apple ID from a different region (e.g., US)._
- **Quick Setup**:
  1.  **Import**: Copy the link, open V2Box, tap **"Configs"**, then tap the **"+"** icon and select **"Import from clipboard"**.
  2.  **Connect**: Go to the **"Home"** tab, tap the large connection button, or slide the bottom toggle.
  3.  **Authorize**: On first connection, tap **"Allow"** when prompted to add VPN configurations and authorize with your passcode or FaceID.

### ⚠️ General Notes

1.  **Routing Mode**: It is recommended to choose **"Bypass Mainland China"** or **"Rule Mode"** on all platforms. This ensures local traffic does not go through the proxy, resulting in faster speeds and saved data.

---

## 5\. Further Learning

- [Project V Official Website (v2fly.org)](https://www.v2fly.org/)
- [V2Ray Beginner's Guide (White Paper)](https://guide.v2fly.org/)
- [v2ray-core GitHub Repository](https://github.com/v2fly/v2ray-core)
