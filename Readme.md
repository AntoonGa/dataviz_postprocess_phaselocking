
This repo contains a python version of the algorithm used in my old paper: 
"Constraints on bosonic dark matter from ultralow-field nuclear magnetic resonance"
published on Science Advances (DOI: 10.1126/sciadv.aax4539 ; https://www.science.org/doi/10.1126/sciadv.aax4539)

In short the algorithm switches the frequency-domain into a new frame of reference. The frame rotating at the carrier frequency. This enables canceling of the main carrier oscillation, while maintaining any modulation after averaging. This is basically a rotating frame approximation done on a coherent oscillating signal.

To do this, we perform post-processing phase-cycling to enhance the signal-to-noise ratio of our spectra. This technique involves incrementally shifting the phase of the spectra and averaging them together. By matching the phase shift to the phase accumulated by the oscillating field, we are able to coherently average the complex spectra and improve the SNR by a factor of N^1/2, where N is the number of transients. However, since the dark matter Compton frequency is unknown, we have to repeat this operation with many different phase increments.

![ezcv logo](https://www.science.org/cms/10.1126/sciadv.aax4539/asset/36b0d935-6949-4b6c-adcb-f5a8770d0bdb/assets/graphic/aax4539-f2.jpeg)

