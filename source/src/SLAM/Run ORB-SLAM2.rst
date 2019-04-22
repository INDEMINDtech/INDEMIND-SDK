.. _slam_orb_slam2实时:

`实时运行ORB_SLAM2 <https://github.com/INDEMINDtech/run.ORB>`_ 
==============================================================

.. note:: 

  本次Demo基于双目视觉惯性模组实时运行ORB，代码修改附件请跳转：
  https://github.com/INDEMINDtech/ORB-SLAM2-
  
一：环境介绍
---------------------------------------------------------------

系统：Ubuntu 16.04

ORB依赖库：Pangolin、OpenCV、Eigen3、DBoW2、g2o、ROS

二：下载
---------------------------------------------------------------------------------

SDK：http://indemind.cn/sdk.html

ORB-SLAM：https://github.com/INDEMINDtech/run.ORB

OpenCV3.4.3：https://opencv.org/releases.html

.. warning:: 

  OpenCV 3.4.3必须安装！！用户可前往我们提供的地址下载，安装教程可自行百度。

OpenCV大致安装教程如下：

将下载的Opencv 3.4.3压缩包解压缩，然后进入到OpenCV目录

执行

.. code-block:: bash

  mkdir build
  cd build
  cmake ..
  make -j(视PC线程而定,一般用2-6)
  sudo make install

三：安装SDK依赖环境
---------------------------------------------------------------

安装 cmake

.. code-block:: bash

  sudo apt-get install cmake

安装 google-glog + gflags

.. code-block:: bash

  sudo apt-get install libgoogle-glog-dev

安装 BLAS & LAPACK

.. code-block:: bash

  sudo apt-get install libatlas-base-dev

安装 SuiteSparse and CXSparse

.. code-block:: bash

  sudo apt-get install libsuitesparse-dev

四：执行
---------------------------------------------------------------

将下载的ORB_SLAM2放入到……SDK/demo_ros/src目录下

将下载的CMakeLists.txt替换到……SDK/demo_ros/src目录下

进入……SDK/Demo_ros/src/ORB_SLAM2/Vocabulary目录下，执行

.. code-block:: bash

  tar -xf ORBvoc.txt.tar.gz

进入……SDK/demo_ros/目录，打开终端执行

.. code-block:: bash

  catkin_make

打开一个新终端，执行

.. code-block:: bash

  roscore

进入……SDK/lib/1604（或1804）下，打开终端

执行

.. code-block:: bash

  sudo -s
  ./run.sh

进入……sdk/demo_ros/目录下，打开终端，执行

.. code-block:: bash

  ./stereo_euroc

教程至此结束。

.. tip:: 

  至此，INDEMIND双目视觉惯性模组运行ORB-SLAM工程部署完毕，请参考 `算法Demo <https://v.qq.com/x/page/x0846pm2qbj.html>`_ 