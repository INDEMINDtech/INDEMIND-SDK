.. _shendutuxiang:

获取深度图像
===============

该部分需要用户自己继承IAlgorithmPlugin类之后，写自己需要的相应算法，然后打包成lib文件，通过插件的形式实现调用，具体说明请参考SDK说明文档或参考demo调用示例。

.. warning:: 

  注意demo中将给出深度解算作为参考，用户可以根据需要进行修改

示意如下：

.. code-block:: C++

  void DepthImageCallback(int ret, void* pData, void* pParam) { } 
  pSDK->AddPluginCallback("depthimage", "depth", DepthImageCallback, NULL); 

.. image:: ../../tupian/SDK_19.png

.. tip:: 

深度解算算法的打开/关闭同4.6.6节中的SLAM，通过控制回调函数，进行算法的打开及关闭。深度解算结果：深度图，单位：mm
