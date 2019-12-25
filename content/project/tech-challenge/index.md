---
title: "IV Tech Challenge"
summary: "University competition simulating a start-up."
authors: ['admin']
tags: ['iiot', 'dds']
categories: []
date: 2018-11-04T02:01:00+01:00

image:
  caption: ""
  focal_point: ""
  preview_only: false

links:
- name: Blog
  url: http://blogs.rti.com/2015/01/20/from-college-students-to-entrepreneurs/
  icon_pack: far
  icon: newspaper

url_code: "https://github.com/Prometheus-ETSIIT/locaviewer"
url_pdf: "https://github.com/Prometheus-ETSIIT/locaviewer/blob/master/Fase%20III%20-%20Memoria.pdf"
url_slides: ""
url_video: ""
---

{{< figure src="logo.png" >}}

{{% alert note %}}
Our team won the challenge!
{{% /alert %}}

As part of a group of four students named _Prometheus_, we participated in an
event organized by our university: University of Granada. We participated in the
four edition of the so called _Tech Challenge_. It was sponsored by the company
RTI who proposed the topic of the challenge: _"create a distributed video
system"_. The goal was to simulate a start-up and create from scratch a
prototype ready to go to the market. We did a market research, study of prices
and present a full proposal with a working prototype.

{{< figure src="locaviewer_ui1.png" title="Locaviewer application" >}}

Our proposal was a video-system for kindergartens. The objective was that
parents could get a clear image of their baby only. For that, we tracked the
position of the babies using a Bluetooth wearable device in the wrist. Then,
using Bluetooth devices in the walls, we could locate the babies. That allow us
to select the camera that had the best video for that person and stream only
that video. To send and receive the sensor data and video we use the distributed
protocol DDS with the implementation of RTI Connext DDS.

{{< figure src="dds.png" title="DDS design" >}}
