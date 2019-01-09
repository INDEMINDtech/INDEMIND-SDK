.. _shuju_shebeixinxi:

获取设备信息
==============

获取插件相关信息部分是用户通过继承virtual PluginInfo GetPluginInfo()=0;重写该函数用于获取插件基本信息。

插件信息获取函数定义如下：

.. code-block:: c++

  ImrModuleDeviceInfo GetModuleInfo();

插件基本信息结构定义如下：

.. code-block:: c++

  struct ImrModuleDeviceInfo {
  char _id[32]; 		//硬件ID
  char _designer[32];   	//开发者
  char _firmware_version[32]; 	//固件版本
  char _hardware_version[32]; 	//硬件版本
  char _lens[32]; 		//摄像头型号
  char _imu[32]; 		//IMU型号
  char _viewing_angle[32]; 	//视场角
  char _baseline[32]; 		//基线长度
  };

示例如下：

.. code-block:: c++

  1）	厂家信息；
  a)	INDEMIND
  2）	固件版本；
  a)	1.1.1
  3）	硬件版本；
  a)	1.1.1
  4）	镜头型号；
  a)	OV9281
  5）	IMU型号；
  a)	ICM20602
  6）	视场角；
  a)	H：120°，V：75°
  7）	基线长度。
  a)	120mm
  8）	设备ID
  a)	0x730103E8

更详细的说明请参考demo调用示例。
