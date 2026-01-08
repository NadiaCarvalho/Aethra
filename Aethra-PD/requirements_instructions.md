# Aethra

## Library requirements - pd
cyclone
else
py4pd -> 1.0.2

list-abs

## Instructions

### 1st Time Only
1. Download list-abs (https://github.com/pd-externals/list-abs/tree/master) and put folder on Aethra-PD/dependencies
2. Install Pure Data Libraries (Deken)
3. Restart Pure Data
4. Open aethra.pd
5. Install Python Libraries (within the patch, first option on configurations)
6. Restart Pure Data

### On Running Patch
1. Open aethra.pd
2. Toggle a configuration for pre-prepared ones
3. In the window for latent dimensions weights, put every slide to 1
4. Toggle the volume of output to start dsp
5. Toggle microphone (Optional for instrumental input)
6. Click on Start
    - by default, it starts from event 0
    - you can change by setting the value in the input box next to Start Playing
    - if you pause, it will retain the last value, otherwise it will start from the set value
7. Toggle closeness values to start deviating from original:
    - by default, navigation strategy is set to HMM and event is chosen from jump event
    - you can change these settings whenever you want while the system is running
    - you can also change the interval between event jumps for more coherence, using the option segment length

# Creating Configurations - New Audios and Latent Spaces
