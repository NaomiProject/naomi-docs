---
title: Naobian
source: https://github.com/naomiproject/naomi-docs/blob/dev/setup/index.md
meta:
  - property: og:title
    content: "Naobian Guide"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---
# Setup and Usage
The section deals with the Naomi software post installation setup and how to get the user up and running. It also covers some basic usage topics to allow productive use of the environment.
# Environmental Initialization
Once the software is installed there are a number of settings that need to be made to allow Naomi to run smoothly and to initialize some of the prepackaged speechhandler plugins, ie. Naomi skills. The section deals with the setup configurations that may be required post Naomi software installation.
## Hardware Setup
The configuration of the audio system is usually the first, and often the most involved system to get configured to allow Naomi to begin performing. The details of setting up the audio aspects of the system are found [here](./audio/). It is often possible to proceed with the Profile Setup following and if there are problems with the audio setup you may return to this section.
## Profile Setup
After installation, on first running of Naomi (when this stabilize this section will become clearer.  
run Naomi by entering Naomi and return. (Note: On rare occasion after the **_NAOMI_** logo comes up you are presented with an "Illegal instruction" response. (We are trying to fix.) If so re-run Naomi and choose to update when prompted. This may take a while and Naomi will then run the profile repopulate option,

Naomi comes with many "skills" plugins built right in that give it the ability for example to tell time, give the weather, get the news, etc. Some of thess require installation specific parameter settings in order to work. To facilitate the process of populating these parameters, which are stored in the profile.yml file, Naomi has the **--repopulate startup** option. In addition at the very first start up when running an update the repopulate process runs automatically.

The repopulate process requires walking through the options one at a time entering appropriate values or accepting existing values which will be highlighted in white if they exist. For options you are unsure about the default displayed or blank should be accepted by simply pressing return. You can always return the process when you have a specific need to make changes. One nice feature is that it allows you to test the audio input and output.  
