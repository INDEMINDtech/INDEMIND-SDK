.. _huoqutuxiangshuju:

获取双目图像数据
====================

注册图像回调函数，然后调用该回调函数，来获取所需要的数据。具体如下：

定义回调函数

.. code-block:: C++

  void ImageCallback(double time, unsigned char* pLeft, unsigned char* pRight, int width, int height, int channel, void* pParam){}

调用回调函数

.. code-block:: C++

  pSDK->RegistModuleIMUCallback(ImageCallback,param); 

.. tip:: 
  图像数据为灰度图，时间单位为ms。