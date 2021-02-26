---
title: NPE Editor
source: https://github.com/naomiproject/naomi-docs/blob/master/developer/plugins/npeeditor.md
meta:
  - property: og:title
    content: "NPE Editor"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# NPE Editor

The [Naomi Plugin Exchange Editor](https://npeeditor.projectnaomi.com) was created to simplify the development process for plugin developers. Based on how the editor is filled out, it will return a compressed zip file containing the proper plugin structure as well as the proper formatting of various files so the plugin is compatible with Naomi in addition to the NPE. Besides the plugin programming itself, the `plugin.info` file & `readme.md` file are critical documents for a plugin to work correctly with naomi. The `plugin.info` file holds all the info that Naomi needs to recognize the plugin where as the `readme.md` file holds all of the info needed for the plugin to be compatible with the NPE and show up on the exchange.

Here is a brief summary of the different fields of the editor and what that pertain to:

1. The first field asks for the name of your plugin. Please make a brief, speakable plugin name, capitalizing most words. This field is used for both Naomi and the NPE to designate the plugin.
    > NOTE: Avoid the word "Plugin" in the name.

2. The next field asks for a version number for your plugin. You are able to use any version scheming you would like as long it is maintained throughout the lifespan of the plugin. This field is used by Naomi in the info file for plugin version tracking.

3. The following field asks for the link to the repo that holds the plugin. This is used by Naomi in the info file.

4. Next is a short description for the info file.

5. And finally the next two fields ask for your First & Last name in addition to a link to reach you if an issue arises. This wraps up the required info for the `plugin.info` file.

6. Next is a field for a plugin image. If you would like an image for your plugin and would like it displayed on the exchange you can add that here.
   > NOTE: This is option, if no image is give then the Naomi logo will be shown on the Exchange. Also Please only use .png or .jpg files only

7. Next you select the plugin type you are wanting to create. This allows the zip file to contain the proper python skeleton for the plugin you are creating.

8. Lastly is the long description. This field is used to populate the `readme.md` file and can contain anything from the plugin description, install instructions, to `profile.yml` changes. This is where you describe how the plugin works and how to install it if it requires more dependencies than the standard Naomi install as well as any other pertinent information.

That concludes what is included in the [NPEeditor](https://npeeditor.projectnaomi.com) at this time. If there are any issues or you need any help please reach out to the development team on [discord](https://projectnaomi.com/community/) or at [contact@projectnaomi.com](mailto:contact@projectnaomi.com).

<DocPreviousVersions/>
<EditPageLink/>
