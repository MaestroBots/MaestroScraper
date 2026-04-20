# Changelog

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
