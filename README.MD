Programmable Analog Monosynth
---------
Prototype
========
Digital Board
========

Digital board tested and working but there is some cross-talk on
potentiometer ADC channels. Allowing sufficient settling time at ADC node between reads seems to mostly remedy this
to <= 1 LSB.

============
Analog Board
============
DAC S&H tested and working. There is some cross-talk (<= 10mV) on adjacent CV traces, but these are currently floating. Need to test
for crosstalk again once CV targetsare installed.

Bugs discovered thus far:

1. 7905 power regular pin error. Power supply rendered useless by this, so board requires external supply
2. LFO DG408 demultiplexer address lines are not latched, making LFO source addressing useless. Need to add 74LC75
latch in next revision.
2. C107 S&H sample cap footprint is 0805, but there are no NP0 or film caps in this footprint. Currenty X7R is soldered
in place. 