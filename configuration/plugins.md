---
title: Plugins
source: https://github.com/naomiproject/naomi-docs/blob/dev/configuration/plugins.md
meta:
  - property: og:title
    content: "Plugins Guide"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Preinstalled and available plugins

## Naomi come with preinstalled plugins

* [Birthday](#birthday) (using Facebook API)
  * **Try it:** "Naomi, do i have Facebook notifications?"

* [Clock](#clock)
  * **Try it:** "Naomi, what time is it?

* [Check Email](#check-email) (using IMAP/SMTP)
  * **Try it:** "Naomi, Do I have any email?"

* [Hacker News](#hacker-news)
  * **Try it:** "Naomi, what's in hacker news?"

* [Life](#life) (H2G2 Joke)
  * **Try it:** "Naomi, What is the meaning of life?"

* [Mdpcontrol](#mdpcontrol-music-player-daemon) (Music Player daemon)
  * **Try it:** "Naomi, Play bohemian Rhapsody"

* [News](#news)
  * **Try it:** "Naomi, What’s in the news?"

* [Notification](#notification)
  * **Try it:** "Naomi, any Facebook notifications?

* [WWIS Weather](#wwis-weather)
  * **Try it:** "Naomi, How’s the weather?… What’s the weather like tomorrow?"

## Birthay

The Birthday make you remember your friends and familly birthdays, using the Facebook API services. It demonstrates how to connect a speechhandler plugin to an external API.

**Intent templates:**

WHOSE BIRTHDAY IS IT TODAY?
ARE THERE ANY BIRTHDAYS TODAY?
DO ANY OF MY FRIENDS HAVE BIRTHDAYS TODAY?

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

Clock plugin tells you the current time. It demonstrates a simple query that does not require internet access.

### setup Clock in `profile.yml`

```yaml
timezone: Pacific/Auckland
```

**Intent templates:**

WHAT TIME IS IT?
TELL ME THE TIME
WHAT IS THE TIME?

**Available languages:**

* English
* French
* Deutch

## Hacker News

Top news stories from Hacker News

**Intent templates:**

READ HACKER NEWS
WHAT IS IN HACKER NEWS?
WHAT ARE THE HACKER NEWS HEADLINES?

**Available languages:**

* English
* French
* Deutch

## Email

Uses IMAP to fetch information about unread emails. It demonstrates how to connect Naomi to an email server for querying emails. With a little additional work, Naomi could also read your emails to you and send new emails.

**Intent templates:**

CHECK MY INBOX
DO I HAVE ANY NEW EMAIL?
ARE THERE ANY NEW EMAILS?

**Available languages:**

* English
* French
* Deutch

### setup Email in `profile.yml`

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

## Life

Responds to user-input, typically speech text, by relaying the true meaning of life (Monty Python) or the Ultimate answer to the Ultimate question of Life the Universe and Everything (42).

**Intent templates:**

WHAT IS THE MEANING OF LIFE?
WHAT IS THE ULTIMATE ANSWER TO THE ULTIMATE QUESTION OF LIFE THE UNIVERSE AND EVERYTHING?

**Available languages:**

* English
* French
* Deutch

## MdpControl (Music Player daemon)

Control your MPD server and listen to music.

MPD requires a bit of work to set up. First, you have to install and configure
the server. This is usually accomplished in Raspbian by running `sudo apt install mpd`.
I also recommend installing a couple of clients, one for building playlists and
a second for interacting with the server. I have had good luck building a playlist
with _ncmpcpp_ and using _mpc_ to actually start and stop the player. I haven't tried most of the other clients.
There is also a one-liner for building a playlist [here](https://blog.binchen.org/posts/one-liner-bash-to-createupdate-playlist-for-mpd.html) which looks good with
some tweaks. The resulting playlist file looks fine to me, but I've gotten odd
errors preventing me from using the playlists.

I don't know if I have the best setup, so I'll just tell you what I've done.
I opted to run mpd as the pi user so that I could store MP3 files in the
/home/pi/Music folder. I started by creating an mpd folder under ~/.config
(mkdir -p ~/.config/mpd). Here are the contents of my /home/pi/.config/mpd/mpd.conf file:

```
# Files and directories #######################################################
music_directory		"~/Music"
playlist_directory	"~/.config/mpd/playlists"
db_file			"~/.config/mpd/tag_cache"
log_file			"~/.config/mpd/mpd.log"
pid_file			"~/.config/mpd/pid"

# Input #######################################################################
input {
        plugin "curl"
}

# QOBUZ input plugin
input {
        enabled    "no"
        plugin     "qobuz"
}

# TIDAL input plugin
input {
        enabled      "no"
        plugin       "tidal"
}

# Decoder #####################################################################
decoder {
        plugin                  "hybrid_dsd"
        enabled                 "no"
}

# Audio Output ################################################################
audio_output {
	type		"pulse"
	name		"MPD"
	mixer_type  "software"
}
```

Start the server (later we will make mpd start automatically via systemd):
```bash
$ mpd ~/.config/mpd/mpd.conf
```

Install _ncmpcpp_ using `sudo apt install ncmpcpp` then run the program.
It uses a text user interface which is a little hard to get used to.
Press '2' to go to your directory list, then navigate through your directories
using the spacebar to add files to your playlist. Then press '1' to return to
your playlist and press 'S' to save the playlist. The Naomi MPDControl plugin
currently allows you to play playlists, not individual songs. This means that
you can also add a radio feed to a playlist and launch a radio station by
asking Naomi to play that playlist.

I have not managed to get ncmpcpp to actually play a playlist, so I have
also installed mpc. To test that I have everything working:

```bash
$ mpc load playlist
loading: playlist
$ mpc play
```

At this point, MPD should be set up to work with the MPDControl plugin.

If you would like the mpd server to start automatically, you should be able
to edit the Service section of your /lib/systemd/system/mpd.service file:

```
[Service]
User=pi
Type=notify
EnvironmentFile=/etc/default/mpd
ExecStart=/usr/bin/mpd --no-daemon /home/pi/.config/mpd/mpd.conf
```

Then use systemctl to enable the mpd service:
```bash
$ mpd --kill
$ sudo systemctl enable mpd
$ sudo systemctl start mpd
```

**Intent templates:**

PLAY SOMETHING
PLAY MUSIC
PLAY {PlayList}

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

Stay informed what's going on.

**Intent templates:**

READ THE NEWS
WHAT IS IN THE NEWS?
WHAT IS HAPPENING?
WHAT ARE TODAY'S HEADLINES?

**Available languages:**

* English
* French
* Deutch

## Notifications

Get notifications from Facebook, Naomi tell you when you have a notification,
no triggers needed.

**Intent templates:**

DO I HAVE ANY FACEBOOK NOTIFICATIONS?
CHECK MY NOTIFICATIONS

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

## WWIS Weather

Get weather forecasts from World Weather Information Service

No API key needed :smile:

**Intent templates:**

WHAT IS THE WEATHER IN {LocationKeyword}?
WHAT IS THE FORECAST FOR {DayKeyword}?
WHAT IS THE FORECAST FOR {LocationKeyword}?
WHAT IS THE FORECAST FOR {LocationKeyword} ON {DayKeyword}?
WHAT IS THE FORECAST FOR {LocationKeyword} ON {DayKeyword} {TimeKeyword}?
IS IT {WeatherTypePresentKeyword} IN {LocationKeyword}?
WILL IT {WeatherTypeFutureKeyword} THIS {TimeKeyword}?
WILL IT {WeatherTypeFutureKeyword} {DayKeyword}?
WILL IT {WeatherTypeFutureKeyword} {DayKeyword} {TimeKeyword}?
WHEN WILL IT {WeatherTypeFutureKeyword}?
WHEN WILL IT {WeatherTypeFutureKeyword} IN {LocationKeyword}?

**Example:** "Naomi, what's the forecast for today?"

**Available languages:**

* English
* French
* German

### setup WWIS Weather in `profile.yml`

```yaml
wwis_weather:
  city: ''
  country: New Zealand
  region: Rotorua
```

<DocPreviousVersions/>
<EditPageLink/>
