---
title: Options
source: https://github.com/naomiproject/naomi-docs/blob/dev/setup/options.md
meta:
  - property: og:title
    content: "Options Guide"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Basic Naomi Commandline Options

From the command line Naomi may be run with a significant number of options to fine tune its operation,
handle plugins or control output/input. The following covers only those most commonly
used by newer users.

  **-h, --help** => Shows the full listing of help message and exit.  
  **--debug** => Produce detailed debug messages on the terminal. This is typically a very
long listing so it is usually useful to pipe the output to a file for more convenient review.
This can be done using `--debug |& tee  ~/naomi.log` to put the file into your home directory.
  **--repopulate** => Rebuilds the configuration profile.  
  **--install [PLUGINS_TO_INSTALL]** => Install plugin and exit.  
  **--update [PLUGINS_TO_UPDATE]** => Update specific plugin or all plugins and exit.  
  **--remove [PLUGINS_TO_REMOVE]** => Remove (uninstall) plugin completely from Naomi and exit.  
  **--disable [PLUGINS_TO_DISABLE]** => Disable plugin but leave it installed and exit.  
  **--enable [PLUGINS_TO_ENABLE]** => Enable plugin so that is part of the Naomi operational 
environment and exit.  
  **--list-active-plugins** => List all the active plugins and exit. This is useful to check
if the install and/or enable processes have completed successfully.  

<DocPreviousVersions/>
<EditPageLink/>
