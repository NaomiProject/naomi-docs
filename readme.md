---
title: Introduction
currentVersion: 2.2 
currentMilestoneVersion: 3.0.M16
currentNightlyVersion: Naomi-Nightly
source: https://github.com/naomiproject/naomi-docs/blob/dev/readme.md
meta:
  - name: og:title
    content: Welcome to Naomi!
  - name: og:description
    content: Naomi, The privacy focused personal assistant
---

<h1 class="welcome">Welcome to Naomi!</h1>

<style>
@media (min-width: 720px) {
  .intro-logo {
    margin-left: 3rem; float: right;
  }
}
h1.welcome {
  font-family: 'Open Sans', sans-serif;
  font-weight: 300;
  font-size: 36pt;
}
</style>

<img src="./images/naomi-logo.png" width="600" height="200" class="intro-logo" />

The Naomi Project is an open source, technology agnostic platform for developing always-on, voice-controlled applications!

Naomi **software** integrates different home text-to-speech & speech-to-text systems, plugins and technologies into a single solution.
It provides uniform user interfaces, and a common approach for developing always-on, voice-controlled applications, regardless of the number of devices and sub-systems involved.

You've reached the Naomi documentation, which contains extensive resources for all users. Naomi releases are divided into three group:

- <strong>Stable</strong> versions (**{{$page.frontmatter.currentVersion}}**) are thoroughly tested semi-annual official releases of Naomi. Use the stable version for your production environment if you don't need the latest enhancements and prefer a robust system.
- <strong>Milestone</strong> versions (**{{$page.frontmatter.currentMilestoneVersion}}**) are intermediary releases of the next Naomi version, released about once a month, and they include the new recently added features and bugfixes. They are a good compromise between the current stable version and the bleeding-edge and potentially unstable nightly version. Milestones releases are **Highly Recommended** for most users.
- <strong>Nightly</strong> versions are at most 1 or 2 days old and include the latest code. Use nightly for testing out very recent changes, but be aware some nightly versions might be unstable. Use in production at your own risk!

The docs are divided into two catagories, Stable & Dev, Stable docs matching version **{{$page.frontmatter.currentVersion}}** release and Dev matching version **{{$page.frontmatter.currentMilestoneVersion}}** release. This is represented by the dropdown at the **Top Right** of any documentation pages. Please verify you are viewing the same doc version as your Naomi installation. All past version documentation is archived on our [support site](https://support.projectnaomi.com/document/) to view if need be.

- If you are new to Naomi, we recommend to learn a bit about Naomi first before jumping in - please proceed directly to the [Getting Started](#getting-started) chapter below!
- If you're an experienced user, the [Download](/download) page contains links and installation instructions. The [Manual Configuration Guide](./configuration/) also contain useful information if you chose to manually configure Naomi. If you're looking for the documentation of a specific plugins, go to the [Naomi Plugin Exchange](/plugins). You can also use the search box above to find any page on this site.
- If you would like to contribute to the development of Naomi, please refer to our [Developer Guide](./developer/).

This documentation is always worked on, so expect regular changes. If you feel that something important is missing, please [help us improve the documentation](https://github.com/naomiproject/naomi-docs/blob/gh-pages/README.md#contributing-to-the-documentation)!</p>

## Getting Started

Naomi in theory will run on many platforms that include Python, i.e Linux, Windows and Mac OSx.
You can find specific installation instructions for these and other platforms in the [Installation Guide](./installation/).
Many people find that the simplest way to experiment with Naomi is to get a [Raspberry Pi](https://raspberrypi.org) and install [Naobian](./installation/naobian.html) - the "hassle-free Naomi setup".
While Naobian offers a streamlined and simplified way to get up and running quickly, it is a complete platform for developing always-on, voice-controlled applications.

Along the way, you may have some questions; the Naomi community is here to help.

## The Naomi Community

Naomi is not just software - it is also a **community** of users, contributors and maintainers, working together on an open-source, interoperable approach to virtual assistance.
The center of this community is the [Naomi community forum](https://support.projectnaomi.com).
You can search previous conversations and issues to see if your question has already been answered.
You can post your own question as well (although it is generally considered to be good etiquette to check fairly thoroughly before posting).
One of the great things about Naomi is that it has an active and responsive community of developers and maintainers who generally respond quite quickly to forum questions.
We believe you will find that our community works diligently to make newcomers feel at home.

## Architecture Overview

Naomi is developed in [Python](https://www.python.org/) and mainly based on the [Jasper](https://jasperproject.github.io/) framework.

Naomi is highly modular software that can be extended through "Plugins".
Plugins give Naomi a wide array of capabilities, from User Interfaces, to the ability to interact with a large and growing number of physical Things.
Plugins may come from the Naomi distribution.

The overall architecture of Naomi is shown in the figure below:

![distribution overview](./images/architecture.png "Overall Naomi Architectural View")

<DocPreviousVersions/>
<EditPageLink/>