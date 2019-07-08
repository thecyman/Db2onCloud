---

copyright:
  years: 2014, 2019
lastupdated: "2018-05-11"

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

# Migrando dados para o IBM Cloud
{: #migration}

É possível carregar dados de um arquivo de dados em um formato delimitado (CSV ou TXT) localizado em uma rede local ou em um armazenamento de objeto (Amazon S3 ou IBM Cloud Object Storage) para o {{site.data.keyword.Db2_on_Cloud_long}}. É possível até mesmo migrar seus dados de um sistema no local.
{: shortdesc}

## Carregando dados do armazenamento de objeto
{: #cos}

Para carregar dados do Amazon S3, selecione um dos métodos a seguir:
  * Console da web do {{site.data.keyword.Db2_on_Cloud_short}}. **Carregar > Amazon S3**. 
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

Para carregar dados do IBM Cloud Object Storage usando tabelas externas diretamente, o trecho a seguir é uma instrução SQL de exemplo:

```
INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
  (CCSID 1208 s3('s3-api.us-geo.objectstorage.softlayer.net',
  '<S3-access-key-ID>',
  '<S3-secret-access-key>',
  '<my_bucket>'
     )
  )      
```

Para o IBM Cloud Object Storage, para criar credenciais HMAC ao criar novas credenciais de serviço, especifique {"HMAC:true"} no campo *Incluir parâmetros de configuração sequenciais*.
{: note}

## Migrando dados do sistema no local
{: #onprem}

Para migrar seus dados de um sistema no local, escolha um dos métodos a seguir, dependendo do tamanho do seu conjunto de dados:
* Menor que 25 TB de dados: [CLI do IBM Lift](#lift)
* 25 TB de dados e maiores: [IBM Cloud Mass Data Migration](#mdms)

### Lift CLI
{: #lift}

A CLI do Lift é um aplicativo que pode ser usado sem encargos para migrar seus dados para o {{site.data.keyword.Bluemix_notm}} das várias origens de dados listadas na Tabela 1. 

| Banco de dados de destino no IBM Cloud | Origem de Dados |
|------------------------------|-------------|
| {{site.data.keyword.Db2_on_Cloud_long_notm}}   | IBM Db2 |
|                              | Oracle Database |
|                              | Servidor Microsoft SQL |
|                              | Formato de arquivo CSV |
{: caption="Tabela 1. Origens de dados de migração" caption-side="top"}

Para fazer download e instalar a CLI do Lift, veja: [Fazer download da CLI do Lift](https://www.lift-cli.cloud.ibm.com/#download){:external}.

Para obter instruções passo a passo sobre como migrar seus dados para
o {{site.data.keyword.Bluemix_notm}} usando a CLI do Lift, veja: [Migrar dados para o {{site.data.keyword.Db2_on_Cloud_long_notm}}](https://www.lift-cli.cloud.ibm.com/#docs){:external}.

### IBM Cloud Mass Data Migration
{: #mdms}

Uma maneira rápida, simples e segura para transferir fisicamente terabytes a petabytes de dados para o
{{site.data.keyword.Bluemix_notm}}. O Mass Data Migration é um dispositivo de armazenamento móvel com 120 TB de capacidade de armazenamento utilizável para acelerar a movimentação de dados para o {{site.data.keyword.Bluemix_notm}}. Supere desafios comuns de transferência, tais como altos custos, longos tempos de transferência e preocupações com segurança - tudo em um único serviço.

![Visualização do dispositivo Mass Data Migration](images/mdms.svg "Visualização do dispositivo Mass Data Migration")

Para obter mais informações sobre o dispositivo Mass Data Migration, veja: [Tutorial de introdução](/docs/infrastructure/mass-data-migration?topic=mass-data-migration-getting-started-tutorial#getting-started-with-ibm-cloud-mass-data-migration){:external}.

