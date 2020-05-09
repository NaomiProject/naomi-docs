---
id: checkemail
label: CheckEmail
title: CheckEmail - Speechhandler
type: speechhandlers
description: "Uses IMAP to fetch information about unread emails."
logo: images/plugins/email.jpg
source:
meta:
  - property: og:title
    content: "CheckEmail - Speechhandler"
  - property: og:description
    content: "Uses IMAP to fetch information about unread emails."
---


# CheckEmail - Speechhandler <Badge text="Included"/>

<PluginLogo/> 

Uses IMAP to fetch information about unread emails. It demonstrates how to connect Naomi to an email server for querying emails. With a little additional work, Naomi could also read your emails to you and send new emails.

**Intent templates:**

 CHECK MY INBOX
 DO I HAVE ANY NEW EMAIL?
 ARE THERE ANY NEW EMAILS?

**Available languages:**

* English
* French
* Deutch

### setup Check Email in `~/.config/naomi/configs/profile.yml`

Because your email address, password and username are encrypted, it is best to let Naomi create this section for you, but here are all the fields in case you want to edit the server or port information manually.
```yaml
email:
  address: gAA0AABeOyca37Q2RFFroZo2XnXWn5ipERkwDI0qpR2nmLTDHUC3zo05J4cYA8oem7gUDj9QZg_ZMk1Gb0Nm5lU1tbzay6vZtg==
  imap:
    port: '993'
    server: 'imap.server.net'
  password: 'gAA0AABeOyceiwvIcrrzkZ1U4cDZ7hICoIXsfHQG3qWFvUiNQ2TNPRn8BqboxIH-KJDfwRgYafRSfN8iWYlqcTqg6iI9cloN6q=='
  smtp:
    port: '587'
    server: 'smtp.server.net'
  username: gAA0AABeOyceiwvIcrrGkZ1U4cDZ7hICoIXsfHQG3qWF6iI9cloN6qvU_NQ2TNPRn8BqboxIH-KJDfwRgYafRSfN8iWYlqcTqg==
```

<EditPageLink/>