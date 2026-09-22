<!--suppress HtmlDeprecatedAttribute, HtmlUnknownTarget -->
<div align="center">

# IBM File Manager for z/OS&reg;

[![GitHub Issues](https://img.shields.io/github/issues/IBM/fm-vs-code-extension?logo=GitHub)][github-issues]
[![VS Marketplace](https://vsmarketplacebadges.dev/version-short/IBM.zfilemanager.svg)][vscode-fm]
[![IBM ADFz Extension Pack](https://img.shields.io/badge/IBM-ADFz%20Extension%20Pack-blue)][vscode-pack]
[![IBM Support](https://img.shields.io/badge/IBM-Support-white)][ibm-support]

</div>

The IBM File Manager for z/OS&reg; VS Code extension works in conjunction with the
[Zowe Explorer][vscode-zowe] VS Code extension. IBM File Manager for z/OS&reg; provides flexible,
user-friendly tools for enhanced file processing when working with z/OS data sets.

This comprehensive solution provides intuitive interfaces for accessing, editing, and managing
data sets and files on z/OS systems, and is a modern alternative to working with IBM File Manager
outside the existing ISPF or Eclipse-based clients.

> Simplify your installation experience by using newly bundled extension packs that contain
> IBM File Manager for z/OS as well as other extensions available for [ADFz][vscode-pack] customers.

## Table of contents

- [Changelog](#changelog)
- [Requirements](#requirements)
- [Integration with Zowe Explorer](#integration-with-zowe-explorer)
- [Configuring the extension](#configuring-the-extension)
- [Using the extension](#using-the-extension)
- [Getting help](#getting-help)

## Changelog

See [CHANGELOG.md](./CHANGELOG.md).

## Requirements

### General requirements

- Assumes knowledge of the IBM File Manager for z/OS&reg; product [installation][fm-install] and [features][fm-docs].
- The File Manager VS Code extension connectivity to File Manager host is similar to using
  the Application Delivery Foundation for z/OS&reg; Common Component (ADFzCC) server:
  - Assumes knowledge of how to [install][cc-install] and [configure][cc-docs]
    the ADFz Common Component server.
  - [ADFz Common Component][cc-customize] must use the [AT-TLS][cc-attls] feature
    when configuring TLS support.

### Host requirements

- [IBM File Manager for z/OS&reg;][fm-home] `16.1.0`+
- [IBM Application Delivery Foundation for z/OS&reg; Common Component][cc-docs] `1.10.0`+
  - You must configure and deploy at least one ADFz Common Component server on the host you intend
    to use with the extension.

### VS Code requirements

- [VS Code][vscode] `1.108.0`+
- [Zowe Explorer][vscode-zowe] `3.2.0`+
  - Assumes the user is familiar with the Zowe Explorer extension before using the IBM File Manager extension.

## Integration with Zowe Explorer

The IBM File Manager extension builds on the strong foundation provided by Zowe Explorer.
To preserve the familiar Zowe Explorer user experience, it purposefully avoids contributing highly
customized UI elements whenever possible. Instead, it enhances your current workspace by:

- Reusing your Zowe profiles configuration to manage local and remote resources.
- Adding new functionality directly to Zowe Explorer's existing **Data Sets** view.
- Integrating additional information directly into Zowe Explorer's existing **Attributes** view.

See the [Getting help](#zowe-explorer-issues) section to report issues related to the Zowe Explorer extension.

## Configuring the extension

Configure the following settings under **IBM File Manager** in VS Code Settings.

### Page Size

Use the **Page Size** setting to configure the number of records shown on each page by the Formatted Editor.

### Column Ruler

Use the **Show Ruler** setting to show or hide the column ruler in the Unformatted Editor.

### Input Mode

> **Important:** this is an experimental feature

The **Synchronize Input Mode** setting synchronizes the editor insert or overtype mode with VS Code.
Restart VS Code after changing this setting.

### Character sets

The extension supports decoding and encoding character data using the following character sets:

```text
IBM037  IBM930   IBM1144
IBM273  IBM937   IBM1146
IBM277  IBM939   IBM1147
IBM278  IBM1047  IBM1390
IBM280  IBM1141  IBM1399
IBM285  IBM1142
IBM297  IBM1143
```

> **Important:** DBCS (Double-Byte Character Set) support is still rough around the edges
> and may not work correctly in all cases.

## Using the extension

### Configuring the ADFz Common Component connection

Before you begin, all previously listed [requirements](#requirements) must be satisfied.

1. If necessary, create at least one Zowe profile.
2. Open the Zowe Explorer tool window.
3. Right-click the Zowe profile that matches the z/OS subsystem where the ADFz Common Component server runs.
4. Select **Application Delivery Foundation for z/OS** > **Configure connection**.
5. Enter the ADFz Common Component server port, username, password or pass token, and debug mode.

You are now ready to use the IBM File Manager VS Code extension.

> Note: if you access a File Manager feature before configuring the ADFz Common Component connection,
> you are prompted to provide the required connection information. This prompt occurs only during the
> first access.

For more information on ADFz Common Component connections, see the relevant chapter in the
[IBM ADFz Common Component for z/OS][vscode-cc] extension documentation.

### Opening and editing data sets

Open a data set or member from the Zowe Explorer **Data Sets** tree by right-clicking it and selecting
**IBM File Manager** > **Open Data Set (Formatted Editor)**. You can also run
**IBM File Manager: Open Data Set (Formatted Editor)** from the command palette.

The opening wizard lets you choose the session type and character set. Opening a data set without a
template uses the Unformatted Editor. Selecting a template opens the data set in the Formatted Editor.

Both editors support **View** and **Edit** sessions.

The Unformatted Editor supports essential navigation commands such as `TOP`, `BOTTOM`, `UP`,
`DOWN` and `LOCATE`, and offers toolbar options to display hex line representations, and to enable
a column ruler. It also offers editor actions to work with records directly. All other related
editor actions, such as Cut, Copy and Paste, are supported across different opened data set
sessions in Unformatted mode.

The Formatted mode editor supports the same set of navigation commands, along with the hex
representation of text displayed in table cells.

### Managing templates

Open a template from the Zowe Explorer **Data Sets** tree by selecting **IBM File Manager** >
**Open Template (Template Editor)**, or run **IBM File Manager: Open Template (Template Editor)** from
the command palette. The Template Editor supports layout selection, segmentation, layout criteria,
and Held or Selected column settings.

Run **IBM File Manager: Lock Template** and **IBM File Manager: Unlock Template** from the command palette
to programmatically lock and unlock templates.

### Allocating data sets

Run **IBM File Manager: Allocate Data Set** from the command palette to allocate a data set, or select
**IBM File Manager** > **Allocate Data Set** for an existing data set in the Zowe Explorer **Data Sets**
tree.

When started from the **Data Sets** tree, the allocation form uses the selected data set's properties
as a starting point.

### Exporting data sets

Export a data set or member to a local `CSV` or `XML` file by selecting **IBM File Manager** >
**Export Data Set** in the Zowe Explorer **Data Sets** tree, or by running **IBM File Manager: Export
Data Set** from the command palette. The export wizard prompts for the data set, template, character
set, and output format.

### Importing data sets

Import a local `CSV` file into a data set or member by selecting **IBM File Manager** > **Import Data Set**
in the Zowe Explorer **Data Sets** tree, or by running **IBM File Manager: Import Data Set** from the
command palette. The import wizard prompts to select the `CSV` file, template, character set, destination,
and import options.

> **Important:** Import Data Set might not work correctly with IBM File Manager host versions older than
> `16.1.5` or `17.1.0`.

### Viewing resource attributes

Select **IBM File Manager** > **Show Resource Attributes** from a data set or member in the Zowe Explorer
**Data Sets** tree. The command opens the Zowe Explorer **Attributes** view with File Manager-provided
information for the selected resource.

## Getting help

To ask questions or report issues related to the installation, configuration,
or use of this extension, contact [IBM Support][ibm-support].

### Zowe Explorer issues

The IBM File Manager extension depends on Zowe Explorer.  
Issues might originate from core Zowe Explorer functionality rather than the extension itself.
Examples include:

- Data set and Unix System Services (USS) file browsing
- Job management and submission
- Base Zowe Explorer commands and views

Report issues that are specific to Zowe Explorer to the Zowe Explorer [issue tracker][zowe-support].

To determine the source of an issue and the appropriate reporting channel, consider the following:

- Error notifications include the extension name.
- Log entries displayed in the **Output** view are categorized by extension.

[vscode]: https://code.visualstudio.com
[vscode-pack]: https://marketplace.visualstudio.com/items?itemName=IBM.application-delivery-foundation-for-zos-vscode-extension-pack
[vscode-cc]: https://marketplace.visualstudio.com/items?itemName=IBM.zcommoncomponent
[vscode-fm]: https://marketplace.visualstudio.com/items?itemName=IBM.zfilemanager
[vscode-zowe]: https://marketplace.visualstudio.com/items?itemName=Zowe.vscode-extension-for-zowe
[fm-home]: https://www.ibm.com/products/file-manager-for-zos
[fm-docs]: https://help.blueproddoc.com/filemanager/16.1.0/en/base/index.html
[fm-install]: https://help.blueproddoc.com/filemanager/hadlg10_FM_Program_Directory_V161.pdf
[cc-docs]: https://help.blueproddoc.com/adfz_common_components/1.10.0/en/index.html
[cc-install]: https://help.blueproddoc.com/adfz_common_components/hvwr1a0_ADFzCC_Program_Directory_V1.10.pdf
[cc-customize]: https://help.blueproddoc.com/adfz_common_components/1.10.0/en/svrauth.html
[cc-attls]: https://help.blueproddoc.com/adfz_common_components/1.10.0/en/attls.html
[github-issues]: https://github.com/IBM/fm-vs-code-extension/issues
[ibm-support]: https://www.ibm.com/mysupport/
[zowe-support]: https://github.com/zowe/zowe-explorer-vscode/issues
