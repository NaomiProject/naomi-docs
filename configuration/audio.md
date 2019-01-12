---
title: Audio
source: https://github.com/naomiproject/naomi-docs/blob/master/configuration/audio.md
meta:
  - property: og:title
    content: "Audio Guide"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Audio Configuration

This is the hardest part to setup, but don't worry, if you follow theses steps, everything should be ok

## Test Audio Input

In a terminal window run the following command to record

```console
rec test.wav
```

Press "Ctrl+C" to stop the recording and then type the following command to hear the recording

```console
aplay test.wav
```

If you hear what you recorded everything is setup properly and you can move on to the TTS section. If it did not work correctly continue this section.

# Setup Audio

Run the following command to display every audio output device, i.e. speakers

```console
aplay -l
```

The command should output something like this:

```console
card 0: ALSA [bcm2835 ALSA], device 0: bcm2835 ALSA [bcm2835 ALSA]
  Subdevices: 7/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: ALSA [bcm2835 ALSA], device 1: bcm2835 ALSA [bcm2835 IEC958/HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

Here you can see we have: An analog audio output is on the card 0 and subdevice 0 (card0, device0), & An USB audio output is on the card 1 and subdevice 0
Run the following command to display every audio input device, i.e. microphones

```console
arecord -l
```

The command should output something like this:

```console
List of CAPTURE Hardware Devices
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

Here we can see an USB microphone input on card 1 and subdevice 0

Now we are going to create the appropriate .asoundrc file. Use the analog output as our audio output (speakers on the jack port) & Use the USB input as our audio input (microphone on the USB)

```console
sudo nano /home/pi/.asoundrc
```

Then type the following parameters

```console
pcm.!default {
   type asym
   playback.pcm {
     type plug
     slave.pcm "hw:1,0"
   }
   capture.pcm {
     type plug
     slave.pcm "hw:1,0"
   }
}
```

Save and Close the file and then restart alsa using the following command

```console
sudo /etc/init.d/alsa-utils restart
```

Now redo the Test Audio Input. If you now hear something then everything worked and you can move onto the TTS section.

<DocPreviousVersions/>
<EditPageLink/>
