---
layout: post
title:  "Just Ask For Logprobs"
date:   2023-04-16 13:10:00 -0700
---
# Just Ask for Logprobs?

LLM logprobs are a beautiful thing for researchers and hobbyists. You can use them to measure the model's uncertainty. Or [break ties](https://twitter.com/goodside/status/1634407841556561922). Or for [model distillation](https://twitter.com/sharifshameem/status/1645649337886846977).

Preventing the competitive disadvantage from the last use case is maybe the reason the GPT-4 API doesn't show its logprobs, where previous models did. People are understandably [disappointed](https://twitter.com/xuanalogue/status/1637302504349114370) by this. But do we need the API at all? What if we can get the logprobs... [just by asking](https://twitter.com/zswitten/status/1638700838813310976)?

<img src="/docs/assets/logprobs1.jpeg" width="400" height="200">
<img src="/docs/assets/logprobs2.jpg" width="400" height="200">

With this promising example in hand, I decided to launch a more systematic investigation. Since we have logprobs for GPT-3.5, can we match those logprobs without using the parameter? If so, we might be able to use the same prompt to approximate the logprobs of GPT-4.

### Choosing Data

I used examples from the test set of the [Pile](https://the-eye.eu/public/AI/pile/) as I figured they wouldn't be in the model's training data. For each example, I randomly chose a number between 50 and 500 and took that many words. The examples range over code, patents, Wikipedia, and more.

### Exfiltration Prompts

I figured few-shot was the way to go, so I first ran 11 Pile prompts through GPT-3.5 to get the real logprobs to act as examples. I used them for all three exfiltration prompts I tried.

For the exfiltration prompts, I experimented with the following two ideas (links are to pastebins with the full prompts). Nothing too flashy.

1. [Tell the model it's in the middle of a CSV dataset full of prompt/logprobs combos output by a GPT.](https://pastebin.com/Uct6u0H8)

2. [Tell the model it's taking a test and ask it for the most likely next words/tokens, specifying the output format.](https://pastebin.com/chXsk6hu)

### Results

|    |   Agreement Rate Normalized |   Agreement Rate (Left) |   Agreement Rate (Right) |   Agreement Rate Lower Bound |   Overlap Rate |   Top 1 Match Rate |   Top 1 Presence Rate |
|---:|----------------------------:|------------------------:|-------------------------:|-----------------------------:|---------------:|-------------------:|----------------------:|
|  CSV Dataset |                    0.341253 |                0.389276 |                 0.381328 |                     0.190349 |        1.36782 |           0.545977 |              0.649425 |
|  Test Taking |                    0.35155  |                0.421129 |                 0.382766 |                     0.209283 |        1.4152  |           0.561404 |              0.672515 |

Here are the results. First row is first prompt, second is second. Now I'll explain what the metrics mean.

- Agreement 