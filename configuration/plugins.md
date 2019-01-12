---
title: Plugins
source: https://github.com/naomiproject/naomi-docs/blob/master/configuration/plugins.md
meta:
  - property: og:title
    content: "Plugins Guide"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Preinstalled and available plugins

## Naomi come with preinstalled plugins

* Birthday (using Facebook API)
  * **Try it:** "Naomi, do i have Facebook notifications?"

* Clock
  * **Try it:** "Naomi, What’s the time?

* Gmail (using Gmail API)
  * **Try it:** "Naomi, Do I have any email?"

* Life (H2G2 Joke)
  * **Try it:** "Naomi, What is the meaning of life?"

* Mdpcontrol (Music Player daemon) with Spotify
  * **Try it:** "Naomi, Play bohemian Rhapsody"

* News
  * **Try it:** "Naomi, What’s in the news?"
  
* Notification
  * **Try it:** "Naomi, any Facebook notifications?
  
* Unclear
  
* Weather (Yahoo Weather API) - *Deprecated*, alternative in progress
  * **Try it:** "Naomi, How’s the weather?… What’s the weather like tomorrow?"
  
## Birthay

The Birthday make you remember your friends and familly birthdays, using the Facebook API services

**triggers word are:** *Birthday*

**Example:** "Naomi, Who has a birthday today?"

**Available languages:**

* English
* French
* Deutch

### setup Facebook birthdays in `profile.yml`

```yaml
keys:
  FB_TOKEN:
```

## Clock

Clock plugin give you the time.

### Use it

**triggers word are:** *Time*

**Example:** "Naomi, what time is it ?"

**Available languages:**

* English
* French
* Deutch

## Gmail

Fetches a list of unread email objects from a user's Gmail inbox.

**triggers word are:** *Email*, *Inbox*

**Example:** "Naomi, what are the inbox emails ?"

**Available languages:**

* English
* French
* Deutch

### setup Gmail in `profile.yml`

```yaml
gmail_address: email@gmail.com
gmail_password: xxxxxxxx
```

## Life (H2G2 nerd Joke)

Responds to user-input, typically speech text, by relaying the true meaning of life (42).

**triggers word are:** *MEANING OF LIFE*

**Example:** "Naomi, what's the meaning of life ?"

**Available languages:**

* English
* French
* Deutch

## MdpControl (Music Player daemon)

Control your MPD server and listen to music using Spotify

**triggers word are:** *MUSIC*, *SPOTIFY*

**Example:** "Naomi, play Bohemian Rhapsody by Queen"

**Available languages:**

* English
* French
* Deutch

### setup MdpControl in `profile.yml`

```yaml
mpdclient:
  server: <server_adress>
  port: <server_port>
  password: <server_password>

```

## News

Stay informed what's going on

**Triggers word are:** *NEW*, *HEADLINE*

**Example:** "Naomi, what are the news ?"

**Available languages:**

* English
* French
* Deutch

## Notifications

Get notifications from Facebook, Naomi tell you when you have a notification, no triggers needed.

**Available languages:**

* English
* French
* Deutch

### setup Facebook notifications in `profile.yml`

```yaml
keys:
  FB_TOKEN:
```

## Unclear

Dummy module to handle unknown speech, no triggers.

**Available languages:**

* English
* French
* Deutch

## Weather

Get weather forecasts from Wundeground

No API key needed :smile:

**Triggers word are:** *Weather*, *Today*, *Tomorrow*, *Temperature*, *Forecast*

**Example:** "Naomi, what's the weather today ?"

**Available languages:**

* English
* French
* German

### setup Weather in `profile.yml`

To get your WOEID number: [http://woeid.rosselliot.co.nz/](http://woeid.rosselliot.co.nz/)

```yaml
weather:
  woeid: 'YOUR_WOEID'
## OR
  location: 'YOUR_CITY_NAME'
  unit: celsius *OR* farenheit  
```

<DocPreviousVersions/>
<EditPageLink/>
