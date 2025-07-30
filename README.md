# IBM File Manager for z/OS&reg;

The IBM File Manager for z/OS&reg; VS Code extension works in conjunction with the [Zowe Explorer][link-zowe] VS Code extension.
IBM File Manager for z/OS&reg; provides flexible, user-friendly tools for enhanced file processing when working with z/OS data sets.

This comprehensive solution provides intuitive interfaces for accessing, editing, and managing datasets and files on z/OS systems,
and is a modern alternative to work with IBM File Manager outside the existing Eclipse-based client.

**Simplify your installation experience by using newly bundled extension packs that contain IBM File Manager for z/OS
as well as other extensions available for [ADFz][link-ext-pack] customers.**

## General requirements

- Assumes knowledge of IBM File Manager for z/OS&reg; product [installation][link-fm-install] and [features][link-features]
- The File Manager VS Code extension connectivity to File Manager host is similar to using
  the Application Delivery Foundation for z/OS&reg; common component (ADFzCC) server
  - Assumes knowledge of how to [install][link-adfz-install] and [configure][link-adfz-config]
    the Application Delivery Foundation for z/OS&reg; common component server
  - [ADFzCC][link-adfz-customize] must use the [AT-TLS][link-adfz-attls] feature when configuring TLS support

## VS Code extension requirements

- [VS Code][link-vscode] `1.90.0`+
- [Zowe Explorer][link-zowe] `3.1.0`+
  - Assumes that the user has knowledge of the Zowe Explorer extension before using the IBM File Manager extension

## Host requirements

- [IBM File Manager for z/OS&reg;][link-fm] `16.1.0`+
- [IBM Application Delivery Foundation for z/OS&reg; Common Components][link-adfz-docs] `1.10.0`+
  - There must be at least one ADFz common component server configured and deployed
    on the host that you want to work with

Note that while `15.1.x` host builds might work, they are **not** officially supported.

### Supported charsets

The extension currently supports decoding and encoding character data using the following character sets:

```text
IBM037  IBM939   IBM1390
IBM273  IBM1047  IBM1399
IBM297  IBM1141
IBM930  IBM1147
```

## Features

The current version of the IBM File Manager extension does not have the full
functionality of the ISPF File Manager client, or the Eclipse File Manager client.

The feature set is strictly related to the File Manager Base component.  
Itemized below are the features supported and not supported in broad terms.

### File Manager editor

The File Manager editor can be used in two modes:

- Viewing and editing data sets using the **character mode** editor

  - Hex values display
  - Column ruler
  - Navigation commands
  - Record selection, cut, copy, paste, insertion and deletion
  - Undo history

- Viewing and editing data sets using the **formatted mode** editor
  - Hex values display
  - Navigation commands
  - Tabular record editing, with record insertion and deletion

### Template editor

The template editor offers various options for editing existing templates used with the
File Manager editor in its formatted mode.

The current implementation offers the following feature set:

- Layout selection
- Segmentation toggle
- Layout criteria editing
- Held and Selected column toggle

### ADFz Common Component server connections

- Associate an ADFzCC port with a Zowe Profile
- Remove the association between an ADFzCC port and a Zowe profile

## Unsupported features

- Trust manager for certificates used when connecting to the ADFzCC server

### File Manager editor

- Utility functions for the character mode and formatted editor such as Find/Replace, Exclude, Sort
- Editing of hex values
- Toggling of excluded or suppressed records
- Batch operations
- Other File Manager commands or utilities (masking, import, export, extract, merge, compare, etc.)
- Editing of CICS, DB2, IMS, MQ resources

### Known issues

- Opening a file in _edit_ mode in the File Manager character mode editor while that file has already been opened in _edit_ mode
  by another File Manager editor session (VS Code, Eclipse or ISPF), will result in an error message indicating that the file
  is locked and cannot be opened. When the other edit session ends and releases the lock, you'd normally be able to open it
  in _edit_ mode in your VS Code File Manager editor session. However, the "locked" error will still be reported and the file won't open.
  Currently, the only resolution is to restart VS Code. This issue will be resolved in a future release.

# Getting started

## Specifying the ADFzCC connection port

Before you begin, all the above requirements must be fulfilled.

1. Open VS Code
2. If necessary, create at least one Zowe profile: team configuration profile or v1 profile (deprecated)
3. Switch to the Zowe Explorer toolwindow
4. Right-click on the profile that matches the z/OS subsystem your ADFz common component server is running on
5. From the **Application Delivery Foundation for z/OS** menu item, choose **Configure port**
6. Enter the port that your ADFz common component server is configured to use

You are now ready to use the IBM File Manager VS Code extension.

NOTE: if you access a File Manager feature before configuring the port number,
you will be prompted to specify the port the first time only.

## File Manager editor

Data sets under the Zowe Explorer tree view can be opened in the File Manager editor in both
character and formatted mode (with a template applied). Both the character and the formatted
modes support _View_ and _Edit_ sessions.

The character mode editor supports essential navigation commands such as `TOP`, `BOTTOM`, `UP`,
`DOWN` and `LOCATE`, and offers toolbar options to display hex line representations, and to enable
a column ruler. It also offers editor actions to work with records directly. All other related
editor actions, such as Cut, Copy and Paste, are supported across different opened data set
sessions in character mode.

The formatted mode editor supports the same set of navigation commands, along with the hex
representation of text displayed in table cells. The Cut, Copy and Paste operations are
currently not supported for entire records.

The editor cache page size can be configured via the extension's VS Code Settings.

### File Manager VS Code command palette

The IBM File Manager for z/OS extension supports the **Open Data Set** palette command to open
a data set in the File Manager editor, and the **Open Template** palette command to open a template
in the Template editor.

[link-vscode]: https://code.visualstudio.com
[link-zowe]: https://marketplace.visualstudio.com/items?itemName=Zowe.vscode-extension-for-zowe
[link-fm]: https://www.ibm.com/products/file-manager-for-zos
[link-fm-install]: https://help.blueproddoc.com/filemanager/hadlg10_FM_Program_Directory_V161.pdf
[link-features]: https://help.blueproddoc.com/filemanager/16.1.0/en/base/index.html
[link-adfz-docs]: https://help.blueproddoc.com/adfz_common_components/welcome/index.html
[link-adfz-install]: https://help.blueproddoc.com/adfz_common_components/hvwr1a0_ADFzCC_Program_Directory_V1.10.pdf
[link-adfz-config]: https://help.blueproddoc.com/adfz_common_components/1.10.0/en/index.html
[link-adfz-customize]: https://help.blueproddoc.com/adfz_common_components/1.10.0/en/svrauth.html
[link-adfz-attls]: https://help.blueproddoc.com/adfz_common_components/1.10.0/en/attls.html
[link-ext-pack]: https://marketplace.visualstudio.com/items?itemName=IBM.application-delivery-foundation-for-zos-vscode-extension-pack
