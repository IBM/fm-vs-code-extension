# IBM File Manager for z/OS&reg; Beta

The IBM File Manager for z/OS&reg; VS Code extension works in conjunction with the [Zowe Explorer][link-zowe] VS Code extension.
IBM File Manager for z/OS&reg; provides flexible, user-friendly tools for enhanced file processing when working with z/OS data sets.

This comprehensive solution provides intuitive interfaces for accessing, editing, and managing datasets and files on z/OS systems,
and is a modern alternative to work with IBM File Manager outside the existing Eclipse-based client.

## General requirements

- Assumes knowledge of IBM File Manager for z/OS&reg; product [installation][link-fm-install] and [features][link-features]
- The File Manager VS Code extension connectivity to File Manager host is similar to using
  the Application Delivery Foundation for z/OS&reg; common component (ADFzCC) server
  - Assumes knowledge of how to [install][link-adfz-install] and [configure][link-adfz-config]
    the Application Delivery Foundation for z/OS&reg; common component server
  - [ADFzCC][link-adfz-customize] must use the [AT-TLS][link-adfz-attls] feature when configuring TLS support

## VS Code extension requirements

- [VS Code][link-vscode] `1.90.0`+
- [Zowe Explorer][link-zowe] `2.17.0`+
  - Assumes that the user has knowledge of the Zowe Explorer extension before using the IBM File Manager extension

## Beta host requirements

- [IBM File Manager for z/OS&reg;][link-fm] `15.1.4`+
- [IBM Application Delivery Foundation for z/OS&reg; Common Components][link-adfz-docs] `1.9.4`+
  - There must be at least one ADFz common component server configured and deployed
    on the host that you want to work with

## Beta limitations

- Does not support all platforms that Zowe Explorer supports:
  - &#9989; Windows
  - &#10060; Linux (untested)
  - &#10060; macOS (untested)
- Does not support all Integrated Development Environments:
  - &#9989; VS Code
  - &#10060; Eclipse Theia (untested)
  - &#10060; Eclipse Che (untested)
  - &#10060; Red Hat CodeReady Workspaces (untested)
- Does not support Multi-Factor Authentication (MFA)
- Does not ask to trust self-signed certificates when connecting to the ADFz common component server

## Beta features

This is a beta version of the IBM File Manager extension and does not have the full
functionality of the ISPF File Manager client, or the Eclipse File Manager client.

Itemized below are the features supported and not supported in broad terms.

### Character mode editor

- Viewing and editing Data Sets using the character mode editor
  - Hex values display
  - Column ruler
  - Record selection, cut, copy, paste, insertion and deletion

### ADFz Common Component server connections

- Associate an ADFz port with a Zowe Profile
- Remove the association between an ADFz port and a Zowe profile

## Unsupported Features

- Utility functions for the character mode editor such as Find/Replace, Exclude, Sort
- Editing of hex values
- Toggling of suppressed records
- Formatted editor with templates
- Template editor to modify templates
- Batch operations
- Other File Manager commands or utilities (masking, import, export, extract, merge, compare, etc.)
- Editing of CICS, DB2, IMS, MQ resources

## Known issues

- Opening a file in _edit_ mode in the File Manager character mode editor while that file has already been opened in _edit_ mode
  by another File Manager editor session (VS Code, Eclipse or ISPF), will result in an error message indicating that the file
  is locked and cannot be opened. When the other edit session ends and releases the lock, you'd normally be able to open it
  in _edit_ mode in your VS Code File Manager editor session. However, the "locked" error will still be reported and the file won't open.
  Currently, the only resolution is to restart VS Code. This issue will be resolved in a future beta release.

# Getting started

## Specifying the ADFz connection port

Before you begin, all the above requirements must be fulfilled.

1. Open VS Code
2. If necessary, create at least one Zowe profile: team configuration profile or v1 profile (deprecated)
3. Switch to the Zowe Explorer toolwindow
4. Right-click on the profile that matches the z/OS subsystem your ADFz common component server is running on
5. From the _Application Delivery Foundation for z/OS_ menu item, choose _Configure ADFz port_
6. Enter the port that your ADFz common component server is configured to use

You are now ready to use the IBM File Manager VS Code extension.

**NOTE**: if you access a File Manager feature before configuring the port number,
you will be prompted to specify the port the first time only.

### File Manager editor

Data sets under the Zowe Explorer tree view can be opened in the File Manager character mode
editor (without a template) in read-only or edit mode.

The editor supports essential navigation commands such as TOP, BOTTOM, UP, DOWN and LOCATE,
and offers toolbar options to display hex line representations, and to enable the column ruler.
It also offers handy code actions to work with records.

All other related editor actions, such as Cut, Copy, and Paste, are supported across different
opened data set sessions.

The editor's cache page size can be configured via the extension's VS Code Settings.

### File Manager VS Code command palette

Currently, the IBM File Manager for z/OS extension only supports the "Open Data Set" command to open
a data set in the File Manager character mode editor without having to navigate the Zowe Explorer tree view.

[link-vscode]: https://code.visualstudio.com
[link-zowe]: https://marketplace.visualstudio.com/items?itemName=Zowe.vscode-extension-for-zowe
[link-fm]: https://www.ibm.com/products/file-manager-for-zos
[link-adfz-docs]: https://help.blueproddoc.com/adfz_common_components/welcome/index.html#
[link-fm-install]: https://help.blueproddoc.com/filemanager/i1356321_Program_Directory_V15.pdf
[link-features]: https://help.blueproddoc.com/filemanager/welcome/index.html
[link-adfz-install]: https://help.blueproddoc.com/adfz_common_components/i1356270_Program_Directory_V1.9.pdf
[link-adfz-config]: https://help.blueproddoc.com/adfz_common_components/1.9.0/en/index.html
[link-adfz-customize]: https://help.blueproddoc.com/adfz_common_components/1.9.0/en/svrauth.html
[link-adfz-attls]: https://help.blueproddoc.com/adfz_common_components/1.9.0/en/attls.html
