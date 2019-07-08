---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-02"

keywords: 

subcollection: Db2onCloud

---

<!-- Attribute definitions --> 
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# 備份及還原
{: #bnr}

針對付費方案，每天會進行資料庫的加密備份。針對過去的 14 天，會保留每天的當日備份。
{: shortdesc}

除了標準備份之外，您也可以使用 [Time Travel Query](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:external} 來保留其他用途用的歷程資料，例如舊資料的立即查詢，或是簡化審核。您也可以使用 IBM Data Studio 或任何 Db2 工具來執行自己的匯出作業。
 
如需復原點還原的相關資訊，請參閱[復原點還原](#point-in-time)。

所有付費方案一般都會利用 IBM Cloud Object Storage (COS)，在 3 個不同資料中心保留異地的備份。不過，雪梨及特定較小型的資料中心目前可能不支援使用 IBM COS 進行異地抄寫。請參閱您地區的 [IBM COS 文件](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-endpoints#endpoints)，以判斷哪些地區支援異地抄寫。

您也可以使用 [IBM Lift CLI](https://www.lift-cli.cloud.ibm.com/){:external} 將資料匯入到 {{site.data.keyword.Db2_on_Cloud_short}}。

## 復原點還原
{: #point-in-time}

{{site.data.keyword.Db2_on_Cloud_short}} 已新增復原點還原功能。您可以從您的備份還原至確切的復原點。目前，對大部分的客戶而言，您必須要求支援中心啟動此特性。請參閱下列推出排程。

以下是復原點還原特性的可用性清單：
- 達拉斯資料中心：目前可用於單一伺服器系統
- 所有其他案例，包括歐洲及達拉斯的 HA 系統：請向支援中心要求特性啟動。完整推出至所有系統將在 2019 年 2 月 28 日完成。
- IBM Cloud Dedicated 系統：只可藉由開立支援問題單而提供。

以下是選取的 Web 主控台使用者介面擷取畫面範例，其中已起始復原點還原作業，並指出其進度：

1. 選取**復原點**還原策略，然後選取您要將資料庫還原到的復原點日期。復原點還原程序會從先前 14 天內所做之保留備份儲存區，選取最接近您要求復原點日期的備份。 

   復原點還原程序會使日期在所選取復原點日期之後的任何先前保留備份失效，因為這會造成時間表的分歧。
   {: note}

   ![復原點還原策略強調顯示之選取項目的視圖](images/pit_restore_1.png "備份及還原主控台頁面"){: caption="圖 1. 復原點還原策略強調顯示之選取項目的視圖" caption-side="bottom"}

2. 確認您要繼續使用您的還原選取項目。起始還原作業之後，您便無法變更要求。  
![復原點還原確認對話框的視圖](images/pit_restore_2.png "確認對話框"){: caption="圖 2. 復原點還原確認對話框的視圖" caption-side="bottom"}

3. 還原程序正在起始設定。
![復原點還原起始設定的視圖](images/pit_restore_3.png "復原點還原的起始設定"){: caption="圖 3. 復原點還原起始設定的視圖" caption-side="bottom"}

4. 將資料庫還原至選取的復原點。
![復原點還原進度的視圖](images/pit_restore_4.png "還原進度"){: caption="圖 4. 復原點還原進度的視圖" caption-side="bottom"}

5. 正在建立新的備份點。復原點還原的資料庫已經可以使用。
![建立備份點的視圖](images/pit_restore_5.png "建立備份點"){: caption="圖 5. 建立備份點的視圖" caption-side="bottom"}

6. 還原作業已順利完成。
![順利完成還原作業的視圖](images/pit_restore_6.png "順利完成"){: caption="圖 6. 順利完成還原作業的視圖" caption-side="bottom"}

