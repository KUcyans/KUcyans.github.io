---
layout: post
title: Accelerator and Detector
date: 2025-10-09
permalink: /posts/accelerator_and_detector/
cover: /assets/img/accelerator_cover.png
---

> The article is written based on [this post](https://cms.cern/detector/triggering-and-data-acquisition) about the CERN data aquisition system, mingled with my background knowledge

The CERN consists of multiple experiments. General purpose detectors like ATLAS and CMS seek physics beyond the current Standard Model by investigating the events from the detector. The events are taken place from myriad numbers of proton collisions. How are these detector's events generated?

# Beam Generation
Let's see how the protons are generated first. All is coming from hydrogen atoms in gaseous state. A hydrogen atoms is converted into negatively charged hydrogen ion gaining an additional electron: 
$$H+e^- \rightarrow H^-$$

These ions can be accelerated by the accelerator chain of CERN with alternating electric fields and focused and steered by magnetic fields. (There also are additional facilities to improve the purity(injection efficiency) and alignment of the particles in the accelerator.)

After undergoing all the accelerating and injecting process, the ions travel almost in the speed of light in vacuum (it is already -nearly- vacuum along the accelerator.) They are passed through a thin carbon foil which strips the electrons of the reduced hydrogen to produce proton. 
$$H^- \rightarrow p^++2e^-$$
A beam is the entire ensemble of protons circulating in the accelerator, structured into distinct bunches.

![Proton Generation for LHC](/assets/img/proton_generation_LHC.png){: width="75%" }   

**Figure 1**: Production of Protons from Hydrogen via $H^-$ Ion Acceleration and Foil Stripping


# Bunches and Crossings
Is a beam just a group of protons? Yes, but with some structure. A beam consists of multiple subgroups of protons called bunches. Typically a beam consists of 2808 bunches, which is a constrained value by the hardware and facility. Each bunch contains approximately 100 billion or $10^{11}$ protons, with physical length of 7.5 cm. There is a 25ns temporal spacing between each adjacent pair of bunches. which makes 40MHz crossing frequency. A crossing refers to a passing of one bunch through another that is travelling in the opposite direction.

# So how Events are Generated?
We have crossing every 25ns (=1/40MHz), but each crossing may generate only few tens of proton-proton collision interactions. An event is the full record of everything produced by one bunch crossing. So an event may contain multiple interactions. High-Luminosity LHC (HL-LHC) is aiming at the number of interations per crossings higher than 100. 

![Event Formation for LHC](/assets/img/event_formation_LHC.png){: width="75%" }   

 **Figure 2**: Beam Structure and Event Formation in the LHC. [Detector image](https://cds.cern.ch/record/2677903) and [Example event image](https://cds.cern.ch/record/2114784) can be found in the webpages linked respectively.

# Trigger
Shall all the data produced be kept? No, since they are too big. Each experiment stores the data selectively and the selection is done in multiple levels called triggers. The firsthand trigger L1 of CMS, for example, keeps only around 100,000 events.


# What Signals Do the Detectors Record?
There are mutiple channels in a detector. These are the main dimensions of the data by the detectors:
* charged particle tracks
* electromagnetic showers
* hadronic showers
* muon trajectories
* energy deposits
* timing information
* vertex positions
* calorimeter clusters
* pixel hits

