# Discord Bot Feature Guide

---

## 1. Auto-Moderation System

**Who can manage this:** Server Administrators & Moderators (`Manage Messages` permission required)

### How It Protects Your Server
The bot keeps your server safe by automatically scanning text messages 24/7. If a non-admin posts something that violates community rules, the bot instantly deletes the message and posts a quick warning that disappears after 5 seconds.

* **Banned Words Filter:** Automatically blocks messages containing words or phrases on your banned list.
* **Invite Link Blocker:** Stops unauthorized Discord server invite links (`discord.gg/...`) from being posted.
* **Anti-Spam Protection:** Automatically flags and deletes messages that tag 5 or more members or roles at once.
* **Staff Exemption:** Administrators and moderators are automatically exempt from these restrictions.

### Admin & Moderator Commands
| Command | What It Does | Example |
| :--- | :--- | :--- |
| `/automod_add` | Adds a new word or phrase to the blocked list. | `/automod_add word: spamlink` |
| `/automod_remove` | Removes a word or phrase from the blocked list. | `/automod_remove word: spamlink` |

---

## 2. Auto-Role & Server Verification

**Who can manage this:** Server Administrators & Moderators (`Manage Roles` permission required)

### How It Welcomes New Members
This system manages how new members get their roles and access the server. You can choose one of three setup styles:

* **Instant Role:** Automatically assigns a default role as soon as someone joins.
* **Button Verification Panel:** Places a friendly button in your welcome or rules channel. Members simply click **Accept Rules & Verify** to get their role.
* **Passcode Gatekeeper:** Hides access until new members type a secret password using the `/verify` command.

### Admin & Moderator Commands
| Command | What It Does | Example |
| :--- | :--- | :--- |
| `/set_autorole` | Chooses which role new members receive upon joining or verifying. | `/set_autorole role: @Member` |
| `/setup_gatekeeper_button` | Posts an interactive verification button panel in the current channel. | `/setup_gatekeeper_button role: @Verified` |
| `/set_gatekeeper_code` | Sets the secret password members must enter to gain access. | `/set_gatekeeper_code code: SecretRuleCode2026` |

### Member Commands
| Command | What It Does | Example |
| :--- | :--- | :--- |
| `/verify` | Enter the server's secret password to unlock channels. | `/verify code: SecretRuleCode2026` |

---

## 3. Mini-Games & Server Economy

**Who can use this:** Available to everyone in the server!

### How the Economy Works
Every member receives 100 bonus coins to start! You can claim free daily rewards, check your wallet, or play fun mini-games to build up your coin balance.

* **Daily Coins:** Collect 100 to 250 free coins every 24 hours.
* **Starting Balance:** Every new user starts with 100 coins automatically.

### Commands for Everyone
| Command | What It Does | Example |
| :--- | :--- | :--- |
| `/daily` | Claim your free daily coins (available once every 24 hours). | `/daily` |
| `/balance` | Check how many coins you currently have in your wallet. | `/balance` |
| `/coinflip` | Bet coins on a 50/50 coin toss (Heads or Tails). Win to double your bet! | `/coinflip choice: Heads bet: 50` |
| `/blackjack` | Play a hand of Blackjack against the bot dealer using interactive Hit and Stand buttons! | `/blackjack bet: 100` |
