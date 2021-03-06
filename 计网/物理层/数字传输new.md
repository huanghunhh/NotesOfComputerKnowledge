



# 物理层 - 数字传输

## 线路编码

该部分的笔记重做

### 极性RZ

![极性RZ编码方案](https://gitee.com/twilight_h_1184651848/pic-go-img/raw/master/computerNetworks/digitalTransmission/20201215162002.png)

- 图片解读

  极性：负电平-0，正电平-1

  RZ：后一半归零

### NRZ-L 与 NRZ-I

![极性NRZ-L方案和极性NRZ-I方案](https://gitee.com/twilight_h_1184651848/pic-go-img/raw/master/computerNetworks/digitalTransmission/20201215161017.png)

- 图片解读

  + NRZ-L 

    信号电平决定了位值
  
    正电平-0，负电平-1
  
  + NRZ-I
  
    Invert - 反转
  
    信号电平是否反相转或跳变决定了位值
    
    没有跳变-0，有跳变-1

### 曼切斯特与差分曼切斯特

![曼切斯特编码和差分曼切斯特编码方案](https://gitee.com/twilight_h_1184651848/pic-go-img/raw/master/computerNetworks/digitalTransmission/20201215162431.png)

- 图片解读

  + 共同特征

    中间有跳变

  + 曼切斯特

    信号电平决定了位值

    高 $\to$ 低：0，低 $\to$ 高：1

  + 差分曼切斯特

    有跳变-0，没有跳变-1

### 双极方案（多电平二进制）：AMI和伪三元码

![AMI和伪三元码](https://gitee.com/twilight_h_1184651848/pic-go-img/raw/master/computerNetworks/digitalTransmission/20201215163027.png)

- 图片解读

  + AMI

    0电平-0， 交替正负电平-1

  + 伪三元编码

    0电平-1， 交替正负电平-0

### 多电平方案

$$
mBnl 编码类型\\
m - 二进制模式的长度\\
B - 二进制数据\\
n - 信号模式的长度\\
L - 信号中的电平数\\
L=2(二元) - B，L=3(三元) - T，L=4(四元) - Q
$$

#### 2B1Q

![2B1Q编码方案](https://gitee.com/twilight_h_1184651848/pic-go-img/raw/master/computerNetworks/digitalTransmission/20201215164344.png)

- 图片解读

  想知道这个编码，需要记转换表呀？

#### 8B6T

![8B6T编码](https://gitee.com/twilight_h_1184651848/pic-go-img/raw/master/computerNetworks/digitalTransmission/20201215200319.png)

- 冗余的信号元素

  提供同步和差错检测，DC平衡

### 多电平：4D-PAM5

![4D-PAM5方案](https://gitee.com/twilight_h_1184651848/pic-go-img/raw/master/computerNetworks/digitalTransmission/20201215165426.png)

- 图片解读

  4D：数据同时通过4条线路发送

  5个电平：-2、-1、0、1和2，电平0-发送差错检测

### 多线路：MLT-3方案

![MLT-3方案](https://gitee.com/twilight_h_1184651848/pic-go-img/raw/master/computerNetworks/digitalTransmission/20201215172629.png)

- 图片解读

  使用三个电平和三个跳变规则在电平间变动

  跳变规则：

    1. 下一位是0 - 没有跳变
    2. 下一位是1且当前电平不是0 - 下一个电平是0
    3. 下一位是1且当前电平是0 - 下一个电平是最后一个非零电平的相反值

- 线路编码小结

  ![image-20201215200513316](https://gitee.com/twilight_h_1184651848/pic-go-img/raw/master/computerNetworks/digitalTransmission/20201215200514.png)

### 线性编码结

- 极性RZ

  负电平-0，正电平-1，后一半归零

- NRZ-L

  信号电平决定了位值，正电平-0，负电平-1

- NRZ-I

  信号电平是否反相转或跳变决定了位值，没有跳变-0，有跳变-1

- 曼切斯特

  信号电平决定了位值，高 $\to$ 低：0，低 $\to$ 高：1

- 差分曼切斯特

  有跳变-0，没有跳变-1

- AMI

  0电平-0， 交替正负电平-1

- 伪三元编码

  0电平-1， 交替正负电平-0

- MLT-3

  使用三个电平和三个跳变规则在电平间变动
  跳变规则：
  
    1. 下一位是0 - 没有跳变
    2. 下一位是1且当前电平不是0 - 下一个电平是0
    3. 下一位是1且当前电平是0 - 下一个电平是最后一个非零电平的相反值

## 块编码

### 编码思想

![块编码概念图](https://gitee.com/twilight_h_1184651848/pic-go-img/raw/master/computerNetworks/digitalTransmission/20201216122939.png)

把m位的块变成n位的块（n>m），称为mB/nB编码技术（/用以区别多电平编码）

增加了比特率（数据发送的位数变多）

### 4B/5B

与NRZ-I组合使用

### 8B/10B

是5B/6B编码和3B/4B编码的组合

## 扰动

### B8ZS

![B8ZS扰动技术](https://gitee.com/twilight_h_1184651848/pic-go-img/raw/master/computerNetworks/digitalTransmission/20201216170604.png)

- 图片解读

  8个连续的0电平会被替换为000VB0VB（V-与前一个非零脉冲极性相同的极性，B-与前一个非零脉冲极性相反的极性）

### HDB3

![HDB3扰动技术](https://gitee.com/twilight_h_1184651848/pic-go-img/raw/master/computerNetworks/digitalTransmission/20201216171136.png)

4个连续零电平被置换成000V或B00V，使非零脉冲总数为偶数——如果最后一次置换后的非零脉冲是奇数-置换模式为000V，如果最后一次置换后的非零脉冲是偶数-置换模式为B00V