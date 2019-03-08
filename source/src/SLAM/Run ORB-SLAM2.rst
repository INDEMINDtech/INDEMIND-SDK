.. _slam_orb_slam2实时:

`实时运行ORB_SLAM2 <https://github.com/raulmur/ORB_SLAM2>`_ 
==============================================================

.. note:: 

  本次Demo基于双目视觉惯性模组实时运行ORB，代码修改附件请跳转：
  https://github.com/INDEMINDtech/ORB-SLAM2-
  
1.下载SDK及安装
---------------------------------------------------------------

下载地址：http://indemind.cn/sdk.html


2.按照一般方式安装ORB-SLAM
---------------------------------------------------------------------------------

下载地址：https://github.com/raulmur/ORB_SLAM2

3.代码修改说明
---------------------------------------------------------------

下载地址：https://github.com/INDEMINDtech/ORB-SLAM2-

修改 ``stereo_euroc.cc`` 中的内容,程序见Git

添加 ``FileYaml.cc`` 到ORB_SLAM目录下的 ``src`` 中,程序见Git

添加 ``FileYaml.h`` 到ORB_SLAM目录下的 ``include`` 中,程序见Git

将 ``Tracking.cc`` 中的 ``fx,fy,cx,cy`` 进行修改：其值为去畸变后P_l的值

例如：

     float fx = 597.935;

     float fy = 597.935;

     float cx = 476.987;

     float cy = 442.158;

修改`` CMakeLists.txt`` 代码见Git

执行

.. tip:: 

  至此，INDEMIND双目视觉惯性模组运行ORB-SLAM工程部署完毕，请参考 `算法Demo <https://v.qq.com/x/page/x0846pm2qbj.html>`_ 