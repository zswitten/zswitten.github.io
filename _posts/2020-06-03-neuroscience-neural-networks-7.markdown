---
layout: post
title:  "Chapter 7: Wiring of the Nervous System"
date:   2020-06-03 10:45:00 -0700
---

[Part 0: Introduction](https://zswitten.github.io/2019/08/04/neuroscience-neural-networks-0.html)  
[Part 1-3: Properties of Neurons](https://zswitten.github.io/2019/08/04/neuroscience-neural-networks-1-3.html)  
[Part 4: Vision](https://zswitten.github.io/2019/09/08/neuroscience-neural-networks-4.html)  
[Part 5: Wiring of the Visual System](https://zswitten.github.io/2019/10/07/neuroscience-neural-networks-5.html)  
[Part 6: Smell, Taste, Hearing, and Touch](https://zswitten.github.io/2019/11/13/neuroscience-neural-networks-6.html)  
[Part 7: Wiring of the Nervous System](https://zswitten.github.io/2020/06/03/neuroscience-neural-networks-7.html)

We have billions of neurons. And 10^14 connections between those neurons. But our instruction manual for putting it together is a mere 20,000 genes. How does a neuron know what other neurons it's supposed to connect to?

First, let's talk about how the basic shape of the brain gets made. A sperm fertilizes an egg. The fertilized egg cell-divides a few thousand times. Then you have a hollow ball. The cells in the ball self-sort into three layers (outside/skin, middle, inside), and the ball of cells flattens out into a plate. Then the plate curves around to form a tube.

Next, on the tube, forward/backward and up/down axes get defined. The way this works is, there are proteins called "morphogens" [short for mighty morphing power generators] that are produced at specific places on the tube. The morphogens spread out from their sources, creating a gradient: the closer a cell is to a morphogen factory, the more morphogen a cell gets. The morphogens control how active various genes are in a cell, and that determines its "cell fate", i.e. what type of cell it becomes.

Keep in mind this is all happening before the cells have started extending their axons and dendrites to communicate with each other. They have to get their own act together first. In particular, they are deciding whether they will be excitatory, inhibitory, or modulatory, and what neurotransmitter they're going to use.

But even though they aren't directly communicating with each other, their fates are intertwined. For instance, each Drosophila (fruit fly) (my biology-knowledgable friends keep yelling at me for calling it "Drosophilia") sensory organ is supposed to have one socket cell, one hair cell, one sheath cell, and one sensory neuron. If the organ doesn't have all those things, it doesn't work, so it's important for nearby cells to coordinate their cell fate decisions.

This is handled by a protein called Numb. Socket, hair, sheath, and sensory cells all start from the same precursor. When that precursor divides, one child gets most of the Numb. Numb makes another protein called Notch stop working, and one of the things Notch does is 1. upregulate itself and 2. downregulate a different protein called Delta, so the four siblings end up with different amounts of Notch and Delta which makes one of them become socket, one hair, etc. [More like me, less like you!](https://www.youtube.com/watch?v=kXYiU_JCYtU)

Cells don't stay in the same place their whole lives. They migrate. In particular, in the cortex, you can tell a cell's age by how far it is from the center. Cells that are born later migrate to the outer layers of the cortex. Kind of like tree rings.

Now that all the pieces are in place, it's time for the cells to link up. Remember, cells have one long poky part, the axon, that carries information out, and a bushy bunch of dendrites that take information in. Cells know they're only meant to have one axon; if you cut off a cell's axon while it's growing, one and only one developing dendrite will become the new axon.

Because the axons can grow very long, it's their job to grow their way to the appropriate dendrites. As we saw in the [chapter](https://zswitten.github.io/2019/10/07/neuroscience-neural-networks-5.html) about wiring of the visual system, axons are attracted to or repulsed by various proteins that appear in different amounts in different places, and that determines where they go.

Sometimes, axons have to travel quite a long way to get to their final destination. These long journeys get broken up into multiple steps. For example, there's a really strong attractant protein at the spine that draws axons to it. But the axon's true purpose lies elsewhere. So once it reaches the spine, there's another protein hanging out nearby that makes it so the axon isn't attracted to the first protein anymore. And meanwhile, there's a third protein in the area that actively repels the axon away. Grass is always greener!

Axons and dendrites from the same cell repel each other, to induce them to spread out and cover the whole of an area -- "dendritic tiling". But they're chill with being around axons and dendrites from other cells.

OK, so an axon found the right general area. Now it has to mate with a dendrite to form a synapse. Axons produce a protein called agrin that triggers a bunch of receptors for action potentials to come cluster around it, while also breaking up any random other clusters that happened to be nearby. To make things easier, the axons are attracted to places where there were already preexisting clusters of receptors.

Some of these synapses are lifelong partnerships between two cells, but the divorce rate is real. In mouse muscles, the divorce rate is 90%; each muscle fiber in a mouse newborn gets input from ten neurons, but as the mouse gets older, one of those synapses dominates, taking all the territory from the other synapses which then shrink to nothing. The pattern of which synapses win is unpredictable and differs between individuals and even between the two sides of an individual's body. This indicates that it's being driven by activity-dependent competition AKA Nurture not Nature. Synapses can also die out if the axons get pruned, or if the entire cell dies. Long axons are especially likely to get pruned. Also, axons that aren't firing a lot get pruned.

The second part of the chapter/of this blog post is a case study of the formation of the olfactory map of a mouse. We've seen two types of neural map. The first is continuous, in the mathy sense of a continuous function where two points that are close together in the input space will be mapped to close-together points in the output space. Vision is like this: two nextdoor neighbor pixels of your visual screen will map to two nextdoor neighbor neurons. Touch is also mostly continuous. Two nerve cells in your left foot map to two nearby cells in your brain. But it's not always totally continuous: an example is that signals from mouse whiskers go to their own special place that's not especially near input from the rest of the face.

Smell is the other kind of map: discrete. Rather than being organized spatially, the smell map is organized by odorant. You could imagine three strategies for making a neural map. Number one: the input neurons are in charge. They know their own identities, and so they know what target neurons in the next layer they should connect to. The target neurons are dumb and define their identity by which input neurons choose them. Number two: the input neurons are dumb and connect randomly to target neurons. It's the target neurons that are in control and tell the input neurons what to be. Number three: the input neurons and target neurons are both smart. In vision, it's number three. Both the neurons in the eye and the retinal ganglia cells they connect to are smart. Smart in this sense: different cells in each layer have different amounts of attractor/repeller proteins, and if you turn off the genes that make those proteins, the whole thing stops working. You could call it a healthy equal relationship where both sides contribute.

Smell is the same way, but with another fun twist: the axons sort themselves out along the way. Axons that are coming from cells that sense two different odorants repel each other, while axons that are coming from cells that sense the same odorant attract each other. Like if your tangled-up headphones could magically unscramble themselves on the way to your ears.

Summing it all up, how do we get from 20,000 genes to 10^14 connections?

- Some genes make multiple different proteins
- The amount of a protein that's present makes a difference, not just whether it's present vs. absent
- Proteins do different stuff in different contexts
- Combinations of proteins do stuff that neither can do alone
- Wiring decisions can have multiple steps, both spatially (multi-step journeys) and temporally (pruning)
- Activity/learned experience can help make connection decisions
- Some of the details don't matter, like as long as an odorant axon is going to the right glomerulus, it doesn't really matter which exact cell in the glomerulus it connects to.

And finally, what you've all been waiting for: half-baked speculation about how we could use this info to make machine learning work better!

Neural networks come into existence with all their connections fully specified. Some of the weights die/go to zero during training, which is like axon pruning. I wonder what it would be like to build up the connectome gradually over time, and to add an element of indeterminism where cells occasionally connect to the "wrong place". AutoML is arguably like the former, while skip connections are arguably like the latter.

I'm intrigued by the idea of having some concept of a protein, that operates in some "area" (i.e. subset) of different layers, and attracts connections from some neurons in the layers before and after it, while repelling others. Or a whole family of proteins that regulate each other. I wonder whether the practical difficulties of assembling a brain can act as a kind of regularizer. Like, the [VC dimension](https://en.wikipedia.org/wiki/Vapnik%E2%80%93Chervonenkis_dimension#VC_dimension_of_a_neural_network) of a brain with 86 billion neurons that can connect to each other in any arbitrary way is huge. The VC dimension of brains that are physically and biologically possible to assemble is a lot smaller.
