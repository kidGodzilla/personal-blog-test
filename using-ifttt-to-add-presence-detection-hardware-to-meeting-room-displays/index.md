---
title: "Using IFTTT to Add Presence Detection Hardware to Meeting Room Displays"
description: "We’ve added an IFTTT integration, which allows you to connect hundreds of hardware devices to Meeting Room 365, including Blink and Wyze cameras, and various IR presence detection sensors, to enable…"
date: "2019-05-12T22:55:15.410Z"
categories: 
  - IFTTT
  - Meetings
  - DIY
  - Business
  - Startup

published: true
canonicalLink: https://medium.com/@jamesfuthey/using-ifttt-to-add-presence-detection-hardware-to-meeting-room-displays-11b632295a7d
---

## Force check-ins without the hassle.

We’ve added an IFTTT integration, which allows you to connect hundreds of hardware devices to Meeting Room 365, including Blink and Wyze cameras, and various IR presence detection sensors, to enable room booking, automatic reservations, end early, forced check-ins, and calendar sync, based on the physical presence of employees in a particular meeting room.

![](./asset-1.jpg)

This makes it much easier to enable the “force-check-in” option, and “end-early” features, since they happen automatically, regardless of whether your team knows how to use them (or remembers).

![](./asset-2.png)

### Choosing Hardware

We’ve tested presence detection ourselves extensively with the inexpensive [Wyze camera](https://www.wyze.com/wyze-cam/) ($26 shipped), and the [Blink](https://www.amazon.com/Blink-Home-Security-Detection-Included/dp/B019S3ULQM/) cameras (from $64). Additionally, there are hundreds of supported devices in the IFTTT ecosystem, which can be used for presence detection.

While every situation is different, there seems to be many paths to reliably implementing this and many factors to consider. Purchasing a single test device for a pilot is almost always a safe bet.

### Setting up your Camera in Meeting Room 365

Your first step will be to set up your camera hardware in Meeting Room 365. To do this, just open your display, head to the Hardware tab, and check `Receive Motion events from IFTTT`.

![](./asset-3.png)

This will give you a unique URL which you can later use in IFTTT to configure a webhook trigger.

Optionally, you can disable automated check-ins from the Meeting Room 365 admin portal, by later checking the box **“Disable automated check-ins”**. This lets you keep IFTTT configured if you need to modify or disable this feature in the future.

### Configure a trigger in IFTTT

Next, you’ll want to configure a trigger in IFTTT. We’ll be setting up the Wyze camera in our example, but you should be able to do this with a variety of hardware products, including motion sensors, and cameras with presence detection.

#### Create a New Applet

![](./asset-4.png)

**Choose your service**

![](./asset-5.png)

**Choose a motion detection trigger**

![](./asset-6.png)

**Choose a device  
**You may have to configure this device by connecting it to IFTTT

![](./asset-7.png)

**Configure a Trigger**

![](./asset-8.png)

Select **Webhooks**

![](./asset-9.png)

Choose **Make a Web Request**

![](./asset-10.png)

**Grab your Webhook URL from Meeting Room 365**

![](./asset-11.png)

**Configure this as your trigger URL**

![](./asset-12.png)

Make sure to select GET method and text/plain content type.

**Turn off notifications**

![](./asset-13.png)

You won’t want to get an email each time motion is detected, unless you’re just troubleshooting your initial setup.

**Click Finish**

![](./asset-14.png)

That’s it!

**You should now see this IFTTT applet enabled:**

![](./asset-15.png)

Now, if you have I**nstant Reservations** enabled, they will happen automatically (in 15 minute increments) when someone walks into an empty meeting room.

If you have **End Early** enabled, your meetings will end early when no one is in the room for 5 minutes or longer, keeping Outlook current.

If you have **Force Check-in** enabled, this will occur automatically when users are present in the room.

As always, if you have any questions, please reach out to support and let us know. **Thanks for reading!**