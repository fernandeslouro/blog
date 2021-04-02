---
layout: post
title: Sentinel-2 is great
tags: [projects]
---

I've only recently found out that you can access satellite images captured by ESA's [Sentinel-2](https://sentinel.esa.int/web/sentinel/missions/sentinel-2) for free. The Sentinel-2 satellites cover a sizeable area of the globe, providing updated images every 5 days. I've always wanted to play with images of my home area, a sparsely populated zone in central Portugal, and I was pleasantly surprised at the simplicity of getting images using this resource.

There is even an excellent [API](https://github.com/sentinelsat/sentinelsat/tree/98fbe9c8bf20912aa683c106266b422653b61035) (for python and command line). This really is a great tool, and I wish more European satellites had similar data availability schemes. They are paid for by the people, and in my opinion it makes sense to have the data available to the public as easily as possible.

## What will I do with these images?

Currently, I've been working on some scripts to automatically get images from the service. You can check the progress on [Github](https://github.com/fernandeslouro/terras). My idea is to make a kind of time-lapse video showing the devastating effects several forest fires had in my municipality and parish in the last few years. The effects are extremely noticeable in selected images I've looked at. It's interesting to see a perspective other than the one at ground level, and it gives me a different perspective about these disasters. I also want a script to download the most recent available images, which I plan to run as a cron job every 5 days/every week. It would be interesting to show these recent images on this website as well (I'm pretty sure that would be interesting mostly to me, but I'll still probably do it). I would also like to run some ML models to classify the use of the land and changes across time, but the ideas I had about that aren't as clear at the moment.

I've also been working on a few different projects for fun, and I want to share those as soon as I have something more polished ready. 
