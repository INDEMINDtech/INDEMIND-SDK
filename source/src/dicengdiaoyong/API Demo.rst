.. _API_Demo:

API Demo
=============================

aarch64:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**交叉编译工具下载**

下载地址：https://releases.linaro.org/components/toolchain/binaries/7.3-2018.05/aarch64-linux-gnu/

选择 gcc-linaro-7.3.1-2018.05-x86_64_aarch64-linux-gnu.tar.xz
    
解压交叉编译工具,可根据需要修改交叉编译工具(同时修改 ``build.sh`` 中  ``CROSS_COMPILE`` 选项)：

tar -xvJf gcc-linaro-7.3.1-2018.05-x86_64_aarch64-linux-gnu.tar.xz

编译：

.. code-block:: bash

  ./build.sh

运行：

.. code-block:: bash

  sudo ./main.sh width height camfps imufreq

  如：sudo ./main.sh 640 400 25 200

x86_64:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

编译：

.. code-block:: bash

  ./build.sh

运行：

.. code-block:: bash

  sudo ./main.sh width height camfps imufreq
  如：sudo ./main.sh 640 400 25 200
