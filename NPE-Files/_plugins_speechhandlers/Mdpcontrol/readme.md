---
id: mdpcontrol
label: MdpControl
title: MdpControl - Speechhandler
type: speechhandlers
description: "Control your MPD server and listen to music."
logo: images/plugins/mdpcontrol.png
source:
meta:
  - property: og:title
    content: "MdpControl - Speechhandler"
  - property: og:description
    content: "Control your MPD server and listen to music."
---


# MdpControl - Speechhandler

<PluginLogo/> 

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

### setup MdpControl in `~/.config/naomi/configs/profile.yml`

```yaml
mpdclient:
  server: <server_adress>
  port: <server_port>
  password: <server_password>
```

<EditPageLink/>