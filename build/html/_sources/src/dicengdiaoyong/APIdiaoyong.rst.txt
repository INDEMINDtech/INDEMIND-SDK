.. _API_diaoyong:

API调用
=========================

.. note:: 

以下是基本函数调用说明，具体操作参考main.c

下载地址：https://github.com/INDEMIND/Driver_Linux

indem命名空间
---------------------------------------------------------------

.. code-block:: bash

  using namespace indem;

调用DriverFactory()函数返回api对象指针

.. code-block:: bash

  如：IDriverInterface *driver = DriverFactory();


设置回调函数
---------------------------------------------------------------

**根据以下几个定义，实现三个回调函数，用于接收相关数据，回调函数参数定义可参考include/DriverInterface.h**

.. code-block:: bash

  typedef void(*DriverCameraDataCallback)(cameraData* data);
  typedef void(*DriverIMUDataCallback)(IMUData* data);
  typedef void(*DriverHotplugCallback)(bool bArrive);

  如：
  void ImuCallBackFunction(IMUData* data)；
  void CameraCallbackFunction(cameraData* data)；
  void HMDHotplugCallback_func (bool bArrive)；

**获取标定参数**

函数原型:

.. code-block:: bash

  bool GetModuleParams(int& version, unsigned char* params, size_t& len)
  version: 模组内部固件版本标记，备用
  params:    模组信息标定信息存放缓冲区
  len: 接收到数据的长度，单位:byte
  return: true 获取参数成功， false 获取参数失败

调用如下:

.. code-block:: bash

  int version = 255;
  size_t info_size = 0;
  unsigned char *module_info = new unsigned char[(sizeof(struct ModuleParameters))];
  struct ModuleParameters moddule_param;//标定参数等信息
  driver->GetModuleParams(version, module_info, info_size);
  memcpy(&moddule_param, module_info, sizeof(struct ModuleParameters));

**调用设备打开接口，打开模组**

函数原型:

.. code-block:: bash

  bool Open(int imuFreq=1000,int imgFreq=50, IMAGE_RESOLUTION resolution= RESOLUTION_DEFAULT)

  param1: imu数据频率(imuFreq) 目前只支持 <1000hz 且需要满足 1000/imuFreq 为>0 整数（imu寄存器中是以时间间隔为单位配置的）

  param2: 图像频率 目前支持 25、50

  param3: 图像分辨率 参数只支持 RESOLUTION_1280（1280x800x2）、RESOLUTION_640（640x400x2）

  return：false 设备打开失败

  调用如下:

  driver->Open(1000, 50, RESOLUTION_1280);

**调用回调函数接口配置回调函数**

.. code-block:: bash

  如： 
  driver->SetCameraCallback(CameraCallbackFunction);
  driver->SetIMUCallback(ImuCallBackFunction);
  SetHotplugCallback(HMDHotplugCallback_func);

更多内容请参考main.c
