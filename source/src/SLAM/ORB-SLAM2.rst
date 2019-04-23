.. _slam_orb_slam2:

`离线运行ORB_SLAM2 <https://github.com/INDEMINDtech/ORB_SLAM2_general>`_ 
==============================================================

.. note:: 

  本次Demo基于双目视觉惯性模组离线运行ORB
  
1.下载
---------------------------------------------------------------

ORB-SLAM2下载地址：https://github.com/INDEMINDtech/ORB_SLAM2_general

SDK下载地址：http://indemind.cn/sdk.html

ModuleInfo图像采集软件下载地址：https://github.com/INDEMIND/ModuleInfo_Linux

.. tip:: 

  详细使用见模组信息采集（客户手册）

2.编译执行流程
---------------------------------------------------------------

1）使用ModuleInfo进行数据采集，获得双目和imu数据集，将数据集拷贝到ORB_SLAM2目录下

2）SDK依赖库编译

安装 cmake

.. code-block:: bash

  sudo apt-get install cmake

安装 google-glog + gflags

.. code-block:: bash

  sudo apt-get install libgoogle-glog-dev

安装 BLAS & LAPACK

.. code-block:: bash

  sudo apt-get install libsuitesparse-dev

安装 SuiteSparse and CXSparse

.. code-block:: bash

  sudo apt-get install libsuitesparse-dev

编译器

.. warning:: 

  使用 Ubuntu 16.04 编译 demo 程序需要使用 GCC5.4 版本,否则可能链接失败。
  
  使用 Ubuntu 18.04 编译 demo 程序需要使用 GCC7.3 版本,否则可能链接失败。

3）SDK编译

.. code-block:: bash

  cd build
  cmake ..
  make

4）SDK执行

把刚才编译的可执行文件 ``TestIndem 拷贝到刚才解压 SDK 的lib 目录下的 1604 目录下`` ，在 lib/1604 目录下使用 ``sudo ./TestIndem.sh`` 命令启动程序。

TestIndem 和 TestIndem.sh 需要可执行权限。 使用命令 ``chmod 777 TestIndem`` 和 ``chmod 777 TestIndem.sh`` 进行修改。

为了提高系统稳定性,请运行时使用超级用户(root 权限)运行,或者使用 ``sudo ./程序名`` 运行,例如 DEMO 运行 ``sudo ./TestIndem.sh`` 。

.. warning:: 

  在 Ubuntu 18.04 上使用 GCC7.3 编译 demo 的时候,需要把 demo 里的 CMakeLists.txt 的1604 改成 1804 才能编译成功，编译成功后把 TestIndem 拷贝到 lib/1804 下运行。

最后将 ``1604目录`` 下的 ``headset.yaml`` 拷贝到 ``ORB_SLAM2`` 目录下。

5）ORB-SLAM2依赖库编译

Pangolin安装

.. code-block:: bash

  sudo apt-get install libglew-dev
  sudo apt-get install cmake
  sudo apt-get install libboost-dev libboost-thread-dev libboost-filesystem-dev
  git clone https://github.com/stevenlovegrove/Pangolin.git
  cd Pangolin
  mkdir build
  cd build
  cmake -DCPP11_NO_BOOST=1 ..
  make -j

OpenCV安装

.. code-block:: bash

  sudo apt-get install build-essential libgtk2.0-dev libavcodec-dev libavformat-dev libjpeg.dev libtiff4.dev libswscale-dev libjasper-dev

https://opencv.org/releases/page/2/网站下 选择3.4.3的Sources，点击下载解压

.. code-block:: bash

  mkdir build
  cd build
  cmake ..
  sudo make -j4
  sudo make install

Eigen安装

.. code-block:: bash

  sudo apt-get install libeigen3-dev
  sudo updatedb

6) ORB编译

.. code-block:: bash

  cd ORB_SLAM2
  chmod +x build.sh
  ./build.sh

7）执行

.. code-block:: bash

  ./Examples/Stereo/stereo_euroc Vocabulary/ORBvoc.txt Examples/Stereo/EuRoC.yaml PATH_TO_SEQUENCE/mav0/cam0/data PATH_TO_SEQUENCE/mav0/cam1/data Examples/Stereo/EuRoC_TimeStamps/SEQUENCE.txt

至此，INDEMIND双目视觉惯性模组运行ORB-SLAM工程全部部署完毕，请参考 `算法Demo <https://v.qq.com/x/page/t0815wifet5.html>`_ 