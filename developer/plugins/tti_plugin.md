---
title: Text to Intent Plugin Development
source: https://github.com/naomiproject/naomi-docs/blob/dev/developer/plugins/tti_plugin.md
meta:
  - property: og:title
    content: "Text to Intent Plugin Development"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Text to Intent Plugin Development

Parent Class: plugin.TTIPlugin
Required Methods:
&nbsp;&nbsp;**add_intents(intents)**
&nbsp;&nbsp;&nbsp;&nbsp;Parameters:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;intents - an intent structure
&nbsp;&nbsp;&nbsp;&nbsp;Returns null

&nbsp;&nbsp;**get_plugin_phrases(passive_listen=False)**
&nbsp;&nbsp;&nbsp;&nbsp;Parameters:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;passive_listen can be True or False
&nbsp;&nbsp;&nbsp;&nbsp;Returns a list of phrases

&nbsp;&nbsp;**determine_intent(phrase)**
&nbsp;&nbsp;&nbsp;&nbsp;Parameters:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;phrase is text to be analyzed
&nbsp;&nbsp;&nbsp;&nbsp;Returns a [return intent](./returnintent.html)

<DocPreviousVersions/>
<EditPageLink/>
