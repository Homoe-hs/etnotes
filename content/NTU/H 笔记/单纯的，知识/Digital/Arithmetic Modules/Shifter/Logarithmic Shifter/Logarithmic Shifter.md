---
aliases:
  - 对数移位器
tags:
  - shifter
  - digital
  - arthmetic_modules
---
![[Logarithmic Shifter.png|Logarithmic Shifter]]

- Total shift value is decomposed into shifts over powers of 2: i.e. 1, 2, 4. A maximum shift width of $M$ consists of $log_2M$ stages
  以对数形式运行的移位器，每一级可以移$2^n$位，所以省略了解码器。每一级可以被设置为移位模式和通过模式，级数为$log_2M$
- 移位模式下的一级和[[Barrel Shifter|桶形移位器]]挺像的

# 优势

- Control signals are in encoded form, hence, less control signals.
  控制信号是以编码形式存在的，因此控制信号较少。
- No decoder is needed
  不需要解码器
- More effective than barrel shifter for large shift values.
  对于大位移值来说，比桶式移位器更有效。
- Smaller in area and faster in speed than barrel shifter.
  比桶形移位器速度快、面积小

# Layout

![[Pasted image 20241029032108.png|Logarithmic shifter Layout]]