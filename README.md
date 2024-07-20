# inverter
# inverter-design-and-analysis-using-sky130pdk  
MOTIVE: to experiment with the working of an inverter understand all its parameters and get hands-on practice with open-source design tools.  

TOOLS : XSCHEM, NGSPICE, MAGIC, NETGEN   

Description: The project encompasses the complete design flow, from initial schematic creation to layout implementation and performance evaluation through simulation.

Key Skills Demonstrated :
>Schematic capture using Xschem
>Layout design with Magic (with minimum area and zero DRC)
>Circuit simulation and analysis using NgSpice(using .spice language for simulations)
   1. Voltage transfer characteristic (VTC) analysis
   2. Power consumption analysis
   3. Propagation delay and rise-time & fall-time delay analysis
---

#Project Structure:
- [1. schematic](#1-schematic)
  - [1.1 symbol](#11-symbol)
  - [1.2 testbench](#12-testbench)
- [2. Analysis of INVERTER models](#2-Analysis-of-INVERTER-models)
  - [2.1 General VTC analysis](#21-General-VTC-analysis)
  - [2.2 delay analysis ](#22-delay-analysis)
  - [2.3 Power analysis](#23-power-analysis)
- [3. layout](#2-layout)
---
##schematic 
>My project starts with a schematic.		
>>I take nfet_01v8 and pfet_01v8 and connect their gate, drain, and source with i/p & o/p pins,name pins correctly.

HERE IS THE IMAGE:
![image](https://github.com/Devyani-EC/inverter-/blob/main/Screenshot%20(41).png)
---
##symbol
> Now I create a symbol file by pressing "A" on the keyboard, in that file I create a visual representation of the inverter.
> HERE IS IT :
![image](https://github.com/Devyani-EC/inverter-/commit/ef2a019d14b763fa7327d418fd28dd1457323953#diff-c06faeada9d0f665ff37cb2994fe91ad17506e3a7d15514ffacc90aa30e2ed0a)
