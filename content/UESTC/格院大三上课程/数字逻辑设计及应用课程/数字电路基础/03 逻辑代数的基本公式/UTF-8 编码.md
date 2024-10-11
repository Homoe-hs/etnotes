---
aliases:
  - 8-bit Unicode Transformation Format
tags: []
publish: "true"
---

# UTF-8 编码
## 概念
UTF-8 是一种**针对 Unicode 的可变长度字符编码，又称万国码**。

## 编码规则
如果只有一个字节则其最高二进制位为 0；如果是多字节，其第一个字节从最高位开始，连续的二进制位值为 1 的个数决定了其编码的字节数，其余各字节均以 10 开头。
**UTF-8 转换表**表示如下：
| Unicode/UCS-4 | bit 数 | UTF-8 | byte 数 | 备注 |
| --- | --- | --- | --- | --- |
| 0000 ~ 007F | 0~7 | 0XXXXXXX | 1 |  |
| 0080 ~ 07FF | 8~11 | 110XXXXX10XXXXXX | 2 |
| 0800 ~FFFF | 12~16 | 1110XXXX10XXXXXX  10XXXXXX | 3 | 基本定义范围：0~FFFF |
| 1 0000 ~1FFFFF | 17~21 | 11110XXX  10XXXXXX  10XXXXXX  10XXXXXX | 4 | Unicode6.1 定义范围：0~10 FFFF |
| 20 0000 ~  3FFFFFF | 22~26 | 111110XX  10XXXXXX  10XXXXXX  10XXXXXX  10XXXXXX | 5 | 说明：此非 unicode 编码范围，属于 UCS-4 编码  早期的规范 UTF-8 可以到达 6 字节序列，可以覆盖到 31 位元（通用字符集原来的极限）。尽管如此，2003 年 11 月 UTF-8 被 RFC 3629 重新规范，只能使用原来 Unicode 定义的区域， U+0000 到 U+10FFFF。根据规范，这些字节值将无法出现在合法 UTF-8 序列中 |
| 400 0000 ~  7FFF FFFF | 27~31 | 1111 110X  10XXXXXX  10XXXXXX  10XXXXXX  10XXXXXX  10XXXXXX | 6 | 同上 |

实际表示 `ASCII` 字符的 `UNICODE` 字符，将会编码成 1 个字节，并且 `UTF-8` 表示与 `ASCII` 字符表示是一样的。所有其他的 `UNICODE` 字符转化成 `UTF-8` 将需要至少 2 个字节。每个字节由一个换码序列开始。第一个字节由唯一的换码序列，由 `n` 位连续的 1 加一位 0 组成, 首字节连续的 1 的个数表示字符编码所需的字节数。

`Unicode` 转换为 `UTF-8` 时，可以将 `Unicode` 二进制从低位往高位取出二进制数字，每次取 6 位，如上述的二进制就可以分别取出为如下示例所示的格式，前面按格式填补，不足 8 位用 0 填补。

**注**：`Unicode` 转换为 `UTF-8` 需要的字节数可以根据这个规则计算：如果 `Unicode` 小于 0X80（Ascii 字符），则转换后为 1 个字节。否则转换后的字节数为 `Unicode` 二进制位数+3 再除以 5。

> [!info] 笔记来源
> 

