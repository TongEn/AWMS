==============
物流出货单【OutboundForm】
==============
.. 本文档记录了 **拣货单VM** 的相关资讯: 
物流出货单 **生成** 、 **查询** 、 **修改** 、 **出货** 、 **截单还原**  相关VM和Vistor

物流出货单生成VM【OutboundFormGenerateVm】
--------------
按订单类别拆单
>>>>>>>>>>>>>>>>>>>>>>>
   物流出货单生成依相同客户不同订单类别拆单


按配送地址拆单
>>>>>>>>>>>>>>>>>>>>>>>
   物流出货单生成依相同客户不同配送地址拆单


按收货人拆单
>>>>>>>>>>>>>>>>>>>>>>>
   物流出货单生成依相同客户不同收货人拆单

按配送方式拆单
>>>>>>>>>>>>>>>>>>>>>>>
   物流出货单生成依相同客户不同配送方式拆单

按上位车次号拆单
>>>>>>>>>>>>>>>>>>>>>>>
   物流出货单生成依相同客户不同上位车次号拆单   

.. note::
   订单不存在多次出货时，订单与物流出货单是多对一的关系
   订单存在多次出货时，订单与物流出货单是多对多的关系

物流出货单查询VM【OutboundFormQueryVm】
---------------------
.. note::
   提供当前截单批次的物流出货单资料查询

筛选Vistor清单
>>>>>>>>>>>>>>>
1. 仓库编号
2. 截单批次
3. 客户编号
4. 地址
5. 来源单号
6. 订单号
7. 上位车次号
8. 流程状态
9. 建立日期
10. 商品编号
11. 物流出货单号

物流出货单修改VM【OutboundFormModifyVm】
------------
.. note::
   1.	物流出货单不直接拣货、检验、停出，通过子拣货单的拣货、检验、停出修改物流出货单单据状态

物流出货单修改
>>>>>>>>>>>>>>>
   主要是单据状态、数量的修改

物流出货单出货VM【OutboundFormConfirmVm】
------------
.. note::
   适用于不须运输管理作业的流程。例如：医院内出货流程

物流出货单出货确认
>>>>>>>>>>>>>>>
   库存扣除，当前截单批次下所有的物流出货单出货确认后整个截单批次结束




物流出货单截单还原VM【OutboundFormRestoreVm】
--------------------
物流出货单截单还原是否允许判定
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
   是否已经进行了拣货

物流出货单截单还原确认
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
   截单还原确认：物流出货单取消
