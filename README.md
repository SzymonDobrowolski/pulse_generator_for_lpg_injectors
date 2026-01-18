# Pulse_generator_for_lpg_injectors
This is the project of pulse generator, which is desgined for cleaning **Tartarini** LPG injectors.
## Concept
Whole device is build on two NE555. One works as a master and is responsible for work time. Secoond IC sends signal to the incjector. 
Our injectors are (uzupełnić), with (uzupełnić) ohm impedancy.
## Analysis
We've provided analysis in LTspice. Default settings are:
- 5 minutes of working,
- 50 Hz in output of NE555.
If you would like to change any setting here's little guide:
- time changing -> (podać nazwy sygnałów),
- frequency changing -> (też podać nazwy).
## PCB
Project of PCB was made in Altium designer, but devices used in this device are co common, that you can easily make it in KiCad etc.
If you'd like to order PCB you have to download **gerber** files and send it to a factory such as JLCPCB.
## TEST

