.. _slam_vins:

高精度Vi-SLAM
============================================================================


SLAM (Simultaneous Localization and Mapping)，即时定位与地图构建。SDK 提供的 Vi-SLAM 包含有前端特征提取，匹配，后端优化，闭环、建图和重定位功能。

Vi-SLAM 支持 Windows 及 Linux 平台，有效的节约算法开发周期及成本，让开发者可以 迅速调试及部署，直接应用于机器人、无人机、AGV、AR/VR 等领域。

Vi-SLAM 工作过程中的特征点匹配显示状态控制在文件“slam_imp.yaml”中， displayImages: true 表示打开特征点匹配显示，displayImages: false 表示关闭特征点匹配显示， 该状态默认开启。

Vi-SLAM开启运行
^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: C++

  MRCONFIG config = { 0 }; 
  config.bSlam = true; //true 开启 SLAM,false 不开启 SLAM

Vi-SLAM关闭
^^^^^^^^^^^^^^^^^^^^^^^^ 

当运行 SDK，但是不需要 SDK 自带 SLAM 运行时，将 MRCONFIG 结构体中的 bSlam 设置 为 false。

效果Demo示意
^^^^^^^^^^^^^^^^^^^^^^^^ 


.. image:: ../../tupian/SDK_20.png