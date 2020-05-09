---
id: adapt
label: Adapt
title: Adapt - Text to Intent
type: ttis
description: "Adapt is useful for interpreting natural language input"
logo: images/plugins/adapt.jpg
source:
meta:
  - property: og:title
    content: "Adapt - Text to Intent"
  - property: og:description
    content: "Adapt is useful for interpreting natural language input"
---

# Adapt - Text to Intent

<PluginLogo/>

Adapt is a keyword based parser. Intents are built atomically from keywords
that are either "required" or "optional". This is quite different from the way
intent templates are entered into Naomi, as complete sentences representing ways
in which a user might ask for a service. Adapt, in it's default form, is also
not set up to avoid name collisions between intents. For these reasons, we do a
pre-parsing step to both ensure that every intent name is unique, even if
written by different authors with no knowledge of each other, then parse
through the intents in order to identify words that either appear in every
template for the intent (required) or that appear in some intents (optional),
plus use intent keywords.

For example, a Naomi intent might look like this:
```
{
    'CalendarIntent': {
        'locale': {
            'en-US': {
                'keywords': {
                    'WhenKeyword': [
                        'TODAY',
                        'TOMORROW',
                        'SUNDAY',
                        'MONDAY',
                        'TUESDAY',
                        'WEDNESDAY',
                        'THURSDAY',
                        'FRIDAY',
                        'SATURDAY'
                    ]
                },
                'templates': [
                    "ADD CALENDAR EVENT",
                    "ADD AN EVENT TO MY CALENDAR",
                    "DO I HAVE ANY CALENDAR EVENTS {WhenKeyword}",
                    "WHAT IS ON MY CALENDAR {WhenKeyword}"
                ]
            }
        },
        'action': self.handle
    }
}
```

We would see that the word "CALENDAR" appears in every template, so that
would become a "required" word. "EVENT" appears in three templates, and
"ADD" and "{WhenKeyword}" both appear in two templates, so they would
be "optional". Words such as "AN", "TO", "MY", "I", "ANY", "HAVE", "WHAT",
"IS" and "ON" are likely to appear in other intents, and thus will have lower
weights.

This means the Adapt intent would look something like

```
CalendarEvent01=IntentBuilder('calendar_event')\
  .require("CALENDAR")\
  .optionally("EVENT")\
  .optionally("ADD")\
  .optionally("{CalendarEvent01_WhenKeyword}")
```

When processing a request, if any words match one of the words under {WhenKeyword}
then that word is stored as a value for WhenKeyword. So the request "WHAT DO I HAVE ON MY CALENDAR TODAY"
comes in, it is converted to "WHAT DO I HAVE ON MY CALENDAR {CalendarEvent01_WhenKeyword}, CalendarEvent01_WhenKeyword: TODAY"
before being matched.

Project home:
[https://github.com/MycroftAI/adapt](https://github.com/MycroftAI/adapt)

Installation:
`sudo pip3 install adapt-parser`

profile.yml:
```
tti_engine: Adapt TTI
```


<EditPageLink/>
