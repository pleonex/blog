+++
# Project title.
title = "Dissertation"

# Date this page was created.
date = 2018-11-04T02:01:00+01:00

# Project summary to display on homepage.
summary = "Bachelor dissertation: _Data protection mechanisms in video games_."

# Tags: can be used for filtering projects.
tags = ["reverse-engineering"]

# Optional external URL for project (replaces project detail page).
external_link = ""

+++

# Data Protection Mechanisms in Video Games

Electrical Engineering Bachelor dissertation.
I researched different video games of Nintendo DS to find out how they were
protecting different sensitive content like text, video and audio to avoid
modifications and/or access. I documented the different algorithms, their
weakness and several recommendations to improve the protection.

* Project code name: `AiroRom`.
* [Report PDF](https://es.scribd.com/document/273318415/Mecanismos-de-proteccion-de-datos-en-videojuegos)
* [Presentation Slides](https://es.slideshare.net/pleonex/mecanismos-de-proteccin-de-datos-en-videojuegos)
* [Source code](https://github.com/pleonex/AiroRom)
* [Wiki](https://github.com/pleonex/AiroRom/wiki) with temporal results.

### Abstract

Video games are getting one of the most important elements of our culture.
The mobile market boom has made companies behind games like _Candy Crush_ very successful.
In that specific case, the game has about 356 millions of unique users and 1.300 millions of dollars in benefits.
The video game industry is in fact only before the book's one in top of profits and it gets over music and cinema.
It is not only about entertainment but also for education, specially for children, for instance, to learn new languages and help with mathematics.

All that benefit makes to think about how to protect against possible 'attacks'.
They started fighting piracy with Digital Rights Management techniques, that is, releasing copy of games without permissions from the author, but nowadays it deals with more fields.
Mods, cheats in online plays and translations made by fans to languages where the company is going to release a port of the game are only some examples.

This project aims to offer a new perspective about game security.
In it, we analyze products from Nintendo DS and Play Station 3 devices and mobile platforms like Android and iOS, to show what kind of techniques has been used to protect both text and images files, as well as sound archives.
Communication protocols for online services, download content protection and wireless code transmission will be studied too.
The general purpose of all these protection is to avoid doing reverse engineering, that is, disassemble the product to study all its pieces and resources.

Reverse engineering is one of the main topics of this dissertation.
Usually it is done as a hobby but, with the rights tools and knowledge it is a powerful way to test the security of a system.
Related to video games, it is called _romhacking_, since it is about modify (_hack_) a game (usually distributed in _Read Only Memories_).
These project will use common tools like disassemblers and debuggers.
For instance, for Nintendo DS games two emulators will be used.
The first one, DeSmuME, since it is open source, it will allow to hack its code to automatize task and save network packets.
The second one, No$GBA, _freeware_, includes a built-in debugger so it will be used to analyze code and algorithms.
Some tools have been developed to help with the task of studying games, like binary searcher, database manager and some game specific exporters.
Furthermore, all the methodology followed to figure out formats and algorithms will be explained in detail.

This project concludes with a summary of the mechanism analyzed, with recommendations to improve them.
Most copyright contents, that usually contains DRM in virtual stores, are not protected in games.
That refers to music, electronic books and videos.
However, text and images are usually protected with encryption by using `XOR` operand, `HMAC` algorithm or a digital signature.
About the online services, it will show how bad protocol designs has been found, with some vulnerabilities that allow to users to cheat, but also how in some games the download content has a good protection against external modifications and man-in-the-middle attacks.
