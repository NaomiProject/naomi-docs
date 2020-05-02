---
id: wwisweather
label: WWIS Weather
title: WWIS Weather - Speechhandler
type: speechhandlers
description: "Get weather forecasts from World Weather Information Service"
logo: images/plugins/wwis.png
source:
meta:
  - property: og:title
    content: "WWIS Weather - Speechhandler"
  - property: og:description
    content: "Get weather forecasts from World Weather Information Service"
---


# WWIS Weather - Speechhandler <Badge text="Included"/>

<PluginLogo/> 

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

### setup WWIS Weather in `~/.config/naomi/configs/profile.yml`

```yaml
wwis_weather:
  city: ''
  country: New Zealand
  region: Rotorua
```

<EditPageLink/>