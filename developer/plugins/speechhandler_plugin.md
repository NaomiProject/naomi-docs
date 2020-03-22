---
title: SpeechHandler Plugins Development
source: https://github.com/naomiproject/naomi-docs/blob/dev/developer/plugins/speechhandler_plugin.md
meta:
  - property: og:title
    content: "SpeechHandler Plugins Development"
  - property: og:description
    content: Naomi, The privacy focused personal assistant
---

# SpeechHandler Plugin Development

Parent Class: plugin.SpeechHandlerPlugin<br />
Required Methods:<br />
&nbsp;&nbsp;**intents()**<br />
&nbsp;&nbsp;&nbsp;&nbsp;Parameters:<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;none<br />
&nbsp;&nbsp;&nbsp;&nbsp;Returns an intents structure<br />

&nbsp;&nbsp;**handle(intent, mic)**<br />
&nbsp;&nbsp;&nbsp;&nbsp;Parameters:<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;intent: a returned intent structure<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;mic: allows naomi to listen and speak<br />
&nbsp;&nbsp;&nbsp;&nbsp;Returns null<br />

Optional Methods:<br />
&nbsp;&nbsp;**settings()**<br />
&nbsp;&nbsp;&nbsp;&nbsp;Parameters:<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;none<br />
&nbsp;&nbsp;&nbsp;&nbsp;Returns a settings structure<br />

## Writing a speechhandler plugin

So you installed Naomi and had a pleasant conversation about the time and
weather. Now you have an idea for something you would like Naomi to do, but
aren’t sure how to start working on it. We welcome new ideas for Naomi, and
now we have a store where you can make your plugin available to everyone using
Naomi. Let's walk through the process of creating a SpeechHandler plugin.

Start by creating a new project on Github or some other online git repository
(the Naomi Project does not host the plugins in the store, just links to them,
so you need to put your source code someplace where others will be able to
access it). Give your project a name and select a license (we use the MIT
license, so if you choose a more restrictive license like GPL and decide to
distribute Naomi with your plugin, you can distribute the whole thing under
GPL. If you would like the NaomiProject to consider bundling your plugin with
Naomi, you should use the MIT license).

Now, navigate to the ~/.naomi/plugins/speechhandler folder (or wherever your
local settings folder is located, this is the default, so this is where it
will be unless you changed it) and git clone your repository (if that sentence
didn’t make any sense to you, try searching for “git clone” online). Now
create the following files in your cloned project folder:

* `plugin.info` (basic information about a plugin, like name and version)
* `__init__.py` (this lets python know that this is a package)
* `yourproject.py` (this can be named anything)

There are a lot of examples of packages in the plugins/ directory under the
main Naomi folder, so you can look to them for examples of what can go into
this file. Here are the most important parts:

### `plugin.info` File

The info file is set up with major sections marked by a section header which
is surrounded by square brackets ([Plugin]) followed by Name = Value pairs.
Naomi only looks at the [Plugin] section, and only requires the _Name_,
_Version_, _URL_ and _Description_ fields. Your plugin must either contain
a license file (`LICENSE`, `LICENSE.md`, `LICENSE.txt`) or have a value in the
License line under the [Plugin] section. Version and Description are only used
when listing or installing plugins. The URL is used to determine whether you
are trying to update an existing plugin, or install a new plugin with a
similar name.

Here is a typical `plugin.info` file:

```
[Plugin]
Name = You are Welcome
Version = 1.0.0
License = MIT
URL = https://github.com/aaronchantrill/yourwelcome.git
Description = Responds to “Thank you” with “You are Welcome”
```

You are welcome to include additional information and add additional
sections, but this is all that is required. The sections that users most
commonly add are [Author], [Contact] and/or [Support].

### `__init__.py`

Now the `__init__.py` file provides the actual entry point into your plugin.
In fact, you could put your entire plugin into the `__info__.py` file, but
traditionally people tend to keep this file pretty sparse and just use it to
import the main module:

