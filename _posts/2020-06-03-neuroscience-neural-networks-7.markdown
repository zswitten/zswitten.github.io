---
layout: post
title:  "Chapter 7: Wiring of the Nervous System"
date:   2020-06-03 10:45:00 -0700
---

[Part 0](https://zswitten.github.io/2019/08/04/neuroscience-neural-networks-0.html)

[Part 1-3](https://zswitten.github.io/2019/08/04/neuroscience-neural-networks-1-3.html)
 
[Part 4](https://zswitten.github.io/2019/09/08/neuroscience-neural-networks-4.html)

[Part 5](https://zswitten.github.io/2019/10/07/neuroscience-neural-networks-5.html)

[Part 6](https://zswitten.github.io/2019/11/13/neuroscience-neural-networks-6.html)

We have billions of neurons. And 10^14 connections between those neurons. But our instruction manual for putting it together is a mere 20,000 genes. How do all the neurons know what other neurons they're supposed to connect to?

First, let's talk about how the basic shape of the nervous system gets made. A sperm fertilizes an egg. The fertilized egg cell-divides a few thousand times. Then you have a hollow ball. The cells in the ball self-sort into three layers (outside/skin, middle, inside), and then the ball of cells flattens out into a plate. Then the plate curves around to form a tube.

Next, on the tube, forward-backward and up-down axes get defined. The way this works is there are these proteins called "morphogens" [short for mighty morphing power generators] that get made at a few different places on/in the tube. Then they spread out from those sources creating a gradient: the closer a cell is to the source, the more of the morphogen it gets. The morphogens control how active various genes are, and that determines the cell's fate i.e. what type of cell it becomes.

Cells don't stay in the same place their whole lives. They migrate. In particular, in the cortex, you can tell a cell's age by how far it is from the center. Cells that are born later migrate to the outer layers of the cortex. Kind of like tree rings.

Keep in mind this is all happening before the cells have started extending their axons and dendrites to communicate with each other. They're getting their own shit figured out. In particular, they are deciding whether they will be excitatory, inhibitory, or modulatory, and what neurotransmitter they're going to use.

But even though they're not directly communicating with each other, their fate decisions are intertwined. For instance, each Drosophila (fruit fly) (my biology-knowledgable friends keep yelling at me for calling it "Drosophilia") sensory organ is supposed to have one socket cell, one hair cell, one sheath cell, and one sensory neuron. If the organ doesn't have all those things, it doesn't work, so it's important for nearby cells to coordinate their cell fate decisions.

This is handled by a protein called Numb. Socket, hair, sheath, and sensory cells all start from the same precursor. When that precursor divides, one child gets most of the Numb. Numb makes another protein called Notch stop working, and one of the things Notch does is 1. upregulate itself and 2. downregulate a different protein called Delta, so the four siblings end up with different amounts of Notch and Delta which makes one of them become socket, one hair, etc. [More like me, less like you!](https://www.youtube.com/watch?v=kXYiU_JCYtU)

Now it's time for the cells to link up. Remember, cells have one long poky part, the axon, that carries information out, and a bushy bunch of dendrites that take information in. Cells know they're only meant to have one axon, in that if you cut off the axon while it's growing, one and only one developing dendrite will become the new axon.

Because the axons are longer, it's the axons that have to find their way to the appropriate dendrites. As we saw in the [chapter](https://zswitten.github.io/2019/10/07/neuroscience-neural-networks-5.html) about wiring of the visual system, axons are attracted to or repulsed by various proteins that appear in different amounts in different places, and that determines where they go.

Sometimes, axons have to travel quite a long way to get to their final destination. These long journeys get broken up into multiple steps. Like, there's a really strong attractant protein at the halfway point that draws axons to it. But the axon's true purpose lies elsewhere. So at the halfway point, there's another protein that makes it so the axon isn't attracted to the first thing anymore. Grass is greener and all that. And meanwhile, there's a third protein that actively repels the axon away.

Axons and dendrites from the same cell are repelled by each other, to induce them to spread out and cover the whole of an area -- "dendritic tiling". But they're chill with being around axons and dendrites from other cells.

OK, so an axon found the right general area. Now it has to mate with a dendrite to form a synapse. Axons produce a protein called agrin that triggers a bunch of receptors for action potentials to come cluster around it, while also breaking up any random other clusters that happened to be nearby. Meanwhile, the axons are also attracted to areas where there were already such clusters.

Some of these synapses are lifelong partnerships between two cells, but there's a nonzero divorce rate. In mouse muscles, the divorce rate is 90%; each muscle fiber in a mouse newborn gets input from ten neurons, but as the mouse gets older, one of those synapses gets bigger and dominant and takes all the territory from the other synapses which then shrink to nothing. The pattern of which synapses win is different from one side of the body to the other, and from one individual to another, which indicates that it's being driven by activity-dependent competition AKA Nurture not Nature. Synapses can also die out if the axons get pruned, or if the entire cell dies. Long axons are especially likely to get pruned. Also, axons that aren't firing a lot can get pruned.

The second part of the chapter/of this blog post is a case study of the formation of the olfactory map of a mouse. We've seen two types of map. The first is continuous, in the mathy sense of a continuous function where two points that are close together in the real world will be mapped to close-together points in the brain. Vision is like this. Touch is also mostly continuous. Two nerve cells in your left foot map to two nearby cells in your brain. But it's not always totally continuous: an example is that signals from mouse whiskers go to their own special place that's not especially near input from the rest of the face.

Smell is the other kind of map: discrete. Rather than being organized spatially, the smell map is organized by odorant. You could imagine three strategies for making a neural map. Number one: the input neurons are in charge. They know where to go. The target neurons are dumb and get their identity based on which input neurons choose them. Number two: the input neurons are dumb, it's the target neurons that are in control and tell the input neurons what to be. Number three: the input neurons and target neurons are both smart. In vision, it's number three. Both the neurons in the eye and the retinal ganglia cells they connect to are smart. Smart in this sense: different cells in each layer have different amounts of attractor/repeller proteins, and if you turn off the genes that make those proteins, the whole thing stops working. You could call it a healthy equal relationship where both sides contribute.

Smell is the same way, but with another fun twist: the axons sort themselves out along the way. Axons from sweet-sensing cells and axons from salty-sensing cells repel each other. And same for all the other pairs of odorants.

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