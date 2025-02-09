# Hi3861开发板介绍<a name="ZH-CN_TOPIC_0000001174270685"></a>

-   [简介](#section19352114194115)
-   [资源和约束](#section82610215014)
-   [开发板规格](#section169054431017)
-   [OpenHarmony关键特性](#section1317173016507)

## 简介<a name="section19352114194115"></a>

Hi3861 WLAN模组是一片大约2cm\*5cm大小的开发板，是一款高度集成的2.4GHz WLAN SoC芯片，集成IEEE 802.11b/g/n基带和RF（Radio Frequency）电路。支持OpenHarmony，并配套提供开放、易用的开发和调试运行环境。

**图 1**  Hi3861 WLAN模组外观图<a name="fig74884420237"></a>  


![](figure/3861正面.png)

另外，Hi3861 WLAN模组还可以通过与Hi3861底板连接，扩充自身的外设能力，底板如下图所示。

**图 2**  Hi3861底板外观图<a name="fig111746288192"></a>  


![](figure/zh-cn_image_0000001174350615.png)

-   RF电路包括功率放大器PA（Power Amplifier）、低噪声放大器LNA（Low Noise Amplifier）、RF Balun、天线开关以及电源管理等模块；支持20MHz标准带宽和5MHz/10MHz窄带宽，提供最大72.2Mbit/s物理层速率。
-   Hi3861 WLAN基带支持正交频分复用（OFDM）技术，并向下兼容直接序列扩频（DSSS）和补码键控（CCK）技术，支持IEEE 802.11 b/g/n协议的各种数据速率。
-   Hi3861芯片集成高性能32bit微处理器、硬件安全引擎以及丰富的外设接口，外设接口包括SPI（Synchronous Peripheral Interface）、UART（Universal Asynchronous Receiver & Transmitter）、I2C（The Inter Integrated Circuit）、PWM（Pulse Width Modulation）、GPIO（General Purpose Input/Output）和多路ADC（Analog to Digital Converter），同时支持高速SDIO2.0（Secure Digital Input/Output）接口，最高时钟可达50MHz；芯片内置SRAM（Static Random Access Memory）和Flash，可独立运行，并支持在Flash上运行程序。
-   Hi3861芯片适用于智能家电等物联网智能终端领域。

    **图 3**  Hi3861功能框图<a name="f0d52fa2f3b094c688c805a373a6ec970"></a>  
    

    ![](figure/zh-cn_image_0000001128311066.png)


## 资源和约束<a name="section82610215014"></a>

Hi3861 WLAN模组资源十分有限，整板共2MB FLASH，352KB RAM。在编写业务代码时，需注意资源使用效率。

## 开发板规格<a name="section169054431017"></a>

**表 1**  Hi3861 WLAN模组规格清单

<a name="t672b053e2ac94cbdb5244857fed4764e"></a>
<table><thead align="left"><tr id="r54b3810e43d24e1887c1d6a41394996b"><th class="cellrowborder" valign="top" width="18.060000000000002%" id="mcps1.2.3.1.1"><p id="a2b235e9ed55f4338886788f140e648a0"><a name="a2b235e9ed55f4338886788f140e648a0"></a><a name="a2b235e9ed55f4338886788f140e648a0"></a>规格类型</p>
</th>
<th class="cellrowborder" valign="top" width="81.94%" id="mcps1.2.3.1.2"><p id="a95c4ba2e404f4a45b65984746aaa56ab"><a name="a95c4ba2e404f4a45b65984746aaa56ab"></a><a name="a95c4ba2e404f4a45b65984746aaa56ab"></a>规格清单</p>
</th>
</tr>
</thead>
<tbody><tr id="r71f534ea66af4191b020408df5978f41"><td class="cellrowborder" valign="top" width="18.060000000000002%" headers="mcps1.2.3.1.1 "><p id="a0531f1bb62d5443880576cc5de23f2e6"><a name="a0531f1bb62d5443880576cc5de23f2e6"></a><a name="a0531f1bb62d5443880576cc5de23f2e6"></a>通用规格</p>
</td>
<td class="cellrowborder" valign="top" width="81.94%" headers="mcps1.2.3.1.2 "><a name="u2a0d06f28d454d30818ced9a0432211b"></a><a name="u2a0d06f28d454d30818ced9a0432211b"></a><ul id="u2a0d06f28d454d30818ced9a0432211b"><li>1×1 2.4GHz频段（ch1～ch14）</li><li>PHY支持IEEE 802.11b/g/n</li><li>MAC支持IEEE802.11 d/e/h/i/k/v/w</li></ul>
<a name="u8f31d142d92147789195a18b50836d2c"></a><a name="u8f31d142d92147789195a18b50836d2c"></a><ul id="u8f31d142d92147789195a18b50836d2c"><li>内置PA和LNA，集成TX/RX Switch、Balun等</li><li>支持STA和AP形态，作为AP时最大支持6 个STA接入</li><li>支持WFA WPA/WPA2 personal、WPS2.0</li><li>支持与BT/BLE芯片共存的2/3/4 线PTA方案</li><li>电源电压输入范围：2.3V～3.6V</li></ul>
<a name="ul114549122110"></a><a name="ul114549122110"></a><ul id="ul114549122110"><li>IO电源电压支持1.8V和3.3V</li></ul>
<a name="ue044275c53b84dd29dda674e16e72823"></a><a name="ue044275c53b84dd29dda674e16e72823"></a><ul id="ue044275c53b84dd29dda674e16e72823"><li>支持RF自校准方案</li><li>低功耗：<a name="ul0879143622219"></a><a name="ul0879143622219"></a><ul id="ul0879143622219"><li>Ultra Deep Sleep模式：5μA@3.3V</li><li>DTIM1：1.5mA@3.3V</li><li>DTIM3：0.8mA@3.3V</li></ul>
</li></ul>
</td>
</tr>
<tr id="rd9b56e759af34950b6887ca1bf5bb7cf"><td class="cellrowborder" valign="top" width="18.060000000000002%" headers="mcps1.2.3.1.1 "><p id="a0aed3860a78a4b50bedf60699afd3996"><a name="a0aed3860a78a4b50bedf60699afd3996"></a><a name="a0aed3860a78a4b50bedf60699afd3996"></a>PHY特性</p>
</td>
<td class="cellrowborder" valign="top" width="81.94%" headers="mcps1.2.3.1.2 "><a name="u6568aa052152432aa1f44372445ca634"></a><a name="u6568aa052152432aa1f44372445ca634"></a><ul id="u6568aa052152432aa1f44372445ca634"><li>支持IEEE802.11b/g/n单天线所有的数据速率</li><li>支持最大速率：72.2Mbps@HT20 MCS7</li><li>支持标准20MHz带宽和5M/10M窄带宽</li><li>支持STBC</li><li>支持Short-GI</li></ul>
</td>
</tr>
<tr id="r3563f9df9759486794952d46c5d2d03f"><td class="cellrowborder" valign="top" width="18.060000000000002%" headers="mcps1.2.3.1.1 "><p id="afd48a2d879dc4aada8b60bebb96523c7"><a name="afd48a2d879dc4aada8b60bebb96523c7"></a><a name="afd48a2d879dc4aada8b60bebb96523c7"></a>MAC特性</p>
</td>
<td class="cellrowborder" valign="top" width="81.94%" headers="mcps1.2.3.1.2 "><a name="uca57d799e7814925a5bf1b891335bd79"></a><a name="uca57d799e7814925a5bf1b891335bd79"></a><ul id="uca57d799e7814925a5bf1b891335bd79"><li>支持A-MPDU，A-MSDU</li><li>支持Blk-ACK</li><li>支持QoS，满足不同业务服务质量需求</li></ul>
</td>
</tr>
<tr id="r3e1c86e5f6cd4df0a1b30a08fb8481a2"><td class="cellrowborder" valign="top" width="18.060000000000002%" headers="mcps1.2.3.1.1 "><p id="a57086ea97a1b46cdb21953bf0fc22d94"><a name="a57086ea97a1b46cdb21953bf0fc22d94"></a><a name="a57086ea97a1b46cdb21953bf0fc22d94"></a>CPU子系统</p>
</td>
<td class="cellrowborder" valign="top" width="81.94%" headers="mcps1.2.3.1.2 "><a name="u612cc2cd0cfe40229263c4f506c0c69c"></a><a name="u612cc2cd0cfe40229263c4f506c0c69c"></a><ul id="u612cc2cd0cfe40229263c4f506c0c69c"><li>高性能 32bit微处理器，最大工作频率160MHz</li><li>内嵌SRAM 352KB、ROM 288KB</li><li>内嵌 2MB Flash</li></ul>
</td>
</tr>
<tr id="rae93c5236b084cd2a2c0d5c29027b40e"><td class="cellrowborder" valign="top" width="18.060000000000002%" headers="mcps1.2.3.1.1 "><p id="a9b14a9e95b3849278c332259d8add1b2"><a name="a9b14a9e95b3849278c332259d8add1b2"></a><a name="a9b14a9e95b3849278c332259d8add1b2"></a>外围接口</p>
</td>
<td class="cellrowborder" valign="top" width="81.94%" headers="mcps1.2.3.1.2 "><a name="u7c73ebffd89e4092bd65f0d878d59b22"></a><a name="u7c73ebffd89e4092bd65f0d878d59b22"></a><ul id="u7c73ebffd89e4092bd65f0d878d59b22"><li>1个SDIO接口、2个SPI接口、2个I2C接口、3个UART接口、15个GPIO接口、7路ADC输入、6路PWM、1个I2S接口（注：上述接口通过复用实现）</li><li>外部主晶体频率40M或24M</li></ul>
</td>
</tr>
<tr id="r18810701aafe42ad8d9a7d882730c210"><td class="cellrowborder" valign="top" width="18.060000000000002%" headers="mcps1.2.3.1.1 "><p id="ae8f47db913724e458c265e858409950b"><a name="ae8f47db913724e458c265e858409950b"></a><a name="ae8f47db913724e458c265e858409950b"></a>其他信息</p>
</td>
<td class="cellrowborder" valign="top" width="81.94%" headers="mcps1.2.3.1.2 "><a name="u25f28919a3b044c5af50f9f5f5616083"></a><a name="u25f28919a3b044c5af50f9f5f5616083"></a><ul id="u25f28919a3b044c5af50f9f5f5616083"><li>封装：QFN-32，5mm×5mm</li><li>工作温度：-40℃ ～ +85℃</li></ul>
</td>
</tr>
</tbody>
</table>

## OpenHarmony关键特性<a name="section1317173016507"></a>

OpenHarmony基于Hi3861平台提供了多种开放能力，提供的关键组件如下表所示。

**表 2**  OpenHarmony关键组件列表

<a name="table1659013482514"></a>
<table><thead align="left"><tr id="row1368918486512"><th class="cellrowborder" valign="top" width="22.63%" id="mcps1.2.3.1.1"><p id="p668914812516"><a name="p668914812516"></a><a name="p668914812516"></a>组件名</p>
</th>
<th class="cellrowborder" valign="top" width="77.37%" id="mcps1.2.3.1.2"><p id="p9689154855115"><a name="p9689154855115"></a><a name="p9689154855115"></a>能力介绍</p>
</th>
</tr>
</thead>
<tbody><tr id="row868910487517"><td class="cellrowborder" valign="top" width="22.63%" headers="mcps1.2.3.1.1 "><p id="p13689248165114"><a name="p13689248165114"></a><a name="p13689248165114"></a>WLAN服务</p>
</td>
<td class="cellrowborder" valign="top" width="77.37%" headers="mcps1.2.3.1.2 "><p id="p11689144816511"><a name="p11689144816511"></a><a name="p11689144816511"></a>提供WLAN服务能力。包括：station和hotspot模式的连接、断开、状态查询等。</p>
</td>
</tr>
<tr id="row568964819514"><td class="cellrowborder" valign="top" width="22.63%" headers="mcps1.2.3.1.1 "><p id="p5689548175113"><a name="p5689548175113"></a><a name="p5689548175113"></a>模组外设控制</p>
</td>
<td class="cellrowborder" valign="top" width="77.37%" headers="mcps1.2.3.1.2 "><p id="p176893480517"><a name="p176893480517"></a><a name="p176893480517"></a>提供操作外设的能力。包括：I2C、I2S、ADC、UART、SPI、SDIO、GPIO、PWM、FLASH等。</p>
</td>
</tr>
<tr id="row143420119366"><td class="cellrowborder" valign="top" width="22.63%" headers="mcps1.2.3.1.1 "><p id="p1737117331480"><a name="p1737117331480"></a><a name="p1737117331480"></a>分布式软总线</p>
</td>
<td class="cellrowborder" valign="top" width="77.37%" headers="mcps1.2.3.1.2 "><p id="p1037123314485"><a name="p1037123314485"></a><a name="p1037123314485"></a>在<span id="text1538015458506"><a name="text1538015458506"></a><a name="text1538015458506"></a>OpenHarmony</span>分布式网络中，提供设备被发现、数据传输的能力。</p>
</td>
</tr>
<tr id="row1383559163617"><td class="cellrowborder" valign="top" width="22.63%" headers="mcps1.2.3.1.1 "><p id="p2379233113914"><a name="p2379233113914"></a><a name="p2379233113914"></a>设备安全绑定</p>
</td>
<td class="cellrowborder" valign="top" width="77.37%" headers="mcps1.2.3.1.2 "><p id="p5809349205012"><a name="p5809349205012"></a><a name="p5809349205012"></a>提供在设备互联场景中，数据在设备之间的安全流转的能力。</p>
</td>
</tr>
<tr id="row54428163612"><td class="cellrowborder" valign="top" width="22.63%" headers="mcps1.2.3.1.1 "><p id="p3775133619587"><a name="p3775133619587"></a><a name="p3775133619587"></a>基础加解密</p>
</td>
<td class="cellrowborder" valign="top" width="77.37%" headers="mcps1.2.3.1.2 "><p id="p11304151710555"><a name="p11304151710555"></a><a name="p11304151710555"></a>提供密钥管理、加解密等能力。</p>
</td>
</tr>
<tr id="row12690548135110"><td class="cellrowborder" valign="top" width="22.63%" headers="mcps1.2.3.1.1 "><p id="p176901648115111"><a name="p176901648115111"></a><a name="p176901648115111"></a>系统服务管理</p>
</td>
<td class="cellrowborder" valign="top" width="77.37%" headers="mcps1.2.3.1.2 "><p id="p1181353173111"><a name="p1181353173111"></a><a name="p1181353173111"></a>系统服务管理基于面向服务的架构，提供了<span id="text10778141516322"><a name="text10778141516322"></a><a name="text10778141516322"></a>OpenHarmony</span>统一化的系统服务开发框架。</p>
</td>
</tr>
<tr id="row1657310121587"><td class="cellrowborder" valign="top" width="22.63%" headers="mcps1.2.3.1.1 "><p id="p730664220114"><a name="p730664220114"></a><a name="p730664220114"></a>启动引导</p>
</td>
<td class="cellrowborder" valign="top" width="77.37%" headers="mcps1.2.3.1.2 "><p id="p39689262310"><a name="p39689262310"></a><a name="p39689262310"></a>提供系统服务的启动入口标识。在系统服务管理启动时，调用boostrap标识的入口函数，并启动系统服务。</p>
</td>
</tr>
<tr id="row15763812165616"><td class="cellrowborder" valign="top" width="22.63%" headers="mcps1.2.3.1.1 "><p id="p17171118128"><a name="p17171118128"></a><a name="p17171118128"></a>系统属性</p>
</td>
<td class="cellrowborder" valign="top" width="77.37%" headers="mcps1.2.3.1.2 "><p id="p12763912125617"><a name="p12763912125617"></a><a name="p12763912125617"></a>提供获取与设置系统属性的能力。</p>
</td>
</tr>
<tr id="row121911343566"><td class="cellrowborder" valign="top" width="22.63%" headers="mcps1.2.3.1.1 "><p id="p1097517270361"><a name="p1097517270361"></a><a name="p1097517270361"></a>基础库</p>
</td>
<td class="cellrowborder" valign="top" width="77.37%" headers="mcps1.2.3.1.2 "><p id="p6848159569"><a name="p6848159569"></a><a name="p6848159569"></a>提供公共基础库能力。包括：文件操作、KV存储管理等。</p>
</td>
</tr>
<tr id="row144219192579"><td class="cellrowborder" valign="top" width="22.63%" headers="mcps1.2.3.1.1 "><p id="p8333104843714"><a name="p8333104843714"></a><a name="p8333104843714"></a>DFX</p>
</td>
<td class="cellrowborder" valign="top" width="77.37%" headers="mcps1.2.3.1.2 "><p id="p65111025155711"><a name="p65111025155711"></a><a name="p65111025155711"></a>提供DFX能力。包括：流水日志、时间打点等。</p>
</td>
</tr>
<tr id="row16159522125710"><td class="cellrowborder" valign="top" width="22.63%" headers="mcps1.2.3.1.1 "><p id="p18835202765718"><a name="p18835202765718"></a><a name="p18835202765718"></a>XTS</p>
</td>
<td class="cellrowborder" valign="top" width="77.37%" headers="mcps1.2.3.1.2 "><p id="p3835192795717"><a name="p3835192795717"></a><a name="p3835192795717"></a>提供<span id="text1482414523409"><a name="text1482414523409"></a><a name="text1482414523409"></a>OpenHarmony</span>生态认证测试套件的集合能力。</p>
</td>
</tr>
</tbody>
</table>

