# Chapter 3 通讯对象类（Communication Object Classes）

## 目录
[TOC]

## 3-1 介绍
CIP的通讯对象管理和提供运行时的消息交换。在本章节详细介绍通讯对象类的服务（Services），属性（Attributes）和行为（Behaviors）。对象定义部分涉及属性的数据类型。可以查看附录C（Appendix C）获得CIP数据类型和数据管理的详细信息。

重要：以下各节的目的不在于指定任何特定的内部实现。

通讯对象类通过以下描述定义：
* 对象类的属性
* 对象类的服务
* 对象实例的属性
* 对象实例的服务
* 对象实例的行为

每个CIP连接由一个连接对象（Class code 0x05）表示。这个通讯对象资源的创建有两种方法。不同的子网类型决定使用哪种方法：
* 使用Connection对象的Create服务（Service code 0x08）
* 使用Connection Manager对象的Forward_Open服务

子网类型可能定义其它创建通讯对象资源的方法。例如DeviceNet的Allocate_Master/Slave_Connection_Set服务。有关子网类型特定方法的详细信息，请参阅相应的规范卷。

### 3-1.1 通过Connection对象创建连接

当子网定义通过Connection对象创建连接时，CIP设备将支持这个对象的Create服务。Create服务使用对象定义的默认值创建Connection实例。然后通过对每个Connection实例属性的访问来完成配置。最后需要独立的服务请求（Apply_Attributes,Service code 0x0D）才能将连接状态转换为确定状态（Established state）。

### 3-1.2 通过Connection Manager对象创建连接

当子网定义通过Connection Manager对象创建连接时，CIP设备将支持这个对象的Forward_Open服务。当服务成功完成，Connection Manager会创建一个Connection实例。这个实例使用Forward_Open服务中的值来配置，同时连接状态转换为确定状态（Established state）。这个单一的CIP服务请求在内部建模成一个Connection对象的服务请求（使用Create服务）和若干个内部服务请求（使用Set_Attribute_Single和Apply_Attributes服务）。支持通过Connection Manager对象连接Connection的设备可能会也可能不会为Connection实例提供外部可见性。

## 3-2 链接生产者对象类定义 （Link Producer）
## 3-3 链接消费者对象类定义
## 3-4 连接管理器对象类定义
## 3-5 使用0类或1类传输的应用程序连接类型
## 3-6 端口对象类定义