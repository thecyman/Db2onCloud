---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-21"

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

# IBM Cloud 上的身份和访问权管理 (IAM)
{: #iam}

利用身份和访问权管理 (IAM)，您可以为平台服务进行安全的用户认证，并控制对 {{site.data.keyword.Bluemix_notm}} 平台上所有资源的访问权一致性。例如，只需用 IBM 标识单点登录到 {{site.data.keyword.Bluemix_notm}}，就可以访问任何服务控制台及其应用程序，而无需逐个单独登录。
{: shortdesc}

## 实例上是否启用了 IAM？
{: #enabled}

经过一段时间以后，{{site.data.keyword.Db2_on_Cloud_long}} 在 {{site.data.keyword.Bluemix_notm}} 上管理的数据库实例就会被启用，以便使用 IAM 进行访问控制。要检查实例上是否已启用 IAM，请运行以下查询：

`SELECT CASE WHEN VALUE = 'IBMIAMauth' THEN 1 ELSE 0 END AS IAM_ENABLED FROM SYSIBMADM.DBMCFG WHERE NAME = 'srvcon_gssplugin_list'`

如果 **IAM_ENABLED** 的返回值是 1，说明实例上已启用 IAM。

## IBM Cloud IAM 的功能
{: #features}

下列 IAM 功能是针对 {{site.data.keyword.Db2_on_Cloud_short}} 管理的服务使用两种类型的受支持身份实现的：

**IBM 标识**

数据库管理员必须先通过控制台或 REST API 将具有 IBM 标识的用户添加到每个数据库服务实例中，然后这些用户才能连接到特定的数据库服务实例。就像非 IBM 标识用户一样，必须在添加 IBM 标识用户的同时输入数据库服务实例的用户标识。此用户标识在数据库服务实例中应该是唯一的。此用户标识也是数据库中的授权 (AUTH) 标识。数据库管理员可以根据 AUTH 标识授予或撤销许可权。

**服务标识**

服务标识用于标识服务或应用程序，类似于用户标识对用户进行标识的方式。服务标识是应用程序可以用来进行 IBM Cloud 服务认证的标识。服务标识表示不同于其所属 IBM 标识的单独实体。因此，在数据库中，可以为特定的服务标识授予不同的权限和许可权。服务标识没有密码。必须为每个服务标识创建 API 密钥，该服务标识才能连接到数据库服务实例。有关服务标识的更多信息，请参阅：[介绍 IBM Cloud IAM 服务标识和 API 密钥 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/blogs/bluemix/2017/10/introducing-ibm-cloud-iam-service-ids-api-keys/){:new_window}。

## 客户机连接和用户登录
{: #connect_user}

**必备软件**：Db2 Client V11.1 FP3 及更高版本。

可以使用下列方法进行 IAM 认证：

**访问令牌**

应用程序可以使用 API 密钥通过 REST API 直接从 IAM 服务获取访问令牌。有关更多信息，请参阅：[使用 API 密钥获取 IBM Cloud IAM 令牌 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/iam/apikey_iamtoken.html#iamtoken_from_apikey){:new_window}。访问令牌的缺省有效期为 60 分钟，之后即到期。如果令牌已到期，那么 Db2 服务器不会允许建立连接。但在建立连接之后，不会检查令牌是否到期。就像在 IAM 集成之前一样，仍将保持已连接状态，直到应用程序断开连接或连接由于其他原因被终止。

```
curl -k -X POST \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=<apikey>" \
  "https://iam.bluemix.net/identity/token"
```

访问令牌为数据库识别 IBM 标识用户或服务标识。数据库服务器先验证访问令牌的有效性，然后接受令牌。如果应用程序需要连接多个数据库服务实例或其他 {{site.data.keyword.Bluemix_notm}} 服务实例，那么这是最佳方法，因为可以将与 IAM 服务进行通信已验证访问令牌的通信量降到最低。

**API 密钥**

可以为每个 IBM 标识用户或服务标识创建多个 API 密钥。通常情况下，每个 API 密钥都是为单个应用程序创建的。这样只要将其所属的 IBM 标识或服务标识作为用户添加到数据库服务实例中，应用程序就可以一直连接到该数据库服务实例。在数据库中，API 密钥与所属的 IBM 标识或服务标识具有相同的权限和许可权。如果应该不再允许应用程序连接到数据库，那么可以除去相应的 API 密钥。跟使用访问令牌相比，此认证方法需要在应用程序中进行的更改更少，这是因为它不需要与 IAM 服务进行直接交互。有关创建和管理 API 密钥的更多信息，请参阅：[管理用户 API 密钥 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/docs/iam/userid_keys.html#userapikey){:new_window}。

**IBM 标识/密码**

IBM 标识/密码可用于登录控制台，也可在应用程序中发挥与用户标识/密码相同的作用。如果联合 IBM 标识，就会发生异常，这是因为无法重定向到组织的登录页面。但我们建议用使用访问令牌的方法来建立应用程序与数据库服务实例的连接。

## 受支持的接口
{: #sup-if}

支持下列数据库客户机接口：

* [ODBC](#odbc-clpplus)
* [CLP](#odbc-clpplus)
* [CLPPLUS](#odbc-clpplus)
* [JDBC](#jdbc)

### ODBC、CLP 和 CLPPLUS
{: #odbc-clpplus}

要让 ODBC 应用程序或命令行客户机（CLP 和 CLPPLUS）使用 IAM 认证连接到 Db2 服务器，需要先运行以下命令以在 `db2dsdriver.cfg` 配置文件中配置数据源名称 (DSN)：

`db2cli writecfg add -dsn <dsn_alias> -database <database_name> -host <host_name_or_IP_address> -port 50001 -parameter "Authentication=GSSPLUGIN;SecurityTransportMode=SSL"`

`db2dsdriver.cfg` 配置文件是 XML 文件，通常位于 `sqllib/cfg` 目录中，其中包含 DSN 别名的列表及其属性。

下面的 `db2dsdriver.cfg` 配置文件的示例显示了用于与数据库服务实例建立连接的配置。该配置文件提供 DSN 别名、数据库名称、主机名（或 IP 地址），以及**认证**类型和 **SecurityTransportMode** 参数值。

```
<?xml version="1.0" encoding="UTF-8" standalone="no" ?>
<configuration>
        <dsncollection>
        <dsn alias="<data_source_name>" name="bludb" host="<host_name_or_IP_address>" port="50001">
            <parameter name="Authentication" value="GSSPLUGIN"/>
            <parameter name="SecurityTransportMode" value="SSL"/>
        </dsn>
        </dsncollection>
        <databases>
            <database name="bludb" host="<host_name_or_IP_address>" port="50001"/>
        </databases>
</configuration>
```

* ODBC 连接字符串可包含下列某项：

    **访问令牌**

    `DSN=<dsn>;ACCESSTOKEN=<access_token>`

    **API 密钥**

    `DSN=<dsn>;APIKEY=<api_key>`

    **IBM 标识/密码**
    
    `DSN=<dsn>;UID=<ibmid>;PWD=<password>`

    对于 ODBC，**AUTHENTICATION=GSSPLUGIN** 可以在 `db2dsdriver.cfg` 配置文件或应用程序的连接字符串中进行配置。

* CLP CONNECT 语句可以包含以下某项：

    **访问令牌**

    连接到数据库服务器 `<database_server_name>` 并传递访问令牌，方法是在 CLP 命令提示符或脚本处运行以下命令：

    `CONNECT TO <database_server_name> ACCESSTOKEN <access_token_string>`

    **API 密钥**

    连接到数据库服务器 `<database_server_name>`，方法是在 CLP 命令提示符或脚本处运行以下命令：

    `CONNECT TO <database_server_name> APIKEY <api-key-string>`

    **IBM 标识/密码**

    连接到数据库服务器 `<database_server_name>`，方法是在 CLP 命令提示符或脚本处运行以下命令：

    `CONNECT TO <database_server_name> USER <IBMid> USING <password>`

    有关使用 CLP 连接到数据库服务器的更多详细信息，请参阅：[CONNECT (type 2) statement ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.sql.ref.doc/doc/r0000908.html){:new_window}。 

* CLPPLUS CONNECT 语句可以包含以下某项：

    **访问令牌**

    连接到 DSN 别名 (`@<data_source_name>`) 并传递访问令牌，方法是在 CLPPLUS 命令提示符或脚本处运行以下命令：

    `connect @<data_source_name> using(accesstoken <access_token_string>)`

    **API 密钥**

    连接到 DSN 别名 (`@<data_source_name>`) ，方法是在 CLPPLUS 命令提示符或脚本处运行以下命令：

    `connect @<data_source_name> using(apikey <api-key-string>)`

    **IBM 标识/密码**

    连接到 DSN 别名 (`@<data_source_name>`) ，方法是在 CLPPLUS 命令提示符或脚本处运行以下命令：

    `connect <IBMid>/<password>@<data_source_name>`

    有关使用 CLPPLUS 连接到 DSN 别名的更多详细信息，请参阅：[CLPPlUS 中的 DSN 别名 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.swg.im.dbclient.clpplus.doc/doc/c0057148.html){:new_window}。

### JDBC
{: #jdbc}

IAM 认证支持第 4 类 JDBC 驱动程序。

以下示例显示了三种方法的连接片段：

**访问令牌**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<host_name_or_IP_address>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
dataSource.setAccessToken( "<access_token>" );
Connection conn = dataSource.getConnection( );
```

或者

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:accessToken=<access_token>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

**API 密钥**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<host_name_or_IP_address>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
dataSource.setApiKey( "<api_key>" );
Connection conn = dataSource.getConnection( );
```

或者

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:apikey=<api_key>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

**IBM 标识/密码**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<host_name_or_IP_address>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
Connection conn = dataSource.getConnection( "<IBMid>", "<password>" );
```

或者

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:user=<IBMid>;password=<password>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

## 控制台用户体验
{: #console-ux}

服务控制台登录页面上有使用 IBM 标识和密码登录的选项。单击**通过 IBM 标识登录**按钮之后，系统将引导用户进入 IAM 登录页面，请在该页面上输入密码。完成认证之后，系统会将用户重定向回控制台。要成功登录，数据库管理员必须先通过控制台或 REST API 将 IBM 标识用户添加到每个数据库服务实例。就像非 IBM 标识用户一样，必须在添加 IBM 标识用户的同时输入数据库服务实例的用户标识。用户标识在数据库服务实例中应该是唯一的。此用户标识也是数据库中的授权 (AUTH) 标识。

## REST API 体验
{: #api}

{{site.data.keyword.Db2_on_Cloud_short}} REST API 经过功能增强，那些以前只接受数据库服务生成的访问令牌的功能，现在也可以接受 IAM 访问令牌。

* 要添加新的 IBM 标识用户，请运行以下示例 API 调用：

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid>","ibmid":"<userid>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  `"id"` 和 `"ibmid"` 的 `<userid>` 值可以不同。无论如何，两种不同的标识都不会链接在一起。
  {: note}

* 要迁移现有的非 IBM 标识数据库用户（例如，`abcuser`），并使其成为 IBM 标识用户，首先要运行以下示例 API 调用来删除非 IBM 标识用户标识：

  `curl --tlsv1.2 -X DELETE "https://<IPaddress>/dbapi/v3/users/abcuser" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json"`

  接下来，要通过运行以下示例 API 调用来使用与先前用户标识 (`abcuser`) 相同的 IBM 标识来重新添加用户：

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"abcuser","ibmid":"abcuser@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  因为该用户的新 IBM 标识与用户标识 (`abcuser`) 保持一致，所以为该用户授予的数据库许可权也保持不变。如果需要迁移现有的非 IBM 标识数据库用户的列表以使其成为 IBM 标识用户，需要为每个用户运行先前的两个 API 调用。

* 如果要同时添加多个新 IBM 标识用户，请为每个用户创建一个列出以下示例 API 调用的批处理文件：

  ```
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid1>","ibmid":"<userid1>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid2>","ibmid":"<userid2>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  .
  .
  .
  ```

有关服务 API 的更多详细信息，请参阅：[{{site.data.keyword.Db2_on_Cloud_short}} REST API ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://ibm.biz/db2oc_api){:new_window}。

## IBM 标识联合
{: #fed_ibmid}

要使用您自己的身份提供程序（如 LDAP），必须先将 LDAP 服务器与 IBM 标识联合。有关将 LDAP 服务器与 IBM 标识联合的指示信息，请参阅：[IBMid Enterprise Federation Adoption Guide ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.ent.box.com/notes/78040808400?s=nhuzrhlsn0ly338zddomx329tlpmfghc){:new_window}。在数据库管理员完成 IBM 标识联合并将允许的用户添加到数据库服务实例之后，这些用户就可以使用他们的公司用户标识和密码登录到控制台。或者，这些用户也可以使用表示他们用户标识的访问令牌或 API 密钥通过一个受支持的数据库客户机接口来连接数据库服务实例。

## 限制
{: #restrictions}

下面是关于 IAM 认证的限制：

* 仅支持通过 SSL 连接对连接到 Db2 服务器的 Db2 客户机进行 IAM 认证。
* 支持 IBM 标识联合以允许使用定制用户管理门户网站或服务器进行认证。此支持不包含任何组联合。
* 不支持数据库联合的 IAM 认证。
* 不支持通过 CLPPlus 运行 IDA 和用户定义的扩展 (UDX) 命令。
* 不支持第 2 类 JDBC 驱动程序。




