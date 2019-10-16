---
title: Return Intent Structure
source: https://github.com/naomiproject/naomi-docs/blob/dev/developer/plugins/returnintent.md
meta:
  - property: og:title
    content: "Return Intent Structure"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Return Intent Structure

A return intent has the following structure:
<pre>
{
  'action': <function <lambda> at 0x7f85d000b6a8>,
  'input': 'SEARCH FOR CATS ON YOUTUBE',
  'intent': 'SearchIntent',
  'matches': {
    'Query': ['cats'],
    'EngineKeyword': ['youtube']
  },
  'score': 0.8333333333333334
}
</pre>

**action** - a reference to the function to be activated
**intent** - the name of the intent that was matched
**matches** - a dictionary of the different variables that
were matched in the intent. The value of each match is a
list containing all of the matched values.

<DocPreviousVersions/>
<EditPageLink/>
