---

copyright:
  years: 2014, 2018
lastupdated: "2018-03-14"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}

# 備份及還原
{: #br}

針對付費方案，每天會進行資料庫的加密備份。針對過去的 14 天，會保留每天的當日備份。
{: shortdesc}

保留的備份由 IBM 在發生災難或系統流失時用於系統回復目的。請使用 [Time Travel Query ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} 來保留歷程資料，以用於您自己的用途。此外，您也可以使用 IBM Data Studio 或任何 Db2 工具來執行自己的匯出作業。

若要將備份異地儲存在遠端儲存站台，請向 IBM 支援中心提出要求。

您也可以使用 [IBM Lift CLI](https://lift.ng.bluemix.net/){:new_window} 將資料匯入到 {{site.data.keyword.Db2_on_Cloud_short}}。
