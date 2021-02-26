---
title: Text to Intent Plugins
source: https://github.com/naomiproject/naomi-docs/blob/master/developer/plugins/tti_plugin.md
meta:
  - property: og:title
    content: "Text to Intent Plugin Development"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Text to Intent Plugin Development

Parent Class: plugin.TTIPlugin<br />
Required Methods:<br />
&nbsp;&nbsp;**add_intents(intents)**<br />
&nbsp;&nbsp;&nbsp;&nbsp;Parameters:<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;intents - an intent structure<br />
&nbsp;&nbsp;&nbsp;&nbsp;Returns null<br />

&nbsp;&nbsp;**get_plugin_phrases(passive_listen=False)**<br />
&nbsp;&nbsp;&nbsp;&nbsp;Parameters:<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;passive_listen can be True or False<br />
&nbsp;&nbsp;&nbsp;&nbsp;Returns a list of phrases<br />

&nbsp;&nbsp;**determine_intent(phrase)**<br />
&nbsp;&nbsp;&nbsp;&nbsp;Parameters:<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;phrase is text to be analyzed<br />
&nbsp;&nbsp;&nbsp;&nbsp;Returns a [return intent](./returnintent.html)<br />

<DocPreviousVersions/>
<EditPageLink/>
