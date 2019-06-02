---
title: "“Anita Jacket”: Designing an Alexa Skill to determine if you need a jacket"
description: "So, both Alexa and Google Home give me a weather report when I say something like “Hey Alexa, do I need a jacket?” or “Should I wear a coat outside today?”. However, neither one of them actually…"
date: "2017-10-30T19:51:43.203Z"
categories: 
  - Amazon Echo
  - Alexa
  - Alexa Skills
  - Design Process
  - Design

published: true
canonicalLink: https://medium.com/@jamesfuthey/anita-jacket-designing-an-alexa-skill-to-determine-if-you-need-a-jacket-ebc8b35c285f
---

## A Modern Voice-Design & Development process for an Alexa Skill

So, both Alexa and Google Home give me a weather report when I say something like “Hey Alexa, do I need a jacket?” or “Should I wear a coat outside today?”. However, neither one of them actually answers the question: Do I need a jacket?

![]([https://raw.githubusercontent.com/kidGodzilla/personal-blog-test/master/adding-a-meeting-room-resource-to-g-suite/](https://raw.githubusercontent.com/kidGodzilla/personal-blog-test/master/adding-a-meeting-room-resource-to-g-suite/asset-1.png)

I understand this is a personal preference issue. For some, 55 degrees may be nothing. For others, 65 may warrant a light jacket. But, interested in diving deeper into the Alexa skills API, I thought this would be a nice intermediate-level challenge to create a skill.

#### Invocation Name

So, the first stumbling block appeared rather quickly. Invocation names for Alexa need to be a clunky two-to-three-word noun-graph. And I mean exactly two or three words. No flexibility there. Ideally, Amazon would like you to ask:

> “Hey Alexa, can you ask the weather channel if it’s going to rain today?”

And avoid giving developers access to things like:

> “Hey Alexa, is it snowing right now?”

So, I went out searching for alternatives.

#### Knock Knock

My lack of maturity immediately swooped in to save the day, in the form of a knock-knock joke.

![Anita minute to come up with a better Alexa skill name.]([https://raw.githubusercontent.com/kidGodzilla/personal-blog-test/master/adding-a-meeting-room-resource-to-g-suite/](https://raw.githubusercontent.com/kidGodzilla/personal-blog-test/master/adding-a-meeting-room-resource-to-g-suite/asset-2.png)

> Knock, knock!  
> Who’s there?  
> Anita.  
> Anita who?  
> Anita nother minute to think it over.

This is a bit of a hack, but, I decided to name the app **“Anita Jacket”**. Perhaps if it gets a bit colder out, I’ll create a follow-up intent called **“Anita Coat”**.

### Brainstorming

Next, I took a few minutes to contemplate how the app should work.

![](https://raw.githubusercontent.com/kidGodzilla/personal-blog-test/master/adding-a-meeting-room-resource-to-g-suite/asset-3.png)

#### Design Guidelines & Heuristics

I spent some time thinking about this topic in a [previous post](https://medium.com/@jamesfuthey/a-ux-design-process-for-designing-an-alexa-skill-8580e132fc78). You should give it a quick read if you’re interested in [designing for Alexa](https://medium.com/@jamesfuthey/a-ux-design-process-for-designing-an-alexa-skill-8580e132fc78).

[https://medium.com/@jamesfuthey/a-ux-design-process-for-designing-an-alexa-skill-8580e132fc78](https://medium.com/@jamesfuthey/a-ux-design-process-for-designing-an-alexa-skill-8580e132fc78)

#### Role Playing as Usability Testing

I would recommend writing a short script as a text document, printing it out (leave plenty of margins / double space), and grabbing a friend to role play your interaction with Alexa.

Pretend you are Alexa, and read every word. Note every deviation your tester makes from the “happy path”, and use this as a guideline to make changes to your app, to add increased flexibility.

Use their feedback to tweak your response, while striving to make it as concise as possible.

This will save you a lot of work down the line!

### API Research

_What do I need?_

-   Ability to lookup by zip code
-   Weather condition forecast for the current day
-   Current Temperature & Temperature forecast (high/low)

**Best Solution:** [MetaWeather API](https://www.metaweather.com/api/)

[**API — MetaWeather**  
_MetaWeather provides an API that delivers JSON over HTTPS for access to our data._www.metaweather.com](https://www.metaweather.com/api/ "https://www.metaweather.com/api/")[](https://www.metaweather.com/api/)

**Pros**

-   Does not require an API key
-   Works in the US
-   Returns temperature and forecast data
-   It’s **free\***

**Cons**

-   Values in Metric / Centigrade
-   Cannot directly look up a WOEID by zip-code. Requires an intermediate lookup table or API.

### Dialogue Flow

Next, I created a dialog flow diagram to iterate on the concept.

![]([https://raw.githubusercontent.com/kidGodzilla/personal-blog-test/master/adding-a-meeting-room-resource-to-g-suite/](https://raw.githubusercontent.com/kidGodzilla/personal-blog-test/master/adding-a-meeting-room-resource-to-g-suite/asset-4.png)

### Prototype

For the prototype, I used [Storyline](https://thestoryline.io/). This allowed me to create a functional prototype, even including the API, without coding.

**Preview / Prototype on Storyline:** [https://thestoryline.io/preview/ba5fd654ca928e9afd2bf3f193143adc4d39cc5c](https://thestoryline.io/preview/ba5fd654ca928e9afd2bf3f193143adc4d39cc5c)

_This helped identify issues such as:_

-   The need for a ZIP lookup table
-   The need for an “inflection” step (**Heavy Rain** -> **Raining**, **Light Cloud** -> **Partially Cloudy**, etc.)

As well as create a sharable webpage I could use to get feedback.

### Development

#### ZIP code database

There are a few APIs that will do this for you. Google can do it, but it requires an API access key to do so. I’ve managed to avoid getting one thus far for this project, so I kept looking for alternatives. Quickly, I found:

[**Free Zipcode Database | Free Zip Code Database**  
_Current, Free ZIP Code Database: All US Zipcodes listed in database formats_federalgovernmentzipcodes.us](http://federalgovernmentzipcodes.us/ "http://federalgovernmentzipcodes.us/")[](http://federalgovernmentzipcodes.us/)

They offer two relatively-small databases. I chose the one that gives only a single location per zip code entered. It comes in CSV format.

![]([https://raw.githubusercontent.com/kidGodzilla/personal-blog-test/master/adding-a-meeting-room-resource-to-g-suite/](https://raw.githubusercontent.com/kidGodzilla/personal-blog-test/master/adding-a-meeting-room-resource-to-g-suite/asset-5.png)

Also, I’m perfectly fine with a relatively-accurate solution. I’m not mailing anything. I’m looking up the weather. If we’re one city off, the forecast probably doesn’t differ enough to matter.

Then, I removed the extra columns so that only **ZIP Code, City, State, Lat,** & **Long** remained.

**Original size:** 4.2mb

**Reduced size:** 1.4mb

**Reduced size (2):** 840kb (only lats & longs)

**Reduced size (3):** 799kb (Single-line, parseable blob of text)

![This lookup table looks a bit like a rainbow table, but at under 800kb, it can be inserted directly into my Lambda skill Javascript file, so I don’t have to pay execution milliseconds for an extra lookup request.]([https://raw.githubusercontent.com/kidGodzilla/personal-blog-test/master/adding-a-meeting-room-resource-to-g-suite/](https://raw.githubusercontent.com/kidGodzilla/personal-blog-test/master/adding-a-meeting-room-resource-to-g-suite/asset-6.png)

**_Note:_** _This could be further reduced if you were ok with ZIP code ranges, but I do not have the expertise for this task._

If you’re looking for a more robust solution (and not too worried about table size), [this package on NPM](https://www.npmjs.com/package/zipcodes) is probably what you’re looking for.

#### Execution / API Lookup Flow

![A brief overview of what our skill needs to accomplish](./asset-7.png)

As you can see, our app needs to accomplish a lot!

1.  Skill is invoked by Alexa
2.  Alexa kicks off the execution of an AWS Lambda function
3.  Our function requests the device ID, so it can request additional permissions
4.  We get an authorization token from Alexa which allows us to request the device’s location
5.  We request the device’s location, getting back ZIP code+country code (JSON)
6.  We use a lookup table to determine the lat/long for the ZIP code (US Only)
7.  We use the **MetaWeather API** to look up the [**WOEID**](https://en.wikipedia.org/wiki/WOEID) for the lat/long provided
8.  We use the **MetaWeather API** to retrieve a 7-day forecast for our WOEID (we only need the first day)
9.  We work through a simple decision tree to determine if a jacket is required, taking into account current/projected conditions, current temperature, and the future temperature range.
10.  We build a set of responses for Alexa, including a voice response, and a visual display card (appears in the App and in newer Alexa devices with screens)
11.  We send the response and end execution.

#### Testing Hiccups

**TLDR;** **Alexa doesn’t support in-browser testing with a location ID.**

So, you have to do a soft submission of your skill (writing all the metadata, including privacy policies, and creating a set of Skill icons), and invite yourself as a “beta tester” to actually get a country and zip code with an invocation. **This is a minor pain in the a\*\*.**

**Suggestion to the Alexa team:** Let people use **Echosim.io** with a default address (for testing).

**Suggestion for developers:** Build you Skill with dummy data and get everything else working perfectly. Look at the documentation to see the exact JSON response you should expect from Amazon, and mock it. Then, when everything else is completed, work on the **location API** integration.

#### In-browser testing

You can test your app at (almost\*) every step of the way using **echosim.io**. I highly recommend it. However, the forecast will always be for **Seattle, WA**.

[**Alexa Skill Testing Tool - Echosim.io**  
_Echosim.io is an online community tool for developers that simulates the look and feel of an Amazon Echo._echosim.io](https://echosim.io/ "https://echosim.io/")[](https://echosim.io/)

**_Why can’t that just be the default?_** If I ask Echosim.io for the weather it already defaults to Virgina (US-East-1). Grr… :)

Anyway..

### Online Demo

You can’t see this toy app since it’s still unpublished. So, I recorded a short video:

Have your own experience or tips on Designing for Voice & Alexa?

Let me know what you think!
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTkxMzYwNDg0MF19
-->