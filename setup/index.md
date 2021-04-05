---
title: Setup
source: https://github.com/naomiproject/naomi-docs/blob/dev/setup/index.md
meta:
  - property: og:title
    content: "Setup Overview"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Setup and Usage

This section covers the Naomi software post installation setup, cofiguration and initial usage
issue, as well as providing a plugin development tutorial It is intended as a how to on getting 
the user up and running. In addition it deals with 
some basic topics of operation to support productive usage of the environment.

# Environmental Initialization

Once the software is installed then the Naomi system is runnable, however, to get it 
meaningfully operational with full access to the pre-installed speechhandler 
plugins, ie. Naomi's skills, requires some initiallization. In addition, there
is the opportunity to customize many of the operational options available.

## Hardware Setup

The configuration of the audio system is usually the first, and often the most 
involved system to get configured to allow Naomi to begin performing. The 
details of setting up the audio aspects of the system are found [here](audio.html). 
It is often possible to proceed with the Profile Setup in the following and if there 
are problems with the audio setup you may return to the audio setup section.

## Profile Setup

Naomi comes with many "skills" plugins built right in that give it the ability for 
example to tell time, give the weather, get the news, etc. To support these
Naomi makes use of an integrate profile containing parametic values and setting 
used by the various plugins to configure their operation. This file is hand editable
but there is an automated process that will walk the user through the entry or updating of 
profile settings. Typically the user will run Naomi with the --repopulate option on first 
activation and this will take the user through the process. Details of the 
process and the profile settings and options may be found [here](profile.html).

# Naomi Runtime Options

Naomi may be run from the command line with a significant number of options to access
special functionality, such as, handle plugins or control output/input, enable debugging,
feature selection, etc. The more commonly used options are covers [here](options.html).  

# Basic Usage and Simple Development

Once the hardware is connected and setup and the profile has been populated it is time 
to make use of Naomi and/or start developing new Naomi skills. Information along these lines 
can be found [here](usage.html) for usage issues, and [here](tutorial.html) for a plugin
development example.

<DocPreviousVersions/>
<EditPageLink/>
