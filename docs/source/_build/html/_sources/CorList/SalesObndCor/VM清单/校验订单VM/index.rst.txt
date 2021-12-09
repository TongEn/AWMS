================================
校验订单VM【CheckBatchVm】
================================
.. note::
   订单COR会对订单会进行基础校验和过滤，截单时不再进行订单基础校验

1.校验是否订单LIST是否为空【CheckListExistVistor】
  
::

    #'沒有出貨單需要截單!'
    dbo.FN_SHARE_GETMESSAGE('F0402M003',@PI_LANG) 
    

2.校验出貨暫存區儲位是否存在【CheckOutTempSpacecellExistVistor】

::
    
    #'出貨暫存區儲位有{0}個,請檢查！'
    dbo.FN_SHARE_GETMESSAGE('CL00M061',@PI_LANG)+replace(dbo.FN_SHARE_GETMESSAGE('F0302M023',@PI_LANG),'{0}',CONVERT(VARCHAR(10),@CNT))

3.校验商品是否已停用【CheckProductEnableVistor】

::
    
    #商品[{0}]已停用，不允許截單!
    replace(dbo.FN_SHARE_GETMESSAGE('F0402M20',@PI_LANG),'{0}',@PRODUCTNO)


4.原箱出货的品种，出货量必须以箱为单位出货【CheckOriBoxQtyVistor】
::
    
    #存在沒有按原箱量的倍數出貨的原箱出貨品種!
    dbo.FN_SHARE_GETMESSAGE('F0402M019',@PI_LANG) +'['+@ORDNO+']' 

5.校验直配暫存區儲位是否存在【CheckSeedTempSpacecellExistVistor】
::
    
    #直配暫存區儲位有{0}個,請檢查！
    dbo.FN_SHARE_GETMESSAGE('CL00M060', @PI_LANG) + REPLACE(dbo.FN_SHARE_GETMESSAGE('F0302M023', @PI_LANG), '{0}', CONVERT(VARCHAR(10), @CNT)) 

6.校验客户是否设定路线【CheckCustomerRouteExistVistor】
::
    
    #客户[{0}]未设定路线，不允许截单!
    REPLACE(dbo.FN_SHARE_GETMESSAGE('F0402M024', @PI_LANG), '{0}', @CUSTOMNO)

7.校验客户是否设定播种储位【CheckCustomerSeedSpacecellExistVistor】
::
    
    #客戶[{0}]未設定播種儲位，不允許截單!
    REPLACE(dbo.FN_SHARE_GETMESSAGE('F0402M026', @PI_LANG), '{0}', @CUSTOMNO)
