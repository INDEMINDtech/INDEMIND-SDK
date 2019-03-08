.. _slam_DSO:

`DSO_SLAM <https://github.com/JakobEngel/dso>`_ 
==============================================================

.. note:: 

  本次Demo基于双目视觉惯性模组离线运行DSO，实时运行Demo待更新
  
1.下载DSO
---------------------------------------------------------------

下载地址：https://github.com/JakobEngel/dso


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

4.DSO安装配置
---------------------------------------------------------------

编译前准备：

.. code-block:: bash

  sudo apt-get install libsuitesparse-dev libeigen3-dev libboost-all-dev
  sudo apt-get install libopencv-dev
  sudo apt-get install zlib1g-dev
  cd dso/thirdparty
  tar -zxvf libzip-1.1.1.tar.gz
  cd libzip-1.1.1/
  ./configure
  make
  sudo make install
  sudo cp lib/zipconf.h /usr/local/include/zipconf.h

CMakeLists.txt文件内添加：

.. code-block:: bash

  add_definitions(-DBOOST_ERROR_CODE_HEADER_ONLY)

camera.txt的修改：

.. code-block:: bash

  EquiDistant fx fy cx cy k1 k2 r1 r2
  in_width in_height
  "crop" / "full" / "fx fy cx cy 0"
  out_width out_height

.. Tip:: 

  其中fx fy cx cy k1 k2 r1 r2

  in_width in_height需根据实际情况自行配置。



编译

.. code-block:: bash

  cd dso
  mkdir build
  cd build
  cmake ..
  make -j4


执行

.. code-block:: bash

  bin/dso_dataset files=XXXXX/data/images calib=XXXXX/data/camera.txt preset=0 mode=0

.. Tip:: 

  files后的XXXXX/data/images为图像路径；calib=XXXXX/data/camera.txt为配置文件路径。

至此，INDEMIND双目视觉惯性模组运行ORB-SLAM工程全部部署完毕，请参考 ：

`室内Demo <https://v.qq.com/x/page/q07729x79j3.html>`_ 

`室内地税平面Demo <https://v.qq.com/x/page/r0772lkv7yl.html>`_ 

`室外Demo <https://v.qq.com/x/page/d07726x39cm.html>`_ 
