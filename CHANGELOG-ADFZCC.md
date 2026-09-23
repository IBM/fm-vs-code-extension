# 16.1.426091513 - September 2026 (release)

- No changes.

# 16.1.426081911 - August 2026 (release)

- 🛠️ Raised the minimum supported VS Code version to 1.108.0.

# 16.1.426071615 - July 2026 (release)

- ✨ Improved the ADFzCC connection removal flow from the **Manage connections** Command Palette wizard
  by prompting for removal confirmation directly in the wizard instead of showing a notification.
- 🧪 Added experimental support for specifying ADFzCC connection configuration directly in `zowe.config.json`.
  You can now define the ADFzCC-specific `port` and `debug` values alongside other profile `properties` using
  the `adfzcc` object. This makes it easier to store, share, and version ADFzCC configuration
  as part of your workspace setup.

  ```json
  "myprofile": {
    "type": "zosmf",
    "properties": {
      "host": "myhostname",
      "port": 443,
      "adfzcc": {
        "port": 1234,
        "debug": false
      }
    }
  }
  ```

  Because this feature is experimental, the configuration format may change or be removed
  based on your feedback.

# 16.1.426060911 - June 2026 (release)

- Added ADFzCC credentials verification to the connection configuration wizard that appears
  when Zowe profile credentials are updated.
- Added a new **Credentials: Prompt on Profile Update** setting to optionally turn off the
  ADFzCC credentials prompt shown when Zowe profile credentials change.
- Removed the **Remove all connections** Command Palette command.  
  Removing all ADFzCC connections at once is an uncommon and potentially disruptive action,
  so it is no longer exposed to users.
- Improved the overall extension reliability with multiple internal refactorings.

# 16.1.326042215 - April 2026 (release)

- Improved synchronization between Zowe profiles and ADFzCC connections.  
  Changes to `zowe.config.json` profile properties are now reflected immediately.

# 16.1.326040713 - April 2026 (release)

- No changes.

# 16.1.326030310 - March 2026 (release)

- Added a new Command Palette action **Manage connections**, to configure or remove ADFzCC connections
  without using the Zowe Explorer tree view.
- Improved multi-step Command Palette workflows by adding visible step counts and in-place progress
  indication while performing background validation of user input, avoiding shifting focus from the
  Command Palette to a progress notification.

### Requirements

- Changed the minimum supported Zowe Explorer version to 3.2.0 to improve compatibility.
- Raised the minimum supported VS Code version to 1.101.0.

# 16.1.226011417 - January 2026 (release)

- No user-facing changes.  
  This release focuses on internal refactors to improve and consolidate the extension's quality.

# 16.1.225110416 (release)

- No changes.

# 16.1.225101614 (release)

- Added a **Debug** option to the ADFzCC connection configuration wizard, allowing connections
  to start with debug tracing enabled.

# 16.1.125082220 (release)

- Unified and simplified ADFzCC connection management: port number, username, and password can now
  be configured via **Application Delivery Foundation for z/OS** > **Configure connection**.
- Refactored the (currently internal) Extension API to centralize all features under a single entry point.

# 16.1.125072314 (release)

- Added support for pass tokens (e.g., for Multi-factor Authentication).
- Introduced a new `CredentialStore` for securely storing Common Component server credentials.
- Introduced a new `SecretStore` for managing secrets scoped to the extension's namespace.
- Ensured Common Component server credentials are reset when the linked Zowe profile credentials are updated.
- Ensured the extension activates when its API is accessed.

# 16.1.25061109 (release)

- Increased the minimum required Zowe Explorer version to `3.1.0`.

# 16.1.25032015 (release)

- Applied minor changes to menu labels.

# 16.1.25021416 (pre-release)

- Fixed a compatibility issue with Zowe Explorer 3.1.0, and restored ADFz context menu items over the Zowe tree.
- Updated the product's icon.

# 16.1.25013008 (pre-release)

- Cleaned up the extension's code.

# 16.1.24121614 (pre-release)

- Notify deletion listeners when clearing the ADFz information store.
