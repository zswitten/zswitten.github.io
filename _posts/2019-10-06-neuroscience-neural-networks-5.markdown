---
layout: post
title:  "Chapter 5: Wiring of the Visual System"
date:   2019-10-06 21:46:04 -0700
---
[Part 0: Introduction](https://zswitten.github.io/2019/08/04/neuroscience-neural-networks-0.html)\
[Part 1-3: Properties of Neurons](https://zswitten.github.io/2019/08/04/neuroscience-neural-networks-1-3.html)\
[Part 4: Vision](https://zswitten.github.io/2019/09/08/neuroscience-neural-networks-4.html)\
[Part 5: Wiring of the Visual System](https://zswitten.github.io/2019/10/07/neuroscience-neural-networks-5.html)\
[Part 6: Smell, Taste, Hearing, and Touch](https://zswitten.github.io/2019/11/13/neuroscience-neural-networks-6.html)\
[Part 7: Wiring of the Nervous System](https://zswitten.github.io/2020/06/03/neuroscience-neural-networks-7.html)

Gonna try skipping the bullet point system for this one and write it more conversationally.

The pattern of connections in a computer chip was carefully designed by a human engineer, who was like, this row of transistors needs to connect to these other rows, then we have a whole other bank of transistors over here, yadda yadda. But how do our neurons know which other neurons to connect to? Where may this splendid biological IKEA manual be found? 

Humans have 10<sup>11</sup> neurons in our brains. Each one connects to 10<sup>3</sup> other neurons. That's a total of 10<sup>14</sup> connections.* Meanwhile, our genome has 3 x 10<sup>9</sup> base pairs in it. So the manual of self-construction can't specify every single connection that needs to be made in advance. Rather, it has to lay out some general rules and let the neurons figure it out the details on their own.

There seem to be two main mechanisms by which this happens:
1. Neurons from some regions express various proteins that are repelled by or attracted to receptors in neurons they might consider connecting to. [Regional]
2. Neurons that are close together spend a bunch of time firing together spontaneously in the period of early development when these bonds are getting formed, which then makes them latch on to nearby targets in the next layer. [Local]

Let's take a look at the [rather gruesome, as per usual] experimental evidence for each of these.

A scientist surgically rotated the eyeball of a newt 180 degrees, as well as severing the newt's optic nerve, breaking the connections between RGCs and their targets in the *tectum*. Then, they allowed the connections to regrow. The outcome I expected, based on pop sci articles I've read about neuroplasticity, was that the newt would learn to reconstruct the visual field from the new inputs. Instead, while the newt did regain its vision... it saw the world upside down. When they'd drop food into the newt's tank, it swam down toward the bottom of the tank to get it and crashed into the glass :(

This shows that the neurons sort of found their way home even after they'd been cut. And if you track where they connect to, you see a flippy pattern where axons from the top of the retina go to dendrites in the bottom of the tectum, bottom of the retina to top of tectum.

So either your top-side retinal cells are attracted to something on the bottom, or they are repelled by something on the top. Which? Answer: the latter, as can be seen in vitro by letting the top RGC cells choose between top tectum cells and warmed-up, "neutralized" cells (they're like "ew, we don't like the top cells, we'll take neutral") and letting them choose between bottom tectum cells and neutral (they're like, "we're happy to connect to either.")

The specific proteins that mediates the repulsion are called ephrins. Ephrins also mediate left/right swapping, which is even cooler because that's what gives us binocular vision. In mice, only about 5% of RGCs cross over the midline (called the *optic chiasm*) (yes, "chiasm" not "chasm"), which is why they can't really perceive distance. In cats and ferrets, 15-30% cross over. In humans, it's a full 40%.

So it's predetermined what region your RGC cells are going to connect to, but (shifting here to Mechanism 2) it's a different story at the next level up. You might remember from [Chapter 4](https://zswitten.github.io/2019/09/08/neuroscience-neural-networks-4.html) that V1 cells differ in their "ocular dominance" (which eye's input they care about more). Scientists took a cat and stitched one of its eyes shut, and found that its V1 cells were all ocularly dominant for the open eye, and this stayed true even after they reopened the eye. Stitching up one eye messes up cats' binocular vision long-term MORE than stitching both eyes shut, because then the ocular dominance stays 50/50. Scientists tried messing with cats' eyes at various times during their life and found that peak messing-up was achieved when the stitching happened in a key period 4-11 weeks after birth.

Meanwhile, scientists somehow gave a frog a THIRD EYE during embryonic development, and found that its RGCs connected just fine to the next layer, even though the frog's genome could not have set instructions for how to deal with such an event. The third eye ended up splitting receptors with one of the regular two eyes, so it was less like triocular vision, and more like having two right eyes and one left eye. I literally thought the textbook was pulling my leg when I read this but apparently you really can just dab the eye right in there. Three-Eyed Raven < Three-Eyed Frog.

The general rule that is driving this learned wiring is Hebbs' Rule: neurons that fire together, wire together. And the converse is also true: neurons that fire out of sync with each other eventually lose their connectivity.

We see this firing-together in so-called *retinal waves* that occur in humans' early developmental period, which are NOT driven by visual input, but happen spontaneously. Remember, the ephrin stuff just gets the axons to the right general region. Nearby RGC cells fire correlatedly which "teaches" the downstream neurons which inbound connections are correlated. A couple analogies that come to mind:

-A bunch of cords from laptop, monitors, keyboard, mouse, etc. are stuffed together through a small hole in a desk. The ephrins make sure the tangle goes through the right hole. At the other end, retinal waves help sort out which wires correspond to which device.

-A conductor, preparing for a symphony, gestures to the different sections of their orchestra to get a sense of the tone coming from each section.

At a chemical level, Hebbs' Rule is enforced via *NMDAs* which bind to glutamate from presynaptic neurons, but only when postsynaptic neurons are also firing/depolarized which removes a magnesium blockage that was stopping the glutamate from being recepted (not a real word).

And that wraps up this chapter. I think I'll skip writing out ML takeaways this time and just note how cool it is that our brains are self-assembled, starting from only a single cell. Next time: olfaction!

*The textbook says 10<sup>14</sup> but when I read it I was like, wait, shouldn't it really be 10<sup>14</sup>/2 connections which is halfway between 10<sup>14</sup> and 10<sup>13</sup>, since naive multiplication double-counts each connection because they're shared between two neurons? Either way though it's a lot.