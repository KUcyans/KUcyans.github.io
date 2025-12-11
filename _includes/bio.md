
# <span style="color:#51ADDA;">Cyan</span>
## Computational Physicist  

*Affiliation: Shakuras, the pale blue dot, the citrus love association, IcePack team*  

### <span style="color:#51ADDA;">I’m Cyan, a computational physicist, playfully utilising machine learning and high-performance computing techniques. I am trying to build explainable machine learning models and apply them to scientific problems.</span>

<!-- ## In this site you’ll find:
- About myself
- My points of view on ML and its application  
- Notes on physics, ML, and experiments  
- Personal thoughts and research reflections   -->

## My interests include:
- Applying machine learning to scientific problems  
- Hardware optimisation for computation  
- Data pipeline design and implementation  
- Statistical representation of data  
- High-energy (astro)particle physics  

## Research Experience 
### 1. Master's Program: **High Energy Neutrino Event Reconstruction in IceCube**
![High Energy Event Reconstruction](/assets/img/illust_masters_thesis.png){: width="80%" }  

**Figure 1** describes my work on my master's thesis. I statistically summarised IceCube event data, with which I trained transformer. The trained transformer could separate the events that are likely tau neutrino events.

My latest research focuses on transformer (neural network)-based models for high-energy neutrino flavour classification, focusing on [IceCube](https://icecube.wisc.edu/science/icecube/) neutrino event data. I have experimented with different architectural hyperparameters and their contribution to the final performance. I am attracted to the fields where this data-driven approaches can be a prominent approach. I love the joy that nice collaboration can bring. I am always seeking for opportunities for catharsis-evoking teamwork. I enjoy programming, especially I feel alive when I build successfully implement a complex logic in code with a comprehensive and organised structure. Most of my software development experience is done with Python, C++, and Java, and under the object-oriented paradigm. In the process of my research, my fellow master's student and I made our data processing tool public in a GitHub repository, with a cool name of [**IcePack**](https://github.com/KUcyans/IcePack/).


## Professional Experience 
### 1. Staff Software Engineer: **Instrument Control & Automation for Semiconductor Equipment**

![Control & Automation Software Engineering](/assets/img/illust_sw_engineer.png){: width="80%" }   

**Figure 2** illustrates my experience as a software engineer for equmipment control and automisation. I developed and maintained a software application for machines in semiconductor manucaturing lines. 


I worked at a company that designes and manufactures atomic force microscope (AFM)-based metrology tools for semiconductor fabrication lines (FABs). My team developed and maintained the software application that controlled the entire tool from low-level hardware motion to high-level workflow logic.

The development of such a machine requires two different phases of integration.   
1. Intermodulear integration: the integration of the modules that constitute the machine  
2. FAB-level integration: the integration with the FAB facility where the machine is installed

A FAB can be seen as a large ecosystem consists of individual tools. Material transport is coordinated by the factory host system, usually through automated systems such as overhead hoist transport (OHT). To be assimilated in this ecosystem, every tool must follow standardised communication rules. In the semiconductor industry, this is governed by the SECS/GEM specification, which guarantees safe, stable, and consistent automated operation across the entire production line.

Once a lot arrives at the tool’s docking area, the machine must take over and transfer the material to the internal stage for processing. This internal movement depends on multiple component modules, all of which can affect the material and therefore must be tightly synchronised. This modular structure should be logically represented in software as well as the related state machines. 

My main responsibility was the development, expansion, and maintenance of the material-transfer logic. I focused on how a wafer is received, moved safely through the machine, and handed back to the FAB’s automated transport system. This required working across both integration layers: maintaining compatibility with FAB-level automation while ensuring precise coordination of the tool’s internal modules. My work involved refactoring existing control sequences, introducing new abstraction layers, and applying effective design patterns to improve clarity and maintainability. I also ensured synchronisation and orchestration across distributed component modules to support reliable and stable automated operation.

Most development was performed in C++ and Java, following object-oriented design to manage system complexity. The core hardware control layer was implemented in C++, providing deterministic behaviour and direct interaction with the controller. Higher-level logic and the user interative interface were written in Java, which defined the machine’s workflow, state transitions, and operator interaction.

In addition to the hands-on software development experience, the company gave me the opportunity to extend my skills through self-directed, web-based training. I completed a course on modern C++, where I learned the C++11, C++14, and C++17 standards. Modern C++ refers to the newer versions of the language that introduce features such as type inference, smart pointers, improved memory-management utilities, and lambda expressions. I applied these features to the existing codebase to make the software more concise, expressive, and maintainable.

### 2. Analysis Engineer

![Scientific Analysis Engineer](/assets/img/illust_analysis_engineer.png){: width="80%" }    


**Figure 3** illustrates the scientific analysis engineer position's role. The analysis targeted on a component of machines installed in FABs. 


Before I worked as a software engineer, I had the opportunity to work as a chemical analysis engineer in a semiconductor design and manufacturing company. Although semiconductor technology is often associated with electrical engineering, the actual manufacturing of chips is deeply rooted in materials science and chemical engineering. The fabrication process is essentially a long sequence of chemical treatments applied to a silicon wafer.

Semiconductor manufacturing relies heavily on high-purity chemicals. These chemicals are used for many different purposes: removing specific layers such as silicon oxides, cleaning residues left by previous steps, or enabling photolithography, where light-sensitive chemicals create patterned layers on the wafer. In short, chemicals are the primary consumable materials used to turn a blank silicon wafer into a complex integrated circuit (IC).

As the gate size of modern chips continues to shrink to just a few nanometres. Moore’s law observe this trend and captures as: the number of transistors in an IC doubles every year. As a result, the manufacturing process has become extremely sensitive to even the smallest contaminants. FABs therefore control an enormous range of microscopic factors. For example, airborne particles can cause fatal defects, so cleanrooms maintain extremely strict purity levels, sometimes allowing fewer than one particle of a few micrometres per cubic metre. The air pressure inside the FAB is kept higher than outside, so that clean air continuously flows outward rather than allowing contaminated air to enter.

Most of the chemicals used in these processes are toxic and must be handled under highly controlled conditions, often involving high temperature, high pressure, or isolation from the atmosphere. Operators never handle these chemicals directly. Instead, each tool in the FAB is connected to the factory’s chemical delivery system, and the chemical purity is monitored and maintained at multiple points. Each machine typically contains one or more chemical filters to ensure that incoming chemicals meet the purity requirements of the process.

My role was to conduct experiments on these in-tool chemical filters and to analyse their performance. I evaluated filters under different conditions and compared filters of different types, measuring quantities such as particle count and particle size to determine their filtering efficiency. The experiments were carried out in a specifically designed workspace in a chemical lab. The collected data was stored for later analysis, and I noticed that the data processing workflow was not well structured, which motivated me to propose improvements to the analysis pipeline.
