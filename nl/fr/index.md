---

copyright:
  years: 2014, 2018
lastupdated: "2018-03-15"

---

<!-- Attribute definitions --> 
{:javascript: #javascript .ph data-hd-programlang='javascript'}
{:java: #java .ph data-hd-programlang='java'}
{:ruby: #ruby .ph data-hd-programlang='ruby'}
{:php: #php .ph data-hd-programlang='php'}
{:python: #python .ph data-hd-programlang='python'}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:pre: .pre}

# Initiation
{: #getting_started_db2oncloud}

{{site.data.keyword.Db2_on_Cloud_long}} est une base de données SQL mise à votre disposition dans le cloud. Vous pouvez utiliser {{site.data.keyword.Db2_on_Cloud_short}} exactement comme vous le feriez avec tout logiciel de base de données, mais sans avoir à vous préoccuper de configuration du matériel ou d'installation et de maintenance du logiciel. 

Si vous déployez le plan Lite gratuit en dehors de l'Amérique du Nord continentale, voir [Utilisation du plan Lite en dehors de l'Amérique du Nord continentale](free_plan.html#outside_na){:new_window}.
{: shortdesc}

Vous pouvez également installer une base de données Db2 en local en utilisant la [version Db2 Developer Edition téléchargeable gratuitement ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/us-en/marketplace/ibm-db2-direct-and-developer-editions). Une édition prête à l'emploi de Db2 destinée aux développeurs est alors rapidement installée avec des outils au sein d'un conteneur Docker (Docker n'est pas requis ; il installera automatiquement tous les composants nécessaires). 

<!-- ## Free trial
{: #freetrial}

You can try the {{site.data.keyword.Db2_on_Cloud_short}} Precise Performance 500 (2.8.500) plan for 7 days on {{site.data.keyword.Bluemix_notm}} without charge. [Free trial ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/db2){:new_window} -->

## Interfaces
{: #interfaces}

Vous pouvez utiliser votre base de données {{site.data.keyword.Db2_on_Cloud_short}} des manières suivantes :
{: shortdesc}

   * Console Web {{site.data.keyword.Db2_on_Cloud_short}}
   * API REST
   * Connectez des applications ou vos outils préférés depuis votre ordinateur local
   * Utilisez {{site.data.keyword.Db2_on_Cloud_short}} comme source de données pour vos applications ou services {{site.data.keyword.Bluemix_notm}}

### Console Web Db2 on Cloud
{: #web_console}

La console web fournit une interface graphique pour tous les éléments dont vous avez besoin pour utiliser votre base de données : fonctions de chargement, éditeur SQL, téléchargements de pilotes, et plus encore.
{: shortdesc}

<!-- ![View of Db2 on Cloud web console dashboard page](images/console_v2.png) -->
<!-- ![View of {{site.data.keyword.dashdbshort_notm}} web console dashboard page](images/console_v2.jpg) -->

<!-- Click the link to take a tour of the Db2 web console: [General tour ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/dashdb-general-quick-tour){:new_window}. -->

Vous pouvez accéder à la console Web {{site.data.keyword.Db2_on_Cloud_short}} de deux manières :
   * A partir de votre tableau de bord {{site.data.keyword.Bluemix_notm}} : vous pouvez ouvrir la console Web depuis la page Détails du service de votre service {{site.data.keyword.Db2_on_Cloud_long_notm}}.
   * URL directe : vous pouvez ajouter un signet associé à l'URL de la console Web pour votre service {{site.data.keyword.Db2_on_Cloud_short}}.

<!-- ###REST APIs
{: #apis}

With Db2 Warehouse plans, you can perform tasks related to file management, loading data, and running R scripts by using the [Db2 Warehouse REST API ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/dashdb-api){:new_window}.
{: shortdesc} -->

### Connectez des applications ou vos outils préférés depuis votre ordinateur local
{: #connect_apps}

Configurez votre environnement local afin qu'il se connecte à votre base de données {{site.data.keyword.Db2_on_Cloud_short}} en procédant comme suit :
{: shortdesc}

1. Téléchargez le [package de pilote ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package.html){:new_window} à partir de la page Informations de connexion de la console Web {{site.data.keyword.Db2_on_Cloud_short}}.
2. [Installez le package de pilote ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_install.html){:new_window} sur l'ordinateur sur lequel vos applications ou vos outils sont exécutés.
3. [Configurez les fichiers de pilote ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:new_window} pour votre base de données {{site.data.keyword.Db2_on_Cloud_short}}.

### Utilisez Db2 on Cloud comme source de données pour vos applications ou services {{site.data.keyword.Bluemix_notm}}
{: #data_src}

Les applications hébergées sur {{site.data.keyword.Bluemix_notm}} peuvent se connecter à votre base de données {{site.data.keyword.Db2_on_Cloud_short}} exactement de la même manière que vos applications locales se connectent à votre base de données {{site.data.keyword.Db2_on_Cloud_short}}.
{: shortdesc}

Lorsque vos applications utilisent la plateforme {{site.data.keyword.Bluemix_notm}}, vous pouvez tirer parti de la variable d'environnement `VCAP _SERVICES` pour simplifier la spécification des détails et des données d'identification de la base de données :
1. Dans le tableau de bord {{site.data.keyword.Bluemix_notm}}, dans l'onglet **Connexions** de la page Détails du service de votre service {{site.data.keyword.Db2_on_Cloud_long_notm}}, cliquez sur le bouton **Créer une connexion**.
2. Sélectionnez l'application {{site.data.keyword.Bluemix_notm}} à utiliser avec votre base de données {{site.data.keyword.Db2_on_Cloud_short}} comme source de données, puis cliquez sur le bouton **Connecter**.
3. Mettez à jour le code de votre application pour qu'il extraie les détails et les données d'identification de la base de données à partir de la variable d'environnement `VCAP_SERVICES` :

    **Exemple sans `VCAP_SERVICES`**

    ```php
    <?php
    $driver      = "DRIVER={IBM DB2 ODBC DRIVER};";

    $database    = "BLUDB";         # Obtenez ces infos sur la base de données
    $hostname    = "<Host-name>";   # à partir de la page Connect de la
    $port        = 50000;           # console Web Db2 on Cloud.
    $user        = "<User-ID >";    #
    $password    = "<Password>";    #
    $dsn         = "DATABASE=$database;" .
                   "HOSTNAME=$hostname;" .
                   "PORT=$port;" .
                   "PROTOCOL=TCPIP;" .
                   "UID=$user;" .
                   "PWD=$password;";

    $conn_string = $driver . $dsn;

    $conn        = db2_connect( $conn_string, "", "" );
    ?>
    ```

    **Exemple avec `VCAP_SERVICES`**

    ```php
    <?php
    $driver      = "DRIVER={IBM DB2 ODBC DRIVER};";

    $vcap        = json_decode( getenv( "VCAP_SERVICES" ), true );
    $dsn         = $vcap[ "dashDB" ][0][ "credentials" ][ "dsn" ];

    $conn_string = $driver . $dsn;
                                   
    $conn        = db2_connect( $conn_string, "", "" );
    ?>
    ```

## Exemples
{: #samples}

Les liens suivants mènent à des exemples de démonstration indiquant comment se connecter à votre base de données {{site.data.keyword.Db2_on_Cloud_short}} à partir d'applications dans différents langages :
{: shortdesc}

   * [.NET ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:new_window}
<!-- * [JAVA ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_java.html){:new_window} -->
   * [JDBC ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:new_window}
<!-- * [Node.js ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_nodejs.html){:new_window} -->
   * [PHP ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:new_window}
<!-- * [Python ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_python.html){:new_window} -->
   * [Exemples {{site.data.keyword.Db2_on_Cloud_short}} sur GitHub ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/IBM-Bluemix/dashdb-nodejs-helloworld){:new_window}


