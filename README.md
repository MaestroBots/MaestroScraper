# Maestro Scraper

A cross-platform desktop application that scrapes your Telegram channels in real-time, detects cryptocurrency contract addresses, and forwards them to your Maestro trading bot.

**Supports EVM, Solana, TON, and TRON addresses.**

---

## Download

Download the latest release for your platform:

| Platform                  | File                              | Notes             |
| ------------------------- | --------------------------------- | ----------------- |
| **Windows**               | `maestro-scraper-x.x.x-x64.exe`   | Run the installer |
| **macOS (Apple Silicon)** | `maestro-scraper-x.x.x-arm64.dmg` | M1/M2/M3/M4 Macs  |
| **macOS (Intel)**         | `maestro-scraper-x.x.x-x64.dmg`   | Older Intel Macs  |
| **Linux**                 | `maestro-scraper-x.x.x-amd64.deb` | Debian/Ubuntu     |

**[Go to Releases](https://github.com/MaestroBots/MaestroScraper/releases)**

> Not sure which macOS version? Click the Apple menu > **About This Mac**. If it says "Apple M1" (or M2, M3, M4), download the **arm64** version. Otherwise, download **x64**.

---

## Installation

### macOS

Since the app is not signed with an Apple Developer certificate, macOS will show a warning:

> **"Maestro Scraper" was blocked to protect your Mac.**
> Apple could not verify "Maestro Scraper" is free of malware that may harm your Mac or compromise your privacy.

To install:

1. Open the `.dmg` file and drag the app to Applications
2. When the warning appears, click **Open Anyway** — or go to **System Settings → Privacy & Security**, scroll down, and click **Open Anyway** next to the Maestro Scraper message
3. You only need to do this once — subsequent launches will work normally

### Windows

Windows Defender SmartScreen may show a warning:

> **Windows protected your PC**
> Microsoft Defender SmartScreen prevented an unrecognized app from starting.

To install:

1. Run the `.exe` installer
2. When the SmartScreen warning appears, click **More info**
3. Click **Run anyway**
4. Follow the installer prompts to complete the installation

### Linux

```bash
sudo dpkg -i maestro-scraper-*-amd64.deb
```

---

## Getting Started

1. Get your Telegram API credentials from [my.telegram.org/apps](https://my.telegram.org/apps)
2. Open Maestro Scraper and enter your API ID and API Hash
3. Log in with your phone number and verification code
4. Select channels to scrape on the Channels page — scraping starts automatically
5. Check the Activity page to see detected addresses and logs

For detailed instructions, see the **[User Manual](USER_MANUAL.md)**.

---

## Documentation

- **[User Manual](USER_MANUAL.md)** — Full guide covering login, channel setup, scraping, settings, and troubleshooting
- **[Changelog](CHANGELOG.md)** — Release notes and version history
