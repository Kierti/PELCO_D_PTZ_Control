# PELCO_D_PTZ_Control

基于Windows平台下使用C++封装PELCO_D云台镜头控制协议，通过串口RS485发送协议命令

PELCO_D协议：
通信数据格式：1位起始位，8位数据，1位停止位，无校验位
默认通信波特率：9600B/S,默认地址：1

Pelco-D 命令描述： 

+-------+-------+-------+-------+-------+-------+-------+

|  Byte 1   | Byte 2  |  Byte 3   |  Byte 4   | Byte 5 | Byte 6 |  Byte 7  |

+-------+-------+-------+-------+-------+-------+-------+

| Sync Byte | Address | Command 1 | Command 2 | Data 1 | Data 2 | Checksum |

+-------+-------+-------+-------+-------+-------+-------+

1.	该协议中所有数值都为十六进制数
2.	同步字节始终为 FFH
3.	地址码为摄像机的逻辑地址号，地址范围：00H–FFH
4.	指令码表示不同的动作
5.	数据码 1、2 分别表示水平、垂直方向速度（00-3FH）,FFH 表示“turbo”速度
6.	校验码 = MOD[（字节 2 +  字节 3 +  字节 4 +  字节 5 +  字节 6）/100H]
