---
id: padatious
label: Padatious
title: Padatious - Text to Intent
type: ttis
description: "Padatious is trained on the sentence as a whole."
source: https://github.com/NaomiProject/naomi-docs/edit/dev/NPE-Files/_plugins_ttis/Padatious/readme.md
meta:
  - property: og:title
    content: "Padatious - Text to Intent"
  - property: og:description
    content: "Padatious is trained on the sentence as a whole."
---

# Padatious - Text to Intent


Padatious uses the FANN2 (Fast Artificial Neural Net 2) library to train a neural net
to recognize intents.

Project home:
[https://github.com/MycroftAI/padatious](https://github.com/MycroftAI/padatious)

Installation:
```
sudo apt install cmake swig
git clone https://github.com/libfann/fann.git
cd fann
mkdir build
cd build
cmake ..
make
sudo make install
sudo ldconfig
sudo pip3 install padatious
```

profile.yml:
```
tti_engine: Padatious TTI
```

<EditPageLink/>
