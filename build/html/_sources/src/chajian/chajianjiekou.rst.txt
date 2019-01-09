.. _chajian_chajianjiekou:

插件接口类型
==================

插件以C++开发，对插件开发者提供一份接口头文件AlgorithmPlugin.h，其中INTERFACE_MAJOR_VERSION为当前插件接口的版本号，当接口升级的时候提供的新接口会升级该宏，以兼容旧版本的插件。

接口分为基本的逻辑接口和验证性接口。逻辑接口提供算法调用方面的逻辑操作，验证性接口主要提供插件相关信息及第三方插件开发者的验证性需求等。

逻辑接口及功能简要描述
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: javascript

  indem::IAlgorithm* AlgorithmFactory();

创建算法插件实例。该函数是动态库载入接口，通过该接口创建对应的插件实例，之后SDK系统可以通过它进行插件的初始化等操作。

.. code-block:: javascript

  virtual const char* Name() = 0;

插件名，插件的唯一标识，不能跟其他插件同名。

.. code-block:: javascript

  virtual bool Init(CamaraParams pParams) = 0;

插件的初始化

.. code-block:: javascript

  virtual void AddPoseAsync(double time, const Pose& pose) = 0;

SDK系统会以默认的频率调用该接口，将模组的最终位姿（即融合后结果）传给插件

.. code-block:: javascript

  virtual void AddImageAsync(double time, unsigned char* pLeft, unsigned char* pRight,int width,int height,int channel) = 0;

SDK系统会以默认的频率(Hz)调用该接口，模组的图像实时传给插件


.. code-block:: javascript

  virtual int AddCallback(const char* name, PluginCallback pCallback, void* pParam) = 0;

为插件装载回调函数。该回调函数最终将对SDK用户公开，即发布

.. code-block:: javascript

  virtual bool InvokeCommand(const char* commandName, _IN_ void* pIn, _OUT_ void* pOut);

执行指定的操作命令

.. code-block:: javascript

 virtual void Release() = 0;

插件资源释放

验证性接口及功能简要描述
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: javascript

  virtual PluginInfo GetPluginInfo()=0;

获取插件基本信息，详细参考DEMO。