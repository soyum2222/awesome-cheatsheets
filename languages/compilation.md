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
    
    movl %eax   ,%edx   # dex = eax   等价于  movl eax    , edx
    movl $0x123 ,%edx   # edx = 0x123 等价于  movl $0x123 , edx
    movl 0x123  ,%edx   # edx = *(*int32)0x123
    movl (%ebx) ,%edx   # edx = *(*int32)ebx
    movl 4(%ebx),%edx   # edx = *(*int32)(ebx+4)

    关于后缀：
    movb #完成1个字节的复制
    movw #完成2个字节的复制
    movl #完成4个字节的复制
    movq #完成8个字节的复制
    
 ## 指令 PUSH POP CALL RET
    pushl %eax      #   把EAX的内容存放到esp指向的内存位置中，并且esp减小4（根据不同的平台，大端或者小端对应是‘减小’或者是‘增大’，根据不同的平台64位或者32为对应‘8’和‘4’）
                    #   等价于   
                    #   subl $4,%esp  
                    #   movl %eax,(%esp)
                
    pop %eax        #   把esp指向的内存位置中的内容，移动到eax中，并且esp增大4（根据不同的平台，大端或者小端对应是‘减小’或者是‘增大’，根据不同的平台64位或者32为对应‘8’和‘4’）
                    #   等价于
                    #   movl (%esp),%eax
                    #   addl $4,%esp
               
    call funcname   #   调用名字为‘funcname’ 的方法。先PUSH存储当前的IP的值，把IP寄存器的值指向funcname方法所在的内存地址。
                    #   等价于
                    #   pushl %eip
                    #   movl $funcname,%eip
                    
    ret             #   返回方法调用者。从esp的位子中取出caller的ip的值
                    #   等价于
                    #   popl %eip 
                    
                
    
    

