# 安装开发板环境<a name="ZH-CN_TOPIC_0000001128470862"></a>

-   [Hi3518环境搭建](#section1724111409282)
    -   [硬件要求](#section487353718276)
    -   [软件要求](#section17315193935817)

-   [安装Linux服务器工具](#section8831868501)
    -   [将Linux shell改为bash](#section434110241084)
    -   [安装编译依赖基础软件（仅Ubuntu 20+需要）](#section25911132141020)
    -   [安装文件打包工具](#section390214473129)


## Hi3518环境搭建<a name="section1724111409282"></a>

### 硬件要求<a name="section487353718276"></a>

-   Hi3518EV300 IoT Camera开发板
-   USB转串口线、网线（Windows工作台通过USB转串口线、网线与开发板连接）

    各硬件连接关系如下图所示。


**图 1**  硬件连线图<a name="fig8211468392"></a>  
![](figure/硬件连线图-3.png "硬件连线图-3")

### 软件要求<a name="section17315193935817"></a>

>![](../public_sys-resources/icon-notice.gif) **须知：** 
>本节描述安装包方式搭建编译环境的操作步骤。如果是Docker方式安装编译环境，请跳过此章节以及下述[安装Linux服务器工具](#section8831868501)章节。

Hi3518开发板对Linux服务器通用环境配置需要的工具及其获取途径如下表所示。

**表 1**  Linux服务器开发工具及获取途径

<a name="table15485545145811"></a>
<table><thead align="left"><tr id="row1748610451588"><th class="cellrowborder" valign="top" width="23.332333233323332%" id="mcps1.2.4.1.1"><p id="p13486154545816"><a name="p13486154545816"></a><a name="p13486154545816"></a>开发工具</p>
</th>
<th class="cellrowborder" valign="top" width="14.65146514651465%" id="mcps1.2.4.1.2"><p id="p44867452589"><a name="p44867452589"></a><a name="p44867452589"></a>用途</p>
</th>
<th class="cellrowborder" valign="top" width="62.016201620162015%" id="mcps1.2.4.1.3"><p id="p1748619458583"><a name="p1748619458583"></a><a name="p1748619458583"></a>获取途径</p>
</th>
</tr>
</thead>
<tbody><tr id="row18630134151917"><td class="cellrowborder" valign="top" width="23.332333233323332%" headers="mcps1.2.4.1.1 "><p id="p1563113417199"><a name="p1563113417199"></a><a name="p1563113417199"></a>bash</p>
</td>
<td class="cellrowborder" valign="top" width="14.65146514651465%" headers="mcps1.2.4.1.2 "><p id="p463193418190"><a name="p463193418190"></a><a name="p463193418190"></a>命令行处理工具</p>
</td>
<td class="cellrowborder" valign="top" width="62.016201620162015%" headers="mcps1.2.4.1.3 "><p id="p1063118344191"><a name="p1063118344191"></a><a name="p1063118344191"></a>系统配置</p>
</td>
</tr>
<tr id="row7598468212"><td class="cellrowborder" valign="top" width="23.332333233323332%" headers="mcps1.2.4.1.1 "><p id="p659815642111"><a name="p659815642111"></a><a name="p659815642111"></a>编译基础软件包(仅ubuntu 20+需要)</p>
</td>
<td class="cellrowborder" valign="top" width="14.65146514651465%" headers="mcps1.2.4.1.2 "><p id="p137174662119"><a name="p137174662119"></a><a name="p137174662119"></a>编译依赖的基础软件包</p>
</td>
<td class="cellrowborder" valign="top" width="62.016201620162015%" headers="mcps1.2.4.1.3 "><p id="p125983652118"><a name="p125983652118"></a><a name="p125983652118"></a>通过互联网获取</p>
</td>
</tr>
<tr id="row08231641105420"><td class="cellrowborder" valign="top" width="23.332333233323332%" headers="mcps1.2.4.1.1 "><p id="p1682494111548"><a name="p1682494111548"></a><a name="p1682494111548"></a>dosfstools、mtools、mtd-utils</p>
</td>
<td class="cellrowborder" valign="top" width="14.65146514651465%" headers="mcps1.2.4.1.2 "><p id="p1362445934918"><a name="p1362445934918"></a><a name="p1362445934918"></a>文件打包工具</p>
</td>
<td class="cellrowborder" valign="top" width="62.016201620162015%" headers="mcps1.2.4.1.3 "><p id="p1262475944916"><a name="p1262475944916"></a><a name="p1262475944916"></a>通过apt-get install安装</p>
</td>
</tr>
</tbody>
</table>

## 安装Linux服务器工具<a name="section8831868501"></a>

>![](../public_sys-resources/icon-notice.gif) **须知：** 
>-   如果通过“HPM组件方式”或“HPM包管理器命令行工具方式”获取源码，不需要安装hc-gen编译工具。
>-   （推荐）如果通过“镜像站点方式”或“代码仓库方式”获取源码，需要安装hc-gen编译工具。安装hc-gen编译工具时，请确保编译工具的环境变量路径唯一。

### 将Linux shell改为bash<a name="section434110241084"></a>

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

### 安装编译依赖基础软件（仅Ubuntu 20+需要）<a name="section25911132141020"></a>

执行以下命令进行安装：

```
sudo apt-get install build-essential gcc g++ make zlib* libffi-dev
```

### 安装文件打包工具<a name="section390214473129"></a>

1.  打开Linux编译服务器终端。
2.  运行如下命令，安装dosfstools,mtools,mtd-utils。

    ```
    sudo apt-get install dosfstools mtools mtd-utils
    ```


