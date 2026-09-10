# Changelog

## v1.5.0

- Fixed a bug where the app usually couldn't tell whether a message came from a person or a bot. If your **Tracking** settings split **Humans** and **Bots**, most messages were being logged as **Unverified** and held back instead of forwarded. Detection now works for every sender, and a brief Telegram server hiccup no longer freezes a sender as unknown for the rest of the day.
- **Refresh** on the Channels page no longer erases your per-channel **Buy Amount** settings. They stay put, the same way your tracking selections already did.
- Uniswap v4 pool links that show a shortened copy of the pool ID as link text no longer cause the cut-off copy to be forwarded alongside the real one.
- Logging in is more forgiving of pasted input. An API hash copied with a stray space or line break now works, and if your credentials are wrong you see the specific problem instead of a generic "Failed to connect to Telegram."
- Phone numbers are checked before contacting Telegram: spaces, dashes, and parentheses are ignored, and a number typed in national format (starting with 0) gets a message asking for the country code instead of failing later.
- Reopening the app after your Telegram session expired or was signed out elsewhere now takes you straight back to the phone step without a hidden error.
- Updated to the latest Telegram API version so messages from channels using newer Telegram features are read correctly.
- On the release download page, each installer file name is now a direct download link.

## v1.4.0

- New **Buy Amount** tab on each channel's **Tracking** menu. Add a buy amount per chain (up to 3 chains, from **SOL**, **BSC**, **BASE**, **ETH**, **ROBINHOOD**, **MONAD**, **SONIC**, **AVAX**, **ARB**, **HYPE**, **TRX**, **TON**) and remove any you no longer want. When an address is detected in that channel, your amounts are sent with it and the bot uses the one for the token's chain, overriding the Auto Buy amount set in your Scraper channel.
- Address detection now also reads the links and labels on inline buttons, so contracts hidden behind a **Buy** or **Chart** button (or dropped straight into the button text) are picked up too.
- On systems without a secure keychain (some Linux setups, or macOS when Keychain access is denied), you can now choose to save your credentials with a machine-tied fallback. The login page asks first and explains the trade-off, and shows a notice when your keychain becomes available again so you can switch back.
- Signing in is clearer when the code doesn't arrive as a text. The screen now tells you where Telegram actually sent it (your **Telegram app**, a **text message**, or a **call**), accepts codes that come as a word or phrase, and the **Resend** button shows which method it'll try next (with a short wait if Telegram requires one). If no code can be sent to this app, or Telegram needs a step only its official app can complete, you get clear instructions instead of waiting on a code that never comes.
- New **Unverified** (orange) entry in the activity log. Sometimes Telegram won't reveal whether a message's sender is a bot or a person, or an admin or a regular member. If your **Tracking** settings would handle those two cases differently, the app no longer guesses: it logs the address as **Unverified** so you can review it, but doesn't forward it. When your settings would treat both cases the same, scraping continues as normal. Your channels and direct messages aren't affected.

## v1.3.0

- New **Tracking** menu on each channel: pick exactly whose messages to scrape: **Admins** or **Users**, and **Humans** or **Bots**, plus **Pinned** posts and your **own** messages, each toggled independently. This replaces the old single bots switch.
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
- Channels now load progressively as they're fetched, the table fills in batches instead of waiting for everything to finish, making the page feel much faster on large accounts.
- If you're in more chats than the limit, a warning banner appears at the top of the Channels page letting you know older chats were omitted, with instructions on how to surface them.
- Fixed a bug where posts from anonymous admins (signed as the channel itself) were not always recognized as admin posts. With the **Admins** filter enabled, these posts are now scraped correctly in broadcast channels and supergroups.
- Improved address detection from links: addresses inside dexscreener and pump.fun URLs are now picked up correctly, instead of being missed or captured as a wrong, partial address.

## v1.1.1

- Fixed a bug where messages posted in tracked channels by the logged-in account (as an admin or anonymous channel author) were not being scraped. Posts in channels you track are now forwarded to your Maestro bot regardless of who authored them.

## v1.1.0

- Channels table now defaults to Telegram order (pinned first, then by most recent activity).
- Cleaned up the interface: renamed the "Monitor" page to "Activity" and made labels consistent throughout the app.
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
- **Ignore Duplicates**: automatically skip addresses that have already been detected in the same chat.
- **Log Retention Period**: choose how long activity logs are kept (7, 14, 21, or 30 days) to manage storage.
- All stored data (credentials, session, settings) is encrypted using your operating system's secure keychain.
- Native macOS builds (Apple Silicon and Intel) and Windows support.
- Terms of Service agreement on first launch.
