---
title: Naobian
source: https://github.com/naomiproject/naomi-docs/blob/master/installation/naobian.md
meta:
  - property: og:title
    content: "Naobian Guide"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# Naobian - Hassle-free Naomi Setup

The Raspberry Pi and other small single-board computers are quite famous platforms for Naomi.
However, setting up a fully working Linux system with all recommended packages and Naomi recommendations is a **boring task** taking quite some time and **Linux newcomers** shouldn't worry about these technical details.

<p style="text-align: center; font-size: 1.2em; font-style: italic;"><q>A vocal assistant enthusiast doesn't have to be a Linux enthusiast!</q></p>

Naobian aims to provide a **pre-configured** Linux system setup specific to the needs of every Naomi user.
To that end, the project provides two things:

* Complete **SD-card images pre-configured with Naomi** and many other Naomi- and Hardware-specific preparations for the Raspberry Pi and the Pine A64
* The Naobian Configuration Tool to set up and configure Naomi and many related things on any Debian/Ubuntu based system

## How Naobian is Setup

Naobian is setup in a plug-in-play mannor so users can test the software or not worry about how to set everything up. The image comes with Naomi installed, [Flite TTS](http://www.festvox.org/flite/) & [Pocketsphinx STT](https://github.com/cmusphinx/pocketsphinx), as well as a defaulted profile to get started. After trying Naomi out you can to personalize things to your liking.

## To Get Started

<ol>
  <li>Insert the SD card in your device, ensure the network is connected or setup the Wi-Fi first if you want to update & ssh into the device, and reboot!</li>
  <p>Unlike standard Raspbian which has a user <code>'pi'</code> with a password <code>'raspberry'</code>, the Naobian image uses the following as default username and password:</p>
  <div class="language-shell"><pre class="language-shell"><code>Default user:     pi</br>Default password: Naobian</code></pre></div>
  <p>As a network connected device, having a unique password significantly enhances your security and thwarts the majority of hacking attempts.</p>
  <p>We recommend setting a unique password for any device, especially one that is exposed directly to the internet.</p>
  <li>Go into the directory</li>
  <div class="language-shell"><pre class="language-shell"><code>cd Naomi</code></pre></div>
  <li>Run the app</li>
  <div class="language-shell"><pre class="language-shell"><code>./Naomi.py</code></pre></div>
  <p>To check for updates at any given time</p>
  <p>go into the Naomi dir (<code>cd ~/Naomi</code>) and run <code>git pull</code></p>
</ol>

<DocPreviousVersions/>
<EditPageLink/>
