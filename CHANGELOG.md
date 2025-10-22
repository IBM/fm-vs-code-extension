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
