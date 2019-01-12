---
title: Editors
source: https://github.com/naomiproject/naomi-docs/blob/master/configuration/editors.md
meta:
  - property: og:title
    content: "Editor Guide"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Editors - Different Ways to Simplify Your Textual Configuration

Currently there are several existing solutions, that can help you configuring your Naomi instance in a textual way.
This documentation page can give you some guidance in choosing the right one for you and setting it up.

[[toc]]

## Network Preparations

Any editors used to configure Naomi need to be able to access the configuration files on the remote Naomi host.

This can be achieved by using a [network share](https://en.wikipedia.org/wiki/Shared_resource) set up on the remote host and mounted on your local computer.
The steps required to set up a [network share](https://en.wikipedia.org/wiki/Shared_resource) on your local host computer are specific to the host operation system.
How to setup and use Samba on a Linux system is described in the [Linux article](/docs/installation/linux.html#network-sharing).
If you are using [Naobian](/docs/installation/naobian.html), the network shares are readily configured for you, you only need to mount them locally.

*Attention Windows users:* Directly accessing network shares (UNC paths) is often not supported. Please be sure to mount the network share to a drive letter.

## Naomi VS Code Extension

Naomi VS Code is an extension for the [Visual Studio Code](https://code.visualstudio.com) editor.
You can find it in the [Microsoft Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=naomi.naomi).

  ![Naomi VS Code Extension demo](images/vscode_demo.gif)

### Installation

1. Install [Visual Studio Code](https://code.visualstudio.com/Download) on your desktop computer (not on the Naomi host)
2. Open the extension sidebar. ![Naomi VS Code Extension alternative installation](images/vscode_extensiontab_icon.png)
3. Search for Naomi and install the extension.

[Visit the Extensions GitHub Page for further Informations](https://github.com/naomiproject/naomi-vscode/blob/master/README.md "GitHub Repo for the VS Code Extension")

### Rule Validation

This extension has the ability to check rules and validate them through a so called `Language Server`.
(If you want to know more about this in general look [here](https://langserver.org/).)
The validation needs a running Naomi installation in your environment and can be activated with some simple steps.
You can find all important information in the extensions [readme file](https://github.com/naomiproject/naomi-vscode#validating-the-rules).

## Other Editor Integrations

The here summarized projects provide syntax highlighting for different text editors, but have no _on top_ functionality like the two tools above.

### mcedit

mcedit is an editor which comes with mc (Midnight Commander).
You can find the syntax files and installation instructions on [naomi-mcedit](https://github.com/longshotpro2/naomi-mcedit).

### Notepad++

Notepad++ is a free source code editor for Windows.
Version 6.2 or above is required.
You can find the syntax files on [naomi-samples](https://github.com/longshotpro2/naomi-samples) and install the files like it is described in the [editors documentation](http://docs.notepad-plus-plus.org/index.php/User_Defined_Language_Files#How_to_install_user_defined_language_files).

### Vim

Vim is a text editor in Linux systems.
You can find the syntax file and installation instructions on [naomi-vim](https://github.com/longshotpro2/naomi-vim).

### Nano

Nano is a common editor in Linux systems.
You can find the syntax file and installation instructions on [naominano](https://github.com/longshotpro2/naominano).

### TextWrangler

TextWrangler is a text and code editor for macOS.
You can find the syntax file and installation instructions on [naomi-syntax-textwrangler](https://github.com/longshotpro2/naomi-syntax-textwrangler).

### BBEdit

BBEdit is a text and code editor for macOS and the offical successor of TextWrangler.
You can find the syntax file and installation instructions on [BBEdit-Naomi-language](https://github.com/longshotpro2/BBEdit-Naomi-language).

<DocPreviousVersions/>
<EditPageLink/>