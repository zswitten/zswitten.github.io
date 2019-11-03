---
layout: post
title:  "The Perils of Point-Level Train/Test Splits"
date:   2019-08-04 00:13:04 -0700
---

Splitting your data into Train/Valid/Test isn't as simple as `from sklearn.model_selection import train_test_split`. When you have some data points that are really close to other data points, randomly splitting up your examples in a naive way will make you think your model is more accurate than it is. Let me give you a couple examples from personal experience.

1. Named Entity Recognition -- Legal Documents
I worked for a company (http://atrium.co) that had a few thousand documents from a few hundred clients and we wanted a model that would take a document and spit out who the investor was. Used a [CRF](https://en.wikipedia.org/wiki/Conditional_random_field).

Early iterations of the model had validation and "test" accuracies in the high 80s/low 90s but were sub-50 on fresh documents from new clients. What gave?*

You'd want the model to be looking at features like PREVIOUS_WORD2=='Investor', or NEXT_WORD2=='Purchase'. But when we looked at the heaviest-weighted factors the model was considering, the top of the list was all stuff like WORD_IDENTITY=[name of specific investor]. Standard overfitting shit, curable by increasing the % of documents a word has to be in before the model considers it a true word and doesn't just throw it in the \<unk\> heap. But the interesting part is, as far as our train/test splits were concerned, it *wasn't* overfitting because [name of specific investor] appeared in the test set as well!

To get more accurate assessments of how well the model would do, the key was to split at the client level, not at the document level. If we had a bunch of documents from Client A where Investor B gave them money, they'd either all be in the training set, or all in the test set. Doing this aligned our test accuracy and our actual real-life test accuracy.

2. Proteins

Proteins are made of amino acids. There are ~20 amino acids, so each protein is a word made from a 20-character alphabet, or if you prefer, a sentence made from a 20-word dictionary.

You might remember a recent Google paper/announcement called ["Using Deep Learning to Annotate the Protein Universe"](https://www.biorxiv.org/content/10.1101/626507v1.full) where they let loose the dogs of CNN on these words/sentences and learn to predict every property under the sun.

This paper got preprinted in May but hasn't been published anywhere yet, and [these Twitter users](https://twitter.com/ribosaur/status/1124715703423111171) suggested a possible reason: if you check their "Rigorous Benchmark Dataset
" section, they split the sequences into train and test randomly, but there are some sequences in the dataset that are really close to other sequences, and if they get split between train and test, then the model can just say that the "unseen" test sequence has the same properties as the super-similar train sequence that it did see. 

[I'm not knocking the paper authors who seem like cool people//props to them for the breadth of properties they investigated//I might be misunderstanding something about their approach.]

I ran into a similar issue when working on a model to predict how well a protein would work as a battering ram to break through the walls of a cell and deliver whatever precious cargo it happened to have with it. We had a list of 1000 proteins that were good battering rams, gathered from experiments different scientists had run. But a lot of the time experimenters will study a bunch of variants on a theme to see which ones work the best. So the right way to split up the train/test data is not by protein, but by "theme", which we modeled by hierarchical clustering based on your favorite distance metric between amino acid sequences.

In conclusion, don't just split your data lickety split. Ratify before you stratify. Conceive before you cleave. And if you've run into this type of thing before, let me know, I'm collecting examples.

*People say "what gives" so I figured I'd go for a past-tense version.