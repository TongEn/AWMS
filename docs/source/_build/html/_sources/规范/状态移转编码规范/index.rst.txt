状态移转编码规范
===================

狀態輚移圖Table:
    **curState**:			COR 或 VM 當下的狀態 (編碼原則參考下述 State 編碼)

    **eventCode**:			當下的事件編號 (編碼原則參考下述 EventCode 編碼)

    **action**:	
        **actionType**:		Action 的類別 (COR, VM or Visitor)

        **actionBody**:	Akka(COR,VM)	實際呼叫的 COR, VM 或 Visitor 的 class name

        **Publisher**:	呼叫 PublisherVm

        **Method**:	呼叫的 methhod name

    **args**:			呼叫上述的 action 所須引入的參數

    **nextState**:			COR 或 VM 下階段的狀態 (編碼原則參考下述 State 編碼)
			
			
State 編碼 (自左而右結構)：		
	第 1 碼： S，代表 State	

	第 2,3 碼：CorCode，Cor的編號，SalesOrderCor 編號 01、SalesOBndCor 編號 02，InventoryCor 編號 03	

	第 4,5,6 碼：StateCode，該 CorCode 的狀態編號		
			
			
			
EventCode 編碼 (自左而右結構)：		
	第 1 碼： E，代表 EventCode		

	第 2,3 碼：CorCode，Cor的編號，SalesOrderCor 編號 01、SalesOBndCor 編號 02，InventoryCor 編號 03

	第 4,5,6 碼：StateCode，該 CorCode 的狀態編號	
    	
	第 7,8 碼：EventCode，該 StateCode 的事件編號		


Cor编码:
    01:SalesOrderCor  

    02:SalesOBndCor  

    03:InventoryCor  