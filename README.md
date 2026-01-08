# Aethra

Aethra is a co-creative musical system developed in Pure Data (Pd) that redefines the relationship between a live performer and "fixed" electroacoustic media. By leveraging the RAVE (Real-time Audio Variational AutoEncoder) model, Aethra transforms static audio files—such as a pre-recorded tape or electronic score—into a dynamic, navigable 16-dimensional latent manifold.

This system allows performers to engage in a real-time dialogue with the electronic component, navigating through timbral and structural variations using motion-aware sampling and distance-based logic.

## Core Features

* Dynamic Latent Navigation: Move beyond linear playback. Aethra uses a one-knob control interface ($C$ value) to steer the synthesis from absolute fidelity to the original score ($C=0$) toward radical structural and timbral deviation ($C=1$).
* Motion-Aware Sampling: The system identifies and generates musical variations based on a taxonomy of Parallel, Oblique, and Contrary motions, ensuring that the electronic response remains morphologically consistent with the performer’s gestures.
* Neural Interaction via py4pd: Built using the py4pd library, Aethra seamlessly integrates Python-based machine learning (NumPy, SciPy, HMMlearn) into the real-time Pure Data environment.
* Custom Pd Objects:
  * py.load_latent: Initializes and manages the high-dimensional latent space.
  * py.coreChoice: A decision engine that implements k-Nearest Neighbors (k-NN) and Hidden Markov Models (HMM) for predictive navigation.
* Real-time Visualization: Integrated support for TouchDesigner (or other OSC real-time visualization tools) to provide visual feedback of latent space activations, offering a multisensory experience of the co-improvisation process.

## Technical Architecture

Aethra utilizes the py4pd objects to host and manipulate the latent space projections of RAVE models' fixed audio tapes within Pure Data. The navigation logic is abstracted into a "topological map" where Euclidean and Cosine distances determine the proximity of sampled units. To maintain musical flow during high-divergence navigation, the system employs Trajectory Alignment, preventing the rhythmic and timbral artifacts often found in standard concatenative synthesis.

## Use Cases

Aethra was first premiered in the performance "Echoes of the Unseen," where it acted as an autonomous improvisational partner for tenor saxophone, based on a reinterpretation of Jesús Villa-Rojo’s Lamento. 
It is also designed for:

* Mixed Music Performance: Liberating the performer from the "click-track" constraint of traditional tape pieces.
* Jazz Co-Improvisation: Navigating standard corpora to provide stylistically aware accompaniment.
* Sound Design: Exploring the latent intersections in a fixed soundscape to generate real-time, adaptive soundscapes.

##  Requirements

* Pure Data (compiled with py4pd support, at version 1.0.2), tested on PD version 0.56.2

### Library requirements - pd
cyclone
else
list-abs (https://github.com/pd-externals/list-abs/tree/master)
py4pd -> 1.0.2

* Python 3.13 (with numpy, pandas, scipy, scikit-learn, and hmmlearn, installed within the patch)

## Instructions

### 1st Time Only
1. Download the list-abs library and put the list-abs folder in Aethra-PD/dependencies
2. Install remaining Pure Data Libraries (Deken)
3. Restart Pure Data
4. Open aethra.pd
5. Install Python Libraries (within the patch, first option on configurations)
6. Restart Pure Data

### On Running Patch
1. Open aethra.pd
2. Toggle a configuration for pre-prepared ones
3. In the window for latent dimensions weights, put every slide to 1
4. Toggle the volume of output to start DSP
5. Toggle microphone (Optional for instrumental input)
6. Click on Start
    - By default, it starts from event 0
    - You can change by setting the value in the input box next to Start Playing
    - If you pause, it will retain the last value; otherwise, it will start from the set value
7. Toggle closeness values to start deviating from the original:
    - By default, the navigation strategy is set to HMM, andthe  event is chosen from the jump event
    - You can change these settings whenever you want while the system is running
    - You can also change the interval between event jumps for more coherence, using the option segment length

## Creating Configurations - New Audios and Latent Spaces

TODO
_____________________________________________________________________________
_Aethra is part of ongoing research into the explainability of latent spaces and the development of "mutable works" in the post-digital era._
