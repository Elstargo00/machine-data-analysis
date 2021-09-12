# This repository presents data analysing method predicting working schedule of a machine in quarrying factory.

In this repo, I'll briefly tell you about how we get the data and later focus on how we deal with it.

We use PZEM-004T sensors to track each load inside the machine (totally 3 of them). And sent the data keeping in cloud storage.

PZEM-004T module can measure 6 values from the machine motor including voltage, current, power, power factor, frequency, and energy. 
https://innovatorsguru.com/wp-content/uploads/2019/06/PZEM-004T-V3.0-Datasheet-User-Manual.pdf. In this tutorial I'll focus on "voltage" and "current". 

There are so many obstacles applying IoT device with 3-phases electricity in the factory. The data won't be that smooth either. Here is some part of data:

<img src="https://github.com/Elstargo00/machine-data-analysis/blob/main/somepart_data.png" width="800" height="400">

The data shown the voltage and current sending by IoT device that've been installed with the machine R1L1-S1. Yeahh, it's pretty ugly. There're a couple of reasons that we get such a mess data.

1. The data lose its significances via transfering process:
[PZEM-004T sensor] --> [Mega Arduino] --RX/TX serial communication--> [Node Mcu] --> [cloud storage] --> [frontend] --> [export as PDF]
2. We work with couple of team and it's not that consistency. The fun part is our initial data reading from the sensor started as float but end up becoming integer. Can you imagine how mess it is?
3. We have a huge knowledge gap to the motor/machine operating in the factory.

Let's just leave the problems behind and focusing on making progress.

## How can we deal with the ugly data by not knowing anything about the machine or load inside?
### Our goal is to get "machine working schedule"

Let's take a quick look at the data.
Notice the value of -1 in the table is just the logic behind implying that the "NaN" value has been sent from the sensor. We can interpret it as the machine is turning off. There are cases that positive voltage comes along with zero current. From this we really don't know what happend with the data. The fact that we know there are two event classes including: "MACHINE IS ON" and "MACHINE IS OFF"

The analysing process have been described here:
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1vX9_k7IUAlyEpDuMpe55fUWbSmTmmpRN?usp=sharing)


Finally, we got the working schedule of the machine R1L1-S1 from non-perfect data.

<img src="https://github.com/Elstargo00/machine-data-analysis/blob/main/R1L1-S1_working_schedule.png?raw=true" width="1125" height="525">
