# This repository presents data analysing method predicting working schedule of a machine in quarrying factory.

In this repo, I'll briefly tell you about how we get the data and later focus on how we deal with it.

We use PZEM-004T sensors to track each load inside the machine (totally 3 of them). And sent the data keeping in cloud storage.

PZEM-004T module can measure 6 values from the machine motor including voltage, current, power, power factor, frequency, and energy
https://innovatorsguru.com/wp-content/uploads/2019/06/PZEM-004T-V3.0-Datasheet-User-Manual.pdf

In this tutorial I'll focus only on "voltage" and "current". There are so many obstacles applying IoT device with 3-phases electricity in the factory. The data won't be that smooth either. Here is some part of data:

![alt text](https://github.com/Elstargo00/machine-data-analysis/blob/main/somepart_data.png)

Yeahh, it's pretty ugly. There're a couple of reasons that we get such a mess data.

1. The data lose its significances via transfering process:
[PZEM-004T sensor] --> [Mega Arduino] --serial RX/TX serial communication--> [Node Mcu] --> [cloud storage] --> [frontend] --> [export as PDF]
2. We work with couple of team and it's not that consistency. The fun part is our initial data reading from the sensor started as float but end up becoming integer. Can you imagine how mess it is?
3. We have a huge knowledge gap to the motor/machine operating in the factory.

Let's just leave the problems behind and focusing on making progress.

## 1. How can we deal with the ugly data by not knowing anything about the machine or load inside?


Notice the value -1 in the table is just the logic behind implying that the "NaN" value has been sent from the sensor. We can interpret it as the machine is turning off. 
