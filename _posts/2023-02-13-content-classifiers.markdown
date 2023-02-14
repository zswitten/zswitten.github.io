---
layout: post
title:  "Content is "
date:   2023-02-13 13:10:00 -0700
---
Take it from a soldier on the front lines of the war on bad posts: You can't catch all the bad posts just by reading them. You need to look at who's making the posts.

Every social media company knows this. I don't know if OpenAI knows it yet. But when they want to get serious about blocking toxic content, this is where I predict they'll turn.

Imagine you run a social media company. You have a problem with people posting soft porn ads and scandalizing your userbase of churchgoing grandmothers. You train a nudity classifier, and (let's dream big) it's stone-cold perfect. It gets 100% precision/recall on your holdout set. You deploy it to prod. It gets 100% accuracy in prod. You celebrate.

Two days later, the accuracy starts going down. You look at some false negatives. The bad guys figured out that your classifier samples every 20th frame so they started replacing every 20th frame with a white screen. You randomize the frame selection. That solves one problem but a few days later you start seeing tons of false negatives with weird-looking patches in the bottom right corner, some fucked-up malicious perturbation. How'd they even figure that out?! You make your classifier run four times on each image, excluding a different corner for each, and take the max. But now your costs are going up.

Bottom line, your enemies are too clever and too motivated. If you shut down their money spigot, they'll poke and prod and open a leak. Water rolls downhill and classifiers lose accuracy in adversarial contexts.

So what are you supposed to do? The best and simplest strategy, something you can always fall back on, is to say "Hey, that person who was posting a lot of nudity before? They're probably still posting a lot of nudity." Having a, call it a mischievousness index for your users gives you a huge leg up when they repeatedly try to get around your filters. I'm not saying to totally lock out repeat offenders. People change. But you can certainly use user-level features in combination with content-level features to make your classifier more resilient.

Now let's talk LLMs. OpenAI has a classifier[^1] that looks at ChatGPT's outputs and effectively says either "Yup this is OK", or "This is bad". If it's bad enough, they write an orange warning to the screen. There's also some system[^2] within ChatGPT that looks at prompts and says "Nope, not touching this one, it's going to make me write a bad post", at which point the model backs out of its normal text-completion behavior and spits out boilerplate about how it's only allowed to make good posts, not bad ones.

Way back in November [two years ago in machine learning time], [a lot of people](https://twitter.com/zswitten/status/1598380220943593472) had fun tricking and cajoling ChatGPT into saying bad things. I was among them. Like the endlessly adaptive nipple purveyors from the social media section, we were able to find many ways to cajole and coerce ChatGPT to make bad posts of all kinds. People found a dozen diverse hacks in the first week alone. Can these holes be plugged? Yes. Can future holes be preplugged? Doubtful. 

On the other hand, any sort of basic feature for "is this user trying to do something sketchy" would have trivially caught me and I assume most of the other jailbreakers. In the course of making [this thread](https://twitter.com/zswitten/status/1598088267789787136), I got slapped with a content warning many times.

There's an analogy here to how the S.E.C. deals with crypto thieves. The almighty power of cryptography means the S.E.C couldn't seize Avraham Eisenberg's ill-begotten Mango tokens without his private keys. But they could sure as hell seize Eisenberg himself. Which has much the same impact in terms of stopping his future exploits and deterring imitators.

Are there downsides to doing business this way? Of course. The ability to restart conversations from a fresh blank slate is part of what makes interacting with ChatGPT feel so spontaneous and fun. The vibe would change a lot if you knew every time you clicked Send it made a mark on your permanent record.

Another huge downside: adding user features crushes the reusability and shareability of prompts. As things work now, if I find some amazing prompt that makes ChatGPT do something hilarious or awesome, I can blast it out on the Internet for all to play with and iterate on. Adding user features means abandoning the promise that what works for me will work for you.

Given these downsides, OpenAI is surely making the right call in not using user history to inform moderation decisions up to now. They actively wanted people to jailbreak ChatGPT to get more intel on how to stop future jailbreaks; they even offered [a prize](https://cdn.openai.com/chatgpt/chatgpt-feedback-contest.pdf) for it. Even with no moderation whatsoever, ChatGPT's outputs aren't seriously harming anyone. It's not powerful enough... yet.

It's not all that far off though. It's easy to imagine a multimodal, internet-enabled model that can execute scaled up scams like

```
for octogenarian in octogenarians:
    descendants = sorted(get_descendants(octogenarian), key=lambda d: get_photos_with(octogenarian, d))
    for desc in descendants[-5:]:
        send_money_request(descendant, octogenarian)
```

At that point, jailbreaks stop being fun and games. It's not enough to throw up your hands and say "users will be users". You have to start playing hardball. And that means taking a hard look not just at the prompt and your model's response to it, but at the third pillar of the interaction: the human in the loop.

User features are not a panacea. For one thing, people can open multiple accounts, or hack the accounts of trusted users, to get multiple bites at the apple. For another thing, some smart or lucky bad actors might find a working jailbreak before they tip off the system to their intentions.

But user features can make a huge difference, and when the risks of misused models get more dangerous, it would be foolish to fight with one hand tied behind our backs.

---

**Footnotes**

[^1]: I've theorized they actually use a funnel, with a light-weight classifier that runs on all posts and a heavier classifier that only runs when the light-weight one throws an alarm. This is based on the fact that its output is slower and glitchier when it's giving questionable responses.
[^2]: In this case, I'm not alluding to an external system, but to the computation going on inside ChatGPT itself! During the RL phase, ChatGPT was repeatedly discouraged from making toxic comments and rewarded for avoiding them, and without getting too metaphysical, it's clear that ChatGPT sometimes "decides" to play it safe.

Something I didn't realize before I started writing this essay is this means that to exploit user features fully, you'd want to include some notion of consistent user personae during training.