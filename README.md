# A Comparative Analysis between 6T and a proposed 8T SRAM

## Table Of Contents
- [SRAM Design](https://github.com/satabdi25-2000/vlsilab8TSRAM#sram-design)
  - [6T SRAM](https://github.com/satabdi25-2000/vlsilab8TSRAM#6T-SRAM)
  - [8T SRAM](https://github.com/satabdi25-2000/vlsilab8TSRAM#8T-SRAM)
- [Stability Analysis of 6T and 8T](https://github.com/satabdi25-2000/vlsilab8TSRAM#Stability-Analysis-of-6T-and-8T)
  - [Read Stability](https://github.com/satabdi25-2000/vlsilab8TSRAM#Read-Stability)
  - [Write Stability](https://github.com/satabdi25-2000/vlsilab8TSRAM#Write-Stability)
- [Proposed 8T SRAM Cell](https://github.com/satabdi25-2000/vlsilab8T8TSRAM#Proposed-8T-SRAM-Cell)
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

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/master/BlockDiagram/8TSRAMCELL.png)

### Modes of Operation

**Hold State**

WORDLINE=0
Access transistors(M3,M4)-OFF
Precharge Cell-ON
Bistable operating points
Previous data stored

**Read Mode**

WORDLINE=1(WWL and RWL)
Access transistors(M3,M4)-ON
Bitlines Precharged(WBL,WBLB,RBL)
Data(Q) to be read
Q read by separate wordline and Bitline(RWL,RBL)
Increased Stability
Isolated internal node(Q)

**Write Mode**

WORDLINE=1(WWL)
Access transistors(M3,M4)-ON
Bitline/Bitlinebar=0(According to data-Done by write driver)(WBL/WBLB)
Data(Q) to be flipped/written over previous value

### Circuit Diagram

![](https://github.com/satabdi25-2000/vlsilab8TSRAM/blob/master/CircuitDiagram/8TSRAM.png)


