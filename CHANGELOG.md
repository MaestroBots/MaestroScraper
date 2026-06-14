# Changelog

## v1.3.0

- New **Tracking** menu on each channel: pick exactly whose messages to scrape — **Admins** or **Users**, and **Humans** or **Bots** — plus **Pinned** posts and your **own** messages, each toggled independently. This replaces the old single bots switch.
- Fixed a slowdown where the app could lag or freeze during heavy scraping as the activity log and address history grew. Saving now happens in the background, so monitoring stays smooth.
- Clearer login errors: the app now shows the specific reason (and its own prompts, like "Please enter the verification code") instead of a generic "something went wrong."
- Your saved session and credentials are better protected if the stored file is corrupted or a save is interrupted, and logging out now reliably clears your session.
- Address detection now recognizes Uniswap v4 pool links (the newer 64-character `0x` pool IDs) from any site, which were previously missed or read incorrectly.
- The **Self** tracking toggle now captures your own messages in a group on its own, without needing the other toggles enabled.
- More reliable scraping: monitoring no longer silently stops after a background error, and changing your tracking settings while monitoring won't drop incoming messages.
- New **Telegram Server Region** option on the login screen (set to **Auto** by default) for when the default connection is slow or blocked where you are. It only appears when you need to sign in. Once connected, hover the **Connected** indicator in the footer to see your datacenter and current ping, and click to copy it.
- The app now detects if the connection quietly drops while you are scraping and shows it in the footer, recovering on its own once messages start flowing again.
- Connecting no longer hangs forever: if it stalls, you get a clear error and can try again.

## v1.2.0

- The Channels page now lists up to your **5,000 most recently active chats** (up from 500), so users in many channels can finally see and scrape the long tail of their chat list.
- Channels now load progressively as they're fetched — the table fills in batches instead of waiting for everything to finish, making the page feel much faster on large accounts.
- If you're in more chats than the limit, a warning banner appears at the top of the Channels page letting you know older chats were omitted, with instructions on how to surface them.
- Fixed a bug where posts from anonymous admins (signed as the channel itself) were not always recognized as admin posts. With the **Admins** filter enabled, these posts are now scraped correctly in broadcast channels and supergroups.
- Improved address detection from links: addresses inside dexscreener and pump.fun URLs are now picked up correctly, instead of being missed or captured as a wrong, partial address.

## v1.1.1

- Fixed a bug where messages posted in tracked channels by the logged-in account (as an admin or anonymous channel author) were not being scraped. Posts in channels you track are now forwarded to your Maestro bot regardless of who authored them.

## v1.1.0

- Channels table now defaults to Telegram order (pinned first, then by most recent activity).
- Cleaned up the interface — renamed the "Monitor" page to "Activity" and made labels consistent throughout the app.
- Scraping status is now visible in the navbar on all pages.
- New app icon that fits properly in the macOS dock.
- Various bug fixes and stability improvements.

## v1.0.0

v1.0.0 is a major release and a complete evolution from the original TelegramScraper. The app has been rebuilt from the ground up with a new name, new architecture, and a significantly improved user experience.

- **TelegramScraper** has been renamed to **Maestro Scraper** to better reflect its integration with the Maestro trading ecosystem.
- Brand-new multi-page layout with dedicated pages for Channels, Monitor, and Settings.
- Navigation bar with live connection status indicator, user info display, and quick access to your Maestro bot.
- New app icon and branding throughout.
- Step-by-step login wizard with support for two-factor authentication (2FA).
- Option to remember your credentials for faster future logins.
- Ability to securely clear all saved credentials on logout.
- Browse and search all your Telegram channels, groups, and conversations in one place.
- Granular tracking controls per channel: choose to monitor messages from Admins, Users, Bots, and Pinned messages independently.
- Sort and filter channels by name, username, type, or ID.
- Paginated channel list with configurable page sizes.
- One-click "Untrack All" to quickly disable monitoring.
- Live monitoring status indicator showing whether monitoring is active, paused, or has encountered an error.
- At-a-glance statistics: Messages Scanned, Addresses Found, Duplicates Skipped, and Forwarded to Bot.
- Color-coded activity log with real-time entries for every detected address, duplicate, forwarded message, and error.
- Search, filter, and copy activity log entries.
- Multi-chain address detection: **EVM**, **Solana**, **TON**, and **TRON** addresses in both message text and embedded links.
- Detected addresses are automatically forwarded to your Maestro trading bot (**@maestro** or **@maestropro**).
- Forwarded messages include the source channel and a direct link back to the original message.
- **Ignore Duplicates** — automatically skip addresses that have already been detected in the same chat.
- **Log Retention Period** — choose how long activity logs are kept (7, 14, 21, or 30 days) to manage storage.
- All stored data (credentials, session, settings) is encrypted using your operating system's secure keychain.
- Native macOS builds (Apple Silicon and Intel) and Windows support.
- Terms of Service agreement on first launch.
