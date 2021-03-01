---
title: Tutorial
source: https://github.com/naomiproject/naomi-docs/blob/dev/setup/tutorial.md
meta:
  - property: og:title
    content: "Plugin Tutorial"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# A Simple Speechhandler Plugin

In this section we are going to work through the case of developing a simple
speechhandler plugin to give Naomi the skill to implement a one to five second timer. In operation
it will allow the user to verbally specify the number of seconds to use and then Naomi will announce the
timer start, then after the elapse time it will announce the timer finish.

Note that the code developed below has actually two functions that will be used by the TTI and 
Speechhandler modules to "decode" input and implement the output actions.

# Structure of the Plugin
At the top level a speechhandler plugin is a directory containing at minimum of three files. 
For user plugins this directer would be placed under the "hidden" directory **~/.config/naomi/plugin/speechhandler**.
For the purposes of this tutorial name the directory with you files "simple_timer".

## \_\_init.py\_\_ File
This file contains the import instruction for loading the plugin. In this case it is simply two lines.
The value "s_timer" is the name of the Python file containing the code and "SimpleTimerPlugin" is the
name of the module implementing the timer.
```shell 
## -*- coding: utf-8 -*-
from .s_timer import SimpleTimerPlugin
```

## plugin.info File
Contains metadata about the plugin and in our case will contain. The contents should be fairly obvious. 
The "name", "Version", whose scheme is arbitrary' and "Description" are what appear when you run Naomi with the 
--list-active-plugins. Other values are simply informational and not operationally effecting.
```shell 
Plugin]
Name = Simple Timer
Version = 1.0.0
License = MIT
URL = https://github.com/mcoyne1948/simple_timer
Description = Very basic elapse timer

[Author]
Name = Malcolm Coyne
URL = https://malcolmc.ca/
```

## s_timer.py File
Is the actual Python code implementing the plugin and has basically three main divisions. The first 
is initialization statements. The second is a Naomi readable description to assist it in recognizing
the intent of this plugin in the incoming stream of spoken words. Finally, the last division implements
the handler for when this intent is triggered.

### _Initialization_


```shell 
import time
from naomi import plugin
class SimpleTimerPlugin(plugin.SpeechhandlerPlugin):
```
### _Intent Function_

This function provides the framework for interpreting the input word stream and identifying
the timer intent is to be activated. The code can be seen below.
```shell 
def intents(self):
        return {
            'TimerIntent': {
                'locale': {
                    'en-US': {
                        'keywords': {
                            'NumberKeyword': [
                                'ONE',
                                'TWO',
                                'THREE',
                                'FOUR',
                                'FIVE'
                            ]
                        },
                        'templates': [
                            "SET TIMER {NumberKeyword} SECONDS",
                            "SET {NumberKeyword} SECOND TIMER"
                        ]
                    }
                },
                'action': self.handle
            }
        }
```
The **en-US** indicates the start of a language specific section and there can be multiple 
sections of this type in a single file for different languages. Within the language section
there is an optional **keywords** subsection which define the options to be considered for
one of the input ranges being evaluated. The second subsection, **templates**, define the
lexical structures that the input stream is going to be tested against to determine if it
specifies the timer intent.

### _Handler Function_

The handler defines the action(s) to be taken once the timer intent has been identified.
It has four major section; the function specifier, dictionary initialize, inputs test and 
code to perform the timer function. The first line shown below simply defines the function
name and the inputs which in this case are the **intent** information and the **mic** 
voice I/O functions.
```shell 
def handle(self, intent, mic):
```
The next section initialize some function variables. In this case a **NUMBERS** dictionary for decoding
numeric values from textual numbers is define, and default for the **ERROR** and **NUMBER** variable are set.
```shell 
        NUMBERS = {
            'ONE' :    1,
            'TWO' :    2,
            'THREE' :  3,
            'FOUR' :   4,
            'FIVE' :   5
        }
        ERROR = ''
        NUMBER ='ONE'
```
The next section first extracts the number identified by the **NumberKeyword** in the intent
stream. If this is missing or can't be resolve it sets an appropriate error. Next it tries 
to lookup the **NUMBER** in the **NUMBERS** dictionary. If this should fail then another 
error is set.
```shell 
        try:
            NUMBER = intent['matches']['NumberKeyword'][0]
            # print (" Number is: " + NUMBER)      # For debug
        except KeyError:
            ERROR = "Could not understand input. Please try again!"
        try:
            ETimer = NUMBERS[NUMBER]
        except KeyError:  
            ERROR = "Timer input out of range!"
```
The final sections takes the appropriate action for the plugin (skill). If an error has 
been detect Naomi announces it otherwise it proceed with the timer function. The timer
first announces the start, then uses the sleep function to time the elapse implementing
a delay and finishes by announcing the end.
```shell 
        if ERROR != '':
            mic.say(self.gettext("ERROR: %s!" % ERROR))
        # Run elapse timer   
        else:
            mic.say(self.gettext("Start " + NUMBER  + " second timer!"))
            time.sleep(ETimer)
            mic.say(self.gettext(NUMBER + " second timer finished!")
```

# Test and Debug
Once the plugin directory with its three files have been created it needs to be place in 
the **~/.config/naomi/plugin/speechhandler** directory. Then it can be loaded into Naomi with the
following terminal command. (The --debug piece is optional but will be useful for debugging if 
the plugin does not load.)
```shell 
naomi --install "s_timer" --debug |& tee ~/naomi.log
```
To check if the plugin has loaded enter the following:
```shell 
naomi --list-active-plugins
```
This gives an alphabetic listing of all install plugins so you can check if it is in the list.
If not, assuming you installed with --debug, you can open the naomi.log file (it should be in your 
home directory) and check for errors in our plugin code. Search for "simple_timer" 
which should bring up a **WARNING** that your plugin has been "skipped". Following this line should be
a traceback that can help with identifying the error in your code.

Fix your code and rerun the install process. If after reasonable effort you are unable to resolve
your issue help may be available from the sources in the following section.

# Getting Help With Plugin Development

A good method to start figuring out how to create a particular plugin is to see if in the list of
installed plugins in the **~/Naomi/plugins/speechhandler** directory or the 
[Naomi Plugin Exchange](https://projectnaomi.com/plugins/) (NPE) if there is one along the lines 
you are thinking and examine
its code to see if that helps. However, if after taking a crack at it should you run into problems 
you have been unable to work
through you can also consult the [Naomi community forum](https://support.projectnaomi.com) pages
or use the [Discord](https://projectnaomi.com/community) community.

<DocPreviousVersions/>
<EditPageLink/>
