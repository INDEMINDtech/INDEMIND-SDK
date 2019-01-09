.. _huoqubiaoding:

IMU标定信息
==============

.. code-block:: C++

  ·_Gyro compensation parameter 3X4（陀螺补偿参数）
  ·_Gyro bias（第1列，陀螺零偏），单位：°/s
  ·_Gyro compensation parameter（第2/3/4列，陀螺比例因子及正交矩阵乘积）
  ·_ACC compensation parameter 3X4（加速度计补偿参数）
  ·_Acc bias（第1列，加速度计零偏），单位：g
  ·_Acc compensation parameters（第2/3/4列，加速度计比例因子及正交矩阵乘积） 

参考-加速度计补偿模型（陀螺仪模型等同加速度计模型）：

.. code-block:: C++

  X=Ax0 + Kxx*Ax + Kyx*Ay + Kzx*Az
  Y=Ay0 + Kxy*Ax + Kyy*Ay + Kzx*Az
  Z=Az0 + Kxz*Ax + Kyz*Ay + Kzz*Az

.. tip:: 
  式中：X，Y，Z分别表示加表xyz轴输出原始数据；Ax，Ay，Az分别表示标准输入信息；Ax0，Ay0，Az0分别是加表xyz轴的零偏；Kxx，Kyy，Kzz分别为加表的比例因子；Kyx，Kzx，Kxy，Kzx，Kxz，Kyz分别是加表的交叉耦合误差。
