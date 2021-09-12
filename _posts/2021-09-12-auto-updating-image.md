---
layout: post
title: Auto-Refreshing a Satellite Image of my Hometown
tags: [projects]
---

As I mentioned on my latest post, I've found the data ESA provides from their Sentinel satellites very interesting. I wanted to make something with it, and what I've done can be seen on the [Mação](https://blog.louro.xyz/hometown) tab of this blog.

It's a simple page that shows the freshest image from Sentinel of my home municipality. It's updated weekly, which is approximately the frequency with which new images of the area are captured.

I've developed some python scripts which, for now, allow you to download the latest image of <s>all</s> most Portuguese municipalities and parishes (geographical data is a pain to work with). You can find them on [github](https://github.com/fernandeslouro/terras). The way I'm making it work is to have a cron job on my desktop running the `full_page_update.py` script weekly. This script is more narrow in its use, since it's made to update a Jekyll blog such as this one with a Markdown file including an image.

This is essentially a small art project, as well as a little homage to my home town.
