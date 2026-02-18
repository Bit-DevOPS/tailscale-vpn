# Tailscale Client Configuration Guide

This guide provides instructions on how to install and configure the Tailscale client to connect to our private network (**hs.socratecloud.com**).

## Table of Contents
* [Windows (Automated)](#windows-automated)
* [macOS](#macos)
* [Linux](#linux)

---

## Windows (Automated)

We have automated the installation and configuration process for Windows users.

### 1. Download the Installer
Go to the **[Releases](../../releases/latest)** page of this repository and download the latest zip file (e.g., `windows-tailscale-1.94.2`).

### 2. Run the Script
1.  **Extract** the contents of the zip file to a folder on your computer.
    > **Note:** Do not run the files directly from inside the zip archive; they must be extracted first.
2.  Locate the file named **`install_tailscale.bat`**.
3.  Right-click on `install_tailscale.bat` and select **Run as administrator**.
4.  If prompted by Windows SmartScreen ("Windows protected your PC"), click **More info** -> **Run anyway**.

### 3. Authenticate
The script will automatically install Tailscale and attempt to connect.
* Copy the **Auth URL** shown in the terminal window and paste it into your browser.
* Log in with your company credentials.

---

## macOS

### Option A: Mac App Store (GUI)
1.  Install [Tailscale from the Mac App Store](https://apps.apple.com/us/app/tailscale/id1475387142).
2.  **Do not log in yet.** Open the app, click the Tailscale icon in the menu bar, and ensure you are logged out.
3.  Open **Terminal** and run the following command to configure the login server:
    ```bash
    defaults write io.tailscale.ipn.macsys ControlURL https://hs.socratecloud.com
    ```
4.  Restart the Tailscale application.
5.  Click **Log in** from the menu bar icon. It should direct you to `hs.socratecloud.com`.

### Option B: CLI (Homebrew)
If you prefer the command line or don't use the App Store:
1.  Install via Homebrew:
    ```bash
    brew install tailscale
    sudo tailscaled install-system-daemon
    ```
2.  Connect to the network:
    ```bash
    sudo tailscale up --login-server=https://hs.socratecloud.com
    ```

---

## Linux

### 1. Install Tailscale
Use the automated install script provided by Tailscale:

```bash
curl -fsSL https://tailscale.com/install.sh | sh

```

### 2. Connect

Once installed, run the `up` command specifying our login server:

```bash
sudo tailscale up --login-server=https://hs.socratecloud.com

```

### 3. Authenticate

Copy the URL provided in the terminal output (e.g., `https://hs.socratecloud.com/register/nodekey:...`), paste it into your browser, and log in.

---

### Troubleshooting

* **"User not enabled" error:** Please contact the administrator to have your user approved in the ACLs.
* **Windows SmartScreen warning:** The installation script is internal and not signed by Microsoft. This warning is expected; please proceed by clicking "Run anyway."

