.. _analytics_imu:

源码
==================

为提高模组数据采集软件在不同平台的适应性，同时用户可以根据自己的需求做进一步开发，INDEMIND提供了数据采集软件的源码。

依赖部分
^^^^^^^^^^^^^^^^^^^^^^

Qt版本 5.10.1（Windows/Linux)

.. tip::
  下载地址： http://download.qt.io/archive/qt/5.10/5.10.1/

.. image:: ../../tupian/SDK_30.png

.. warning::
  Linux版本请注意安装 g++编译器 Open CV依赖

Windows:

Open CV版本open CV 3.1.0

.. tip::
  下载地址： https://opencv.org/opencv-3-1.html

官方安装 帮助文档

.. tip::
  下载地址：https://docs.opencv.org/3.1.0/d7/d9f/tutorial_linux_install.html

Linux:

Open CV版本open CV 3.4.0

.. tip::
  下载地址：https://opencv.org/opencv-3-4.html

官方安装 帮助文档

.. tip::
  下载地址：https://docs.opencv.org/3.4.0/d7/d9f/tutorial_linux_install.html

请根据实际版本选择安装 例：Ubuntu 18.04/ Ubuntu 16.04

.. code-block:: javascript

  sudo apt install libopencv-dev 

源码部分库连接部分

（请将下载好的Open CV依赖放入源码目录或自行修改pro文件）：

Eigen版本 eigen3.31

源码文档中已经包含

代码清单
^^^^^^^^^^^^^^^^^^^^^^

windows代码清单
---------------------------------------------

.. image:: ../../tupian/SDK_33.png

.. image:: ../../tupian/SDK_34.png

Linux代码清单
---------------------------------------------

Linux代码清单与Windows一致。


.. warning::
  编译阶段可能出现的问题：

.. code-block:: javascript

  can't find -lGL
  collect2:error：ld returned 1 exited status
	
这是由于缺少openGL库引起的，可以在终端输入

.. code-block:: javascript

  sudo apt-get install libgl1-mesa-dev


