.. _biaoding_标定数据:

标定数据
===================

插件初始化的时候会将设备标定参数传入进来，以执行必要的操作。其中数据结构如下所示：

.. code-block:: javascript

  struct CamaraParams {
  int _width;         //图像宽
  int _height;        //图像高
  int _channel;       //通道数

  double _Kl[9];      //3X3 左相机内参矩阵
  double _Kr[9];      //3X3 右相机内参矩阵
  double _Dl[4];      //4X1 左相机畸变差校正参数
  double _Dr[4];      //4X1 右相机畸变差校正参数
  double _Pl[12];     //3X4 基线校正后左相机投影矩阵
  double _Pr[12];     //3X4 基线校正后右相机投影矩阵
  double _Rl[9];      //3X3 基线校正后左相机旋转矩阵
  double _Rr[9];      //3X3 基线校正后左相机旋转矩阵
  double _TSCl[16];   //4X4 左相机系到传感器坐标系的变换
  double _TSCr[16];   //4X4 右相机系到传感器坐标系的变换
  /*  加计参数,3X4矩阵,每个元素如下
  *    Ax0  11  12  13
  *    Ay0  21  22  23
  *    Az0  31  32  33
  */
  double _Acc[12];
  /*  陀螺参数,3X4矩阵,每个元素如下
  *    Gx0  11  12  13
  *    Gy0  21  22  23
  *    Gz0  31  32  33
  */
  double _Gyr[12];
  };

