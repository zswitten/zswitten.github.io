---
layout: post
title:  "Data as an Undersupplied Public Good"
date:   2022-04-14 00:40:04 -0700
---

## Summary
The most valuable data in the world is public. Stuff like Wikipedia and Github. So it's underfunded, like all public goods. And it's even more underfunded because its value is hard to measure. Finding cheap ways to measure the incremental effects of a dataset would let us reward dataset creators and unlock massive value.

## Data as a public good
**The best things in life are free**

What makes data valuable? Data is valuable because it makes an ML model do better on some task. For private data, this can be estimated by companys' willingness to pay. For instance, your browsing/shopping habits are [allegedly](https://www.invisibly.com/learn-blog/how-much-is-data-worth) worth about $65/year/person because they improve the performance of a what-ads-are-worth-showing-to-you model.

But these days most valuable data in the world, the data that powers the biggest, best, models, is *completely public*.

- [OpenAI Codex](https://openai.com/blog/openai-codex/), which powers [Copilot](https://copilot.github.com/), is trained on publicly available source code from Github. Codex can already [write video games](https://andrewmayneblog.wordpress.com/2022/03/17/building-games-and-apps-entirely-through-natural-language-using-openais-davinci-code-model/) essentially from scratch and already has many devotees who say it makes their work faster and better.
- [Alphafold](https://www.deepmind.com/blog/alphafold-a-solution-to-a-50-year-old-grand-challenge-in-biology), which can replicate an entire PhD's worth of work finding the structure of a protein with one inference call, is trained on publicly available data from the [Protein Data Bank](https://www.rcsb.org/).
- [GPT-3](), OpenAI's language model that blew everyone away in 2020 with its ability to do style transfer, open-ended dialogues, and FILLMEIN, was [trained](https://en.wikipedia.org/wiki/GPT-3#Training_and_capabilities) on Common Crawl, Reddit, Wikipedia, and a bunch of books. Again, public domain.
- DALL-E 2, the new AI art generating hotness at time of this writing, is [trained](https://arxiv.org/pdf/2102.12092.pdf) (see Appendix C; this is for DALL-E 1 but in the [paper](https://cdn.openai.com/papers/dall-e-2.pdf) for 2 they say they used the same data) on a combination of [Conceptual Captions](https://ai.google.com/research/ConceptualCaptions/), which is made of up pairs of images and their alt-text, and images from Wikipedia along with their captions.

GPT-3 and Copilot are already earning income, gating access to their models through a paid API. AlphaFold and DALL-E haven't directly made anyone money yet as far as I know, but it's a mortal lock that AlphaFold or its successor will speed up the process of finding boutique molecules to cure diseases and help insert DNA into our genome, and artists are shook about DALL-E hitting their pocketbook which is a good sign for art consumers.

Wikipedia isn't going to see a penny of that, though, unless their yearly donation pledge headers happen to catch Sam Altman in a generous mood. But of course it's not only Wikipedia the organization who is providing the value here. A lot (most?) of the value of Wikipedia qua dataset was created by the people who wrote the entries.

Because of this lack of ownership and attribution, economic theory tells us that large public datasets are *massively underproduced*. To produce the socially optimal amount of data, every time you write a Wikipedia entry or write an answer on Stack Overflow, you should earn royalties equal to the expected improvement of all the models trained on what you wrote, multiplied by the value of that improvement to all the users of those models.

Aside from being underproduced, data is also tragically *undershared*. I know a biologist who's into ML who got fed up with trying to get the data in a paper by email and wrote an image-processing script to scrape it directly from the pixels of the tables in the PDF. In general academics have little incentive to share their data. It can be a lot of work and there's not much in it for them. People talk about this in terms of the "replication crisis" but it also slows down new work.

The creators of ImageNet [almost gave up](https://qz.com/1034972/the-data-that-changed-the-direction-of-ai-research-and-possibly-the-world/) because they didn't have the budget to pay undergrads to label it. Only the existence of Amazon Mechanical Turk allowed the project to be completed. In retrospect, given how much ImageNet galvanized the field of computer vision, it clearly would have been worth creating ImageNet even if the professors had to label it all themselves. Imagine if someone had the foresight to subsidize its creation earlier.

## Measuring the impact of a dataset
**Your calorie values may be higher or lower depending on your data needs**

How should we think about the value of an individual Wikipedia entry, or of the Wikipedia corpus as a whole?

Machine learning does have a tool for measuring the impact of a dataset: [ablation](https://en.wikipedia.org/wiki/Ablation_(artificial_intelligence). AKA taking out the dataset, training the model, and then comparing performance. As Wikipedia helpfully reminds us, there's an analogy with biological studies where they take out some portion of a fruit fly's brain and see if it still flies.

The catch is that these models cost millions of dollars to train. And as long as the [scaling laws](https://www.gwern.net/Scaling-hypothesis) keep holding, they're only going to get more expensive over time. It's tough enough to make the argument for OpenAI to do full retrains of GPT-3-minus-Wikipedia, GPT-3-minus-Reddit, ..., and of course GPT-3-minus-wikieditorxyz's-contributions for all wiki editors would be prohibitively expensive.

There is another problem as well: even if we could perfectly measure the contribution of each Wikipedia entry to model performance on the training set, the connection between training performance and real-world value seems to be highly nonlinear and hard to predict. We don't know the magical threshold for accuracy in predicting the next token in a sequence that will enable Copilot to write code fluently and to-spec in a way that makes software engineers as shook as artists.

I'd argue that the uncertainty of that translation can be ignored as a form of "ML luck" akin to "moral luck" -- if the magical perplexity threshold is 50, your data brings it halfway from 60 to 50, and then later mine brings it the other half, and causes a phase change, we both deserve the same reward.

Let's leave that complication aside and pretend that test set impact = real world impact. Here's three possible strategies to approximate the impact of a given subset of data.

1. Do ablations with small versions of the model. Hopefully data valuable to small versions would also be valuable to big versions. We could build confidence in this via scaling laws: correlation between contribution to 1e9-scale GPT, 1e8-scale GPT, and 1e7-scale GPT would give us confidence that the same data would be valuable to full-scale GPT.

2. Model it directly. Amass a dataset where the samples are [dataset, supplemental data] pairs, and the labels are the improvement of a model (or a menagerie of models) when trained on [dataset + supplemental data] compared to [dataset] alone. Or, rather than (dataset, supplemental pair), you could use (parametrized model, supplemental dataset), and the label would be the improvement in performance for that specific model.

3. "Untrain" the model on the data using gradient ascent. It makes intuitive sense that moving away from good performance on important data would hurt performance more than for unimportant data. A nice feature of this approach is that the cost is exactly 2x the cost of training (plus the cost of inferences on the test set). Untrain on a subset, measure, then restore the model to checkpoint before untraining on the next subset until it's unseen everything once. This one is hilariously naive but maybe just naive enough to work and I would love to see someone try it.

Food you buy in a store usually comes with a label for Nutrition Facts: how many calories, how much sodium, protein, niacin it has. In this world, datasets would have labels showing how much they contribute to model performance on various tasks. We would talk about information-rich datasets the way we talk about spinach being high in fiber.

## Solving the data shortage
**Hm maybe that would have made a clickbaitier/catchier title**

What would the world look like if datasets had reliable nutrition facts, and model providers like OpenAI paid out royalties to data providers each time they served an inference proportional to the nutrition of the data?

1. Data labeling, along with scraping and other creative forms of data acquisition, become more lucrative and high-status.
2. The pace of development for large data-constrained ML models is accelerated. Profits for large model providers go up as the pie grows even though they pay out much of their new income to data providers.
3. Compute-constrained models benefit from the nutrition fact labels as it's easier to know what to train them on.

And some other consequences that make the picture less rosy:

4. Whatever method we choose for measuring data nutrition will be heavily analyzed and gamed. An arms race will develop as it's only a matter of time before each imperfect metric gets [Goodharted](https://en.wikipedia.org/wiki/Goodhart%27s_law) to death. Some model providers may keep their valuation methods secret to prevent this, publishing only their total payouts or not even that.

Developing powerful, cheap methods for measuring data nutrition would on its own provide model providers with strong incentive to purchase more data on purely selfish grounds. They already do this (Facebook spends tens of millions each year paying people to label data; Google has us all doing Captchas all the time; OpenAI pays Turkers to help with their reinforcement learning projects). This would be more incentive for them to do more of what they're already going.

The legal system could be brought to bear, mandating the payment of "data royalties". This would have a strong stimulative effect on data production but would be difficult to enforce. In particular, model distillation (the training of one model on the outputs of another model) presents a problem for enforcement, as this occludes the value of whatever data was used to train the original model. The bet would be that the biggest companies are both the most important targets and the easiest targets.

One strategy for enforcement would be for dataset owners to spot-check generative language models with prompts from their dataset. If the model has "memorized" the continuation, returning the ground truth with high confidence, that's evidence the model saw it during training. This is a sort of white-hat version of getting GPT-2 to [divulge people's phone numbers](https://bair.berkeley.edu/blog/2020/12/20/lmmem/). Instead of extracting people's personal information from the model, you'd extract the model's information from itself.


## Notes
**(Arguments from Authority)**

- [Chinchilla paper](https://arxiv.org/pdf/2203.15556.pdf), showing that at current margins models benefit more from extra data than extra size
- Andrew Ng: "So for many practical applications, it’s now more productive to hold the neural network architecture fixed, and instead find ways to improve the data... This is the time to take the things that some individuals have been doing intuitively and make it a systematic engineering discipline." [Link](https://spectrum.ieee.org/andrew-ng-data-centric-ai)
- Andrej Karpathy [blogpost](https://karpathy.github.io/2022/03/14/lecun1989/) on 33 years of progress in ML. Predictions for 2055: "2055 neural nets are basically the same as 2022 neural nets on the macro level, except bigger. Our datasets and models today look like a joke. Both are somewhere around 10,000,000X larger." Models can get bigger off Moore's law but where does the 10,000,000x increase in data come from?
- I definitely didn't invent the data as a public good formulation. In fact I happened to read Anthropic's [latest paper](https://arxiv.org/pdf/2204.05862.pdf) using the phrase while I was editing this essay. Not sure if other people have connected this to public goods being undersupplied. It's kind of hard to Google because of people talking about data FOR public good.