```python
from .youarewelcome import YouAreWelcomePlugin
```

### Main plugin module

So far, pretty simple. Now the main part of the plugin contains a class with
a couple of specific methods.

```python
from naomi import plugin

class YouAreWelcomePlugin(plugin.SpeechHandlerPlugin):

    def intents(self):
        return {
            'Youre_WelcomeIntent': {
                'templates': [
                    self.gettext('Thank you'),
                    self.gettext('Thanks')
                ],
                'action': self.handle
            }
        }

    def handle(self, text, mic):
        response = random.choice([
            self.gettext("You are welcome"),
            self.gettext("You’re welcome"),
            self.gettext("Don’t mention it"),
            self.gettext("It was nothing, I’m serious, it meant nothing to me")
        ])
        mic.say(response)
```

**intents**

The first method that every SpeechHandler plugin has to have is “intents”.
This returns a dictionary structure telling Naomi how you expect people to
activate your plugin. Here is a typical intents method:

```python
def intents(self):
  return {
    “YouAreWelcomeIntent”: {
      ‘templates’: [
        self.gettext(“Thank you”),
        self.gettext(“Thanks”)
      ],
      ‘action’: self.handle
    }
  }
```

This is a simple intent with only two elements: templates and action. This is
the minimum required. The templates node contains a single list of things
someone might say to activate this plugin, and the action node contains a
reference to the entry method for the plugin. Note that this is an actual
reference to the method, not just the name of the method, and the method does
not have parenthesis after it because you are passing a reference to the method
itself, not the result of calling the method.

There are currently two other elements that can be added to an intent,
keywords and regex.

_keywords_ are a list of words that can be matched by the intent parser. For
instance, Naomi's confidence would most likely increase if you rewrote the
above intent as:

```python
def intents(self):
  return {
    “YouAreWelcomeIntent”: {
      'keywords': {
          'ThanksKeyword': [
              "thank you",
              "thanks"
          ]
      },
      'templates': [
          '{ThanksKeyword}'
      ],
      ‘action’: self.handle
    }
  }
```

This way, the intent parser will see '{ThanksKeyword}' as a single word that
appears in every template for this intent, and not in any of the templates
belonging to other intents.

_regex_ are currently only used by the Adapt intent parser, but they are so
central to the way Adapt and other atomic type intent parsers work that we had
to include it. This allows you to extract a value from a phrase based on a
regular expression. For instance, if you wanted to match and return the value
to be searched for from the requests "search for cats on youtube" or "search
youtube for cats", you could write an intents method like this:

```python
def intents(self):
  return {
    'SearchIntent': {
      'keywords': {
        'EngineKeyword': [
          "google",
          "youtube",
          "instagram"
        ]
      },
      'regex': {
        'Query': [
          " for (?P<Query>) on ",
          " for (?P<Query>) using ",
          " for (?P<Query>.*)$"
        ]
      },
      'templates': [
        'search for {Query} using {EngineKeyword}',
        'search for {Query} on {EngineKeyword}',
        'search {EngineKeyword} for {Query}'
      ],
      'action': self.handle
    }
  }
```

**handle**

The handle method must have the following declaration:

```python
def handle(self, intent, mic):
```

The structure passed to the "intent" parameter tells the plugin why it was
activated and may contain some information about matched words, and the object
passed to the “mic” parameter can be used to communicate with the user.
For example, the SearchIntent above would return a return intent structure
like this:

```python
{
  'action': &lt;function &lt;lambda&gt; at 0x7f85d000b6a8&gt;,
  'input': 'SEARCH FOR CATS ON YOUTUBE',
  'intent': 'SearchIntent',
  'matches': {
    'Query': ['cats'],
    'EngineKeyword': ['youtube']
  },
  'score': 0.8333333333333334
}
```

From this, it is easy to see that the intent parser believes that the user
probably wants to perform a youtube search for cats.

In our YouAreWelcome plugin example, the handle method is really simple:

