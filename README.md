# QPSK-Demodulation-Signal-Recovery-Analysis
This repository documents an experiment on the full demodulation of a Quadrature Phase Shift Keying (QPSK) signal. The primary goal is to demonstrate how a complex modulated signal is split into In-phase (I) and Quadrature (Q) components to recover the original serial data stream.

## TABLE OF CONTENTS
* [Part 1: The Demodulation Core (I/Q Separation)](#1-the-demodulation-core-iq-separation)
* [Part 2: Signal Conditioning & Recombination](#2-signal-conditioning--recombination)
* [Part 3: Constellation & Noise Analysis](#3-constellation--noise-analysis)
* [Results & Data Analysis](#results--data-analysis)

## Overview
Quadrature Phase Shift Keying (QPSK) is a bandwidth-efficient modulation scheme that transmits two bits of digital information per symbol by varying the phase of a carrier wave. This experiment focuses on the coherent demodulation process, where a complex, multi-phase signal is decomposed into its constituent In-phase ($I$) and Quadrature ($Q$) components to reconstruct the original high-speed serial data.

## 1. The Demodulation Core (I/Q Separation)
The recovery process relies on the orthogonality of sine and cosine waves. The implementation was achieved using the following hardware stages:
- The Local Carrier: A $100\text{ kHz}$ sine wave was split into two paths. One path was phase-shifted by $90^\circ$ to create the Quadrature carrier ($\sin$), while the other remained at $0^\circ$ for the In-phase carrier ($\cos$).
- Product Detection: The incoming QPSK signal was fed into two separate Multiplier modules:
  - I-Channel: Multiplied the signal by the $0^\circ$ carrier.
  - Q-Channel: Multiplied the signal by the $90^\circ$ carrier.
- Mathematical Isolation: Because the carriers are orthogonal, the I-multiplier rejects the Q-data, and the Q-multiplier rejects the I-data, effectively isolating the two parallel bitstreams.

#### **1.1 The Demodulation Core (I/Q Separation) Experimental Diagrams**
<details>
<summary>View Part 1.1 Diagrams</summary>

![Calibration Waveform](Diagrams/FM_Modulation_Demodulation/IMG_4314.jpg)
*Figure 1.1.1: The Demodulation Core (I/Q Separation) Setup.*

</details>

#### **1.2 The Demodulation Core (I/Q Separation) Experimental Results**
<details>
<summary>View Part 1.2 Documentation</summary>

![Calibration Waveform](Waveform_Captures/FM-Modulation-Demodulation/9.2.jpg)
*Figure 1.2.1: The Demodulation Core (I/Q Separation) Signal*

</details>

## 2. Signal Conditioning & Recombination
Once the components were separated, they required processing to return to a digital format:
- Filtering: Low-Pass Filters (LPFs) were used at the output of each multiplier to remove the $200\text{ kHz}$ sum-frequency components, leaving only the baseband $I$ and $Q$ pulses.
- Parallel-to-Serial Conversion: The recovered $I$ and $Q$ bits were fed into a 2-bit P/S Converter. Controlled by the system clock, this module interleaves the bits to reconstruct the original serial bitstream.
- Phase Sensitivity: A critical observation was made regarding phase alignment; a phase error of $\Delta\phi = 90^\circ$ in the local carrier resulted in total signal loss, demonstrating the high precision required for coherent detection.

#### **2.1 Signal Conditioning & Recombination Experimental Diagrams**
<details>
<summary>View Part 2.1 Diagrams</summary>

![Calibration Waveform](Diagrams/FM_Modulation_Demodulation/IMG_4314.jpg)
*Figure 2.1.1: Signal Conditioning & Recombination Setup.*

</details>

#### **2.2 Signal Conditioning & Recombination Experimental Results**
<details>
<summary>View Part 2.2 Documentation</summary>

![Calibration Waveform](Waveform_Captures/FM-Modulation-Demodulation/9.2.jpg)
*Figure 2.2.1: Signal Conditioning & Recombination Signal*

</details>

## 3. Constellation & Noise Analysis
To evaluate signal integrity, the system was analyzed in the Vector domain:
- Constellation Mapping: By switching the oscilloscope to XY Mode (I-channel to X, Q-channel to Y), the four phase states were visualized as distinct points in the complex plane.
- Noise Impact: Using the Adder module, Additive White Gaussian Noise (AWGN) was introduced. This resulted in "clustering" or spreading of the constellation points, visually representing the increase in Bit Error Rate (BER) as the Signal-to-Noise Ratio (SNR) decreased.

#### **3.1 Constellation & Noise Analysis Experimental Diagrams**
<details>
<summary>View Part 3.1 Diagrams</summary>

![Calibration Waveform](Diagrams/FM_Modulation_Demodulation/IMG_4314.jpg)
*Figure 3.1.1: Constellation & Noise Analysis Setup.*

</details>

#### **3.2 Constellation & Noise Analysis Experimental Results**
<details>
<summary>View Part 3.2 Documentation</summary>

![Calibration Waveform](Waveform_Captures/FM-Modulation-Demodulation/9.2.jpg)
*Figure 3.2.1: Constellation & Noise Analysis Signal*

</details>

## Results & Data Analysis
**[View or Download Complete Experimental Question and Answers (PDF)](Data/Q&A-Telecommunications-Engineering-Modular-Analysis-of-Analog-FM-and-Digital-PCM-Architectures-.pdf)**

## Project Resources
For full access to the raw datasets, formulas, and the complete Q&A worksheet, please use the links below:

* **[Download Complete Experimental Q&A (PDF)](Data/Q&A-Telecommunications-Engineering-Modular-Analysis-of-Analog-FM-and-Digital-PCM-Architectures-.pdf)**
* **[Browse All Captured Documentation](Waveform_Captures/)**
