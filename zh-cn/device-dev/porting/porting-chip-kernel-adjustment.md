# 内核基础适配<a name="ZH-CN_TOPIC_0000001063432950"></a>

-   [基础适配](#section14523241594)
-   [特性配置项](#section112994366592)

芯片架构适配完成后，liteos-m提供系统运行所需的系统初始化流程和定制化配置选项。移植过程中，需要关注初始化流程中跟硬件配置相关的函数；了解内核配置选项，才能裁剪出适合单板的最小内核。

## 基础适配<a name="section14523241594"></a>

如下图所示，基础适配主要分为以下两步：

1.  启动文件startup.S和相应链接配置文件。
2.  main. c中的串口初始化和tick中断注册。

**图 1**  启动流程<a name="fig10838105524917"></a>  


![](figure/zh-cn_image_0000001073943511.png)

启动文件startup.S需要确保中断向量表的入口函数（例如reset\_vector）放在RAM的首地址，它由链接配置文件来指定。其中iar、keil和gcc工程的链接配置文件分别为xxx.icf、xxx.sct和xxx.ld，如果startup.S已经完成系统时钟初始化，并且能够引导到main函数，则启动文件不需要进行修改，采用厂商自带的startup.S即可，否则需要实现以上功能。

在main.c文件中，需要关注串口初始化UartInit和系统Tick的handler函数注册。

-   UartInit函数表示单板串口的初始化，具体的函数名根据单板自行定义。这个函数是可选的，用户可以根据硬件单板是否支持串口来自行选择调用该函数。如果硬件单板支持串口，则该函数需要完成使能串口TX和RX通道，设置波特率。
-   HalTickStart设置tick中断的handler函数OsTickHandler。

对于中断向量表不可重定向的芯片，需要关闭LOSCFG\_PLATFORM\_HWI宏，并且在startup.S中新增tick中断的handler函数。

## 特性配置项<a name="section112994366592"></a>

liteos\_m的完整配置能力及默认配置在los\_config.h定义，该头文件中的配置项可以根据不同的单板进行裁剪配置。

如果针对这些配置项需要进行不同的板级配置，则可将对应的配置项直接定义到对应单板的device/xxxx/target\_config.h文件中，其他未定义的配置项，采用los\_config.h中的默认值。

一份典型的配置参数如下：

**表 1**  内核典型配置项说明

<a name="table1343954214199"></a>
<table><thead align="left"><tr id="row1244014425196"><th class="cellrowborder" valign="top" width="34.81%" id="mcps1.2.3.1.1"><p id="p1544044212197"><a name="p1544044212197"></a><a name="p1544044212197"></a>配置项</p>
</th>
<th class="cellrowborder" valign="top" width="65.19%" id="mcps1.2.3.1.2"><p id="p7440194281913"><a name="p7440194281913"></a><a name="p7440194281913"></a>说明</p>
</th>
</tr>
</thead>
<tbody><tr id="row1944094221913"><td class="cellrowborder" valign="top" width="34.81%" headers="mcps1.2.3.1.1 "><p id="p84407426198"><a name="p84407426198"></a><a name="p84407426198"></a>LOSCFG_BASE_CORE_SWTMR</p>
</td>
<td class="cellrowborder" valign="top" width="65.19%" headers="mcps1.2.3.1.2 "><p id="p84408426194"><a name="p84408426194"></a><a name="p84408426194"></a>软件定时器特性开关，1表示打开，0表示关闭</p>
</td>
</tr>
<tr id="row1225026133717"><td class="cellrowborder" valign="top" width="34.81%" headers="mcps1.2.3.1.1 "><p id="p725015663718"><a name="p725015663718"></a><a name="p725015663718"></a>LOSCFG_BASE_CORE_SWTMR_ALIGN</p>
</td>
<td class="cellrowborder" valign="top" width="65.19%" headers="mcps1.2.3.1.2 "><p id="p62502611378"><a name="p62502611378"></a><a name="p62502611378"></a>对齐软件定时器特性开，1表示打开，依赖软件定时器特性打开，0表示关闭</p>
</td>
</tr>
<tr id="row7440742191919"><td class="cellrowborder" valign="top" width="34.81%" headers="mcps1.2.3.1.1 "><p id="p19440134241919"><a name="p19440134241919"></a><a name="p19440134241919"></a>LOSCFG_BASE_IPC_MUX</p>
</td>
<td class="cellrowborder" valign="top" width="65.19%" headers="mcps1.2.3.1.2 "><p id="p1144017426191"><a name="p1144017426191"></a><a name="p1144017426191"></a>mux功能开关，1表示打开，0表示关闭</p>
</td>
</tr>
<tr id="row3440642161918"><td class="cellrowborder" valign="top" width="34.81%" headers="mcps1.2.3.1.1 "><p id="p1144004261916"><a name="p1144004261916"></a><a name="p1144004261916"></a>LOSCFG_BASE_IPC_QUEUE</p>
</td>
<td class="cellrowborder" valign="top" width="65.19%" headers="mcps1.2.3.1.2 "><p id="p1644094201917"><a name="p1644094201917"></a><a name="p1644094201917"></a>队列功能开关，1表示打开，0表示关闭</p>
</td>
</tr>
<tr id="row16440124216198"><td class="cellrowborder" valign="top" width="34.81%" headers="mcps1.2.3.1.1 "><p id="p9440184271915"><a name="p9440184271915"></a><a name="p9440184271915"></a>LOSCFG_BASE_IPC_SEM</p>
</td>
<td class="cellrowborder" valign="top" width="65.19%" headers="mcps1.2.3.1.2 "><p id="p1044024261912"><a name="p1044024261912"></a><a name="p1044024261912"></a>信号量功能开关，1表示打开，0表示关闭</p>
</td>
</tr>
<tr id="row444064216197"><td class="cellrowborder" valign="top" width="34.81%" headers="mcps1.2.3.1.1 "><p id="p14441642121912"><a name="p14441642121912"></a><a name="p14441642121912"></a>LOSCFG_PLATFORM_EXC</p>
</td>
<td class="cellrowborder" valign="top" width="65.19%" headers="mcps1.2.3.1.2 "><p id="p13441154216198"><a name="p13441154216198"></a><a name="p13441154216198"></a>异常特性开关，1表示打开，0表示关闭</p>
</td>
</tr>
<tr id="row744111422199"><td class="cellrowborder" valign="top" width="34.81%" headers="mcps1.2.3.1.1 "><p id="p19441942111910"><a name="p19441942111910"></a><a name="p19441942111910"></a>LOSCFG_KERNEL_PRINTF</p>
</td>
<td class="cellrowborder" valign="top" width="65.19%" headers="mcps1.2.3.1.2 "><p id="p1744115424197"><a name="p1744115424197"></a><a name="p1744115424197"></a>打印特性开关，1表示打开，0表示关闭</p>
</td>
</tr>
</tbody>
</table>

