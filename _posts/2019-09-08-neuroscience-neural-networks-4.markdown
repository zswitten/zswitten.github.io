---
layout: post
title:  "Chapter 4: Vision"
date:   2019-09-08 00:13:04 -0700
---
[Part 0](https://zswitten.github.io/2019/08/04/neuroscience-neural-networks-0.html)
[Part 1](https://zswitten.github.io/2019/08/04/neuroscience-neural-networks-1-3.html)

***Big-picture flow of information***

We take in light through our eyes. We have photosensitive cells (rods and cones) that detect how intense the light is at different places in our visual field. The rods and cones send info to Retinal Ganglion Cells that look for contrasts. The RGCs send info to Lateral Geniculate Nucleus cells which send it to cells in the visual cortex that look for lines and edges. From there it goes to the Ventral Stream AKA the "What Stream", and the Dorsal Stream AKA the "Where Stream", and from there... unclear.

Meanwhile these cells are axon-uploading into (and dendrite-downloading from) other parts of the brain too. Like the subconscious pupil-controller to decide if we need to let in more light or less, the motor control system for positioning our heads, and the hypothalamus to tell our body whether it's night or day.

***Rods and Cones***

Rods:
- Super-sensitive -- can detect single photons.
    -  Especially helpful for night vision
- More numerous than cones
- Get hyperpolarized by light in vertebrates, depolarized in invertebrates
- Have a refractory period after they fire
- Have feedback mechanisms to control their sensitivity/how long the refractory period is
    - Weber's Law: We can tell 100 grams from 105 grams (weight), but not 1000 from 1005
    - Similar for light

Cones:
- Concentrated in the fovea (center) of the eye where there are fewer blood vessels to interfere
    - That's why you can see dim stars easier when you look slightly to the side of them and let your rods kick in
- Less sensitive than rods, but faster firing rate/more frames per second = better at detecting motion
- Divided into 3 types (Red, Green, Blue), each of which specializes in detecting a different color
- DNA similarity between:
    - Cones and Rods: 40%
    - Blue and Red, and Blue and Green: 40%
    - Red and Green: 96%
        - That's why R/G color-blindness is the most common kind?

***Retinal Ganglion Cells***
- Communicate mostly with graded potentials instead of all-or-nothing action potentials. OK because it's not that far from eye to brain.
- Each RGC has a "receptive field" aka area of the canvas it's paying attention to.
    - RGCs with receptive fields that are near each other, are themselves near each other
- Receptive fields are shaped like bulls-eyes/concentric circles.
    - Some get turned on by stuff in a small circle, and off by stuff in the bigger circle outside
    - Some are the reverse
- Some RGCs can also sense light directly

***Lateral Geniculate Nucleus***
- Same receptive field shapes as RGCs
    - But not just relay stations: 90% of their synapses come from the cortex, brainstem, or thalamus.

***Primary Visual Cortex (V1)***
- V1 "simple cells" have receptive fields that look like lines/bars
- Each V1 simple cell has an area it looks at, and a preferred line orientation
- You COULD make a simple cell receptive field by stacking LGN receptive fields in a cylinder.
    - Unclear if this is how it actually works, but seems like a good theory.
- V1 neurons with similar properties are organized in vertical columns in the brain.
    - What orientation of line they respond to
    - Which eye's input they're weighting more heavily ("ocular dominance")
- V1 also contains complex cells which could be combinations of simple cells

***Neocortex***
- Has 6 layers, organized by cell size, shape, and density
- Info flows from layer 4, to layers 2 and 3, to layers 5 and 6
    - Layer 6 acts as a sort of gain control that determines sensitivity
    - Unclear if this is a property of neocortex in general or just for vision
- Two visual pathways through the neocortex
    - P, which gets its input from small-receptive-field RGCs
        - Good for detail and color
    - M, which gets its input from RGCs with a large receptive field
        - Good for general luminance/contrast + temporal sensitivity
- Two streams on the way out (alluded to in the intro)
    - Ventral AKA What Stream, which gets input from M and P equally
    - Dorsal AKA Where Stream, which gets input mostly from M
        - Contains MT cells that sense motion in a particular direction
- Contains some cells that specifically respond to faces, or to human hands


***ML Takeaways***

Whew! This chapter ended up being so information-dense that I gave it its own post, and ended up formatting it kinda like a high school study guide.

The CNNs that are used in image recognition are famously the type of ANN that's most directly modeled after the human brain, so it's no surprise to see a lot of parallels. You've got distinct layers that successively go from disorganized input to recognizing slightly more abstract spatial concepts to representing whole objects, in a feed-forward style.

That nearby real-world locations get mapped to nearby RGC cells is lowkey crazy to me. Map == territory? Reminds me of homunculus theories of cognition and the [Cartesian Theater](https://en.wikipedia.org/wiki/Cartesian_theater). In ANNs all the weights get initialized at random and there's rarely a concept of distance between two neurons in the same layer. The stacked vertical columns of similar V1 cells also suggest that we could maybe get some good priors from the triangle inequality.

It wasn't covered in detail in this chapter, but the visual system gets all kinds of input from random other parts of the brain. An analogy would be robots informing their visual understanding with other facts like what time of day it is, or what the room smells like, or their own current level of alertness.

This is not really an ML takeaway but just a random note: the experiments they used to figure out this stuff are half-horrifying, half-hilarious. They figured out the receptive field of LGN cells by anesthetizing a cat so its eyes wouldn't move on some Clockwork Orange shit and then moving stimuli around. Meanwhile they discovered that MT cells detected motion by doing the following:
1. Parking monkeys in front of a screen to watch dots move around. Most but not all of the dots move in the same direction. Afterwards, the monkeys get shown two dots, one in the direction the dots were moving, one in the opposite direction. If the monkeys look in the right direction, they get a juice reward.
2. After training the monkeys this way, if you mess with the monkey's MT area, it needs more of the dots to be moving the same direction than it used to. W/e not that impressive, easy to mess stuff up.
3. More impressively, the scientists can influence which direction the monkey picks by using an electrode to lightly stimulate the MT cells that are oriented towards a certain direction.