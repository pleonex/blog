---
featured: false
title: "El misterio de las claves de Pokémon Mundo Misterioso"
event: GDG DevFest Jaén
event_url: https://devfest.gdgjaen.me/
location: Jaén, Spain
summary: "[Spanish] Reverse engineering of the rescue mission key generation and validation in Pokemon Mystery Dungeon (NDS)."
abstract: "En esta charla se explicará cómo se verifican y generan las claves de misiones de rescate en el juego de Nintendo DS Pokemon Mundo Misterioso. Se mostrará todo el proceso de investigación y ROM Hacking llevado mediante el análisis del código en ensamblador del juego y, se detallarán los algoritmos encontrados y como se han desarrollado programas para replicarlos y poder generar las claves. Anécdotas y curiosidades encontradas en cuanto al funcionamiento interno del juego y decisiones que tomaron los desalloradores del juego están incluidas."

date: 2018-11-17T18:00:00+01:00
date_end: 2018-11-17T18:50:00+01:00
all_day: false
publishDate: 2018-11-01T18:00:00+01:00

authors: ['admin']
tags: ['reverse-engineering']
projects: []

image:
  caption: "Image credit: [**chubbykitty**](http://gallery.minitokyo.net/view/607532)"
  focal_point: ""
  preview_only: false

links:
- name: Twitter thread
  url: "https://twitter.com/pleonex/status/1015933593904992256"
  icon_pack: fab
  icon: twitter

url_slides: https://docs.google.com/presentation/d/1B9zXwmY-CIEhco5UP0wZcB_3sx0IwPH05pJU_0rlR58/edit?usp=sharing
url_code: https://github.com/pleonex/PokemonDungeonExplorers
url_pdf:
url_video:
---

Talk at the DevFest 2018 organized by the GDG Jaén (_Google Developer Group_).
The presentation is about a Twitter thread I did on July. For a week I was
figuring out how the game _Pokémon Mistery Dungeon Explorers of Sky_ from
Nintendo DS generate and validate a kind of password for rescue missions,
special events and object sharing. It almost a study of the assembly code
of the game with some notes about the implementation.

{{< tweet 1015933593904992256 >}}

{{< gdocs src="https://docs.google.com/presentation/d/e/2PACX-1vQXQvdFkmg0Qt-4w9XG01Oor1kI9j4-GA_iOlTKy2zudgOa9e-VoR5uBfPLNTY3EzxGjNZcHc4JS16G/embed?start=false&loop=false&delayms=5000" >}}
