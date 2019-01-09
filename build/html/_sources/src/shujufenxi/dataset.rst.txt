.. _yonghuruanjianjieshao:

用户软件介绍
==================

为方便用户基于INDEMIND模组采集数据，进行SLAM等算法开发，开发模组数据采集软件，采集模组图像、IMU数据，并保存成EuRoC数据集格式。

.. tip:: 
  下载地址:
  https://github.com/indemind/ModuleInfo_Win64

.. note:: 
  Linux客户端下载地址：https://github.com/indemind/ModuleInfo_Linux，软件使用方式与windows版一致。
  （建议使用环境：Windows10及Linux18.04/ Linux16.04）
  （图像频率 50hz | imu数据 1000hz）
  （请保证磁盘读写性能在50M/S,采集图像时，请开启高性能模式，笔记本非接电源模式下，磁盘读写性能会有下降，请注意设备内存，避免增长过快，带来的卡死问题，建议使用固态硬盘）
  由于IMU和 图像帧率较高，为保证数据稳定，Linux客户端建议在超级管理员权限下操作,使用 “sudo  ./ModuleInfo” 运行。

