后端架构
=============

AWMS 
    完整物流服務

    最先進技術平台

    最豐富物流知識

    最彈性物流運作
    
    最寬廣鍵值設計


平台技术架构
---------------

.. note:: 

    Kubernetes (K8S) + Docker：雲運算及微服務

    Kafka：訊息佇列 (message queue) 分散式運算

    Redis：內存資料庫 In-memory database 快速查詢

    mongoDB：長存資料庫 persistence database 長期儲存

说明:
    1. Docker 間透過 Kafka 訊息交換啟動運算

    2. Docker 間透過 Redis 共享資料

    3. Redis資料的 Key 透過 Kafka 交換

    4. Docker 內部運算單元以 Akka 實作。初步包括下列Akka:

        4.0 每個 Cor 有一個 Akka ，作為 Cor 的控制器 CorController。負責分派所接到訊息的工作分派。

        4.1 Subscriber 是一個 Akka，將接到的訊息交CorController。

        4.2 Publisher 是一個 Akka，將 CorController 傳來的訊息發布給 Topic。

        4.3 每個 VM  是一個 Akka，作為 VM 的控制器 VMController。 CorController接到的訊息交給Akka 所接到的訊息，由 VM 的控制器 VMController 處理。

        4.4 磁碟 IO  是一個 Akka

        4.5 Subscriber 接到訊息後將訊息交給 CorController，CorController 再將訊息傳給 VMController


.. image:: img/整合微服務.png

.. image:: img/內存資料架構.png

.. image:: img/資料庫架構.png

.. image:: img/平台技術架構.png

物流知识架构
---------------

運算架構
>>>>>>>>>>>

.. note:: 

    1. 階層式運算架構
    2. 積木式組合
    3. 編輯式管理

運算架構頂層
    物流知識鏈

    包含一組最高層物流知識節點 (Chain of Responsibility，Cor) 

積木式組合
    每一個物流知識節點 (Cor)
        1. 拆分成數十個到數百個運算單元 (visitor)
        2. 功能相近的運算單元合成一組，交由一個運算管理員 (visitor manager) 管理
        
Cor、VM、Visitor 共同組成物流運算架構

運算架構與微服務
    一個物流知識節點 (Cor) 對應一個微服務(microservice)

    一個 Cor 管理多個 VM

    一個 VM 管理多個 visitor

    Cor、VM、visitor 均可透過文字，設定其啟動時所需的參數


資料架構
>>>>>>>>>>>

1 以鍵值對(key-value pair，KVP) 紀錄物流的資料內容

內存資料庫 Redis 與長存資料庫 mongoDB 高度整合

彈性化鍵值設計
    透過可編輯的參數和流程，實現可編輯的物流系統
    鍵值設計是物流知識「資料面」的具體實現

    依據下列條件設計鍵值
        物流營運商 

        物流中心  

        交易營運商

        商品供應商

        商品製造商

        商品：時效控制、溫度控制、顏色尺寸控制、政府監管控制、外型包裝控制

        合約：
            商流合約： 採購合約、銷售合約、退貨合約、廠退合約等等

            物流作業合約：揀貨單、補貨單、調整單、加工單、檢驗單、託運單、報廢單等等

        促銷：指定時段、指定客層、指定商品、指定區域、指定金額、指定數量

    鍵值對是搭配 Redis + mongoDB 的最佳選擇

    呈現豐富的物流資料

    實現高速讀寫機制

    落實物流高彈性應用






