[toc]

# UDP

## 基本介绍

> 1. 类 DatagramSocket 和 DatagramPacket (数据包/数据报) 实现了基于 UDP 协议网络程序。
>
> 2. UDP 数据报通过数据报套接字 DatagramSocket 发送和接收，系统不保证 UDP
>   数据报一定能够安全送到目的地，也不能确定什么时候可以抵达。
> 3. DatagramPacket 对象封装了 UDP 数据报，在数据报中包含了发送端的 IP 地址和
>   端口号,以及接收端的IP地址和端口号。
> 4. UDP 协议中每个数据报都给出了完整的地址信息，因此无须建立发送方和接收方的连接。

## 基本流程

> 核心的两个类 / 对象: DatagramSocket 与 DatagramPacket 
>
> 建立发送端，接收端(没有服务端和客户端概念)
>
> 发送数据前，建立数据包 / 报 DatagramPacket 对象
>
> 调用 DatagramSocket 的发送、接收方法
>
> 关闭 DatagramSocket