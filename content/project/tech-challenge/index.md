+++
# Project title.
title = "IV Tech Challenge"

# Date this page was created.
date = 2018-11-04T02:01:00+01:00

# Project summary to display on homepage.
summary = "University tech challenge to simulate a start-up."

# Tags: can be used for filtering projects.
tags = []

# Optional external URL for project (replaces project detail page).
external_link = ""

# Featured image
# To use, add an image named `featured.jpg/png` to your project's folder.
[image]
  # Caption (optional)
  caption = ""

  # Focal point (optional)
  # Options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
  focal_point = "TopLeft"

+++

Three friends and me formed a group named _Prometheus_ and participated in an
event organized by our university: University of Granada. We participated in the
four edition of the so called _Tech Challenge_. It was sponsored by the company
RTI who proposed the topic of the challenge: _"create a distributed video
system"_. The goal was to simulate a start-up and create from scratch a
prototype ready to go to the market. We did a market research, study of prices
and present a full proposal with a working prototype.

Our proposal was a video-system for kindergartens. The objective was that
parents could get a clear image of their baby only. For that, we tracked the
position of the babies using a Bluetooth wearable device in the wrist. Then,
using Bluetooth devices in the walls, we could locate the babies. That allow us
to select the camera that had the best video for that person and stream only
that video. To send and receive the sensor data and video we use the distributed
protocol DDS with the implementation of RTI Connext DDS.

{{% alert note %}}
Our team won the challenge!
{{% /alert %}}

* [English blog post](http://blogs.rti.com/2015/01/20/from-college-students-to-entrepreneurs/) about the experience.
* [Spanish final report](https://github.com/Prometheus-ETSIIT/locaviewer/blob/master/Fase%20III%20-%20Memoria.pdf).
* [Source code](https://github.com/Prometheus-ETSIIT/locaviewer).
