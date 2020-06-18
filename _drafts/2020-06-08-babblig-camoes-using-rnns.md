--
layout: post
title: Babbling Camões using RNNs
tags: [machine-learning]
---

Luís de Camões, born in is the Portuguese national poet. He's one of the largest figures in Portuguese language literature, and one of the great poets of western tradition. His _magna opus_, the Lusiads, is a naionalist epic telling the tale of the portuguese discoveries, was published in the XVI century. It's taught in Portuguese high schools, and has very distinct style any Portuguese will immediately recognize. 

Inspered by Andrej Karpathy's [blog post](http://karpathy.github.io/2015/05/21/rnn-effectiveness/) on RNNs, I thought it woulb de a fun project to try and generate some Lusiads-like text using RNNs. 

More specifically, I'll implement a Character RNN, whci is in essence an RNN that predicts the next character in a sentence. If we have such a network, we can generate new text, one character at a time.

# Getting the text

