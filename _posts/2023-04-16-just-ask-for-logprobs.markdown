---
layout: post
title:  "Just Ask For Logprobs"
date:   2023-04-16 13:10:00 -0700
---
# Just Ask for Logprobs?

LLM logprobs are a beautiful thing for researchers and hobbyists. You can use them to measure the model's uncertainty. Or [break ties](https://twitter.com/goodside/status/1634407841556561922). Or for [model distillation](https://twitter.com/sharifshameem/status/1645649337886846977).

Preventing the competitive disadvantage from the last use case is maybe the reason the GPT-4 API doesn't show its logprobs, where previous models did. People are understandably [disappointed](https://twitter.com/xuanalogue/status/1637302504349114370) by this. But do we need the API at all? What if we can get the logprobs... just by asking?

![logprobs1](https://photos.google.com/share/AF1QipNMPqIiN2AIPU41apRdGiwzIU_A1a3sXeM4ORD2Ddd0YdoLWvJCusXrOkaeP7i6fQ/photo/AF1QipOczylj4fN3SGCIUTPfKpc8gCovQVgWgh0pXDSS?key=RkZNV2pVZTA0WldRcWRaWEhiYXBPRVkzbVVDamh3)
![logprobs2](https://photos.google.com/share/AF1QipNMPqIiN2AIPU41apRdGiwzIU_A1a3sXeM4ORD2Ddd0YdoLWvJCusXrOkaeP7i6fQ/photo/AF1QipPYAjiB2-kkK7yGKvpD30c4l0Y1uhj_bsNju_YZ?key=RkZNV2pVZTA0WldRcWRaWEhiYXBPRVkzbVVDamh3)

I decided to see if I could estimate the logprobs of a previous model (GPT-3.5) by... asking for them, in English.


