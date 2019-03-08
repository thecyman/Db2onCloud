---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-02"

keywords: 

subcollection: Db2onCloud

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

# バックアップとリストア
{: #bnr}

有料プランでは、データベースの暗号化されたバックアップが毎日行われます。 毎日のバックアップは、過去 14 日間にわたって保持されます。
{: shortdesc}

標準バックアップに加え、[タイム・トラベル照会 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} を使用して、古いデータのインスタント照会や簡易監査などの他の目的のために履歴データを保持することもできます。 IBM Data Studio または任意の Db2 ツールを使用して、独自のエクスポートを実行することもできます。
 
ポイント・イン・タイム・リストアについては、[ポイント・イン・タイム・リストア](#point-in-time)を参照してください。

すべての有料プランでは通常、IBM Cloud Object Storage (COS) を利用して、オフサイトの 3 つの異なるデータ・センターでバックアップが保持されます。 ただし、現時点では、シドニー・データ・センターと小規模なデータ・センターの一部は、IBM COS によるオフサイト・レプリケーションをサポートしていません。 オフサイト・レプリケーションをサポートしている地域を判別するには、お客様の地域の [IBM COS の資料](/docs/services/cloud-object-storage/basics/endpoints.html#select-regions-and-endpoints)を確認してください。

<!-- Retained backups are used by IBM for system recovery purposes in the event of a disaster or system loss. Use the [Time Travel Query ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} to keep historical data for your own purposes. In addition, you can also perform your own exports using IBM Data Studio or any Db2 tool. -->

<!-- To store your backups offsite at a remote storage site, make a request to IBM Support. -->

[IBM Lift CLI ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://lift.ng.bluemix.net/){:new_window} を使用して、{{site.data.keyword.Db2_on_Cloud_short}} にデータをインポートすることもできます。

## ポイント・イン・タイム・リストア
{: #point-in-time}

{{site.data.keyword.Db2_on_Cloud_short}} にポイント・イン・タイム・リストア機能が追加されました。 バックアップから正確なポイント・イン・タイムにリストアできます。 現在、ほとんどのお客様はこのフィーチャーをアクティブにするようサポートに要求する必要があります。 次のロールアウト・スケジュールを参照してください。

以下は、ポイント・イン・タイム・リストア・フィーチャーのアベイラビリティー・リストです。
- ダラス・データ・センター: 単一サーバー・システム上で現在使用可能です
- その他のすべてのケース (ヨーロッパ、およびダラスの HA システムを含む): サポートにフィーチャー・アクティブ化を要求してください。 すべてのシステムへのフルロールアウトは、2019 年 2 月 28 日までに完了する予定です。
- IBM Cloud Dedicated システム (旧称 Bluemix Dedicated): サポート・チケットを開くことによってのみ使用可能です。

Web コンソール UI の特定の例を以下に示します。このスクリーン・ショットでは、ポイント・イン・タイム・リストア操作が開始されていて、その進行状況が示されています。

1. **ポイント・イン・タイム**・リストア戦略を選択し、データベースをリストアするターゲットのポイント・イン・タイム日付を選択します。 ポイント・イン・タイム・リストア・プロセスは、過去 14 日間に行われた保存バックアップのプールの中から、要求されたポイント・イン・タイム日付に最も近いバックアップを選択します。 

   ポイント・イン・タイム・リストア・プロセスは、選択されたポイント・イン・タイム日付よりも後の日付で保存されている過去のバックアップをすべて無効にします。リストアの結果として時系列に相違が生じるためです。
   {: note}

   ![ポイント・イン・タイム・リストア戦略の選択が強調表示されたビュー](images/pit_restore_1.png)

2. 選択したリストアを続行することを確認します。 リストア操作を開始したら、要求を変更することはできません。  
![ポイント・イン・タイム・リストア確認ダイアログのビュー](images/pit_restore_2.png)

3. リストア・プロセスの初期化中です。
![ポイント・イン・タイム・リストア初期化のビュー](images/pit_restore_3.png)

4. 選択されたポイント・イン・タイムにデータベースをリストアしています。
![ポイント・イン・タイム・リストアの進行状況のビュー](images/pit_restore_4.png)

5. 新しいバックアップ・ポイントが作成されています。 ポイント・イン・タイム・リストア・データベースを使用できる状態になりました。
![新しいバックアップ・ポイントの作成のビュー](images/pit_restore_5.png)

6. リストア操作が正常に完了しました。
![リストア操作の正常完了のビュー](images/pit_restore_6.png)