```python
def handle(self, intent, mic):
  mic.say(self.gettext(“You are welcome”))
  return True
```

### Internationalization

Now, you might be wondering what self.gettext() is in the above examples.
Self.gettext is created in the plugin.GenericPlugin base class that all plugins
are derived from, and is used for internationalization. Naomi is an
international application and we want to make it available in as many languages
as possible. Right now we have good support for English, French and German.
If you are interested in helping to add a new language through translations,
testing, or documentation, please reach out to the Naomi Project team.

When you run ./update_translations.py, every python program will be searched
for gettext(“.*?”) and the contents of “.*?” will be added to a .pot file. That
.pot file will be combined with the current .po file (if there is one) creating
a .po file. This file is basically just a list of all of these static strings,
with space to add a translation below. For example, here is a small .po file:

```
# #-#-#-#-#  fr-FR.po (Naomi 2.2-dev)  #-#-#-#-#
# Naomi YouAreWelcomePlugin
# Copyright 2019
# Distributed under the MIT license
#
#, fuzzy
msgid ""
msgstr ""
"Project-Id-Version: Naomi 2.2-dev\n"
"Report-Msgid-Bugs-To: https://github.com/NaomiProject/Naomi/issues"
"POT-Creation-Date: 2019-10-09 19:00+0100\n"
"PO-Revision-Date: 2019-10-10 00:16+0100\n"
"Last-Translator: Aaron Chantrill <aaron.chantrill@dottywood.org>\n"
"Language: fr_Fr\n"
"Plural-Forms: nplurals=2; plural=(n>1);"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"
"Generated-By: pygettext.py 1.5\n"

#: youarewelcome.py:19
msgid "Thank you"
msgstr "Je vous remercie"

#: youarewelcome.py:20
msgid "Thanks"
msgstr "Merci"

#: youarewelcome.py:27
msgid "You are welcome"
msgstr "Je vous en prie"
```

It is important to note that when the phrases are extracted, the program is
not running and none of the variable have values. So if you put your gettext
method around a variable, only the variable name is returned to the .pot file.
So, for instance, if you do something like this:

```python
response = random.choice([
  “You are welcome”,
  “You’re welcome”,
  “Don’t mention it”,
  “It was nothing, I’m serious, it meant nothing to me”
])
mic.say(self.gettext(response))
```

Nothing will be returned in the .pot file for response. So always do this:

```python
response = random.choice([
  self.gettext(“You are welcome”),
  self.gettext(“You’re welcome”),
  self.gettext(“Don’t mention it”),
  self.gettext(“It was nothing, I’m serious, it meant nothing to me”)
])
mic.say(response)
```

A common mistake is to try to split up text like this:

```python
self.gettext("It was nothing," +
  "I’m serious, " +
  "it meant nothing to me"
)
```

or this:

```python
self.gettext(" ".join(
    [
        "It was nothing,",
        "I’m serious,",
        "it meant nothing to me"
    ]
))
```

When you go to create a translation file, you will get an error message like:
`*** youarewelcome.py:31: Seen unexpected token "+"`
or
`*** youarewelcome.py:31: Seen unexpected token "."`

You pretty much have to keep the entire line of text on one line between the
quotation marks. Also, please don’t enter any punctuation into the intents,
other than apostrophes that are part of words. We do not currently clean that
input, and punctuation will likely cause an error.

**Settings**

Now suppose you need some information from the user to set up your plugin. Say
you are writing a plugin that uses a web service to list upcoming movie times.
You don’t want to list all movie times all over the country, and you don’t want
the user to have to tell Naomi exactly where they are every time they want
movie information. So when your plugin loads for the first time, the user is
asked to enter their zip code so that information can be passed to the web
service you are using.

You can add the settings method to Naomi:
```python
def settings(self):
        _ = self.gettext
  return OrderedDict(
            [
                ('zipcode',): {
                    "title": _("What is your zip code?"),
                    "description": _("Providing your zip code will help the Movietime plugin bring you the most relevant movie information")
                }
            ]
        )
```

