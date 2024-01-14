# Regulated-Variable-Power-Supply
The objective of this project was to design and make a DC power supply that will convert an AC supply of 220V, using a step-down transformer, into a variable DC output from 1V to 30V. The low AC voltage is converted to pulsating DC voltage using a bridge rectifier. The pulsating DC voltage thus obtained contains ripples in the form of AC voltage. To remove these ripples a filter is needed which filters out the ripples from the DC voltage. A capacitor is placed in parallel to the output such that the capacitor (because of its impedance) allows high-frequency AC signals to pass through get bypassed to ground and low-frequency or DC signal is blocked. Thus the capacitor acts as a low-pass filter. The output produced from a capacitor filter is the unregulated DC voltage. To produce a regulated DC voltage a regulator is used which develops a constant DC voltage, while the output voltage is to be varied using a variable resistor. A filter capacitor was also used so that the rectified pulsating DC output would attain a nearly constant voltage before passing through the regulator, onto the load.  

A regulated power supply is an embedded circuit; it converts unregulated AC into a constant DC. A transformer is used to convert the voltage from the mains to a lower voltage. With the help of a rectifier, it converts the AC supply into a pulsating DC, followed by a filter, comprising one or more capacitors, and resistors to filter out (smooth) most of the pulsation. Its function is to supply a stable voltage (or less often current), to a circuit or device that must be operated within certain power supply limits.  

## Problem Statement  
Design and implement an inverter circuit to meet the following load specifications:  
- Current = 1 A
- Voltage= 220 V
- Sine wave having frequency = 50 Hz
- THD = 10%
- Overcharging protection of battery
- Design with minimal complexity is preferred

## Project Objectives  
- To design a regulated power supply that will give a variable output of 1V-30V.
- To design the power supply such that it will give 1A current at output
- To design a regulated power supply that will have a 10% ripple factor

