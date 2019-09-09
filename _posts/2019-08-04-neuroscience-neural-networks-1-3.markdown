---
layout: post
title:  "Neural Networks: Biological vs. Artificial (Chapters 1-3)"
date:   2019-08-04 00:13:04 -0700
---
[Part 0](https://zswitten.github.io/2019/08/04/neuroscience-neural-networks-0.html)
[Part 2](https://zswitten.github.io/2019/09/08/neuroscience-neural-networks-4.html)

***Neuroscience Facts/Summary***

Neurons are made of three types of things:
**Soma**, the cell body. DNA is stored here.
**Axons**, long tendrily outcroppings that can reach all the way from your head to your toe.
**Dendrites**, which are short and bushy and connect to the axons of neighboring neurons.

Axons and dendrites are both made of **microtubules**. In an axon they all point the same cardinal direction (information flows only one way). In dendrites, they can be pointing in different directions.

Neurons communicate with each other in two ways: action potentials, and via sending each other proteins. In both cases, information flows from the soma to the axons, to other neurons' dendrites, and then to their soma.

Sometimes neurons will ship proteins directly, but more commonly they'll ship the RNA that codes for the proteins.

Action potentials are like waves of electricity that pass through a neuron and then leave it the way it was. They can move as slow as 2 meters/second or as fast as 120 meters/second. They travel faster when passing through wider microtubules (less resistance from the walls), and faster when moving through axons that are sheathed in myelin.

Action potentials trigger the release of neurotransmitters. Some neurotransmitters are inhibitory, others excitatory.

Neurotransmitters' default state is to be hanging out in **vesicles**. When an action potential comes, if there are a bunch of positively charged calcium ions around, the vesicles fuse with the membranes of the next cell over and release the neurotransmitter, it does its thing, then gets reabsorbed into the vesicle.

Many common poisons work by inhibiting either the release of neurotransmitters, or their reabsorption. You can tell that a lot of structure for neuronal communication is conserved between humans and animal because a lot of the same toxins mess up humans and animals in the same way.

***Takeaways for ML***
1. Biological neurons are surprisingly *quantized.*

Action potentials either fire, or they don't. There's no half-fire. Stimulus intensity isn't expressed in higher activation peaks, but in a faster cadence of activation. Similarly, neurotransmitters either get released or they don't. This is a huge contrast to artificial neurons where higher stimulus = higher response for all the commonly used activation functions.

2. Biological neural networks use *time* to regulate their behavior.

Neurons have refractory periods where they can't fire again because they've already fired too recently. And their functioning depends on the presence of calcium ions which are only sometimes around to work their magic.

Some types of artificial neural networks (I'll start saying "ANNs") such as RNNs have a time-dependent quality but time generally corresponds to chunks of input, not real external time.

3. Neurons send each other code.

I can't think of an ANN analogue for proteins shipping each other RNA (and if you can, please tell me about it). Could analogize it to neurons sending each other hyperparameters, weights, or even local architectural schema. Could also make this time-based: specific ANN sections that are experiencing very high gains in accuracy could ship whatever we decide RNA is to other parts of the network to maximally exploit the current training conditions.
