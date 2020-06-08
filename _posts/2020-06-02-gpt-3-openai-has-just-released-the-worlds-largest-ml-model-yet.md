---
layout: post
title: GPT-3&#58; OpenAI has just released the world's largest ML model (yet)
tags: [machine-learning]
---

OpenAI has just released the largest ML model yet. It's larger by an order of magnitude than the previous record holder. This new model, sensibly named GPT-3 (short for Generative Pretrained Transformer 3) has 175 million parameters, surpassing Microsoft's Turing-NLG with its 17 billion parameters. Below you can see a plot of several language models, which Microsoft compiled for their [announcement](https://www.microsoft.com/en-us/research/blog/turing-nlg-a-17-billion-parameter-language-model-by-microsoft/) for Turing-NLG. You can also see in the graph where GPT-2 stands, as well as [MegatronLM](https://nv-adlr.github.io/MegatronLM) named like that because it was the "biggest, baddest transformer" of its day. GPT-3 would blow up the scale. 

![Number of parameters of preious language models](/assets/images/transformer-parameters.png)

The chief scientist of OpenAI, Ilya Sutskever, presented on an interview for the [Artificial Intelligence](https://www.youtube.com/watch?v=13CZPWmke6A&list=PLrAXtmErZgOdP_8GztsuKi9nrraNbKKp4) podcast a simple intuition on why language models need to be large in order to be good:

> In order to predict the next word, when you don't know anything, you'll notice very broad strokes, surface level patterns, like... sometimes there are characters and there is space between those characters, you'll notice that sometimes there is a comma and the next character is a capital letter. Eventually you may start to notice that certain words occurr often, you may notice spelling and syntax. And when you get really good at all these, you start to notice the semantycs. You start to notice the facts. But for that to happen, the language model needs to be larger.

After being debuted on a 2017 [paper on machine translation](https://arxiv.org/abs/1706.03762) the Transformer architecture has revolutionized the field of NLP. The previous state-of-the-art in language models, Recurrent Neural Networks (specifically LSTMs), while showing potential, was severely limited by its recurrent nature, in the sense that it was not parallelizable. The Transformer, with its attention mechanism, presented a solution to this lack of paralellization. This may have been its greatest breakthrough.

# Arctecture of GPT-3

As for the architecture, there is nothing too new here, since it's essentially the same as the previous GPT-2, though much larger. For a detailed description of the GPT-2 architecture, check out Jay Alammar's fantastic post [The Illustrated GPT-2](http://jalammar.github.io/illustrated-gpt2/). Remember, GPT-2 was said to be "too dangerous for he world" at the time of its release. It only has 1.3 billion parameters, a very small number when compared to the 175 billion of GPT-3.

# Language Model as Few-Shot Learner

Perhaps the most surprising new capability of GPT-3 is the fact that it managed to beat the state-of-the art in some NLP tasks with no fine-tuning. Previous language models have shown great capabilities in a number of tasks, like question answering or text summariation. However, in order to perform these tasks (which are different from the normal text generation language models are trained to do) the models must be fine-tuned specifically for each individual task. This requires having training and test datasets for the new task, as well as additional compute.

In the paper, no fine-tuning was performed on GPT-3. However, three different situations were esperimented: **no-shot**, **single-show** and **few-shot** learning.

(Insert image from paper)

As you can see, the task settings are provided to the language model simply as sentences for it to complete, with no gradient updates whatsoever. In the zero-shot setting, only a description of the task is provided. In the single-shot setting, the model is provided with a simple example of the task to perform (in the case of English to French translation, this single example is an English-French pair. For the few-shot setting, several examples of the solved task are provided, as part of the expression the language model must complete. Using this few-shot method of understanding tasks, GPT-3 managed to break the state-of-the-art in several different tasks, surpassing previous models, which ad been fine-tuned for those specific tasks. 

# Can a better language model be built by increasing size?

As for the experimental resutls on language modelling, it has been verified by past experiments that as the number of parameters is increased, the validation loss (calculaing used log probability, a.k.a. perplexity) for trained models decreases. Essentialy, as model size, compute time and dataset size increase in the same fashion, it follows a powe law where the model will get better and better. A question still to be ansered is: _how far can this take us?_ It seems like, at 175B parameters, the limit hasn't yet been discovered, since GPT-3 is still in this trend of improvement.

# Question Answering

Either you get a question, or context + a question. The model should either simply answer the question or choose from several options which one is the most likely to be correct. For GPT-3, as the model scaled up in number of parameters, the zero-shot, one-shot and few-shot (with 64 different examples) variants. In these tasks, the model can not query any outside information, we simply want to know information that is encodeed in the model's 175B parameters. In some of these question answering tasks, GPT-3 managed to outperform a fine-tuned SOTA model in both the one-shot and few-shot settings. Another interesting point is that some of the SOTA models Open Domain (vs. Closed Book) which means that they can access websites like Wikipedia. The question-answering tasks where GPT-3 cound't beat the SOTA (e.g. NaturalQS) were tasks that depended mostly on factual knowledge, where open domain models have the advantage.

![Question Answering](/assets/images/question-answering.PNG)

# Translation

For tasks in translation, the performance also increases with the number of parameters. In translation tasks, GPT-3 showed the best performance when translating into English, be it in no-shot, one-shot, or few shot settings. This makes sense, considering most of the corpus the model trained on was in English, and GPT-3 was intended from the start to be an English language model. The performance when translating from Eglish to other languages is therefore not as good. When translating from other languages into English, the model maintains similar perfrmance across languages, but that is not the case when translating from English into other languages, in which case the performance varies significantly across output languages. In some cases, GPT-3 managed to improve on the current supervised SOTA when translating into English.


![Translation](/assets/images/translation.PNG)

# Winograd Schemes

Winograd is a classic task in NLP, which involves figuring out which word a pronounrefers to, in cases when the pronoun is grammatically ambiguous but semantically unambiguous to a human. In some Winograd-Style tasks, GPT-3 managed to beat the fine-tuned SOTA performance in all its three settings (even no-shot), while for others it comes close. In earlier Winograd-Style tasks, the SOTA is close to human performance, while for newer, more adversarial tasks, there is still some distance between the current best performance and humans. In more adversarial tasks, there were bigger differences between no-shot and few-shot perfomance for GPT-3.

# Commonsense Reasoning

Several tasks were tried in order to evaluate GPT-3's capacity for reasoning. The three analysed datasets attempt to capture physical or scientific reasoning. They are not tasks of sentence completion, reading comprehension, or broad knowledge question answering. In one of the tasks (PIQA, comprising common sense questions about the physical world, which tries to evaluate for a grounded understanding of the world) GPT-3 in the no-shot setting managed to beat the current fine-tuned SOTA, while for the other two it didn't. However, in the case of the PIQA dataset, the authors claimed that there is possible contamination in this dataset, meaning that a portion of this dataset might be in the training dataset of GPT-3. This was only noticed after the training, 

# Reading Comprehension

To test GPT-3's reading comprehension, 5 datasets were used, which include abstractive, multiple choice, and span based answer formats in both dialog and single question settings. GPT-3 couldn't beat the fine-tuned SOTA in any of these tasks, and performance varied across datasets.

SuperGLUE
NLI

# Synthetic Datasets

Given the way that GPT-3 is tested (simply giving it some text to complete) it's easy to devise new tasks for it to solve. No training datasets are required, since there is no fine-tuning, which is an advantage that comes from performing no fine-tuning. In order to evaluate GPT-3 further, OpenAI devised some additional tasks, and it intends to relase the test datasets soon. 

## Arithmetic Expressions

It turns out that GPT-3 is quite good at arithmetics, especially in two-digit addition and subtraction, which it's able to consistently perform. Three digit addition and subtraction is also surprising, with over 80 and 90% accuracy respectively. Keep in mind that GPT-3 is a language model, not a calculator, and these results start to appear quite good. Results for arithmetics above three digits and for multiplication were not as good. As can be seen in the image, arithmetics is a capability only shown by very large models.

One-shot and zero-shot performance are somewhat degraded relative to few-shot performance, suggesting that adaptationto the task (or at the very least recognition of the task) is important to performing these computations correctly.Nevertheless, one-shot performance is still quite strong, and even zero-shot performance of the full GPT-3 significantly outperforms few-shot learning for all smaller models.

![Arithmetic](/assets/images/arithmetic.PNG)

Word Unscrambling
# SAT Analogies
# News Article Generation
# Made-up Words
# Training Set Contamination
Task Examples


