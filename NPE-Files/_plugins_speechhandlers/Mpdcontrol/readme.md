---
id: mpdcontrol
label: MpdControl
title: MpdControl - Speechhandler
type: speechhandlers
description: "Control your MPD server and listen to music."
logo: images/plugins/mpdcontrol.png
source: https://github.com/NaomiProject/naomi-docs/edit/dev/NPE-Files/_plugins_speechhandlers/Mpdcontrol/readme.md
meta:
  - property: og:title
    content: "MpdControl - Speechhandler"
  - property: og:description
    content: "Control your MPD server and listen to music."
---


# MpdControl - Speechhandler

<PluginLogo/>

Control your MPD server and listen to music.

MPD requires a bit of work to set up. First, you have to install and configure
the server. This is usually accomplished in Raspbian by running `sudo apt install mpd`.
I also recommend installing a couple of clients, one for building playlists and
a second for interacting with the server. I have had good luck building a playlist
with _ncmpcpp_ and using _mpc_ to actually start and stop the player. I haven't tried most of the other clients.
There is also a one-liner for building a playlist [here](https://blog.binchen.org/posts/one-liner-bash-to-createupdate-playlist-for-mpd.html) which looks good with
some tweaks.

```
$ find /home/pi/Music -name '.mp3' -o -name '.flac' | all.m3u
```

The resulting playlist file looks fine to me, but I've gotten odd
errors preventing me from using the playlists, so your mileage may vary.

m3u playlists are also a great way to add access to streaming radio stations.
This makes it easy to train Naomi to "Play NPR" or "Play Jazz FM"
by setting the name of the m3u file to something appropriate.

I don't know if I have the best setup, so I'll just tell you what I've done.
Originally I opted to run mpd as the pi user so that I could store MP3 files in the
/home/pi/Music folder, but that became a really painful experience full of odd errors
about permission denied to the pulseaudio server. Eventually I have learned to just
leave well enough alone. MPD as installed from apt will start its own pulseaudio server,
and the different pulseaudio processes seem to get along fine. Fixing the permission
errors to allow the mpd user access to my Music folder was way easier than battling
with pulseaudio.

I started by creating an mpd folder under ~/.config
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

Restart the server with systemd
```bash
$ sudo systemctl restart mpd
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

Of course, you can also set up Naomi to control an MPD server running on
another computer on your network. And m3u playlists are easy to use with


**Intent templates:**

* PLAY SOMETHING
* PLAY MUSIC
* PLAY {PlayList}

**Available languages:**

* English
* French
* Deutch

### setup MdpControl in `~/.config/naomi/configs/profile.yml`

```yaml
mpdclient:
  server: localhost
  port: 6600
```

<EditPageLink/>
