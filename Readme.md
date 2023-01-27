
# This repo contains a Python version of the data_viz algorithm designed in my old paper: 
"Constraints on bosonic dark matter from ultralow-field nuclear magnetic resonance"
published on Science Advances (DOI: 10.1126/sciadv.aax4539 ; https://www.science.org/doi/10.1126/sciadv.aax4539)


# What is this ?:
The algorithm performs a cute visualisation trick to help you recover the phase of a signal of an unknown frequency. Once that phase is recovered, you can infer the signal frequency. This is especially usefull is you are looking for weak signal and want to test your null hypothesis.
As I discovered later, it is essentially equivalent to entering a frame rotating at the signal frequency. If you are interested in knowning more have a look at the "rotating wave approximation" on wiki : https://en.wikipedia.org/wiki/Rotating-wave_approximation

Since many people seemed more interested in the algorithm itself rather than the actual subject of the paper I'm putting a short description of the algorithm in this repo. Please note that the notebook provided is not optimized and is only here to help you implement the algo in your own experiment. If you wish to know more about it, have a look at the supplementary materials of the paper or contact me.

# Context:
We were facing a frequency modulated signal, containing a carrier frequency (which contained no information) and a slow external modulation of unknown frequency (which we were interested in detecting: if the modulation was present, it could have been dark matter). The challenge was to figure out a way to average thousands of transient signals to increase the signal-to-noise ratio (SNR) of the modulation (appearing as sidebands in the spectra).

However, averaging in time domain or frequency domain simply averages down the sidebands, while increasing the SNR of the carrier. Which was exactly what we wanted to avoid.

In short the algorithm switches the frequency-domain frame into a new frame of reference. This enables canceling of the main carrier oscillation, while maintaining any modulation after averaging. As I figured out later, this is basically a rotating frame approximation done on a coherent oscillating signal.

To do this, we perform post-processing phase-cycling to enhance the signal-to-noise ratio of our spectra. This technique involves incrementally shifting the phase of the spectra and averaging them together. By matching the phase shift to the phase accumulated by the oscillating field, we are able to coherently average the complex spectra and improve the SNR by a factor of N^1/2, where N is the number of transients. However, since the modulation frequency is unknown, we have to repeat this operation with many different phase increments.

# The following illustration is taken from my paper in Sc. Adv.

![ezcv logo](https://www.science.org/cms/10.1126/sciadv.aax4539/asset/36b0d935-6949-4b6c-adcb-f5a8770d0bdb/assets/graphic/aax4539-f2.jpeg)
Fig. 2 Signal acquisition and processing schemes.
Top: Signal acquisition scheme with simulated spectra. After polarization, each transient acquisition starts following a magnetic π-pulse (corresponding to a 180° flip of the 13C spin along any direction). The external AC magnetic field’s phase varies between transient acquisitions (orange). As a result, the sidebands generally have different phases in each transient spectrum. Averaging the transients yields a spectrum in which the sidebands are destructively averaged out (purple). Shifting each transient by a phase equal to the external field’s accumulated phase restores the sidebands’ phase coherence, yielding a spectrum with high SNR sidebands (orange). For clarity, only one of the two Zeeman-split J-coupling peaks and its two sidebands are shown. Bottom: Result of the phase-shifting procedure for actual data. (A) Transients are averaged using 2001 phase increments and stacked into a two-dimensional plot. (B) Side view of (A); sidebands are rescaled by a factor 10 for clarity. (C) Averaging with φ = 0 rad corresponds to averaging the transients without phase shift; sidebands are averaged out and carrier peaks appear with maximum amplitude. When the optimal phase (for ω/2π = 0.73 Hz, φ = 2.93 rad) is approached, sidebands appear. These spectra were acquired in an experiment during which the AC field frequency and amplitude were set to 0.73 Hz and 0.24 nT. Transient acquisitions of 30 s were repeated 850 times with a time interval between each transient of τ = 61 s.

## The repo contains the core algorithm, the dataviz tool and a test case. Feel free to ask any question if you had any !:)



