# ICND Frame
資料框的內容解讀 (根據 IEEE 802.3 和 802.2 標準)

* MAC sublayer (IEEE 802.3)


      +----------+----------+-----------+--------+----------------+-----+
      | Preamble | Dest Add | Sorce Add | Length | Variable (Data)| FCS |
      +----------+----------+-----------+--------+----------------+-----+
      /* 第一欄位在於通知第二欄位接收者：『 哎喔！資料框進來囉～～～ 』*/
      /* 實體位址會被燒錄在網路介面卡中的唯讀記憶體內 */
      /* 網路介面卡啟動時，實體位址也會被載入到隨機存取記憶體內 */
      /* 發送端永遠都是單點位址 */
      /* 接受端可為單點、多點、廣播位址(flooding 影響頻寬)、除了自己（avoid loop） */
      /* FCS 為 Frame Checksum Sequence, 資料框（序號）檢查碼，內含 CRC (循環冗余)檢查值，
         由發送端運算出來，附加在資料框尾端的特定值，接收端收到 frame 後，經由對 CRC 
         值得重新計算與核對，便可確認收到的資料框是否在傳輸中發生過錯誤。 */
         
* Frame Checksum

http://www.tsnien.idv.tw/Network_WebBook/chap18/18-5%20FDDI%20訊框格式.html


* Cyclic Redundancy Check

https://zh.wikipedia.org/wiki/循環冗餘校驗 (某種提供驗證傳輸與儲存是否符合的雜湊函數)

            Input ---> Hash Function ---> Hash Sum


* LLC sublayer - SAP (IEEE 802.2)
   
   
      MAC
    
      +----------+----------+-----------+--------+----------------+-----+
      | Preamble | Dest Add | Sorce Add | Length | Variable (Data)| FCS |
      +----------+----------+-----------+--------+----------------+-----+
      
                                                          |
                                                          |
                                                          |
                                                          V                                                    
                             
                               +----------+----------+------+----------------+
                               | Dest SAP | Sorce SAP| ctrl | Variable (Data)| 
                               +----------+----------+------+----------------+
                               /* 單純為 服務存取點 */
                               
  
 * LLC sublayer - SNAP (IEEE 802.2)
 
 
 
            +----------+----------+-----------+--------+----------------+-----+
            | Preamble | Dest Add | Sorce Add | Length | Variable (Data)| FCS |
            +----------+----------+-----------+--------+----------------+-----+

                                                                |
                                                                |
                                                                |
                                                                V

              +----------+----------+------+--------+-----------+----------------+
              | Dest SAP | Sorce SAP| ctrl | OUI ID | Type Code | Variable (Data)|
              +----------+----------+------+--------+-----------+----------------+
              /* Type code 即類別碼，藉此分辨出是否為子網路存取通訊協定 */
