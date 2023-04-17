---
layout: post
title:  "Just Ask For Logprobs"
date:   2023-04-16 13:10:00 -0700
---
# Just Ask for Logprobs?

LLM logprobs are a beautiful thing for researchers and hobbyists. You can use them to measure the model's uncertainty. Or [break ties](https://twitter.com/goodside/status/1634407841556561922). Or for [model distillation](https://twitter.com/sharifshameem/status/1645649337886846977).

Preventing the competitive disadvantage from the last use case is maybe the reason the GPT-4 API doesn't show its logprobs, where previous models did. People are understandably [disappointed](https://twitter.com/xuanalogue/status/1637302504349114370) by this. But do we need the API at all? What if we can get the logprobs... just by asking?

<img src="https://github.com/zswitten/zswitten.github.io/blob/master/photos/logprobs1.jpeg" width=50% height=50%>
<img src="https://github.com/zswitten/zswitten.github.io/blob/master/photos/logprobs2.jpeg" width=50% height=50%>
![test3](../docs/assets/logprobs1.jpeg)
![test4](/zswitten.github.io/docs/assets/logprobs2.jpeg)
![test5](/docs/assets/logprobs1.jpeg)

I decided to see if I could estimate the logprobs of a previous model (GPT-3.5) by... asking for them, in English.