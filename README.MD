=============================
Programmable Analog Monosynth
=============================
Prototype 
-------------
Digital Board
-------------

Digital board tested and working. SPI LED driving and switch reading tested. ADC pot reading but there is some cross-talk on
potentiometer ADC channels. Allowing sufficient settling time at ADC node between reads seems to mostly remedy this
to <= 1 LSB.

------------
Analog Board
------------
DAC S&H tested and working. There is some cross-talk (<= 10mV) on adjacent CV traces, but these are currently floating. Need to test
for crosstalk again once CV targets are installed.

NOISE/LFO/S&H tested and working, except for multiplexer latch problem mentioned below. Noise gain needed to be adjusted by
changing R180 to 10K and R181 to 750K (two 1.5M 0603s stacked in parallel). Also LFO module needede R3 (on module board) changed to 270K from 1M to get proper adjustment of sine/tri symmetry.
Sine symmetry is too 'pointy' on negative transition. Perhaps D1 and D2 need to be matched for Vf?

Bugs discovered thus far:

1. 7905 power regular pin error. Power supply rendered useless by this, so board requires external supply
2. LFO DG408 demultiplexer address lines are not latched, making LFO source addressing useless. Need to add 74LC75
latch in next revision.
2. C107 S&H sample cap footprint is 0805, but there are no NP0 or film caps in this footprint. Tried X7R and there was too much
droop. Through-hole film cap is in there now and droop is better, but still about 50-60 mV per second.