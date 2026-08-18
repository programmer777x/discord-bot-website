# Discord Bot Feature Documentation

---

## 1. Auto-Moderation System (`automod.py`)

**Permissions Required:** `Manage Messages` *(administrators & moderators only)*

### Automated Server Shield (Passive Protection)
The bot automatically scans incoming text messages in real time. If a non-administrative user posts content violating server guidelines, the bot instantly deletes the message and sends a self-deleting warning message (clears after 5 seconds).

* **Banned Words Filter:** Blocks any message containing forbidden phrases specified in your server's banned word list.
* **Invite Link Blocker:** Detects and removes unauthorized Discord server invite links (`discord.gg/...`, `discord.com/invite/...`).
* **Anti-Spam / Mass-Mention Protection:** Flags and deletes messages tagging 5 or more users or roles simultaneously.
* **Admin/Mod Exemption:** Server staff with `Manage Messages` permissions are automatically exempt from automod restrictions.

### Management Commands
| Command | Description | Example Usage |
| :--- | :--- | :--- |
| `/automod_add` | Adds a new term to the word filter and updates persistence immediately. | `/automod_add word: spamlink` |
| `/automod_remove` | Removes a term from the active word filter list. | `/automod_remove word: spamlink` |

### Configuration Structure (`automod_words.json`)
```json
{
  "default_banned_words": [
    "badword1",
    "badword2",
    "spam phrase"
  ]
}
```

---

## 2. Auto-Role Assignment & Gatekeeper (`autorole.py`)

**Permissions Required:** `Manage Roles` *(administrators & moderators only)*

### Overview & Verification Workflows
The Auto-Role system manages member onboarding and server entry. It supports three operational modes:

* **Instant Auto-Grant:** Automatically assigns a designated role to new members upon joining.
* **Button Verification Panel:** Displays an interactive button panel in a welcome or rules channel. Members click **Accept Rules & Verify** to receive their role.
* **Passcode Gatekeeper:** Restricts entry until members submit a hidden server passcode using `/verify <code>`.

### Management Commands
| Command | Description | Example Usage |
| :--- | :--- | :--- |
| `/set_autorole` | Configures the default role granted on join or upon verification. | `/set_autorole role: @Member` |
| `/setup_gatekeeper_button` | Deploys an interactive verification panel in the active channel. | `/setup_gatekeeper_button role: @Verified` |
| `/set_gatekeeper_code` | Configures the secret passcode required for gatekeeper access. | `/set_gatekeeper_code code: SecretRuleCode2026` |

### Member Commands
| Command | Description | Example Usage |
| :--- | :--- | :--- |
| `/verify` | Submits the server passcode to unlock access. | `/verify code: SecretRuleCode2026` |

### Configuration Structure (`autorole_config.json`)
```json
{
  "123456789012345678": {
    "default_role_id": 987654321098765432,
    "gatekeeper_code": "SecretRuleCode2026"
  }
}
```

---

## 3. Mini-Games & Mini-Economy (`minigames.py`)

**Permissions Required:** None *(available to all server members by default)*

### Economy & Daily Rewards
Each member starts with an automatic starting balance of 100 coins. Users can collect daily rewards and check their wallet at any time:

* **Daily Rewards:** Claims a daily bonus of 100–250 coins with a strict 24-hour cooldown timer per user.
* **Wallet Balance:** Displays the user's current coin balance in chat.

### Member Commands
| Command | Description | Example Usage |
| :--- | :--- | :--- |
| `/daily` | Claims a daily bonus of 100–250 coins (24-hour cooldown). | `/daily` |
| `/balance` | Displays your current coin balance in chat. | `/balance` |
| `/coinflip` | Wager coins on a 50/50 flip (Heads or Tails). Double your bet on a win! | `/coinflip choice: Heads bet: 50` |
| `/blackjack` | Play a live hand of Blackjack against the dealer using interactive Hit and Stand buttons. Natural Blackjack pays 3:2! | `/blackjack bet: 100` |

### Data Persistence (`minigames_data.json`)
```json
{
  "123456789012345678": {
    "balance": 350,
    "last_daily": 1755500000.0
  }
}
```
