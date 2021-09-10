# This repository presents data analysing method predicting working schedule of a machine in quarrying factory.

In this repo, I'll briefly tell you about how we get the data and later focus on how we deal with it.

We use PZEM-004T sensors to track each load inside the machine (totally 3 of them). And sent the data keeping in cloud storage.

PZEM-004T module can measure 6 values from the machine motor including voltage, current, power, power factor, frequency, and energy
https://innovatorsguru.com/wp-content/uploads/2019/06/PZEM-004T-V3.0-Datasheet-User-Manual.pdf

In this tutorial I'll focus only on "voltage" and "current". There are so many obstacles applying IoT device with 3-phases electricity in the factory. The data won't be that smooth either. Here is some part of data:

