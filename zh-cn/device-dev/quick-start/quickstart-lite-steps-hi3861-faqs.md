# 常见问题<a name="ZH-CN_TOPIC_0000001128311054"></a>

-   [安装python3过程中，提示“configure: error: no acceptable C compiler found in $PATH”](#section1221016541119)
-   [安装python3过程中，提示“-bash: make: command not found”](#section1913477181213)
-   [安装python3过程中，提示“zlib not available”](#section108211415131210)
-   [安装python3过程中，提示“No module named '\_ctypes'”](#section2062268124)
-   [编译构建过程中，提示“No module named 'Crypto'”](#section982315398121)
-   [编译构建过程中，提示“No module named 'ecdsa'”](#section102035451216)
-   [编译构建过程中，提示“Could not find a version that satisfies the requirement six\>=1.9.0”](#section4498158162320)
-   [编译构建过程中，提示找不到“-lgcc”](#section11181036112615)
-   [编译构建过程中，提示找不到“python”](#section1571810194619)
-   [安装 kconfiglib时，遇到lsb\_release错误](#section691681635814)

## 安装python3过程中，提示“configure: error: no acceptable C compiler found in $PATH”<a name="section1221016541119"></a>

-   **现象描述**

    安装python3过程中出现以下错误：

    ```
    configure: error: no acceptable C compiler found in $PATH. See 'config.log' for more details
    ```

-   **可能原因**

    环境中未安装“gcc”。

-   **解决办法**

    1、通过命令“apt-get install gcc”在线安装。

    2、完成后，重新安装python3。


## 安装python3过程中，提示“-bash: make: command not found”<a name="section1913477181213"></a>

-   **现象描述**

    安装python3过程中出现以下错误：

    ```
    -bash: make: command not found
    ```

-   **可能原因**

    环境中未安装“make”。

-   **解决办法**

    1、通过命令“apt-get install make”在线安装。

    2、完成后，重新安装python3。


## 安装python3过程中，提示“zlib not available”<a name="section108211415131210"></a>

-   **现象描述**

    安装python3过程中出现以下错误：

    ```
    zipimport.ZipImportError: can't decompress data; zlib not avaliable
    ```

-   **可能原因**

    环境中未安装“zlib”。

-   **解决办法**

    方法1：通过命令“apt-get install zlib”在线安装。

    方法2：如果软件源中没有该软件，请从“www.zlib.net”下载版本代码，并离线安装。

    ![](figure/10.png)

    完成下载后，通过以下命令安装：

    ```
    # tar xvf zlib-1.2.11.tar.gz
    # cd zlib-1.2.11
    # ./configure
    # make && make install
    ```

    完成后，重新安装python3。


## 安装python3过程中，提示“No module named '\_ctypes'”<a name="section2062268124"></a>

-   **现象描述**

    安装python3过程中出现以下错误：

    ```
    ModuleNotFoundError：No module named ‘_ctypes’
    ```


-   **可能原因**

    环境中未安装“libffi”和“libffi-devel”。


-   **解决办法**

    1、通过命令“apt-get install libffi\* -y”，在线安装。

    2、完成后，重新安装python3。


## 编译构建过程中，提示“No module named 'Crypto'”<a name="section982315398121"></a>

-   **现象描述**

    编译构建过程中出现以下错误：

    ```
    ModuleNotFoundError: No module named 'Crypto'
    ```


-   **可能原因**

    环境中未安装“Crypto”。


-   **解决办法**

    方法1：通过命令“pip3 install Crypto”，在线安装。

    方法2：离线安装

    通过网页[https://pypi.org/project/pycrypto/\#files](https://pypi.org/project/pycrypto/#files)，下载源码。

    ![](figure/zh-cn_image_0000001128470864.png)

    将源码放置在Linux服务器中，解压，并安装“python3 setup.py install”。

    完成上述安装后，重新构建。


## 编译构建过程中，提示“No module named 'ecdsa'”<a name="section102035451216"></a>

-   **现象描述**

    编译构建过程中出现以下错误：

    ```
    ModuleNotFoundError：No module named 'ecdsa'
    ```


-   **可能原因**

    环境中未安装“ecdsa”。


-   **解决办法**

    方法1：通过命令“pip3 install ecdsa”，在线安装。

    方法2：离线安装

    通过网页[https://pypi.org/project/ecdsa/\#files](https://pypi.org/project/ecdsa/#files)，下载安装包。

    ![](figure/zh-cn_image_0000001128311072.png)

    将安装包放置Linux服务器中，并安装“pip3 install ecdsa-0.15-py2.py3-none-any.whl”。

    完成上述安装后，重新构建。


## 编译构建过程中，提示“Could not find a version that satisfies the requirement six\>=1.9.0”<a name="section4498158162320"></a>

-   **现象描述**

    编译构建过程中出现以下错误：

    ```
    Could not find a version that satisfies the requirement six>=1.9.0
    ```


-   **可能原因**

    环境中未安装合适的“six”。


-   **解决办法**

    方法1：通过命令“pip3 install six”，在线安装。

    方法2：离线安装

    通过网页[https://pypi.org/project/six/\#files](https://pypi.org/project/six/#files)，下载安装包。

    ![](figure/zh-cn_image_0000001174270699.png)

    将源码放置在Linux服务器中，并安装“pip3 install six-1.14.0-py2.py3-none-any.whl”。

    完成上述安装后，重新构建。


## 编译构建过程中，提示找不到“-lgcc”<a name="section11181036112615"></a>

-   **现象描述**

    编译构建过程中出现以下错误：

    ```
    riscv32-unknown-elf-ld: cannot find -lgcc
    ```


-   **可能原因**

    交叉编译器gcc\_riscv32的PATH添加错误，如下，在"bin"后多添加了一个“/”，应该删除。

    ```
    ~/gcc_riscv32/bin/:/data/toolchain/
    ```


-   **解决办法**

    重新修改gcc\_riscv32的PATH，将多余的“/”删除。

    ```
    ~/gcc_riscv32/bin:/data/toolchain/
    ```


## 编译构建过程中，提示找不到“python”<a name="section1571810194619"></a>

-   **现象描述**

    编译构建过程中出现以下错误：

    ```
    -bash: /usr/bin/python: No such file or directory
    ```


-   **可能原因**1

    没有装python。

-   **解决办法**

    请按照[安装Python环境](quickstart-lite-env-setup-linux.md#section1238412211211)

-   **可能原因2**

    ![](figure/zh-cn_image_0000001128311070.png)

-   **解决办法**

    usr/bin目录下没有python软链接，请运行以下命令添加软链接：

    ```
    # cd /usr/bin/
    # which python3
    # ln -s /usr/local/bin/python3 python
    # python --version
    ```

    例：

    ![](figure/zh-cn_image_0000001174350623.png)


## 安装 kconfiglib时，遇到lsb\_release错误<a name="section691681635814"></a>

-   **现象描述**

    安装kconfiglib过程中遇到如下错误打印：

    ```
    subprocess.CalledProcessError: Command '('lsb_release', '-a')' returned non-zero exit status 1.
    ```

-   **可能原因**

    lsb\_release模块基于的python版本与现有python版本不一致

-   **解决办法**

    执行"find / -name lsb\_release"，找到lsb\_release位置并删除，如："sudo rm -rf /usr/bin/lsb\_release"


