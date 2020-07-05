## 指令lea:
    lea指令用于把源操作数的地址偏移量传送目的操作数。
    指令格式：LEA des,src 或者 LEA src,des (取决于具体汇编版本)下面都以LEA src,des举例
    ex：
    SI=1000H , DS=5000H, (51000H)=1234H
    leal [SI],EAX # EAX = 1000H
    leal SI,EAX # EAX = 1000H
    
    在NASM汇编下
    movl EAX,SI
    leal EAX,SI   两个等价
    
    可用于乘法计算
    leal a(b, c, d), EAX # EAX=a+b+(c*d)
    
