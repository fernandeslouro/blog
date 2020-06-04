---
layout: post
title: GPT-3&#58; OpenAI has just released the world's largest ML model (yet)
tags: [machine-learning]
---

OpenAI has just released the largest ML model yet. It's larger by an order of magnitude than the previous record holder. This new model, sensibly named GPT-3 (short for Generative Pretrained Transformer 3) has 175 million parameters, surpassing Microsoft's Turing-NLG with its 17 billion parameters. Below you can see a plot of several language models, which Microsoft compiled for their [announcement](https://www.microsoft.com/en-us/research/blog/turing-nlg-a-17-billion-parameter-language-model-by-microsoft/) for Turing-NLG. You can also see in the graph where GPT-2 stands, as well as [MegatronLM](https://nv-adlr.github.io/MegatronLM) named like that because it was the "biggest, baddest" transformer of its day. GPT-3 would blow up the scale. 

![Number of parameters of preious language models](/assets/images/transformer-parameters.png)

The chief scientist of OpenAI, Ilya Sutskever, presented on an interview for the [Artificial Intelligence](https://www.youtube.com/watch?v=13CZPWmke6A&list=PLrAXtmErZgOdP_8GztsuKi9nrraNbKKp4) podcast a simple intuition on why language models need to be large in order to be good:

> In order to predict the next word, when you don't know anything, you'll notice very broad strokes, surface level patterns, like... sometimes there are characters and there is space between those characters, you'll notice that sometimes there is a comma and the next character is a capital letter. Eventually you may start to notice that certain words occurr often, you may notice spelling and syntax. And when you get really good at all these, you start to notice the semantycs. You start to notice the facts. But for that to happen, the language model needs to be larger.

After being debuted on a 2017 [paper on machine translation](https://arxiv.org/abs/1706.03762) the Transformer architecture has revolutionized the field of NLP. The previous state-of-the-art in language models, Recurrent Neural Networks (specifically LSTMs), while showing potential, was severely limited by its recurrent nature, in the sense that it was not parallelizable. The Transformer, with its attention mechanism, presented a solution to this lack of paralellization. This may have been its greatest breakthrough.

Since thi
