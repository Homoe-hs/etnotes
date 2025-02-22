---
aliases: 
tags:
  - digital
  - verification
---

Electrical Verification takes a transistor level schematic and checks for some rules:
- The number of inversions between two $\mathrm{C^2MOS}$ gates should be even
- In a pseudo-NMOS gate, a well-defined ratio between the PMOS pull-up and NMOS pull-down devices in necessary to guarantee a good noisemargin low (NML)
- To ensure rise and fall times, minimum bounds should be set on the sizes of the driver transistors as a function of the fanout
