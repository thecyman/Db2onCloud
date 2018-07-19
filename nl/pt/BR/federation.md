---

copyright:
  years: 2014, 2018
lastupdated: "2018-06-15"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:pre: .pre}

# Virtualização de dados (Federação)
{: #overview}

A virtualização de dados do Db2 (também conhecida como federação) é suportada pelo {{site.data.keyword.Db2_on_Cloud_short}}. A virtualização de dados fornece acesso de consulta única a todos os seus dados localizados em múltiplos bancos de dados distribuídos em qualquer lugar em sua organização. É possível acessar dados que estão localizados em qualquer uma das origens de dados Db2 ou Informix, tanto na nuvem quanto nas instalações.
{: shortdesc}

Essa funcionalidade é suportada em todas as versões do {{site.data.keyword.Db2_on_Cloud_short}}, exceto para o plano Lite grátis. No entanto, é possível usar o plano Lite como um destino do qual é possível puxar dados.

## Casos de Uso
{: #use_cases}

### Consolidar origens de dados

Ao federar suas origens de dados que estão localizadas na nuvem e nas instalações em qualquer lugar em sua organização, seus dados virtualizados parecem ser recuperados de uma única origem. A virtualização de dados elimina o processo caro e difícil de migração de dados, fornecendo a você a capacidade de analisar todos os seus dados de maneira eficiente e com efetividade em custo.

<!-- A company may have started their operations with an on-premises Db2 server. As cloud technology becomes more widespread and companies start to operate on cloud in a cost-effective fashion, there will be continued Cloud growth. However, the organization’s data on both sources remain as a critical component to their decision-making processes. By way of example, a client operating in retail industry needs to be able to access all data, say customer information, to run further analysis on their customers’ consumption behaviors. They need to be able to identify customers, match their records on cloud with already existing ones from an on-premises database and compose them as if the data is being retrieved from a single source. Federation capability here prevents the burdensome data migration process and allows the user to access the data without moving the data.

located in the cloud and on-premises -->

### Conectar ao Db2 Warehouse on Cloud

Os usuários de produtos da família Db2 podem federar dados dos bancos de dados {{site.data.keyword.Db2_on_Cloud_short}} e {{site.data.keyword.dashdbshort_notm}}. Em uma interface comum para acessar os dados, é possível incluir, consultar e analisar facilmente seus dados sem processos ETL complexos e sem qualquer código adicional.

<!-- Db2 family users would now be able to federate data between Db2 on Cloud and Db2 Warehouse on Cloud. By being provided a common interface for accessing the data, a user can now easily add or query data from or to the Warehouse without complex ETL processes or any additional code. -->

### Dados compartilhados entre múltiplos servidores

Talvez você escolha particionar (shard) seus dados algumas vezes. Com os recursos de federação, os dados em shard podem ser consultados com uma interface unificada. A federação fornece a capacidade de equilibrar melhor suas cargas de trabalho, escalar partes específicas de um app e criar microsserviços que funcionem juntos. 

<!-- At times, users may choose to partition (shard). With federation capabilities, data can be queried with a unified interface and this lets the user better balance the workload, scale specific parts of an app or create microservices that work together. -->

### Aumentar a capacidade do banco de dados além dos limites fixos

A federação fornece a capacidade de aumentar a capacidade de um banco de dados no local ao federar com um banco de dados na nuvem. A virtualização de dados nesse caso é uma ótima opção se o seu banco de dados no local estiver em execução fora do armazenamento. Aumentar a capacidade de um banco de dados com federação é útil para o novo desenvolvimento porque os desenvolvedores não precisam mudar um banco de dados já em produção. Também é possível federar entre dois bancos de dados {{site.data.keyword.Db2_on_Cloud_short}} para aumentar a capacidade do banco de dados além dos limites atuais do plano Flex.

<!-- By using federation, users can increase capacity of an on premises database by federating to or from the cloud. This is a great option if your on premises database is running out of storage. Increased capacity will also be useful for new development as our users no longer need to change a database in production. You can also use this feature to federate between two Db2 on Cloud databases to increase the capacity beyond the current limits of the Flex plan. -->

## Introdução
{: #getting_started}

As etapas a seguir são um exemplo de como você vai federar suas origens de dados diferentes para aparecerem como se os dados fossem recuperados de uma fonte isolada. O exemplo a seguir ilustra a federação de dois bancos de dados {{site.data.keyword.Db2_on_Cloud_short}}:

### Na máquina de destino do Db2 on Cloud

Nome do host: targetdotcom

1. Crie uma tabela `testdata` no esquema `admin2`.

2. No console do Db2 on Cloud, carregue a tabela `testdata` com dados como o usuário `admin2` com a senha `YYYY`.

### Em uma máquina cliente do destino

1. Catalogue a máquina de destino:<br/>
   `db2 catalog tcpip node <node_name> remote <host_name> server 50000`<br/>

   Por exemplo:<br/>
   `db2 catalog tcpip node fedS remote targetdotcom server 50000`

2. Catalogue o banco de dados no fedS:<br/>
   `db2 catalog db bludb as <db_name> no nó <node_name>`

   Por exemplo:<br/>
   `db2 catalog db bludb as srcdb at node fedS`

3. Conecte-se ao banco de dados no fedS:<br/>
   `db2 connect to <catalog_db_name> usuários <admin_user> usando '<admin_password>'`

   Por exemplo:<br/>
   `db2 connect to srcdb user 'admin1' with password 'XXXX'`

4. Crie um wrapper no fedS:<br/>
   `db2 "create wrapper drda"`

5. Crie um servidor para conversar com a máquina de destino:<br/>
   `db2 "create server <server_name> type dashdb version 11 wrapper drda authorization \"<admin_user_on_target>\" password \"<admin_password_on_target>\" options (host '<target_host_name>', port '50000', dbname 'bludb')"`

   Por exemplo:<br/>
   `db2 "create server db2server type dashdb version 11 wrapper drda authorization \"admin2\" password \"YYYY\" options (host 'targetdotcom', port '50000', dbname 'bludb')"`

6. Crie o mapeamento de usuário para admin2:<br/>
   `db2 "create user mapping for <admin_user> server db2server options (remote_authid '<admin_user_on_target>', remote_password '<admin_password_on_target>')"`

   Por exemplo:<br/>
   `db2 "create user mapping for admin1 server db2server options (remote_authid 'admin2', remote_password 'YYYY')"`

7. Crie um apelido para o banco de dados:<br/>
   `db2 -v "create nickname <nickname> for <server_name>.<schema_name>.<table_name>"`

   Por exemplo:<br/>
   `db2 -v "create nickname ntest1 for db2server.admin2.testdata"`

### Na máquina de origem do Db2 on Cloud

1. Teste se é possível puxar dados do servidor de destino:<br/>
   `db2 "select * from <nickname>"`

   Por exemplo:<br/>
   `db2 "select * from ntest1"`

## Informações Adicionais

Para obter mais informações sobre virtualização de dados (federação), veja: [Federação ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/fcontainer.html){:new_window}.

Para obter informações sobre as origens de dados suportadas pela federação, veja: [Origens de dados suportadas da federação ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo") ](https://www.ibm.com/support/docview.wss?uid=swg27050561){:new_window}.

