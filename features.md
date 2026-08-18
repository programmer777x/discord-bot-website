# Discord Bot Feature Documentation

---

## 1. Auto-Role Assignment & Gatekeeper (`autorole.py`)

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
