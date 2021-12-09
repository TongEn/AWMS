SalesObndCor
===================================

.. meta::
   :description lang=cn: Automate building, versioning, and hosting of your technical documentation continuously on Read the Docs.
服务介绍
   `SalesObndCor`_ 是一个出货模组批次出货的动态型服务,有自己的生命周期。

   本服务的消费者目前为前端AWMS系统,后续可能会有定时或自动批次出货功能。


.. _SalesObndCor: https://github.com/TongEn/SalesObndCor
.. Check out the :doc:`usage` section for further information, including
.. how to :ref:`installation` the project1.
.. git@github.com:TongEn/SalesObndCor.git

.. .... note::

所属模组
   出货模组

服务类型
   动态型

调用方式 
   1. 当CorManager收到截单出货请求后，会启用一个此服务的实例
   2. 当CorManager收到截单恢复请求后，会启用一个此服务的实例
   
销毁时机
   1. 当前批次下的所有出货单全部出库后
   2. 按批次截单还原后

服务维护者
   挑选1-2个团队的成员，作为该服务的负责人，登记联系方式，以便其他团队遇到问题能及时找到

环境定义
   + 开发环境
   + 生产环境
   + 测试环境

开发
   搭建开发环境
   运行服务
   定位问题

测试
   测试策略
   运行测试
   查看测试的统计结果

部署运维
   + 部署运维  
   + 日志访问  
   + 监控信息访问  
   + 告警信息访问 
   + CI/CD



.. toctree::
   :maxdepth: 3
   :hidden:
   :caption: 时序图:

   时序图/时序图

.. toctree::
   :maxdepth: 3
   :hidden:
   :caption: 状态图:

   状态图/状态图

.. toctree::
   :maxdepth: 3
   :hidden:
   :caption: API接口:

   API接口/Topics

.. toctree::
   :maxdepth: 4
   :hidden:
   :caption: VM清单:

   VM清单/index
   
   .. INITVM/初始化Vm
   .. Priority<PriorityVm/Prioritylist生成VM>
   .. Aggregate/Aggregate
   .. 总量保留VM/总量保留VM
   .. 分量保留VM/分量保留VM
   .. 物流出货单VM/物流出货单VM
   .. 拣货单VM/拣货单VM
   .. 汇总拣货单VM/汇总拣货单VM
   .. 播种单VM/播种单VM
   .. 托运单/托运单
   .. 截单恢复/截单恢复
   .. 截单还原/截单还原