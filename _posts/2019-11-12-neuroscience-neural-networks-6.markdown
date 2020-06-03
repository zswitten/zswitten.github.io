---
layout: post
title:  "Chapter 6: Olfaction, Taste, Audition, and Somatosensation"
date:   2019-11-12 23:45:00 -0700
---

[Part 0: Introduction](https://zswitten.github.io/2019/08/04/neuroscience-neural-networks-0.html)\
[Part 1-3: Properties of Neurons](https://zswitten.github.io/2019/08/04/neuroscience-neural-networks-1-3.html)\
[Part 4: Vision](https://zswitten.github.io/2019/09/08/neuroscience-neural-networks-4.html)\
[Part 5: Wiring of the Visual System](https://zswitten.github.io/2019/10/07/neuroscience-neural-networks-5.html)\
[Part 6: Smell, Taste, Hearing, and Touch](https://zswitten.github.io/2019/11/13/neuroscience-neural-networks-6.html)\
[Part 7: Wiring of the Nervous System](https://zswitten.github.io/2020/06/03/neuroscience-neural-networks-7.html)

This chapter is about the senses: how our bodies notice things that are happening around us. The inputs vary a lot: sound, heat, food. It all gets turned into electrical signals and then sent to the brain. Let's run down the senses.

***Smell***

As photons are to vision, **odorants** are to smell. Little particles that get released by things an animal might care about like predators/food/mates. If they're intrepid enough to make it through the mucus, they can reach the cilia, which are tiny little hairs in the nose. These hairs are dendrites of the Olfactory Receptor Neurons (ORNs).

What's interesting about the ORN <=> odorant relationship is that it's many-to-many -- each odorant can bind to multiple kinds of receptors, and each receptor can recognize multiple odorants. So a perceived smell is a sort of N-dimensional smell vector, where N is how many different kinds of ORNs there are. In humans that's about 400.*

ORNs are jumbled around pretty randomly in human noses. It's not like "all the ones that sense grassy smells in front" or anything. (Although in mice, they tend to be on the same side of the short axis.) But in the next layer, the **olfactory bulb**, axons from a given ORN type converge, making a kind of "smell map". Shades of how eye neurons that are picking up light from a certain patch of the visual field also project near each other. This map is mostly the same across individuals in a species.

Another similarity to vision is that nearby cells in the olfactory bulb inhibit each other, like competing royals in a court. In vision, this helps create contrast, say between a super-bright area and the merely regular bright surrounding parts. In smell, it could be doing something similar, acting as a kind of gain control where when all the ORNs are firing a lot, they calm each other down.

It's a direct flight from the olfactory bulb to the cortex. This makes smell the sensory data that gets to our brain with the fewest number of hops. In the cortex, the spatial info from the bulb gets thrown out, and the neurons there are more sensitive to the onset of a stimulus than its continuation. This matches what I hear people say about smell, that if you're exposed to it for a while you get used to it and stop noticing it.

That's pretty much it for smell, except for a fun experimental aside: flies have a parallel smell track (now extinct in humans) for detecting pheromones. Scientists took some flies and stressed them out by shaking them, then put them at one end of a T, put regular air at the other end, and had normal flies fly into the bottom of the T. The "naive flies" (I love this name! These flies have seen nothing! They don't know what it's like out there) avoid the end of the tube with the bummerish air exhaled by the stressed flies.


*Our genes code for 800, but a little more than half of these are "nonfunctional" i.e. they don't get made any more. Researchers think this means that we as a species are gradually becoming less refined in our smelling abilities, which proves that I, who can't smell at all, am actually an ultra-evolved future being.

***Taste***
You'll never guess what the taste analogue of odorants is. OK, you guessed: it's **tastants**. They are distinguished by being nonvolatile, and hydrophilic (easily dissolved by water). There are five tastes: bitter, sweet, salty, sour, and umami. The book then defines "flavor" as a combination of taste and smell. Of these five tastes, three (bitter, sweet, umami) get detected by receptors, while the other two (salty, sour) use ion channels. Some quick receptor facts, along with the book's just-so stories to explain them:

- There are more kinds of bitter receptors than there are sweet and umami receptors.
    - There are more different kinds of bad things to eat in the wild (everything that's not food) than there are good things (food)
- Bitter receptors have a lower threshold of activation than sweet/umami, so they can detect smaller amounts
    - It's important to avoid even small amounts of bad things, whereas with good things, you need there to be enough good thing that it's worth the effort to put it in your body
        - I'm not sure I buy this one, since I don't see why bitter vs. sweet tastants should appear at the same concentration in stuff we eat.
- Cats (carnivores) can't taste sweet, while pandas (herbivores) can't taste umami.

All right, now here's the coolest thing I learned in this chapter. Scientists did some nifty mouse gene engineering to take bitter receptors and put them into the kinds of cells that normally contain sweet receptors. Will the mouse now just avoid everything, because even its sweet cells are getting fed by bitter receptors? Or will the mouse now like bitter things, because they are triggering the sweet cell? In other words, does perception come from the nature of the input, or from the wiring of the cell that is perceiving the input? Answer: the wiring. The mouse tastes bitter things as sweet. And if you do the reverse (put sweet receptors into bitter cells), sweet things then get perceived as bitter.

***Sound***

Of the senses in this chapter, sound feels the most physical. Less chemicals binding, more things bashing into other things.

It starts with waves of air pressure causing vibrations in the eardrum, which is kind of like a regular drum in that it's a thin, stretched-out membrane. This causes 3 tiny bones to tap against the **cochlea**, which are chambers filled with fluid. This makes the fluid levels in the chamber go up and down. In between the three chambers lies the vacation destination-sounding Organ of Corti. Within the organ can be found the hair cells, which are arranged in ascending staircases, locked together at the base and connected at their tips by thin "tip links". If the hair cell a step higher than you in the staircase gets pushed over by shear force from the cochlear chambers, that will pull open your ion channel and allow polarized calcium and potassium to get in, which polarizes the neurons and we're off to the races. Imagine an ascending series of manholes whose covers are stitched together by twine.

The ear has a lot of mechanical tricks for describing the sound to the brain. The eardrum is a different thickness at different points, and different thicknesses resonate best with certain sound frequencies. And after the hair cells get activated, the **spiral ganglion neurons** that take their information to the brain stem are differentially sensitive to how much the hair cells are moving based on how close to the base of the hair cell they are. At low frequencies, firing patterns sync up with the frequency of the sound itself. That stops working about 2-3 kilohertz. I wondered while reading this section if this is why bassists are commonly considered to be part of the rhythm section.

Neurons that detect sounds of similar frequencies keep that "tonotopic map" going up a few levels in the neuronal hierarchy, like how vision maps get projected upward. A difference between audition and vision is that the flow of information in audition is less linear. For vision it's retina -> thalamus -> cortex. For sound, it actually goes back from the outer hair cells to get temporal precision, as well as to other parts of the brain to get info about where the sound is coming from.

Speaking of which, how do we know where different sounds are coming from? Owls do it in a really cool way: they have **coincidence detectors** that are like AND gates for their ears, only firing when they get signal from both ears at once. But the detectors are spread out -- some are closer to the left ear, some the right. So you can tell where sound is coming from laterally by which detectors are firing. What about the vertical plane? Easy: owls' ears aren't vertically aligned, and the detectors are also not vertically aligned, so they can use the same trick.

Humans also appear to cross-compare info from the two ears to decide where sounds are coming from, although our ears aren't vertically displaced so we're doing the vertical plane in some other way. If you've ever seen a dog (or human) cock its head like "say what?", that's to get vertical displacement. But if we cock our heads how does our brain know which ear is on top? Well, there's a parallel system to hearing, called the **vestibular system**, that's devoted to exactly this. Like hearing, there are hair cells that sense shifting fluid levels to decide what angle our heads are at.

That brings us to the last sense in the chapter...

***Somatosensation***

You say somato, I say somato.

Our touch system is the physically largest out of any of our senses since it encompasses the entire skin, along with muscles. It detects movement, temperature, touch, pain, and itch.

Structurally, we have 31 paired zones running up our spines, each with about 14K sensory neurons that are connected to our skin and musculature. Intensity of sensation is expressed through firing rate, and the location the sensation is coming from is preserved in the 31 zones ("somatopic map").

What distinguishes these 14K neurons from each other? A few factors: the thickness of the axon fiber, how myelinated the fiber is (remember myelin is the sheath that some neurons are surrounded in that makes signals flow faster), and the type of stimulus they respond to. I'll now go through the different types of stimulus and what kinds of neurons pay attention to each.

Proprioceptive neurons, the ones that help you keep your balance or do "grasping" which always makes me imagine our hands as fleshy arcade claws, are the most highly myelinated and have the highest diameter, since balance and grasping require constant minute adjustments. To make these adjustments, proprioceptive neurons relate feedback about muscle tension and strength.

Touch neurons are divided into two classes. There's a kind on the surface of the skin that only fire when a sensation starts or ends. These are referred to as "rapidly adapting" because they get used to sensations right away and only care about changes. But they're very sensitive to changes in that their threshold of activation is quite low. Then there's another kind deeper down in the skin that senses pressure. A key experiment to figure this out involved stroking mice gently and then less gently.

Then you have the nociceptive neurons, which sense pain. Things ("modalities") that cause pain include temperature, being poked with unpleasant objects (the book calls this "noxious mechanical stimuli"), and chemicals released inside the body to respond to inflammation. Some nociceptive neurons can sense multiple modalities. Within the nociceptive category, larger myelinated axons carry info about heat and noxious mechanical stimuli: pain that is acute and well-defined. Meanwhile the smaller, unmyelinated axons handle poorly localized pain caused by reaction to inflammation.

A cousin of pain is itch. As with the taste receptor/cell distinction, transferring a receptor to a different cell also transforms the sensation when the receptor is triggered.

***Some ML Takeaways***

The senses in this chapter have themes of modularity and reuse of components. The plug-and-play nature of the taste receptors and pain/itch receptors could be analogized to the way that two NNs trying to do very different tasks might both use some common layer architectures like a convolutional layer.

Information flow between the brain and the senses is a two-way dialogue. For instance, all our senses get turned way down when we are drowsy/sleeping.
