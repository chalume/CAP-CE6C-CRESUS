# CAP-CE6C-CRESUS

CAP-CE6C PCB evolution to be used for CRESUS application. 
The limitation of the CE6c PCB for CRESUS application is the expected count rate on summed crystals that would probably saturate the system.

- 7 MCUs :
MCU 1 : CANID, GAIN, histo 6 channels, SPI master for DAC control, SPI master for digipot control, SPI master for histo/counting control and readout.
MCU2-7 : SPI slave : Histo/counting control and readout
-6x inverting amp and peak detector

Process modification : 
Start/stop functions direct porting to SPI.
DAC and digipot functions remain only on MCU1.
Trigg level can now be controlled individually (modification needed on the application).
Read histogramm : Histogram are transfered completely through SPI before sending on CAN.
Read counting : countings are transfered through SPI before sending on CAN.

Other possible modification, to be discussed : 
An interrution is generated on each incoming signal. at very high rate, it could interfere with core code execution. A modification form interrupt initiation of the acquitions to I/O monitoring would have less impact on the core execution, but would introduce dead time in the process. This is a soft only topic.
