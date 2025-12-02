PA 4-2 外设与I/O

为计算机接上眼睛和嘴巴，完成实现一台现代计算机的“最后的拼图”。

CPU完成与外设通信（进行输入输出）的方式

（1）端口映射I/O(port-mapped I/O)

串口（Serial），键盘（Keyboard），硬盘（IDE）（成块进行数据交换）

将外设的数据、状态、控制寄存器称为I/O端口；**对端口进行编号**；CPU使用in与out指令同端口间通过**按编号“打电话”的方式通信**

假设有65536个I/O端口，由16位无符号整型编码，可以做如下分配：键盘分配0x60端口，硬盘分配0x1F0~0x1F7端口，串口分配0x3F8~0x3FF端口，可通过如下指令进行端口（0x3F8）输出：

```c++
movb $’A’, %al
movw $0x3F8, %dx
outb %al, %dx
```

!!!question "PA 4-2 任务一"
	完成串口的模拟，实现in与out指令以及实现serial_printc()函数。运行hello-inline测试用例，对比实现串口前后的输出内容的区别。

!!!question "PA 4-2 任务二"
	改造loader函数（第三次修改【PA 2-2】【PA 3-3】），

!!!question "PA 4-2 任务三"
	通过echo测试用例，


（2）内存映射I/O (Memory Mapped I/O)

显卡（VGA）

声卡（Audio），时钟（Timer）只产生时钟中断【PA 4-1】