## Block Diagram 
![image](https://github.com/izmanaveed/Regulated-Variable-Power-Supply/assets/59065717/06967e94-42b8-49e4-a03e-5d808e7a65b6)

## Components  
- LM317 Voltage Regulator
- Full wave bridge rectifier
- Filter Capacitor (4.7mF)
- 220-ohm resistor
- 5K variable resistor
- 12-0-12 transformer
- AC source
- Digital Voltmeter
- Metal box
- Knobs
- Switch
- Volume control

## Design Procedure 
![image](https://github.com/izmanaveed/Regulated-Variable-Power-Supply/assets/59065717/cb78ec07-de87-4d3e-8bfa-4b232f51906d)  
A step-by-step procedure has been taken to explain the above block diagram, block by block.  

### BLOCK 1: TRANSFORMER
A step-down transformer consists of two windings, namely primary and secondary windings where primary can be designed using a less-gauge wire with more number of turns as it is used for carrying low-current high-voltage power, and the secondary winding uses a high-gauge wire with less number of turns as it is used for carrying high-current low-voltage power. Transformers works on the principle of Faraday’s laws of electromagnetic induction.  

The step-down converters are used for converting the high voltage into low voltage. The converter with an output voltage less than the input voltage is called a step-down converter. 230V AC is converted into 24V AC using a step-down transformer. 24V output of the step-down transformer is an RMS value and its peak value is given by the product of the square root of two with an RMS value, which is approximately 34V.    

Calculations for primary and secondary coil for 12-0-12 transformer:  
V(primary)= 230 V(RMS)= 325.269V (pp)  
V(secondary)= 24V (RMS)= 33.94V (pp)  
(Vpri^2)/(Vsec^2)= (Lpri)/ (Lsec)  
100/1= Lpri/Lsec  
i.e. primary inductance value= 100, secondary inductance value= 1  

### BLOCK 2: FULL-WAVE RECTIFIER   
During the Positive half cycle of the input AC waveform diodes D1 and D2 are forward biased and D3 and D4 are reverse biased. When the voltage, more than the threshold level of the diodes D1 and D2, starts conducting – the load current starts flowing through it, shown as red lines in the diagram below.

![image](https://github.com/izmanaveed/Regulated-Variable-Power-Supply/assets/59065717/b71ba709-f29f-49dc-a3f7-c2643e51aaef)
![image](https://github.com/izmanaveed/Regulated-Variable-Power-Supply/assets/59065717/e53387e2-3958-4647-a06e-d8c32f49e20f)

During the negative half cycle of the input AC waveform, the diodes D3 and D4 are forward-biased, and D1 and D2 are reverse-biased. Load current starts flowing through the D3 and D4 diodes when these diodes start conducting as shown in the figure.  

We can observe that in both cases, the load current direction is the same, i.e., up to down as shown in the figure – so unidirectional, which means DC. Thus, by the usage of a bridge rectifier, the input AC is converted into a DC. The output at the load with this bridge wave rectifier is pulsating in nature, i.e. it contains pulses, but producing a pure DC requires an additional filter like a capacitor. The voltage drop across the diodes is (2*0.7V) = 1.4V;  therefore, the peak voltage at the output of this rectifier circuit is 32V (34-1.4) approx.  

### BLOCK 3: FILTER CAPACITOR
The output from an electronic rectifier circuit is technically direct current because all of the current flows in the same direction but it isn’t stable enough for most purposes. And that pulsing current isn’t suitable for most electronic circuits.  

That’s where filtering comes in. The filtering stage of a power supply circuit smoothes out the ripples in the rectified DC to produce a smooth direct current that’s suitable for even the most sensitive of circuits.  

Filtering is usually accomplished by introducing a capacitor into the power supply circuit. Here, the capacitor is simply placed across the DC output.  

A capacitor has the useful characteristic of resisting changes in voltage. It accomplishes this by building up a charge across its plates when the input voltage is increasing. When the input voltage decreases, the voltage across the capacitor’s plates decreases as well, but more slowly than the input voltage decreases. This has the effect of leveling out the voltage ripple.  

The difference between the minimum DC voltage and the maximum DC voltage in the filtering stage is called the voltage ripple, or just ripple, which is usually measured as a percentage of the average voltage. For example, a 10% ripple in a 30 V power supply means that the actual output voltage varies by 3 V.  
The filter capacitor must usually be large to provide an acceptable level of filtering. The bigger the capacitor, the lower the resulting ripple voltage.  

Capacitor Calculations are as follows:  
Vin= 33.94-1.4= 32.54V  
r= Vr(pp)/Vdc --------- 1  
Vdc= 0.63Vm  
=0.63(32.54)  
=20.5V  
Using eq1  
(r) x (Vdc)= Vr(pp)  
20.5 x 0.1= 2.05= Vr(pp)  
Now,  
Vr(pp)= (1/fRlC) Vm  
= (32.54)/ (100 x 32.54 x 2.05)    
=4.8mF   
Thus, a Polar capacitor of 4.8m or 4800uF has been used.  

### BLOCK 4: VOLTAGE REGULATOR (LM317)  
To maintain a steady voltage level regardless of the amount of current drawn from a power supply, the power supply can incorporate a voltage regulator circuit. The voltage regulator monitors the current drawn by the load and increases or decreases the voltage accordingly to keep the voltage level constant.  

Here we require to have a voltage of 1V-30V at 1A with positive polarity of the output voltage. For this reason, we need a regulator which can provide an output voltage of up to 30V. An ideal and efficient choice would be the regulator IC LM317 which has a minimum output voltage of 1.2V and a maximum output voltage of up to 37V.  

Our next requirement is to calculate the input voltage requirement for the regulator. For a regulator, the minimum input voltage should be the output voltage added by a value of three. In that case, here to have a maximum voltage of 30V, we need a minimum input voltage of 33V.   

The 5K variable resistor is connected with the Adjust pin of the LM317. The resistor is used to vary the output voltage.  

The calculation for the value of the variable resistor is as follows:  
Vdc= 1.25 x (1+ R1/R2)  
Given that Vdc= 30V and R2= 220 ohm  
30= 1.25 x (1+ R1/R2)  
R1= 23 x 220= 5060 ohm (calculated)  
R1= 5000 ohm (used)  

## Working 
![image](https://github.com/izmanaveed/Regulated-Variable-Power-Supply/assets/59065717/29e70b20-d355-4bbf-8608-f878e7dffdd4)  

The circuit is connected as follows:  
- The primary coil of the transformer is connected to the AC supply source.
- The secondary coil is connected at 2 nodes of the rectifier bridge.
- The two n-sides of the diode are connected to the positive of the filter capacitor
- The two p-sides are connected with the ground.
- The positive terminal of the filter capacitor is connected with the Input terminal of LM317.
- The Adjuster is connected to the 5K variable resistor.
- The Output pin of LM317 is connected to a 220-ohm resistor.

## Hardware Implementation
![image](https://github.com/izmanaveed/Regulated-Variable-Power-Supply/assets/59065717/94b67e9e-d079-449f-b829-c7b0dbcc7dbe)
![image](https://github.com/izmanaveed/Regulated-Variable-Power-Supply/assets/59065717/3b526007-b96f-4a0f-a742-eda4859d89d9)  

## Problems Faced  
- During the etching process the parts of the circuit that were not covered by the permanent marker had its coper removed, thus, hampering the conduction of the circuit.
- The imprint of the butter paper was not completely transferred on the PCB board so we had to darken the imprints using a permanent marker.
- After the soldering process, the PCB circuit was not functioning properly so the whole circuit had to be de-soldered.
- During resolding the solder wire was not sticking to the circuit again due to the desold paste used during desolding. All this had fairly affected the copper of the PCB around the component holes.
- The 5K variable resistance had to be soldered very carefully because its resistance increased every time it got heated by the soldering iron which in turn changed the voltage range of the whole power supply itself.

## Conclusion  
We can conclude this project report with the observations that a minimum output voltage of 1.2V and a maximum output voltage of 30.9V. The ripple factor obtained was 8%. 
![image](https://github.com/izmanaveed/Regulated-Variable-Power-Supply/assets/59065717/e19e58b3-9515-41b7-8014-80b4b8252bb1)
