# 16.1.326042215 (release)

- No changes.

# 16.1.326040713 (release)

- Added support for the IBM-277 and IBM-1142 character sets (Denmark/Norway).

# 16.1.326030310 (release)

### Unformatted Editor

- Fixed a data corruption issue caused by an invalid undo/redo stack when creating a new record.

### Templates

- Improved error handling when locking or unlocking a non-existent template.
- Improved template editor start-up time. Opening a template is now almost immediate.

### Other Changes

- Improved multi-step Command Palette workflows by adding visible step counts and in-place progress
  indication while performing background validation of user input, avoiding shifting focus from the
  Command Palette to a progress notification.
- Fixed Zowe Explorer for IBM CICS Transaction Server extensions registration to handle cases where
  the CICS extension is installed or activated after the File Manager extension, or where the
  File Manager extension is uninstalled or deactivated.

### Requirements

- Changed the minimum supported Zowe Explorer version to 3.2.0 to improve compatibility.
- Raised the minimum supported VS Code version to 1.101.0.

### Blocked Items

- Native VS Code Undo/Redo integration for the Unformatted and Formatted editors.  
  Blocked by an upstream VS Code issue: https://github.com/microsoft/vscode/issues/296528

# 16.1.226011417 (release)

- Extended Zowe Explorer for IBM CICS Transaction Server to support opening data sets
  and members from CICS-contributed actions.
- Extended Zowe Explorer's Attributes view (via **Show Attributes**) to include attributes
  provided by File Manager.
- Added an **IBM File Manager** > **Show Resource Attributes** context menu action to
  display PDS member attributes, due to a current limitation in the Zowe Explorer extension API.
- Improved the usability of template **locking** and **unlocking** by adding progress
  notifications and additional Command Palette actions.
- Added support for the IBM-285 and IBM-1146 character sets (UK/Ireland).
- Added support for the IBM-280 and IBM-1144 character sets (Italy).
- Improved and consolidated the extension's overall quality.

# 16.1.225110416 (release)

### Formatted Editor

- Added support for the IBM-278, IBM-937, and IBM-1143 character sets.
- Improved the usability of the (un)formatted editor header.  
  The command input now maintains a minimum usable size, and the layout selector displays
  the full layout name when expanded, even for long names.

# 16.1.225101614 (release)

### Template Editor

- Reworked the interface to match the VS Code UI style and correctly support all themes.
- Improved data rollback handling if an error occurs while saving.
- Added a loading spinner while saving or loading data.

### Formatted Editor

- Fixed saving changes for files displayed using segmented templates.
- Disabled record insertion and deletion for files displayed using segmented templates.

### Other

- Sorted Zowe profile and charset selections by last used, aligning the Command Palette behavior with other extensions.
- Improved the overall presentation and consistency of UI elements in custom editors.

# 16.1.125082220 (release)

- Added brief descriptions to charsets in the selection prompt.
- Prevented the template data set name prompt from closing when it loses focus.

# 16.1.125072314 (release)

- Added support for pass tokens (e.g., for Multi-factor Authentication).
- Improved the Template Editor with minor UI enhancements. Additional improvements are planned for future updates.

# 16.1.25061109 (release)

- Increased the minimum required Zowe Explorer version to `3.1.0`.
- Added support for opening data sets and members with more character sets (e.g., IBM-273, IBM-1147, IBM-930, IBM-1390).
- Fixed an issue where data sets couldn't always be opened from the Zowe Explorer tree due to incorrect name parsing.
- Enabled logging for protocol-level interactions with the z/OS host.

# 16.1.25032015 (release)

- Implemented cell editing capabilities for the formatted editor view.
- Implemented an initial version of the template editor (the UI will be redesigned during following iterations).
- Switched the formatted editor cells to masked characters (non-printable characters are replaced by a placeholder)
- Fixed the start column logic in the formatted editor view.  
  Previously, column 1 would correspond to column 2 in the underlying implementation,
  and changing template via the dropdown would not reset the value.

# 16.1.25021416 (pre-release)

- Fixed the data set name validation to allow specifying a PDS member.
- Updated the product's icon.

# 16.1.25013008 (pre-release)

- Added a read-only formatted editor view to visualize data sets in a tabular format (limited functionalities).
- Cleaned up the extension's code.

# 16.1.24121614 (pre-release)

- Fixed an issue in the character-mode editor where inserting and saving multiple records
  failed to preserve their original order.
- Reduced the size of the packaged standalone Monaco Editor by improving the bundling process.
- Improved protocol APIs to deliver better performance and reliability.
