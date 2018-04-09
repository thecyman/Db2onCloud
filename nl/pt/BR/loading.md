---

copyright:
  years: 2014, 2018
lastupdated: "2018-03-23"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}

# Carregando dados
{: #load}

É possível carregar dados de um arquivo de dados em um formato delimitado, como CSV ou TXT localizado em uma rede local, um
armazenamento de objeto (Amazon S3 ou IBM Cloud Object Storage (anteriormente Swift SoftLayer)) ou usando as ferramentas do DB2®. 
Também é possível preencher uma instância de banco de dados com dados executando um processo de carregamento de um aplicativo
como o InfoSphere® DataStage®.
{: shortdesc}

* [Carregando dados com a CLI Lift
![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Carregando dados do Oracle
![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Carregando dados do SQL Server
![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Carregando um arquivo CSV
![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://lift.ng.bluemix.net/#docs){:new_window}
<!-- * [Loading data from IBM Cloud Object Storage (formerly SoftLayer Swift) ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/loaddata_swift.html){:new_window} -->
* Carregue dados do Amazon S3 usando um dos métodos a seguir:
    * Console da web do {{site.data.keyword.dashdbshort_notm}}. **Carregar > Amazon S3**. 
    * Tabelas externas diretamente. A seguinte é uma instrução SQL de exemplo:

    ```
      INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
        (CCSID 1208 s3('s3.amazonaws.com', 
        '<S3-access-key-ID>',
        '<S3-secret-access-key>', 
        '<my_bucket>'
           )
        )      
    ```
<!-- * [Loading data from Amazon S3 ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/s3.html){:new_window} -->
