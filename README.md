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
## 1. schematic 
My project starts with a schematic.		
I take nfet_01v8 and pfet_01v8 and connect their gate, drain, and source with i/p & o/p pins,name pins correctly.

HERE IS THE IMAGE:
![image](https://github.com/Devyani-EC/inverter-/blob/main/Screenshot%20(41).png)
---
## 1.1 symbol
 Now I create a symbol file by pressing "A" on the keyboard, in that file I create a visual representation of the inverter.
>
  #IMPORTANCE:
 This is important as in the parent hierarchical development we did have to create an inverter from scratch we can simply add its symbol.
>
It is also important for representation purposes.


HERE IS IT :
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(42).png)

## 1.2 testbench
>
 Now I create a new testbench file "inverter_test"
> 
 In this, I added a symbol that I just created.
> 
Also add voltage sources "vin" "vdd", and code-window.

HERE IS IT :
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(55).png)
---
## 2. Analysis of INVERTER models
as I created the testbench file, now it's time  for analysis of the schematic
First I create a spice netlist.
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(45).png)

After a successful netlist generate a simulation.
Simulation should appear errorless.
   1. by using the >display> command we can see the plots there available.

## 2.1 General VTC analysis
##Q.why vtc analysis? 
  >>> From vtc we can tell whether the inverter is strong p or n, it is useful in "noise analysis".

here I do "dc" simulation. 
first I calculate the ##"VM" point in the vin vs vout graph.
here vdd is 1.8 which is max, therefore vm should be 0.9. if there is too much deviation, in that case, we face a noise margin effect.
![image](




