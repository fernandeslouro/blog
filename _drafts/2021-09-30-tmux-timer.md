--
layout: post
title: Making a Timer for Tmux
tags: [projects]
---

I like using timers when I work. I find it's a good way to actively track how much time I'm actually working. The way I use them is that I'll stop the counter when I get distracted, and reset it only when I'm working in a focused manner. That helps me stay consistent, and the fact that I have to stop the counter makes me ponder more if the distraction is actually worth stopping the counter for.

Since I'm on my terminal a lot, I initally started using [termdown](https://github.com/trehn/termdown), a nice CLI countdown and timer app written in Python. However, it wasn't perfect for me, since I needed to always have a terminal window open for it. Ideally, I wanted to have a timer right on my tmux bar, which I could start and pause with a simple key binding. I also wanted the time count to be hidden unless I pause the count, since I don't want to be looking at the timer at all times. There was already [thyme](https://github.com/hughbien/thyme), but I didn't like the fact it was written in Crystal and that it seemed somewhat complicated. So I decided to build an alternative in bash, with as little in the way of dependencies as possible.

What I came up with was tmux_tempus. It's a simple shell script thought for integration with tmux. It has two commands: one for starting and clearing a timer, and the other for pausing and continuing a timer.

# How do I add it to my tmux confing?

In order to add it to your config, all you need is the tmux_tempus.sh somewhere in your computer (I like keeping it in the same folder as my tmux config) and to add the two commands to your config in order to have the start/end and the pause/continue commands accessible through tmux shortcuts. Personally, I like having the pause command on my prefix+g key, since it is very easily accessible, and the start command on prefix+S.

Again, all I have on my tmux config are the two lines:

bind g run-shell 'bash ~/.tmux/tmux_tempus.sh pause > /dev/null'\; refresh-client -S
bind S run-shell 'bash ~/.tmux/tmux_tempus.sh start > /dev/null'\; refresh-client -S




