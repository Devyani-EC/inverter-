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
  - [2.2 noise margin ](#22-noise-margin)
  - [2.3 delay analysis ](#22-delay-analysis)
  - [2.4 Power analysis](#23-power-analysis)
- [3. layout](#2-layout)
---
## 1. schematic 
>
My project starts with a schematic.
>		
 I take nfet_01v8 and pfet_01v8 and connect their gate, drain, and source with i/p & o/p pins,name pins correctly.
**Here is it:**
![image](https://github.com/Devyani-EC/inverter-/blob/main/Screenshot%20(41).png)

### 1.1 symbol
 Now I create a symbol file by pressing "A" on the keyboard, in that file I create a visual representation of the inverter.
>
  #IMPORTANCE:
 This is important as in the parent hierarchical development we did have to create an inverter from scratch we can simply add its symbol.
>
It is also important for representation purposes.      
**HERE IS IT:**  
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(42).png)

### 1.2 testbench
>
Now I create a new testbench file "inverter_test"
>
 In this, I added a symbol that I just created.   
 
Also add voltage sources "vin" "vdd", and code-window.

**Here is it:**   
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(55).png)
---
## 2. Analysis of INVERTER models
as I created the testbench file, now it's time  for analysis of the schematic
First I create a spice netlist.
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(45).png)

After a successful netlist generate a simulation.
Simulation should appear errorless.
   1. by using the >display> command we can see the plots there available.

### 2.1 General VTC analysis
#### Q.why vtc analysis? 
  --- From vtc we can tell whether the inverter is strong p or n, it is useful in "noise analysis".--- 
  
here "dc" simulation is needed.     
first I calculate the **VM** point in the vin vs vout graph.  
here vdd is 1.8 which is max, therefore vm should be 0.9. if there is too much deviation, in that case, we face a noise margin effect.
#### for WIDTH(P)=2
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(49).png)

now I am proving the theory of "VM" THAT if I increase "VM" then the graph should shift right.
#### for WIDTH(P)=2.5
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(47).png)
for perfect 0.9 WIDTH(P) SHOULD BE =>3 >> best noise margin

## 2.2 noise margin 
FOR NOISE MARGIN : I split the output(vout) wave into three parts by using the concept of gain   
gain = dvout/dvin .    
 first, i get the "gain=1" region.  
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(50).png)

GAIN VS VOUT

![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(52).png)

VIL(INPUT LOW) > The highest low input voltage FOR my inverter is 0.743V   
VLH(INPUT HIGH) >lowest high input voltage for my inverter is 0.980V
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(54).png)

## 2.3 Delay analysis 
for delay analysis "transient" analysis is needed.
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(56).png)  

**delay** = propagation delay + rise/fall time delay  
to reduce delay there are some techniques:

                                   1. increase power supply
                                   2. Reduce load capacitance 
                                   3. increase width
                                   
#### 1. Propagation delay
  Time for input change to be reflected on output OR  time needed for 50% of i/p value to 50% of o/p value     
 -> 'Tphl' & 'Tplh'   
 -> It has a dependency on the clock signal and input signal.
 ![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(58).png)

![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(60).png)
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(61).png)


![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(62).png)  
#### 2.Rise/fall time delay 
   It is independent  of  input signal time, it's a measure of time for which output goes from 10% to 90% of value.  
   there are many equations but majorly I can say that this delay comes due to two types of CAPACITANCE :  
                                                                                                    
         1. unloaded capacitance
         2. loaded capacitance 
#### 1. unloaded capacitance 
   the rise time(tr) delay & fall time(tf) delay :
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(81).png)   

1. increase power  >> Here I already give the maximum voltage 1.8v so, now I reduce it to 1v   
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(65).png)   

3. increase the width of inverter  >> pfet--- 2 to 4 & nfet--- 1 to 2
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(84).png)
as we can see here there is  not much change in tr & tf because is ratio of width remains the same at 2:1 so there is no effect on unloaded capacitance. c increases with width.
        
#### 2. Loaded capacitance 
Here we include 0.5p F of capacitance   
 ![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(71).png)
 now take a look at a graph of vout vs vin.  
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(72).png)  
here is the delay calculation: here width of pfet & nfet is 4 & 2.
![image](https://github.com/Devyani-EC/inverter-/blob/new-branch/images1/Screenshot%20(76).png)

