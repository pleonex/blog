+++
title = "Tinke"
summary = "Program to modify files from Nintendo DS games. Superseded by Yarhl."
authors = ['admin']
tags = ['reverse-engineering']
categories = []
date = 2018-11-04T02:01:00+01:00

url_code = "https://github.com/pleonex/tinke"
url_pdf = ""
url_slides = ""
url_video = ""

[[links]]
name = "Forum"
url = "http://gbatemp.net/topic/303529-tinke-072/"
icon_pack = "fas"
icon = "comments"

# Album
[[gallery_item]]
album = "tinke"
image = "tinke/tinke.png"
caption = "Tinke UI"

[[gallery_item]]
album = "tinke"
image = "tinke/nds_header.png"
caption = "Information of Nintendo DS game header"

[[gallery_item]]
album = "tinke"
image = "tinke/texture.png"
caption = "View game textures"

[[gallery_item]]
album = "tinke"
image = "tinke/layton.png"
caption = "Specific game support via plugins (Professor Layton)"

[[gallery_item]]
album = "tinke"
image = "tinke/sprite.png"
caption = "View game sprites"

[[gallery_item]]
album = "tinke"
image = "tinke/audio.png"
caption = "Listen to game music (and edit it)"

[[gallery_item]]
album = "tinke"
image = "tinke/font.png"
caption = "View and edit game fonts"
+++

{{% alert warning %}}
Deprecated program. Superseded by [Yarhl]({{< ref "/project/yarhl/index.md" >}})

Don't judge the code, I wrote the whole program while learning programming 😄
{{% /alert %}}

Tinke is a program to see, convert, and edit the files of NDS games.
You can see a lot of format files like images, text, sounds, fonts and textures.
Furthermore it works with plugins made in NET Framework languages
(C# and VB.NET) so it's so easy to support new formats.

## Features

- Show the ROM header with the banner and edit it.
- Show and convert to common format a lot of files.
- Edit a lot of image files from BMP files (NCLR, NCGR, NSCR, NCER), audio files from WAV (SWAV, SWAR, STRM) and fonts (NFTR).
- Hexadecimal visor.
- Change the content of the files and save the new ROM.
- Translated to multiple languages.

{{< gallery album="tinke" >}}
