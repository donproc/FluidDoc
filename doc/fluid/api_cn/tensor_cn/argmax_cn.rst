.. _cn_api_tensor_argmax:

argmax
-------------------------------

.. py:function:: paddle.argmax(x, axis=None, dtype=None, keepdim=False, name=None)


该OP沿 ``axis`` 计算输入 ``x`` 的最大元素的索引。

参数
::::::::
    - **x** （Tensor） - 输入的多维 ``Tensor`` ，支持的数据类型：float32、float64、int16、int32、int64、uint8。
    - **axis** （int，可选） - 指定对输入Tensor进行运算的轴， ``axis`` 的有效范围是[-R, R），R是输入 ``x`` 的维度个数， ``axis`` 为负数时，进行计算的 ``axis`` 与 ``axis`` + R 一致。默认值为None, 将会对输入的 `x` 进行平铺展开，返回最大值的索引。
    - **dtype** （np.dtype|str）- 输出Tensor的数据类型，可选值为int32，int64，默认值为None，将返回int64类型的结果。
    - **keepdim** （bool，可选）- 是否保留进行最大值索引操作的轴，默认值为False。
    - **name** （str，可选） – 具体用法请参见 :ref:`api_guide_Name` ，一般无需设置，默认值为None。

返回
::::::::
``Tensor``, 如果设置 :attr:`dtype` 为 `int32` 时，返回的tensor的数据类型为 `int32` ，其它情况将返回的tensor的数据类型为 `int64` 。


示例代码
::::::::

.. code-block:: python

     import numpy as np
     import paddle

     paddle.disable_static()
     data = [[5,8,9,5],
             [0,0,1,7],
             [6,9,2,4]]
     x =  paddle.to_tensor(data)
     out1 = paddle.argmax(x)
     print(out1.numpy()) # 2
     out2 = paddle.argmax(x, axis=1)
     print(out2.numpy()) 
     # [2 3 1]
     out3 = paddle.argmax(x, axis=-1)
     print(out3.numpy()) 
     # [2 3 1]
