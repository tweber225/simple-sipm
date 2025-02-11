# simple-sipm

[![DOI](https://zenodo.org/badge/331415388.svg)](https://doi.org/10.5281/zenodo.14853177)

Silicon PhotoMultipliers (SiPM), also called Multi-Pixel Photon Counters by Hamamatsu, are a game-changing technology for high-sensitivity photon detection. They are essentially an array of tiny avalanche photodiodes. Geiger mode operation ensures each detected photoelectron produces a virtually identical current pulse. They stand to replace older, vacuum tubed-base photomultipliers in applications such as laser scanning microscopy. You can find plenty of information about the virtues of these devices many places on the internet.

Here, I am posting a quick and simple 1"-round PCB to house a Hamamatsu S14420-series SiPM with onboard transimpedance amplification. I mainly used this with the 1.5 mm diameter, 50 um cell size S14420 variant for confocal microscopy. The SiPM has an intrinsically slow fall time—about 50 ns. This was adequate for my application, but note that faster designs also exist: [OpenSiPM](https://github.com/OpenSiPM/sipm-bias-control), [Thorlabs products](https://www.thorlabs.com/newgrouppage9.cfm?objectgroup_id=15959).

Picture of the completed circuit mounted in a standard 1" lens tube:

![Completed PCB front](https://github.com/tweber225/simple-sipm/blob/main/media/completed.jpg?raw=true)


## Board & Components:
- https://oshpark.com/shared_projects/mHE8cHZ9
- D1: Hamamatsu S14420 series (see datasheet for options)
- U1: Texas Instruments OPA847IDBVR (SOT23-6 package)
- J1: Hirose DF13-5P-1.25DSA (mating socket: DF13-5S-1.25C)
- J2: Linx Technologies CONSMA001-C-G
- R1,2: 10 Ω, 0603
- R3,4: 1 kΩ, 0603
- R5: 50 Ω, 0603
- C1,2: 1 uF, 1206 (make sure to choose 100 V rating here)
- C3: 0.1 uF, 0603
- C4: 1 uF, 0603
- C5: 6.2 pF, 0603
- C6,7: 0.1 uF, 0603
- C8,9: 4.7 uF, 1206

## Circuit diagram
![circuit diagram](https://github.com/tweber225/simple-sipm/blob/main/media/circuit.PNG?raw=true)

## Comments:
- Please pay special attention to the intended polarity of the HV input (should be *negative*)
- Along with HV (for diode bias, 40-50V), you will need to provided +/-5V.
- I chose 0603 and larger SMD components to facilitate easy hand soldering. Still, you will probably need very fine solder wire, a fine solder tip, plenty of flux, and some binocular magnification. Also don't drink coffee just before.
- The OPA847 is overkill for this applicaiton. You can probably use a cheaper opamp.
- Special thanks to Prof. M. Giacomelli. His well-documented project (https://github.com/OpenSiPM/sipm-bias-control) was an inspiration for this design. It also contains some helpful fabrication tips.

## Bonus images
<img src="https://github.com/tweber225/simple-sipm/blob/main/media/back.jpg?raw=true" width="400"> <img src="https://github.com/tweber225/simple-sipm/blob/main/media/close%20up.jpg?raw=true" width="400">
<img src="https://github.com/tweber225/simple-sipm/blob/main/media/really%20close%20up.jpg?raw=true" width="400"> <img src="https://github.com/tweber225/simple-sipm/blob/main/media/single%20photon%20pulses.PNG?raw=true" width="400">

Single photon response function for S14420-1550MG + my amplification circuit

![circuit diagram](https://github.com/tweber225/simple-sipm/blob/main/media/-1550MG%20response.png?raw=true)


