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
    

## 指令 mov:
    mov 指令用于在寄存器和寄存器，寄存器和内存之间交换数据。
    指令格式：MOV des,src 或 MOV src,des (取决于具体汇编版本),src 和 des 中必须有一个是寄存器，下面都以LEA src,des举例
    
    ex:
    
    movl %eax   ,%edx   # dex = eax  等价于  movl eax    , edx
    movl $0x123 ,%edx   # edx = 0x123 等价于  movl $0x123 , edx
    movl 0x123  ,%edx   # edx = *(*int32)0x123
    movl (%ebx) ,%edx   # edx = *(*int32)ebx
    movl 4(%ebx),%edx   # edx = *(*int32)(ebx+4)
