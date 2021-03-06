﻿.. _slam_Vins:

`VINS_Mono <https://github.com/heguixiang/Remove_ROS_VINS>`_ 
=============================================================

.. note:: 

  本次Demo基于双目视觉惯性模组离线运行VINS，实时运行Demo待更新
  
1.下载VINS
---------------------------------------------------------------

下载地址：https://github.com/heguixiang/Remove_ROS_VINS


2.下载INDEMIND双目视觉惯性模组SDK
---------------------------------------------------------------------------------

INDEMIND双目视觉惯性模组的SDK为开发者提供了丰富的开发工具与辅助，省去了开发者对相机的标定、数据同步等开发工作，加速开发进程。因此，我们直接根据自身操作系统直接下载INDEMIND双目视觉惯性模组的SDK即可。

下载地址：http://indemind.cn/sdk.html

3.使用SDK
---------------------------------------------------------------

创建SDK对象

.. code-block:: bash

  CIMRSDK* pSDK = new CIMRSDK();

设置使用的 SLAM

.. code-block:: bash

  MRCONFIG config = { 0 };
  config.bSlam = true; //true 开启 SLAM,false 不开启 SLAM

获取模组标定信息

.. code-block:: bash

  CameraCalibrationParameter param;

获取模组图像数据

.. code-block:: bash

  pSDK->RegistModuleCameraCallback(SdkCameraCallBack,NULL);

获取 SLAM 结果

.. code-block:: bash

  pSDK->RegistModulePoseCallback(sdkSLAMResult,NULL);

将param的参数写入文件中

.. code-block:: bash

  ofstream out("./datafile.txt");

  param = pSDK->GetModuleParams();	//查询模组标定信息
  out<<"param.width: "<<param._width<<std::endl;		//图像宽
  out<<"param.width: "<<param._height<<std::endl;	//图像高
  out<<"param.width: "<<param._channel<<std::endl;	//通道数

如上，写入相机内外参

释放资源

.. code-block:: bash

  pSDK->Release();
  delete pSDK;

编译

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

编译器

.. warning:: 

  使用 Ubuntu 16.04 编译 demo 程序需要使用 GCC5.4 版本,否则可能链接失败。

  使用 Ubuntu 18.04 编译 demo 程序需要使用 GCC7.3 版本,否则可能链接失败。


编译

.. code-block:: bash

  cd build
  cmake ..
  make

执行

把刚才编译的可执行文件 ``TestIndem 拷贝到刚才解压 SDK 的lib 目录下的 1604 目录下`` ，在 lib/1604 目录下使用 ``sudo ./TestIndem.sh`` 命令启动程序。

TestIndem 和 TestIndem.sh 需要可执行权限。 使用命令 ``chmod 777 TestIndem`` 和 ``chmod 777 TestIndem.sh`` 进行修改。

为了提高系统稳定性,请运行时使用超级用户(root 权限)运行,或者使用 ``sudo ./程序名`` 运行,例如 DEMO 运行 ``sudo ./TestIndem.sh`` 。

.. warning:: 

  在 Ubuntu 18.04 上使用 GCC7.3 编译 demo 的时候,需要把 demo 里的 CMakeLists.txt 的1604 改成 1804 才能编译成功，编译成功后把 TestIndem 拷贝到 lib/1804 下运行。

4.VINS参数设置及矫正
---------------------------------------------------------------

在estimator_node.cpp中添加去畸变命令

.. code-block:: bash

  cv::fisheye::initUndistortRectifyMap(K_l,D_l,R_l,P_l.rowRange(0,3).colRange(0,3),cv::Size(cols_l,rows_l),CV_32FC1,M1l,M2l);

将去畸变后，获取到的P_l值传给/home/indemind/SDKbackup/indem/u/vins/src/config/euroc/euroc_config.yaml中的 ``fx、fy、cx和cy`` 。

编译前要下载的库

 1. Ceres Solver
 2. Opencv 3.1
 3. Eigen 3.2.0
 4. boost
 5. Pangolin

编译

.. code-block:: bash

  mv Remove_ROS_VINS src
  ./generate.sh


执行

.. code-block:: bash

  cd VINS_Workspace
  ./src/vins_estimator/build/vins_estimator ./src/config/euroc/euroc_config.yaml ./data/mav1/cam0/data ./data/mav1/filename.txt ./data/mav1/imu0/data.csv

至此，INDEMIND双目视觉惯性模组运行ORB-SLAM工程全部部署完毕，请参考 `算法Demo <https://v.qq.com/x/page/o082495ojpb.html>`_ 