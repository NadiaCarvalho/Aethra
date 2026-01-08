# Aethra

Aethra is a co-creative musical system developed in Pure Data (Pd) that redefines the relationship between a live performer and "fixed" electroacoustic media. By leveraging the RAVE (Real-time Audio Variational Autoencoder) model, Aethra transforms static audio files—such as pre-recorded tapes or electronic scores—into a dynamic, navigable 16-dimensional latent manifold.

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

##  System Requirements

### Pure Data Environment
* Pure Data Distribution: Tested and verified on Pd version 0.55.0 or higher.
* Py4PD Support: Requires py4pd version 1.0.2 or later, properly compiled, and added to your Pd search paths.

#### Library Dependencies (Pd Externals)
To ensure the patch functions correctly, the following libraries must be installed via the Deken package manager or added manually to your /dependencies folder:

* cyclone: For various Max/MSP-style object compatibility.
* else: Required for advanced UI elements and processing utilities.
* list-abs: Required for list processing.

Note: If not available via Deken, download manually from the list-abs GitHub repository and place the folder into Aethra-PD/dependencies.

### Python Environment
Aethra utilizes a Python backend for processing high-dimensional data. The following environment is required:

* Python Version: Python 3.13 (Py4PD v1.0.2 requirement)
* Core Libraries:
 * numpy & pandas: For latent space data structures and matrix operations.
 * scipy & scikit-learn: For distance calculations and manifold navigation.
 * hmmlearn: For the HMM predictive navigation.

Note: These libraries can be installed automatically using the "Install Python Libraries" button within aethra.pd configuration panel.

## Setup & Usage Guide

### First-Time Configuration
1. Install Dependencies: Download the list-abs library and place the folder into Aethra-PD/dependencies.
2. Add Libraries: Use the Pure Data Deken package manager to install any remaining missing libraries.
3. Restart Pure Data to ensure all paths and external objects are correctly initialized.
4. Python Environment: Open aethra.pd, select the Configurations tab, and click the first option to automatically install the required Python libraries.
5. Finalize: Restart Pure Data to ensure all Python libraries are correctly initialized.

### For Every Running Patch
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
    - By default, the navigation strategy is set to HMM, and the event is chosen from the jump event
    - You can change these settings whenever you want while the system is running
    - You can also change the interval between event jumps for more coherence, using the option segment length

### Running the System

1. Initialize Patch: Open aethra.pd and select a pre-prepared configuration toggle.
2. Weight Latent Dimensions: In the Latent Dimensions Weights window, initialize the system by setting every slider to 1.
3. Enable Audio: Toggle the Output Volume to start the DSP engine. If using a live instrument, toggle the Microphone input.
4. Playback Control: Click Start to begin the performance.
   * The system begins at Event 0 by default.
   * To start from a specific point, enter the event number in the box next to Start Playing.
   * If paused, the system retains its position; otherwise, it resumes from the manually set value.
5. Live Navigation & Deviation: Toggle the Closeness Value ($C$) to begin deviating from the original score.
   * Strategy: The system defaults to HMM for navigation.
   * Real-time Control: You can switch strategies or adjust the Segment Length (the interval between event jumps) on the fly to increase or decrease musical coherence.

## Troubleshooting & Common Fixes

If you encounter issues during your first run, check the following common solutions:

### Initialization & Pathing
* Missing py.load_latent or py.coreChoice: This indicates that Py4PD is not properly installed or its path is not set in File -> Preferences -> Path. Ensure the py4pd folder is visible to Pd.
* No method for 'pip': This usually means you are running an older version of py4pd. Update to v1.0 via Deken or follow the terminal installation method mentioned in the technical documentation.

### Python Environment
* Library Import Errors: If the internal Python install fails, manually run pip install numpy pandas scipy hmmlearn in your system terminal.
* Model Loading: Ensure your latent space and HMM models are placed in the /models directory within the Aethra folder. The system will look for them there by default.

### Audio & Performance
* Crackling or High Latency: Check your Audio Settings in Pure Data. A buffer size of 256 or 512 is recommended for stability.
* No Sound in either mode with closeness above .05: Ensure the pd_distances and pd_HMMmodel variables have been successfully initialized by clicking one of the Load Configuration buttons once before starting playback.

## Creating Configurations - New Audios and Latent Spaces

TODO
_____________________________________________________________________________
_Aethra is part of ongoing research into the explainability of latent spaces and the development of "mutable works" in the post-digital era._
