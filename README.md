# A Comparative Analysis between 6T and a proposed 8T SRAM

## Table Of Contents
- [SRAM Design](https://github.com/satabdi25-2000/vlsilab8TSRAM#sram-design)
  - [6T SRAM](https://github.com/satabdi25-2000/vlsilab8TSRAM#6T-SRAM)
  - [8T SRAM](https://github.com/satabdi25-2000/vlsilab8TSRAM#8T-SRAM)
- [Stability Analysis of 6T and 8T](https://github.com/satabdi25-2000/vlsilab8TSRAM#Stability-Analysis-of-6T-and-8T)
  - [Read Stability](https://github.com/satabdi25-2000/vlsilab8TSRAM#Read-Stability)
  - [Write Stability](https://github.com/satabdi25-2000/vlsilab8TSRAM#Write-Stability)
- [Proposed 8T SRAM Cell](https://github.com/satabdi25-2000/vlsilab8TSRAM#Proposed-8T-SRAM-Cell)
  - [PreLayout Simulations](https://github.com/satabdi25-2000/vlsilab8TSRAM#PreLayout-Simulations)
  - [PostLayout Simulations](https://github.com/satabdi25-2000/vlsilab8TSRAM#PostLayout-Simulations)
- [Future Works](https://github.com/satabdi25-2000/vlsilab8TSRAM#Future-Works)
- [Acknowledgements](https://github.com/satabdi25-2000/vlsilab8TSRAM#Acknowledgements)
-[Contact Information](https://github.com/satabdi25-2000/vlsilab8TSRAM#Contact-Information)




# SRAM Design

This project focuses on a way for improvisation of Read and Write Stability of a Conventional 6T SRAM Cell.An 8T SRAM Cell is an optimized cell that can be used as memory circuits during read and write Operation for greater Stability,hereby increasing the Performance rate.

## 6T SRAM

It is a Static Memory cell to store data where two cross-coupled CMOS inverters are connected storing DATA(**Q**) and complement of data(**Qbar**).It permits the modification(write) of data bits,as well as their retrieval(read) when needed.

For more Information,[Click here](https://github.com/satabdi25-2000/vlsilabSRAM).

## 8T SRAM

### Block Diagram

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/BlockDiagram8T/8TSRAMCELL.png)

### Modes of Operation

**Hold State**

- WORDLINE=0
- Access transistors(M3,M4)-OFF
- Precharge Cell-ON
- Bistable operating points
- Previous data stored

**Read Mode**

- WORDLINE=1(WWL and RWL)
- Access transistors(M3,M4)-ON
- Bitlines Precharged(WBL,WBLB,RBL)
- Data(Q) to be read
- Q read by separate wordline and Bitline(RWL,RBL)
- Increased Stability
- Isolated internal node(Q)

**Write Mode**

- WORDLINE=1(WWL)
- Access transistors(M3,M4)-ON
- Bitline/Bitlinebar=0(According to data-Done by write driver)(WBL/WBLB)
- Data(Q) to be flipped/written over previous value

### Circuit Diagram

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/CircuitDiagram8T/8TSRAM.png)



The Proposed SRAM consists of Two more Stacked NMOS transistors connected to separate wordlines ans bitlines **RBL** and **RWL** for READ Operation.Without read disturbs, the worst-case stability condition for an 8T cell is eliminated which provides a significantly larger **SNM**.


# Stability Analysis of 6T and 8T

The Stability of the Cell is quantified by its Signal to Noise Margin(SNM).It determines the maximum DC noise that can be tolerated at the inputs of the memory cell during the read/write operation.

**Hold State**

**6T-SNM**

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/8TSimulations/SNM6T.png)

**8T-SNM**

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/8TSimulations/SNM8T.png)


## Read Stability

**Read SNM 0f 6T**

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/8TSimulations/SNMREAD6T.png)

The Read SNM can be determined by fitting a square in the upper and lower butterfly curve loop.

`SNM = min(SNM1,SNM2) = min(0.5,0.45) = 0.45`

**Read SNM of 8T**

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/8TSimulations/SNM8T.png)

Similarly,`SNM = min(1.5,1.35) = 1.35`

The Fundamental Stability problem in 6T cells is in the Read condition where the pass gates M3 and M4 pulls the “0” storage node up to a nonzero value and directly access the internal nodes of the Cell which increases the variability in the Stability.
The 8T SRAM Cell eliminates this problem by adding two NMOS to a 6T cell, Provides a read condition that does not disturb the internal nodes of the cell.

## Write Stability

**Write SNM of 6T**

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/8TSimulations/SNMWRITE6T.png)

**Write SNM of 8T**

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/8TSimulations/SNMWRITE8T.png)

The Write SNM can be determined by fitting the smallest square between the two curves.

`SNM = 1.3V`

## Stability Analysis using N-Curve

N-Curve is another way of measurement of Stability of the Cell.It provides the Voltage as well as the Current metrics which quantifies the Stability.

**N-Curve of 6T SRAM**

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/8TSimulations/NCURVE.png)

**N-Curve of 8T SRAM**

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/8TSimulations/NCURVE8T.png)


### Read Stability

The difference between Point A and Point B is the **Static Voltage Noise Margin** which determines the maximum tolerable dc noise voltage at internal nodes(Q) of the memory cell before flipping of the data.
`6T-SVNM = 1.36V`
`8T-SVNM = 1.6V`

The Current value at Point C is the **Static Current Noise Margin** which determines the maximum tolerable dc noise current at internal nodes(Q) of the memory cell before flipping of the data.
`6T-SINM = 246uA`
`8T-SINM = 703uA`

### Write Stability

The difference between Point D and Point C is the **Write Trip Voltage** which determines the minimum voltage needed to flip the internal nodes of the cell(**Q**).
`6T-WTV = 2.72V`
`8T-WTV = 3.57V`

The Current value at Point E is the **Write Trip Current** which determines the minimum amount of current to flip the data(**Q**).
`6T-WTI = -172uA`
`8T-WTI = -209uA`

**8T SRAM Cell has more Read and Write Stability as compared to 6T SRAM Cell.**

# Proposed 8T SRAM Cell

## PreLayout Simulations

Before doing the Layout,the prelayout simulatons should be done.The read/write timing estimation in Spice is done using a fast-single-8T parasitic model. Fast-single-8T parasitic models considers and estimates the parasitics of the wordlines and bitlines in the bit cell array analysing the capacitance for only 1-Bit Cell.

**Simulation**

**Input Signals**

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/8TSimulations/PreLayoutSimulationInput.png)

**Output Signals**

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/8TSimulations/PreLayoutSimulationOutput.png)

## PostLayout Simulations

### 6T SRAM Cell

**Layout**

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/Layouts/6TSRAMCELL.jpg)

