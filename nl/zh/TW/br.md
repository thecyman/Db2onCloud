---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-02"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# 備份及還原
{: #br}

針對付費方案，每天會進行資料庫的加密備份。針對過去的 14 天，會保留每天的當日備份。
{: shortdesc}

除了標準備份之外，您也可以使用 [Time Travel Query ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} 來保留其他用途用的歷程資料，例如舊資料的立即查詢，或是簡化審核。您也可以使用 IBM Data Studio 或任何 Db2 工具來執行自己的匯出作業。
 
如需復原點還原的相關資訊，請參閱[復原點還原](#point-in-time)。

所有付費方案一般都會利用 IBM Cloud Object Storage (COS)，在 3 個不同資料中心保留異地的備份。不過，雪梨及特定較小型的資料中心目前可能不支援使用 IBM COS 進行異地抄寫。請參閱您地區的 [IBM COS 文件](/docs/services/cloud-object-storage/basics/endpoints.html#select-regions-and-endpoints)，以判斷哪些地區支援異地抄寫。

<!-- Retained backups are used by IBM for system recovery purposes in the event of a disaster or system loss. Use the [Time Travel Query ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} to keep historical data for your own purposes. In addition, you can also perform your own exports using IBM Data Studio or any Db2 tool. -->

<!-- To store your backups offsite at a remote storage site, make a request to IBM Support. -->

您也可以使用 [IBM Lift CLI ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://lift.ng.bluemix.net/){:new_window} 將資料匯入到 {{site.data.keyword.Db2_on_Cloud_short}}。

## 復原點還原
{: #point-in-time}

{{site.data.keyword.Db2_on_Cloud_short}} 已新增復原點還原功能。您可以從您的備份還原至確切的復原點。目前，對大部分的客戶而言，您必須要求支援中心啟動此特性。請參閱下列推出排程。

以下是復原點還原特性的可用性清單：
- 達拉斯資料中心：目前可用於單一伺服器系統
- 所有其他案例，包括歐洲及達拉斯的 HA 系統：請向支援中心要求特性啟動。完整推出至所有系統將在 2019 年 2 月 28 日完成。
- IBM Cloud Dedicated system（先前為 Bluemix Dedicated）：只可藉由開立支援問題單而提供。

以下是選取的 Web 主控台使用者介面擷取畫面範例，其中已起始復原點還原作業，並指出其進度：

1. 選取**復原點**還原策略，然後選取您要將資料庫還原到的復原點日期。復原點還原程序會從先前 14 天內所做之保留備份儲存區，選取最接近您要求復原點日期的備份。 

   復原點還原程序會使日期在所選取復原點日期之後的任何先前保留備份失效，因為這會造成時間表的分歧。
   {: note}

   ![強調顯示之復原點還原策略選取項目的視圖](images/pit_restore_1.png)

2. 確認您要繼續使用您的還原選取項目。起始還原作業之後，您便無法變更要求。  
![復原點還原確認對話框的視圖](images/pit_restore_2.png)

3. 還原程序正在起始設定。
![復原點還原起始設定的視圖](images/pit_restore_3.png)

4. 將資料庫還原至選取的復原點。
![復原點還原進度的視圖](images/pit_restore_4.png)

5. 正在建立新的備份點。復原點還原的資料庫已經可以使用。
![建立新備份點的視圖](images/pit_restore_5.png)

6. 還原作業已順利完成。
![順利完成還原作業的視圖](images/pit_restore_6.png)

