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

# Language Model as Few-Shot Learner

Perhaps the most surprising new capability of GPT-3 is the fact that it managed to beat the state-of-the art in some NLP tasks with no fine-tuning. Previous language models have shown great capabilities in a number of tasks, like question answering or text summariation. However, in order to perform these tasks (which are different from the normal text generation language models are trained to do) the models must be fine-tuned specifically for each individual task. This requires having training and test datasets for the new task, as well as additional compute.

In the paper, no fine-tuning was performed on GPT-3. However, three different situations were esperimented: **no-shot**, **single-show** and **few-shot** learning.

(Insert image from paper)

As you can see, the task settings are provided to the language model simply as sentences for it to complete, with no gradient updates whatsoever. In the zero-shot setting, only a description of the task is provided. In the single-shot setting, the model is provided with a simple example of the task to perform (in the case of English to French translation, this single example is an English-French pair. For the few-shot setting, several examples of the solved task are provided, as part of the expression the language model must complete. Using this few-shot method of understanding tasks, GPT-3 managed to break the state-of-the-art in several different tasks, surpassing previous models, which ad been fine-tuned for those specific tasks. 

# Can a better language model be built by increasing size?

As for the experimental resutls on language modelling, it has been verified that as the number of parameters increased, the validation loss (calculaing used log probability, a.k.a. perplexity) for trained models decreased. This matches previous knowledge, that as model size, compute time and dataset size increase in the same fashion, it follows a powe law where the model will get better and better. A question still to be ansered is: __how far can this take us?__ It seems like, at 175B parameters, the limit hasn't yet been discovered, since GPT-3 is still in this trend of improvement.

