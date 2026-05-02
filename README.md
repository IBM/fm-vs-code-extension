# IBM File Manager for z/OS&reg;

<div align="center">

[![GitHub Issues](https://img.shields.io/github/issues/IBM/fm-vs-code-extension?logo=GitHub)][link-fm-vsc-issues]
[![VS Marketplace](https://vsmarketplacebadges.dev/version-short/IBM.zfilemanager.svg)][link-fm-extension]
[![IBM ADFz Extension Pack](https://img.shields.io/badge/IBM-ADFz%20Extension%20Pack-blue)][link-ext-pack]
[![IBM Support](https://img.shields.io/badge/IBM-Support-white)][link-support]

</div>

The IBM File Manager for z/OS&reg; VS Code extension works in conjunction with the
[Zowe Explorer][link-zowe] VS Code extension. IBM File Manager for z/OS&reg; provides flexible,
user-friendly tools for enhanced file processing when working with z/OS data sets.

This comprehensive solution provides intuitive interfaces for accessing, editing, and managing
datasets and files on z/OS systems, and is a modern alternative to work with IBM File Manager
outside the existing ISPF or Eclipse-based clients.

> Simplify your installation experience by using newly bundled extension packs that contain
> IBM File Manager for z/OS as well as other extensions available for [ADFz][link-ext-pack] customers.

## Table of contents

- [Changelog](#changelog)
- [General requirements](#general-requirements)
- [Host requirements](#host-requirements)
- [VS Code requirements](#vs-code-requirements)
- [Integration with Zowe Explorer](#integration-with-zowe-explorer)
- [Features](#features)
- [Unsupported features](#unsupported-features)
- [Getting started](#getting-started)
- [Getting help](#getting-help)

## Changelog

See [CHANGELOG.md](./CHANGELOG.md).

## General requirements

- Assumes knowledge of IBM File Manager for z/OS&reg; product [installation][link-fm-install]
  and [features][link-features].
- The File Manager VS Code extension connectivity to File Manager host is similar to using
  the Application Delivery Foundation for z/OS&reg; Common Component (ADFzCC) server:
  - Assumes knowledge of how to [install][link-adfz-install] and [configure][link-adfz-config]
    the ADFz Common Component server.
  - [ADFz Common Component][link-adfz-customize] must use the [AT-TLS][link-adfz-attls] feature
    when configuring TLS support.

## Host requirements

- [IBM File Manager for z/OS&reg;][link-fm] `16.1.0`+
- [IBM Application Delivery Foundation for z/OS&reg; Common Components][link-adfz-docs] `1.10.0`+
  - You must configure and deploy at least one ADFz Common Component server on the host you intend
    to use with the extension.

## VS Code requirements

- [VS Code][link-vscode] `1.101.0`+
- [Zowe Explorer][link-zowe] `3.2.0`+
  - Assumes the user is familiar with the Zowe Explorer extension before using the IBM File Manager extension.

## Integration with Zowe Explorer

The IBM File Manager extension builds on the strong foundation provided by Zowe Explorer.
To preserve the familiar Zowe Explorer user experience, it purposefully avoids contributing highly
customized UI elements whenever possible. Instead, it enhances your current workspace by:

- Reusing your Zowe profiles configuration to manage local and remote resources.
- Adding new functionality directly to Zowe Explorer's existing **Data Sets** and **Unix System Services** views.
- Integrating additional information directly into Zowe Explorer's existing **Attributes** view.

See the [Getting help](#zowe-explorer-issues) section to report issues related to the Zowe Explorer extension.

## Features

The current version of the IBM File Manager extension does not have the full
functionality of the ISPF File Manager client, or the Eclipse File Manager client.

The feature set is strictly related to the File Manager Base component.  
Itemized below are the features supported and not supported in broad terms.

### Supported character sets

The extension currently supports decoding and encoding character data using the following character sets:

```text
IBM037  IBM930   IBM1144
IBM273  IBM937   IBM1146
IBM277  IBM939   IBM1147
IBM278  IBM1047  IBM1390
IBM280  IBM1141  IBM1399
IBM285  IBM1142
IBM297  IBM1143
```

### File Manager editor

The File Manager editor can be used in two modes:

- Viewing and editing data sets using the **Unformatted** mode editor
  - Hex values display
  - Column ruler
  - Navigation commands
  - Record selection, cut, copy, paste, insertion and deletion
  - Undo history

- Viewing and editing data sets using the **Formatted** mode editor
  - Hex values display
  - Navigation commands
  - Tabular record editing, with record insertion and deletion

### Template editor

The template editor offers various options for editing existing templates used with the
File Manager editor in its Formatted mode.

The current implementation offers the following feature set:

- Layout selection
- Segmentation toggle
- Layout criteria editing
- Held and Selected column toggle

### ADFz Common Component connections

- Associate an ADFz Common Component connection with a Zowe Profile
- Remove the association between an ADFz Common Component connection and a Zowe profile

## Unsupported features

### Secure connections

- Trust manager for certificates used when connecting to the ADFz Common Component server

### File Manager editor

- Utility functions for the Unformatted and Formatted editor such as Find/Replace, Exclude, Sort
- Editing of hex values
- Toggling of excluded or suppressed records
- Batch operations
- Other File Manager commands or utilities (masking, import, export, extract, merge, compare, etc.)
- Editing of CICS, DB2, IMS, MQ resources

### Known issues

- Opening a file in **Edit** mode in the File Manager Unformatted editor while that file has already
  been opened in **Edit** mode by another File Manager editor session (VS Code, Eclipse or ISPF), will
  result in an error message indicating that the file is locked and cannot be opened. When the other
  edit session ends and releases the lock, you'd normally be able to open it in **Edit** mode in your
  VS Code File Manager editor session. However, the "locked" error will still be reported and the file
  won't open. Currently, the only solution is to restart VS Code.

  This issue will be fixed in a future release.

## Getting started

### Configuring the ADFz Common Component connection

Before you begin, all the above requirements must be fulfilled.

1. Open VS Code.
2. If necessary, create at least one Zowe profile: team configuration profile or v1 profile (deprecated).
3. Switch to the Zowe Explorer tool window.
4. Right-click on the profile that matches the z/OS subsystem your ADFz Common Component server is running on.
5. From the **Application Delivery Foundation for z/OS** menu item, choose **Configure connection**.
6. Enter the connection information for the ADFz Common Component server.

You are now ready to use the IBM File Manager VS Code extension.

> Note: if you access a File Manager feature before configuring the ADFz Common Component connection,
> you are prompted to provide the required connection information. This prompt occurs only during the
> first access.

### File Manager editor

Data sets under the Zowe Explorer tree view can be opened in the File Manager editor in both
Unformatted mode (characters view) and Formatted mode (with a template applied). Both modes support
**View** and **Edit** sessions.

The Unformatted mode editor supports essential navigation commands such as `TOP`, `BOTTOM`, `UP`,
`DOWN` and `LOCATE`, and offers toolbar options to display hex line representations, and to enable
a column ruler. It also offers editor actions to work with records directly. All other related
editor actions, such as Cut, Copy and Paste, are supported across different opened data set
sessions in Unformatted mode.

The Formatted mode editor supports the same set of navigation commands, along with the hex
representation of text displayed in table cells. The Cut, Copy and Paste operations are
currently not supported for entire records.

Use the **IBM File Manager** > **Page Size** setting to configure the editor's cache page size.

### Command Palette commands

The IBM File Manager extension adds new commands to the VS Code Command Palette.

#### Open Data Set

This command opens a data set or data set's member in the Unformatted or Formatted mode editor,
depending on whether a template name is inputted while stepping through the palette wizard.

#### Open Template

This command opens a template in the Template editor.

#### Lock Template

This command locks a template.

> Note: your user must have the correct authority over the resource.

#### Unlock Template

This command unlocks a template.

> Note: your user must have the correct authority over the resource.

#### Show Resource Attributes

This command opens the Zowe Explorer **Attributes** view with additional File Manager-provided
data for a specific data set or data set's member name.

## Getting help

To ask questions or report issues related to the installation, configuration,
or use of this extension, contact [IBM Support][link-support].

### Zowe Explorer issues

The IBM File Manager extension depends on Zowe Explorer.  
Issues might originate from core Zowe Explorer functionality rather than the extension itself.
Examples include:

- Data set and Unix System Services (USS) file browsing
- Job management and submission
- Base Zowe Explorer commands and views

Report issues that are specific to Zowe Explorer to the Zowe Explorer [issue tracker][link-zowe-support].

To determine the source of an issue and the appropriate reporting channel, consider the following:

- Error notifications include the extension name.
- Log entries displayed in the **Output** view are categorized by extension.

[link-fm-extension]: https://marketplace.visualstudio.com/items?itemName=IBM.zfilemanager
[link-vscode]: https://code.visualstudio.com
[link-zowe]: https://marketplace.visualstudio.com/items?itemName=Zowe.vscode-extension-for-zowe
[link-fm-vsc-issues]: https://github.com/IBM/fm-vs-code-extension/issues
[link-fm]: https://www.ibm.com/products/file-manager-for-zos
[link-fm-install]: https://help.blueproddoc.com/filemanager/hadlg10_FM_Program_Directory_V161.pdf
[link-features]: https://help.blueproddoc.com/filemanager/16.1.0/en/base/index.html
[link-adfz-docs]: https://help.blueproddoc.com/adfz_common_components/welcome/index.html
[link-adfz-install]: https://help.blueproddoc.com/adfz_common_components/hvwr1a0_ADFzCC_Program_Directory_V1.10.pdf
[link-adfz-config]: https://help.blueproddoc.com/adfz_common_components/1.10.0/en/index.html
[link-adfz-customize]: https://help.blueproddoc.com/adfz_common_components/1.10.0/en/svrauth.html
[link-adfz-attls]: https://help.blueproddoc.com/adfz_common_components/1.10.0/en/attls.html
[link-ext-pack]: https://marketplace.visualstudio.com/items?itemName=IBM.application-delivery-foundation-for-zos-vscode-extension-pack
[link-support]: https://www.ibm.com/mysupport/
[link-zowe-support]: https://github.com/zowe/zowe-explorer-vscode/issues
