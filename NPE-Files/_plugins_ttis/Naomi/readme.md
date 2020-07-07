---
id: naomitti
label: NaomiTTI
title: NaomiTTI - Text to Intent
type: ttis
description: "takes in natural language as an input, and outputs a data structure"
source: https://github.com/NaomiProject/naomi-docs/edit/dev/NPE-Files/_plugins_ttis/Naomi/readme.md
meta:
  - property: og:title
    content: "NaomiTTI - Text to Intent"
  - property: og:description
    content: "takes in natural language as an input, and outputs a data structure"
---

# NaomiTTI - Text to Intent <Badge text="Included"/>


Naomi uses edit distances and word frequencies to determine and process the intent.

profile.yml:
```
tti_engine: Naomi TTI
naomi_tti:
  words_to_ignore:
  - ANY
  - ARE
  - DO
  - IS
  - THE
  - TO
  - WHAT
```

<EditPageLink/>