### 8T SRAM Cell

**Layout**

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/Layouts/8T_SRAM.png)

There is area overhead that can be tolerated due to improvement in important design metrics-**Stability** of the SRAM cell.There is an area penalty of 35% because of adding two stacked NMOS to 6T SRAM Cell.


# Integrated Circuit

The 8T SRAM Cell is integrated with all the SRAM Blocks with all the Layouts and PostLayout Simulation is done.
For more information of SRAM Blocks,Click here(https://github.com/satabdi25-2000/vlsilabSRAM)


**Layout**

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/Layouts/Integrated_Circuit_8T.png)

**Simulation**

**Input Signals**

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/8TSimulations/InputSignals.png)

**Output Signals**

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/main/8TSimulations/OutputSignals.png)

# Future Works

- Implementing the Custom based cell designs in OpenRAM and integrating it to compile SRAM.
- Finding a Conventional approach to reduce leakage current in Low Power Designs.

# Acknowledgements

- Dr.Saroj Rout,Associate Professor,Silicon Institute Of Technology,Bhubaneswar
- Mr.Santunu Sarangi,Assistant Professor,Silicon Institute Of Technology,Bhubaneswar

# Contact Information

- Satabdi Panda,4th year Undergraduate,EIE Department,Silicon Institute Of Technology,Bhubaneswar satabdi.panda25@gmail.com
- Dr.Saroj Rout,Associate Professor,Silicon Institute Of Technology,Bhubaneswar saroj.rout@silicon.ac.in
- Mr.Santunu Sarangi,Assistant Professor,Silicon Institute Of Technology,Bhubaneswar santunu.sarangi@silicon.ac.in






