---
layout: post
title:  "Data is a Public Good"
date:   2022-04-14 00:40:04 -0700
---

## Summary
The most valuable data in the world is public. Like most public goods, data is grotesquely underfunded. To fix this, we need to start measuring how much data is worth, and make the consumers pay the producers.

## Data is a public good

The biggest, coolest, most important models of today are all free-riding off the public commons.

- [OpenAI Codex](https://openai.com/blog/openai-codex/), which powers [Copilot](https://copilot.github.com/), is trained on publicly available source code from Github.
- [Alphafold](https://www.deepmind.com/blog/alphafold-a-solution-to-a-50-year-old-grand-challenge-in-biology) is trained on the [Protein Data Bank](https://www.rcsb.org/).
- [GPT-3](https://arxiv.org/abs/2005.14165) is [trained](https://en.wikipedia.org/wiki/GPT-3#Training_and_capabilities) on text from Common Crawl, Reddit, Wikipedia, and a bunch of books.
- [DALL-E 2](https://openai.com/dall-e-2/), the new AI art generating hotness at time of this writing, is trained on pairs of images and their alt-texts/captions scraped from Wikipedia and elsewhere.

As big as these datasets might seem, they're nothing compared to how big they could be. The world has 1.4 billion English speakers. At 1k words/person/day, that's 368 English Wikipedias (3.8 billion words) a day.

The [Conceptual Captions dataset](https://ai.google.com/research/ConceptualCaptions/) DALL-E uses has 3.3 million annotated images. If just 1% of the human race (10 million people) got paid to go around with cameras strapped to our heads going "full-sized Ikea bed... Crest toothpaste... stationary bicycle... slightly underripe banana" out loud, we could easily generate dozens of Conceptual-Captions-sized datasets an hour. 

Would this data still be valuable if we had way more of it? We would face diminishing marginal returns for sure, but the [scaling laws](https://www.gwern.net/Scaling-hypothesis) are telling us that training bigger models on more data will keep paying dividends for a while.

GPT-3 and Copilot are already bringing in cash via gated access to an API. Artists are shook about DALL-E shrinking their margins. AlphaFold or its successor is a mortal lock to help scientists create boutique billion-dollar molecules to cure diseases and insert DNA into our genome.

The problem is, none of this money is going to the people who make the datasets. Because of this, economic theory tells us that large public datasets are *massively underproduced*. All the good stuff that's coming could come much faster. To get the socially optimal amount of data, every Wikipedia entry author should earn royalties equal to the expected improvement of all the models from that one entry, multiplied by the value of that improvement to all the users of those models.

Aside from being underproduced, data is also tragically *undershared*. I know a biologist who's into ML who got fed up with trying to get the data in a paper by email and wrote an image-processing script to scrape it directly from the pixels of the tables in the PDF. In general, sharing data is a lot of work and academics have very little incentive to do it. People talk about this in terms of the "replication crisis", but it also slows down cross-pollination of ideas and methods.

The creators of ImageNet [almost gave up](https://qz.com/1034972/the-data-that-changed-the-direction-of-ai-research-and-possibly-the-world/) because they didn't have the budget to pay undergrads to label it. Only the existence of Amazon Mechanical Turk allowed the project to be completed. In retrospect, given how much ImageNet galvanized the field of computer vision, it clearly would have been worth creating ImageNet even if the professors had to label it all themselves. Imagine if someone had the foresight to subsidize its creation earlier.

From large unsupervised datasets to smaller hyperspecialized datasets, it's clear that for all the talk about big data, we actually have significantly less data than we ought to if we lined up the incentives right. There are two main hurdles to solving this problem:
1. Measurement. How do we know how much a datapoint/dataset is worth?
2. Enforcement. How can we make sure that people pay for the data they use and eliminate the free rider problem?

If we solve these two problems, we can massively speed up the pace of machine learning discovery and deployment. As a neat side effect, we'll also decimate unemployment. Almost anyone in the world is capable of strapping a video to their head and narrating their actions as they walk around, and the present and future benefits to AI more than pay for the cost of their time and shipping them the equipment.

## Measurement

How should we think about the value of an individual Wikipedia entry, or of the Wikipedia corpus as a whole? 

"Pay by the datapoint" doesn't cut it. It's easy to create a massive, valueless, dataset by splicing together hundreds of hours of video of your motionless couch. If we are going to scale up dataset creation in a big way, we need ways to measure the value of what we incentivize and create.

Machine learning has a classic tool for measuring the impact of a dataset: ablation. The catch is that the models that produce most of the value cost tens of millions of dollars (and rising) to train. It's tough enough to make the argument for OpenAI to do full retrains of GPT-3-minus-Wikipedia, GPT-3-minus-Reddit, etc., and of course GPT-3-minus-wikieditorxyz's-contributions for all wiki editors would be prohibitively expensive.

Here are three possible strategies to approximate the impact of a given subset of data.

1. Do ablations with small versions of the model. Hopefully data valuable to small versions would also be valuable to big versions. We could build confidence in this via scaling laws: correlation between contribution to 1e9-scale GPT, 1e8-scale GPT, and 1e7-scale GPT would give us confidence that the same data would be valuable to full-scale GPT.

2. Model it directly. Amass a dataset where the samples are [dataset, supplemental data] pairs, and the labels are the improvement of a model (or a menagerie of models) when trained on [dataset + supplemental data] compared to [dataset] alone. Or, rather than (dataset, supplemental pair), you could use (parametrized model, supplemental dataset), and the label would be the improvement in performance for that specific model.

3. "Untrain" the model on the data using gradient ascent. It makes intuitive sense that moving away from good performance on important data would hurt performance more than for unimportant data. A nice feature of this approach is that the cost is exactly 2x the cost of training (plus the cost of inferences on the test set). Untrain on a subset, measure, then restore the model to checkpoint before untraining on the next subset until it's unseen everything once. This one sounds kinda dumb but may be just dumb enough to work.

Food you buy in a store usually comes with a label for Nutrition Facts: how many calories, how much sodium, protein, niacin it has. In this world, datasets would have labels showing how much they contribute to model performance on various tasks. We would talk about information-rich datasets the way we talk about spinach being high in fiber.[^1]

Whatever method we choose for measuring data nutrition will be heavily analyzed and gamed/[Goodharted](https://en.wikipedia.org/wiki/Goodhart%27s_law). An arms race will develop as people find new loopholes in the measurement system. Some model providers may keep their valuation methods secret to prevent this, as Google keeps its ranking algorithm private to stop shady SEO tactics.

## Enforcement

Having determined how much a dataset is worth, how do we make its consumers pay its producers that amount?

Vanilla copyright law can form the basis of the solution. Model producers charge model consumers a fee per API call; we would mandate the payment of "data royalties" as a percentage of these fees. Illicit resale of data could become an issue, but it's not that different in principle from regular IP theft.

Model distillation (training one model on the outputs of another model) could allow bad actors to get the benefits of a dataset without explicitly training on it. "Data laundering", you could call it. To fight this, dataset owners could audit generative language models by prompting them with examples from their dataset. If the model has "memorized" the continuation, returning the true continuation with unusually high confidence, that's evidence the model saw it during training. This is a sort of white-hat version of getting GPT-2 to [divulge people's phone numbers](https://bair.berkeley.edu/blog/2020/12/20/lmmem/). Instead of extracting people's personal information from the model, you'd extract the model's information from itself.


[^1]: There is another possible issue: even if we could perfectly measure the contribution of each Wikipedia entry to model performance on the training set, the connection between training performance and real-world value seems to be highly nonlinear and hard to predict. We don't know the magical threshold for accuracy in predicting the next token in a sequence that will enable Copilot to write code fluently and to-spec in a way that makes software engineers as shook as artists.

I'd argue that we can ignore this issue by treating the uncertainty of that translation can be ignored as a form of "ML luck" akin to ["moral luck"](https://en.wikipedia.org/wiki/Moral_luck). Say the magical perplexity threshold is 50, your data brings it from 60 to 55, and then later mine brings it from 55 down to 50 and causes a phase change. I'd say we both deserve the same reward if swapping the order we published our datasets doesn't change the final result.


## Notes
**(Arguments from Authority)**

- [Chinchilla paper](https://arxiv.org/pdf/2203.15556.pdf), showing that at current margins models benefit more from extra data than extra size
- Andrew Ng: "So for many practical applications, it’s now more productive to hold the neural network architecture fixed, and instead find ways to improve the data... This is the time to take the things that some individuals have been doing intuitively and make it a systematic engineering discipline." [Link](https://spectrum.ieee.org/andrew-ng-data-centric-ai)
- Andrej Karpathy [blogpost](https://karpathy.github.io/2022/03/14/lecun1989/) on 33 years of progress in ML. Predictions for 2055: "2055 neural nets are basically the same as 2022 neural nets on the macro level, except bigger. Our datasets and models today look like a joke. Both are somewhere around 10,000,000X larger." Models can get bigger off Moore's law but where does the 10,000,000x increase in data come from?
- I definitely didn't invent the data = public good formulation. In fact I happened to read Anthropic's [latest paper](https://arxiv.org/pdf/2204.05862.pdf) using the phrase while I was editing this essay. Not sure if other people have connected this to public goods being undersupplied. It's kind of hard to Google because of people talking about data FOR public good.