The structure returned by the settings method has a number of different fields that can be used to describe how you want to collect information. Right now, this only happens sequentially through the text interface as you start Naomi. We hope to have a web service that will generate forms that can be accessed via a web browser soon. In the meantime, it is important that you start Naomi manually and not as a service after installing a new plugin, in case that plugin needs to request information.

**NAME** - (required) The name of the variable as seen by the developer. Since this can be a multi-level variable, it will be passed as a tuple containing the nodes to the path. So, to set the value

```yaml
email:
  address: me@myhostname.net
```

you would use the tuple ('email','address'). This will form the key for a
dictionary containing the whole form.

**TYPE** - (optional, default "textbox") - This is the general form for the
control, without specifics about how to implement it. These fall into the
following general categories:
* A simple text input box (default)
* “boolean” - A simple yes/no question (only possible responses are yes or no)
* “combobox” - A combobox where the user can select a value from a list or
enter a new value
* “listbox” - A listbox where the user can only select a value from the
provided list (or an empty string)
* “file” - A file select box where the user can either browse the server
filesystem looking for a file, or can upload a file from their local filesystem
which will be saved in a location on the server.

Notice that I don't specify radio buttons or checkboxes since these are
implementation details covered by the concept of a listbox. We will probably
also need a multiple list box where multiple options can be selected, but there
isn't an instance where that is currently required for Naomi.

**TITLE** - (required) A brief (five words or so) description of the setting.

**DESCRIPTION** - (optional, default "") a longer description of what exactly
the setting does.

**DEFAULT** - (optional, default "") The default value as chosen by the developer
of the plugin. This can be a function. This will only show up if the user has not
previously selected a value.

**OPTIONS** - (optional, default []) In the case of a combo or list box, a list
containing the available choices. This can be a function.

**VALIDATION** - (optional, default True) a function used to validate the user
response and make sure the user entry is valid. If the value entered by the
user is not valid, then the setting will not be saved. On the command line,
the question will continue to be put to the user until they enter a valid
response. An empty response will always be valid and can be taken to mean that
the user has chosen not to respond. Some standard validation functions (for
checking things like email address, number, integer, etc.) have been provided
for developers.

**ACTIVE** - (optional, default True) a function used to tell if this should be
active or not based on the current state of the form. This is used to disable or
enable an option depending on values entered into the system.

### Publishing your plugin

So you have made it all the way through and your plugin works just the way you
always hoped it would. Congratulations! Now we would love for you to share your
creation with us. You did _git commit_ your files and then _git push_ the
changes to your online repository, right? If not, please take a moment to do so
now.

Now publishing your plugin through Naomi requires forking a new repository and
adding a line to a CSV file.

To start, make a fork of the naomi-plugins repository at
https://github.com/NaomiProject/naomi-plugins

Now edit the plugins.csv file and add a line containing information about your
plugin. This is very simple, so you can just use the online editor on GitHub.
There’s no need to clone the file locally, but you can if you like.

Fill in the fields of the table. Most of this information (Name, Version,
Description) can be copied directly from your plugin.info file. The Repository
field should be the URL from the plugin’s [Plugin] section, the category should
be the type of plugin (audioengine, speechhandler, tti, tts, stt,
stt_trainer, vad, or visualizations).

The last field is "commit". This will identify the actual git commit that will
be installed by the store. If you continue to modify the project after
submitting it, the changes will not be available to users downloading your
project through the store until this value is updated. If you don't know
exactly how this works, don't worry about it. One of the Naomi core developers
will add this value for you when your naomi-plugins pull request is merged.

Once you are finished adding your line, create a pull request to merge your
changes back into the naomi-plugins repository. Once your pull request has been
merged, users will be able to use Naomi's built-in store functions to install
your plugin.

<DocPreviousVersions/>
<EditPageLink/>
