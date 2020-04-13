---
id: birthday
label: Birthday
title: Birthday - Speechhandler
type: speechhandlers
description: "The Birthday plugin helps you remember your friends and family birthdays, using the Facebook API services."
logo: images/plugins/birthday.png
source:
meta:
  - property: og:title
    content: "Birthday - Speechhandler"
  - property: og:description
    content: "The Birthday plugin helps you remember your friends and family birthdays, using the Facebook API services."
---


# Birthday - Speechhandler

<PluginLogo/> 

The Birthday plugin helps you remember your friends and family birthdays, using the Facebook API services. It demonstrates how to connect a speechhandler plugin to an external API.

**Intent templates:**

 WHOSE BIRTHDAY IS IT TODAY?
 ARE THERE ANY BIRTHDAYS TODAY?
 DO ANY OF MY FRIENDS HAVE BIRTHDAYS TODAY?

**Available languages:**

* English
* French
* Deutch

### setup Facebook birthdays in `~/.config/naomi/configs/profile.yml`

```yaml
keys:
  FB_TOKEN:
```

<EditPageLink/>