# 安装开发板环境<a name="ZH-CN_TOPIC_0000001174270689"></a>

-   [Hi3516工具要求](#section179175261196)
    -   [硬件要求](#section5840424125014)
    -   [软件要求](#section965634210501)

-   [安装Linux服务器工具](#section182916865219)
    -   [将Linux shell改为bash](#section1715027152617)
    -   [安装编译依赖基础软件（仅Ubuntu 20+需要）](#section45512412251)
    -   [安装文件打包工具及Java虚拟机环境](#section16199102083717)


## Hi3516工具要求<a name="section179175261196"></a>

### 硬件要求<a name="section5840424125014"></a>

-   Hi3516DV300 IoT Camera开发板
-   USB转串口线、网线（Windows工作台通过USB转串口线、网线与Hi3516DV300 开发板连接）

各硬件连接关系如下图所示。

**图 1**  硬件连线图<a name="fig19527104710591"></a>  


![](figure/矩形备份-292.png)

### 软件要求<a name="section965634210501"></a>

>![](../public_sys-resources/icon-notice.gif) **须知：** 
>本节描述安装包方式搭建编译环境的操作步骤。如果是Docker方式安装编译环境，请跳过此章节以及下述[安装Linux服务器工具](#section182916865219)章节。

Hi3516开发板对Linux服务器通用环境配置需要的工具及其获取途径如下表所示。

**表 1**  Linux服务器开发工具及获取途径

<a name="table6299192712513"></a>
<table><thead align="left"><tr id="row122993276512"><th class="cellrowborder" valign="top" width="25.112511251125113%" id="mcps1.2.4.1.1"><p id="p1829914271858"><a name="p1829914271858"></a><a name="p1829914271858"></a>开发工具</p>
</th>
<th class="cellrowborder" valign="top" width="15.13151315131513%" id="mcps1.2.4.1.2"><p id="p429918274517"><a name="p429918274517"></a><a name="p429918274517"></a>用途</p>
</th>
<th class="cellrowborder" valign="top" width="59.75597559755976%" id="mcps1.2.4.1.3"><p id="p12997271757"><a name="p12997271757"></a><a name="p12997271757"></a>获取途径</p>
</th>
</tr>
</thead>
<tbody><tr id="row167343191518"><td class="cellrowborder" valign="top" width="25.112511251125113%" headers="mcps1.2.4.1.1 "><p id="p467443191517"><a name="p467443191517"></a><a name="p467443191517"></a>bash</p>
</td>
<td class="cellrowborder" valign="top" width="15.13151315131513%" headers="mcps1.2.4.1.2 "><p id="p0674153114151"><a name="p0674153114151"></a><a name="p0674153114151"></a>命令行处理工具</p>
</td>
<td class="cellrowborder" valign="top" width="59.75597559755976%" headers="mcps1.2.4.1.3 "><p id="p116746312151"><a name="p116746312151"></a><a name="p116746312151"></a>系统配置</p>
</td>
</tr>
<tr id="row14885193315201"><td class="cellrowborder" valign="top" width="25.112511251125113%" headers="mcps1.2.4.1.1 "><p id="p137174662119"><a name="p137174662119"></a><a name="p137174662119"></a>编译基础软件包(仅ubuntu 20+需要)</p>
</td>
<td class="cellrowborder" valign="top" width="15.13151315131513%" headers="mcps1.2.4.1.2 "><p id="p258814561424"><a name="p258814561424"></a><a name="p258814561424"></a>编译依赖的基础软件包</p>
</td>
<td class="cellrowborder" valign="top" width="59.75597559755976%" headers="mcps1.2.4.1.3 "><p id="p1749611716181"><a name="p1749611716181"></a><a name="p1749611716181"></a>通过互联网获取</p>
</td>
</tr>
<tr id="row52253812238"><td class="cellrowborder" valign="top" width="25.112511251125113%" headers="mcps1.2.4.1.1 "><p id="p28007392236"><a name="p28007392236"></a><a name="p28007392236"></a>dosfstools、mtools、mtd-utils</p>
</td>
<td class="cellrowborder" valign="top" width="15.13151315131513%" headers="mcps1.2.4.1.2 "><p id="p98008390232"><a name="p98008390232"></a><a name="p98008390232"></a>文件打包工具</p>
</td>
<td class="cellrowborder" valign="top" width="59.75597559755976%" headers="mcps1.2.4.1.3 "><p id="p280018394233"><a name="p280018394233"></a><a name="p280018394233"></a>通过apt-get install安装</p>
</td>
</tr>
<tr id="row29204072315"><td class="cellrowborder" valign="top" width="25.112511251125113%" headers="mcps1.2.4.1.1 "><p id="p5921190162318"><a name="p5921190162318"></a><a name="p5921190162318"></a>Java 虚拟机环境</p>
</td>
<td class="cellrowborder" valign="top" width="15.13151315131513%" headers="mcps1.2.4.1.2 "><p id="p17921110152311"><a name="p17921110152311"></a><a name="p17921110152311"></a>编译、调试和运行Java程序</p>
</td>
<td class="cellrowborder" valign="top" width="59.75597559755976%" headers="mcps1.2.4.1.3 "><p id="p16921805237"><a name="p16921805237"></a><a name="p16921805237"></a>通过apt-get install安装</p>
</td>
</tr>
</tbody>
</table>

## 安装Linux服务器工具<a name="section182916865219"></a>

>![](../public_sys-resources/icon-notice.gif) **须知：** 
>-   如果通过“HPM组件方式”或“HPM包管理器命令行工具方式”获取源码，不需要安装LLVM、hc-gen编译工具。
>-   （推荐）如果通过“镜像站点方式”或“代码仓库方式”获取源码，需要安装hc-gen编译工具。安装hc-gen编译工具时，请确保编译工具的环境变量路径唯一。

### 将Linux shell改为bash<a name="section1715027152617"></a>

查看shell是否为bash，在终端运行如下命令

```
ls -l /bin/sh
```

如果显示为“/bin/sh -\> bash”则为正常，否则请按以下方式修改：

**方法一**：在终端运行如下命令，然后选择 no。

```
sudo dpkg-reconfigure dash
```

**方法二**：先删除sh，再创建软链接。

```
sudo rm -rf /bin/sh
sudo ln -s /bin/bash /bin/sh
```

### 安装编译依赖基础软件（仅Ubuntu 20+需要）<a name="section45512412251"></a>

执行以下命令进行安装：

```
sudo apt-get install build-essential gcc g++ make zlib* libffi-dev
```

### 安装文件打包工具及Java虚拟机环境<a name="section16199102083717"></a>

1.  打开Linux编译服务器终端
2.  运行如下命令，安装dosfstools,mtools,mtd-utils,Java运行时环境（JRE）和Java sdk 开发工具包。

    ```
    sudo apt-get install dosfstools mtools mtd-utils default-jre default-jdk
    ```


