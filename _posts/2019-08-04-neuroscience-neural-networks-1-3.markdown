---
layout: post
title:  "Neural Networks: Biological vs. Artificial (Chapters 1-3)"
date:   2019-08-04 00:13:04 -0700
---

**Chapter 1**
-  A neuron is made of long, tendrily *axons*, thick, bushy *dendrites*, and the *soma* i.e. the cell body.
    -  Axons can be super-long. One axon can reach all the way from your head to your toe.
-  Information flows from soma to axons, into the dendrites of other cells, and then in turn to their soma.
-  Stimulus intensity corresponds to frequency of activation, not higher peak activation.
    -  This is super-different from artificial neural networks, where greater stimulus = stronger response. The response could be unbounded (RELU) or top off at 1 (sigmoid, tanh) but there's always at least a correlation where the harder you push the neuron's buttons, the harder it'll push the buttons of the next neuron in line. In the body, if you get burned by a hotter stove, your heat-detection neurons will fire not harder, but more often.
    -  RNNs sort of have this time-dependent quality, but a time-step in an RNN generally corresponds to a new chunk of input.

**Chapter 2: Signaling Within Neurons**
-  Neurons communicate with each other in two ways: *activation potentials* (i.e. electricity) and by sending each other proteins.
-  Sometimes proteins get shipped directly, but more often neurons will ship the RNA to make the protein.
    -  If we think of numerical activations as proteins, shipping RNA might mean shipping a small piece of network architecture, or a set of hyperparameters that are working well or projected to work well in the future.
-  Activation potentials are all-or-nothing; they either fire or don't.
    -  Because of this, they don't get weaker with distance, as opposed to passive electric currents.
-  Axons and dendrites are each made of *microtubules* which have a plus and minus end.
-  Within an axon, all the microtubules are lined up with their +/- ends pointing the same way (and so information only flows one way). Within dendrites, the microtubules aren't lined up so neatly.
-  Action potentials move at different speeds: 2 meters/second at the slow end, 120 meters/second on the fast end.
-  Things that make an action potential travel faster:
    -  Wider microtubules (less resistance from the walls)
    -  When moving through axons that are sheathed in *myelin*

**Chapter 3: Signaling Across Synapses**
-  Action potentials trigger the release of *neurotransmitters*
    -  Quantized particles that either get released or don't.
-  Toxins that inhibit neurotransmitter communication in humans tend to also do it for animals
    -  So a lot of the infrastructure is conserved
    -  Humans and animals happen to make use of the exact same neurotransmitters.
-  Some neurotransmitters are excitatory, others inhibitory.
-  Neurotransmitters hang out in *vesicles*. The vesicles fuse with membranes, release their neurotransmitters, let them do their thing, and then reabsorb them.
    -  Before that reabsorption, there's a refractory period where a neuron can't fire because it already fired too recently.
-  The whole process only works if there's a bunch of positively-charged calcium ions around.
