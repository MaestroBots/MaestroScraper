# Maestro Scraper User Manual

**Version 1.0.0**

---

## Table of Contents

1. [Introduction](#introduction)
2. [System Requirements](#system-requirements)
3. [Installation](#installation)
4. [Getting Your Telegram API Credentials](#getting-your-telegram-api-credentials)
5. [Logging In](#logging-in)
6. [Channels Page](#channels-page)
7. [Monitor Page](#monitor-page)
8. [Settings](#settings)
9. [Supported Blockchains](#supported-blockchains)
10. [Security & Privacy](#security--privacy)
11. [Troubleshooting](#troubleshooting)
12. [FAQ](#faq)

---

## Introduction

Maestro Scraper is a cross-platform desktop application that monitors your Telegram channels and groups in real-time, automatically detects cryptocurrency contract addresses, and forwards them to Maestro trading bots.

### What It Does

- Connects to your Telegram account and listens for messages in channels you choose
- Scans every incoming message for crypto addresses (ETH, SOL, TON, TRON)
- Automatically forwards detected addresses to the Maestro trading bot
- Tracks duplicates so you never forward the same address twice
- Logs all activity so you can review what was detected and forwarded

### Key Features

- **Real-Time Monitoring** - Tracks new messages, edits, and pinned posts as they happen
- **Multi-Chain Detection** - Detects EVM, Solana, TON, and TRON addresses
- **Flexible Filtering** - Choose exactly what to track per channel: admin posts, user messages, bot messages, or pinned messages
- **Duplicate Detection** - Automatically skips addresses that have already been seen in the same chat
- **Bot Forwarding** - Forwards detected addresses to Maestro (`@maestro`) or Maestro Pro (`@maestropro`)
- **Encrypted Storage** - Your Telegram session is encrypted using your operating system's keychain
- **Persistent Stats** - Monitoring statistics and activity logs survive app restarts
- **Forward to Maestro** - Experimental feature to manually resend any detected address to the bot

---

## System Requirements

|                              | Requirement                                                              |
| ---------------------------- | ------------------------------------------------------------------------ |
| **Operating System**         | Windows (x64), macOS (x64, Apple Silicon), or Linux (x64, arm64)         |
| **Telegram Account**         | An active Telegram account                                               |
| **Telegram API Credentials** | API ID and API Hash from [my.telegram.org](https://my.telegram.org/apps) |

---

## Installation

### Download

Download the latest release for your platform from the [GitHub Releases](https://github.com/MaestroBots/MaestroScraper/releases) page:

| Platform                  | File                             |
| ------------------------- | -------------------------------- |
| **Windows**               | `maestro-scraper-x.x.x-x64.exe`   |
| **macOS (Intel)**         | `maestro-scraper-x.x.x-x64.dmg`   |
| **macOS (Apple Silicon)** | `maestro-scraper-x.x.x-arm64.dmg` |
| **Linux**                 | `maestro-scraper-x.x.x-amd64.deb` |

### Install

#### macOS

Since the app is not signed with an Apple Developer certificate, macOS will show a warning:

> **"Maestro Scraper" was blocked to protect your Mac.**
> Apple could not verify "Maestro Scraper" is free of malware that may harm your Mac or compromise your privacy.

To install:
1. Open the `.dmg` file and drag the app to Applications
2. When the warning appears, click **Open Anyway** — or go to **System Settings → Privacy & Security**, scroll down, and click **Open Anyway** next to the Maestro Scraper message
3. You only need to do this once — subsequent launches will work normally

#### Windows

Windows Defender SmartScreen may show a warning:

> **Windows protected your PC**
> Microsoft Defender SmartScreen prevented an unrecognized app from starting.

To install:
1. Run the `.exe` installer
2. When the SmartScreen warning appears, click **More info**
3. Click **Run anyway**
4. Follow the installer prompts to complete the installation

#### Linux

```bash
sudo dpkg -i maestro-scraper-*-amd64.deb
```

---

## Getting Your Telegram API Credentials

Before you can use Maestro Scraper, you need to obtain API credentials from Telegram. These allow the app to connect to your Telegram account.

1. Open [https://my.telegram.org/apps](https://my.telegram.org/apps) in your browser
2. Log in with your phone number
3. Click **"API development tools"**
4. Fill in the form:
   - **App title**: Any name (e.g., "Maestro Scraper")
   - **Short name**: Any short name (e.g., "mscraper")
   - **Platform**: Desktop
5. Click **Create application**
6. You will see your **API ID** (a number) and **API Hash** (a 32-character string)
7. Save these - you will need them to log in

> **Important**: Never share your API ID and API Hash with anyone. These credentials provide access to the Telegram API on your behalf.

---

## Logging In

When you first open Maestro Scraper, you'll be taken to the login screen. The login process has up to 4 steps:

### Step 1: API Credentials

- Enter your **API ID** (the number from my.telegram.org)
- Enter your **API Hash** (the 32-character string)
- Check **"Remember credentials"** if you want the app to save your API credentials for next time
- Click **Continue**

> If you uncheck "Remember credentials" later, the app will clear all saved credentials and your Telegram session. You will need to log in again.

### Step 2: Phone Number

- Enter your phone number **with country code** (e.g., `+1 234 567 8900` for US)
- Click **Send Code**
- A verification code will be sent to your Telegram app

### Step 3: Verification Code

- Open your Telegram app on your phone or desktop
- Find the login code message from Telegram
- Enter the **5-6 digit code** in Maestro Scraper
- Click **Verify**
- If you didn't receive the code, click **Resend code**

### Step 4: Two-Factor Authentication (if enabled)

If you have Two-Factor Authentication (2FA) enabled on your Telegram account:

- Enter your **cloud password** (the 2FA password you set up in Telegram)
- Click **Sign In**

After successful login, you'll be redirected to the Channels page.

> Your session is saved securely. You won't need to log in again unless you explicitly log out or uncheck "Remember credentials."

---

## Channels Page

The Channels page is where you select which Telegram channels and groups to monitor. After logging in, your Telegram dialogs are automatically loaded.

### Viewing Your Channels

The page displays a table of all your Telegram chats with the following columns:

| Column       | Description                                        |
| ------------ | -------------------------------------------------- |
| **Name**     | The display name of the channel, group, or user    |
| **Username** | The `@username` if available                       |
| **Type**     | One of: `channel`, `group`, `user`, `bot`, `self`  |
| **ID**       | The unique Telegram ID for this chat               |
| **Admins**   | Toggle to track messages from channel/group admins |
| **Users**    | Toggle to track messages from regular users        |
| **Pinned**   | Toggle to track pinned messages                    |
| **Bots**     | Toggle to track messages from bots                 |

### Selecting What to Track

For each channel or group, you can independently enable or disable tracking for different message sources by checking the corresponding checkboxes:

- **Admins** - Track messages posted by admins (including posts made by the channel itself). Not available for direct user chats.
- **Users** - Track messages from regular (non-admin) users
- **Pinned** - Track pinned messages. Not available for direct user chats.
- **Bots** - Track messages sent by bots

A channel is considered "tracked" when at least one checkbox is enabled.

> **Tip**: For most crypto alpha channels, you'll want to enable **Admins** only, since the important calls typically come from channel admins.

### Toolbar Actions

- **Search** - Filter channels by name, username, or ID
- **Tracked Only** - Toggle to show only channels that have at least one tracking option enabled
- **Untrack All** - Disable all tracking on all channels at once
- **Refresh** - Re-fetch your channel list from Telegram (useful if you joined new channels)

### Sorting & Pagination

- Click any column header (**Name**, **Username**, **Type**, **ID**) to sort by that column
- Click the same header again to reverse the sort order
- Tracked channels always appear at the top of the list
- Use the pagination controls at the bottom to navigate through your channels
- Change the number of rows displayed per page (10, 20, 50, or 100)

---

## Monitor Page

The Monitor page is the heart of the application. This is where real-time message monitoring and address detection happens.

### Starting & Stopping

- When you navigate to the Monitor page with tracked channels, monitoring **starts automatically**
- Use the **Start Monitoring** / **Stop Monitoring** button to control monitoring manually
- Stopping monitoring requires confirmation to prevent accidental stops
- The status indicator in the top-right shows the current state:
  - **Green (pulsing)** - Monitoring is active
  - **Gray** - Idle (monitoring is stopped)

### Live Statistics

Four stat cards are displayed at the top of the page:

| Stat                   | Description                                                                                                       |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Messages Scanned**   | Total number of messages that passed your tracking filters and were scanned for addresses                         |
| **Addresses Found**    | Number of unique crypto addresses detected                                                                        |
| **Duplicates Skipped** | Number of addresses skipped because they were already seen in the same chat (when duplicate filtering is enabled) |
| **Forwarded to Bot**   | Number of times addresses were successfully forwarded to the Maestro bot                                          |

Stats persist across app restarts.

### Activity Log

Below the statistics, the activity log shows a real-time feed of all monitoring events. Each entry is color-coded:

| Color      | Type          | Meaning                                                     |
| ---------- | ------------- | ----------------------------------------------------------- |
| **Green**  | Address Found | A new crypto address was detected                           |
| **Yellow** | Duplicate     | An address was skipped because it was already seen          |
| **Blue**   | Forwarded     | An address was successfully sent to the Maestro bot         |
| **Red**    | Error         | Something went wrong (e.g., failed to forward)              |
| **Gray**   | Message       | An informational message (e.g., monitoring started/stopped) |

Each log entry shows:

- **Timestamp** - When the event occurred
- **Source** - The channel or group where the message came from (clickable - opens the channel in Telegram)
- **Message** - A description of what happened
- **Address** - The detected address (if applicable, click to copy)

### Activity Log Features

- **Search** - Filter log entries by message content, channel name, or address
- **Copy** - Click the copy icon on any log entry to copy the full entry text
- **Copy Address** - Click on any displayed address to copy it to your clipboard
- **Forward to Maestro** - When enabled in Settings, a "Forward to Maestro" button appears on entries with detected addresses, allowing you to manually resend them
- **Clear Log** - Remove all log entries and reset statistics
- **Infinite Scroll** - Scroll down to load more entries (50 loaded at a time)

### How Message Processing Works

When a new message arrives in a tracked channel:

1. The app checks if the chat is in your tracked list
2. It checks if the message type matches your filters (admin, user, bot, or pinned)
3. The message text and any embedded links are scanned for crypto addresses
4. If duplicate detection is enabled, previously seen addresses are skipped
5. New addresses are formatted and forwarded to the Maestro bot with encrypted metadata
6. All events are logged in the activity log

> **Note on edits**: Messages that are edited more than 30 seconds after the original post are ignored to prevent spam from old edits.

---

## Settings

The Settings page is divided into two sections: **General** and **Data Management**.

### General Settings

#### Ignore Duplicates

When enabled, the app skips addresses that have already been detected in the same chat. This prevents forwarding the same contract address multiple times from the same source.

- **Default**: Enabled
- Duplicate detection is per-channel - the same address from different channels will still be forwarded

#### Use Maestro Pro

Toggle between the standard Maestro bot and Maestro Pro:

- **Maestro** (`@maestro`) - The standard trading bot (default)
- **Maestro Pro** (`@maestropro`) - The premium trading bot

The currently active bot is shown with a green "Active" badge.

#### Forward to Maestro (Experimental)

When enabled, a "Forward to Maestro" button appears on activity log entries that contain detected addresses. This allows you to manually resend any address to the Maestro bot at any time.

### Data Management

#### Log Retention Period

Controls how long activity logs are kept before being automatically cleaned up:

- **7 days** / **14 days** / **21 days** / **30 days**
- Expired entries are removed automatically when the app starts
- Maximum of 10,000 log entries are stored regardless of retention period

#### Clear Activity Logs

Permanently delete all activity log entries. Requires confirmation. This action cannot be undone.

#### Clear Address History

Permanently delete the duplicate detection history. After clearing:

- Previously detected addresses may be forwarded again
- The duplicate counter resets
- Requires confirmation

#### Address History Limit

The address history is capped at **10,000 entries**. When this limit is reached, the oldest 20% of entries are automatically removed to make room for new ones. You can see the current usage on the Settings page (e.g., "3,500 / 10,000 addresses"). A warning appears when usage exceeds 50%.

> **Performance Tip**: If you notice the app becoming slower, check if your activity log or address history has grown very large. The app will show a warning when these exceed recommended limits. Use the clear buttons to free up space.

---

## Supported Blockchains

Maestro Scraper detects addresses for the following blockchains:

| Blockchain         | Address Format                                     | Example           |
| ------------------ | -------------------------------------------------- | ----------------- |
| **EVM**            | Starts with `0x` followed by 40 hex characters     | `0x1234abcd...`   |
| **Solana (SOL)**   | Base58 encoded, 32-44 characters                   | `7xKXtg2CW87...`  |
| **TON**            | Starts with `EQ` or `UQ` followed by 46 characters | `EQAbCdEf123...`  |
| **TRON**           | Starts with `T` followed by 33 characters          | `TAbCdEf12345...` |

The app scans both the message text and any embedded URLs/links for these address patterns.

---

## Security & Privacy

### Encrypted Storage

Your Telegram session is encrypted using your operating system's native keychain:

- **macOS**: Keychain
- **Windows**: DPAPI (Data Protection API)
- **Linux**: libsecret or kwallet

This means your Telegram session is protected by your OS login credentials. Other app data (channel preferences, address history, activity logs) is stored locally but not encrypted.

### What Data Is Stored

- **Telegram session** - An encrypted session token that keeps you logged in
- **API credentials** - Only if "Remember credentials" is checked
- **Channel tracking preferences** - Which channels you're monitoring and filter settings
- **Address history** - Previously detected addresses (for duplicate detection)
- **Activity logs** - A log of monitoring events
- **App settings** - Your preferences (duplicate filtering, bot selection, etc.)

### What Data Is NOT Stored

- Your Telegram password is never stored
- Message content is not persisted (only processed in memory)
- No data is sent to external servers except the Maestro bot, Telegram's own API, and Sentry for error tracking

### Bot Communication

When forwarding addresses to Maestro, the app sends a formatted message containing:

- The detected address(es)
- A link to the source message (if available)
- Encrypted metadata for tracking purposes

---

## Troubleshooting

### "Not connected to Telegram" error

- Make sure you have an active internet connection
- Try logging out and logging back in
- Verify your API credentials are correct at [my.telegram.org/apps](https://my.telegram.org/apps)

### No channels showing up

- Click the **Refresh** button on the Channels page
- Make sure you're connected to Telegram (check the connection status)
- If you just joined new channels, it may take a moment for them to appear

### Addresses not being detected

- Verify that the channel is tracked (at least one checkbox enabled on the Channels page)
- Check that the correct filter is enabled (e.g., if the address comes from an admin, make sure "Admins" is checked)
- The address format must match one of the supported patterns (see [Supported Blockchains](#supported-blockchains))
- Check the Monitor page activity log for any error messages

### Addresses not being forwarded

- Make sure the Maestro bot (`@maestro` or `@maestropro`) is accessible from your Telegram account
- Start a conversation with the Maestro bot on Telegram first if you haven't already
- Check the activity log for "error" entries that may explain the failure

### Duplicate addresses being skipped

- This is expected behavior when "Ignore Duplicates" is enabled in Settings
- Duplicates are tracked per channel - the same address from a different channel will still be forwarded
- To reset duplicate tracking, go to Settings and click **Clear Address History**

### App feels slow

- Check Settings for warnings about large activity logs or address histories
- Clear your activity logs and/or address history
- Lower the log retention period

### Login issues

| Error                            | Solution                                                        |
| -------------------------------- | --------------------------------------------------------------- |
| "API ID must be a valid number"  | Enter only the numeric API ID from my.telegram.org              |
| "API Hash must be 32 characters" | Copy the full API Hash string from my.telegram.org              |
| "Invalid phone number format"    | Include your country code (e.g., +1 for US, +44 for UK)         |
| "Invalid verification code"      | Double-check the code from your Telegram app                    |
| "Verification code expired"      | Click "Resend code" to get a new one                            |
| "Incorrect password"             | This is your Telegram 2FA cloud password, not your app password |
| "Too many attempts"              | Wait a few minutes before trying again                          |
| "This phone number is banned"    | Contact Telegram support                                        |

### "Keychain access is unavailable" warning (macOS)

If you see this warning when enabling "Remember credentials":

- You previously denied Keychain access when macOS prompted you
- Go to **System Settings → Privacy & Security** and allow Keychain access for Maestro Scraper
- Restart the app and try again

Without Keychain access, your credentials and session cannot be saved — you will need to log in again each time you restart the app.

---

## FAQ

**Q: Do I need to keep the app open for monitoring to work?**
A: Yes. Maestro Scraper monitors messages in real-time and must remain running. If you close the app, monitoring stops. When you reopen it, your stats and logs are preserved, and monitoring can be restarted.

**Q: Can I monitor multiple channels at once?**
A: Yes. You can track as many channels and groups as you want simultaneously. Enable tracking on each channel from the Channels page.

**Q: Will this get my Telegram account banned?**
A: Maestro Scraper uses the official Telegram API through gramjs. As long as you use it normally, your account should be safe. Avoid running excessive operations in short periods.

**Q: What happens if I join a new channel?**
A: Click **Refresh** on the Channels page to update your channel list. The new channel will appear, and you can enable tracking on it.

**Q: Can I use this with multiple Telegram accounts?**
A: Currently, you can only be logged in with one account at a time. To switch accounts, log out and log in with different credentials.

**Q: What's the difference between Maestro and Maestro Pro?**
A: Maestro (`@maestro`) is the standard trading bot. Maestro Pro (`@maestropro`) offers premium features. You can switch between them in Settings. The forwarding works the same way for both.

**Q: How does duplicate detection work?**
A: When an address is detected, the app stores a record of `address + chatId`. If the same address appears again in the same chat, it's skipped. Addresses from different chats are treated as separate. You can clear the history in Settings to reset this.

**Q: Are my messages or private chats read?**
A: The app only processes messages from channels and groups you explicitly choose to track. It does not read your private messages or any chats you haven't selected.

**Q: Where is my data stored?**
A: All data is stored locally on your computer. Your Telegram session is encrypted via the OS keychain. No data is sent to external servers besides Telegram's own API and the Maestro bot.

---

_Maestro Scraper v1.0.0 - Built with Electron, React, and gramjs_
