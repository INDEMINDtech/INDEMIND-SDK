.. _chajian_开发示例:

插件开发规范
===================

每次升级，INTERFACE_MAJOR_VERSION版本号都会加1。SDK会根据版本号来确定是否使用新接口。每次升级内容及历史随文档记录同时更新。

以下接口函数应当定义为异步的，且需要在1ms之内返回：

.. code-block:: javascript

  virtual void AddPoseAsync(double time, const Pose& pose) = 0;
  virtual void AddImageAsync(double time, unsigned char* pLeft, unsigned char* pRight,int width,int height,int channel) = 0;
