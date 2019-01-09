.. _chajian_diaoyongshixu:

接口调用时序
===========================

SDK首先载入动态库，调用AlgorithmFactory方法，创建算法插件实例。之后调用插件实例的Init方法，将硬件标定参数传递给算法实例。至此，插件初始化完毕。

之后SDK会以硬件自身的频率调用AddPose函数和AddImage函数，将结算后得到的位姿和图像传给插件。

SDK能够打通插件开发者与SDK使用者之间的通道。如下图所示，SDK通过AddCallback向插件添加数据回调函数，插件开发者有能力将算法结果通过回调函数以自定义频率传给SDK用户。SDK用户可以通过SDK直接调用InvokeCommand，执行算法插件特有的操作。

.. image:: ../../tupian/SDK_17.png