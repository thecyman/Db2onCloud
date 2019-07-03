---

copyright:
  years: 2014, 2019
lastupdated: "2019-04-30"

keywords: 

subcollection: Db2onCloud

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
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# Tutoriel d'initiation
{: #getting-started}

{{site.data.keyword.Db2_on_Cloud_long}} est une base de données SQL mise à votre disposition dans le cloud. Vous pouvez utiliser {{site.data.keyword.Db2_on_Cloud_short}} exactement de la même manière que vous utilisez n'importe quel logiciel de base de données, sans le temps et les frais associés à la configuration du matériel ou à l'installation et la maintenance des logiciels.
{: shortdesc}

Créez des données d'identification. Pour les nouveaux utilisateurs d'IBM Cloud, il est nécessaire de créer un nom d'utilisateur et un mot de passe après la création du service en cliquant sur le bouton **Créer des données d'identification** lorsque vous lancez le service. Techniquement, vous pouvez vous connecter à la console Web sans données d'identification mais vous avez besoin du nom d'utilisateur et du mot de passe pour pouvoir utiliser un grand nombre d'outils Db2.
{: important}

Vous pouvez également installer une base de données Db2 en local en utilisant la [version Db2 Developer Edition téléchargeable gratuitement ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/us-en/marketplace/ibm-db2-direct-and-developer-editions){:new_window}. Une édition prête à l'emploi de Db2 destinée aux développeurs est alors rapidement installée avec des outils au sein d'un conteneur Docker (Docker n'est pas requis ; il installe automatiquement tous les composants nécessaires). 

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

### Installation des pilotes et des clients de ligne de commande Db2 sur votre ordinateur
{: #connect_apps}

Dans la plupart des cas, les utilisateurs ont tendance à utiliser uniquement l'API REST ou à installer des pilotes pour une infrastructure, par exemple, avec la commande `pip` de Python.
{: shortdesc}

Pour installer des modules de pilote Python pour MacOS, vous devez utiliser la commande `pip` avec l'option `--no-cache-dir`. Pour des instructions détaillées, voir [Python support for IBM DB2 and IBM Informix ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/db2-drivers-python){:new_window}
{: note}

<!-- Drivers on site are broken so taking out this one -Simon. 1. Download the [driver package ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package.html){:new_window} from the Connection info page of the {{site.data.keyword.Db2_on_Cloud_short}} web console.-->

Pour installer des pilotes d'infrastructure Python ou Node.js, cliquez sur l'un des liens suivants :
- [Pilotes Python ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/db2-drivers-python){:new_window}
- [Pilotes Node.js ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/db2-drivers-node){:new_window}

Pour installer une ORM (object role modeling, modélisation objet-rôle) Node.js nommée Sequelize, cliquez sur le lien suivant :
[Sequelize ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/ibmdb/sequelize){:new_window}
{: note}

Pour plus d'options d'installation de pilotes, y compris Java, Go, Jupyter Notebooks, Ruby, PHP, et d'autres, cliquez sur le lien suivant : 

- [ibmdb ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/ibmdb){:new_window}

Si vous avez déjà installé des pilotes d'infrastructure, vous pouvez sauter les étapes suivantes. Toutefois, les utilisateurs expérimentés peuvent souhaiter utiliser le client de ligne de commande Db2 pour administrer leur base de données et utiliser des commandes Db2. De plus, certaines applications ODBC ou JDBC peuvent bénéficier d'une installation générale de pilotes Db2. Le cas échéant, procédez comme suit :

1. [Installez le package de pilote ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_install.html){:new_window} sur l'ordinateur sur lequel vos applications ou vos outils sont exécutés.
2. [Configurez les fichiers de pilote ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:new_window} pour votre base de données {{site.data.keyword.Db2_on_Cloud_short}}.

### Utilisez Db2 on Cloud comme source de données pour vos applications ou services {{site.data.keyword.Bluemix_notm}}
{: #data_src}

Les applications hébergées sur {{site.data.keyword.Bluemix_notm}} peuvent se connecter à votre base de données {{site.data.keyword.Db2_on_Cloud_short}} de la même manière que vos applications locales se connectent à votre base de données {{site.data.keyword.Db2_on_Cloud_short}}.
{: shortdesc}

Lorsque vos applications utilisent la plateforme {{site.data.keyword.Bluemix_notm}}, vous pouvez tirer parti de la variable d'environnement `VCAP _SERVICES` pour simplifier la spécification des détails et des données d'identification de la base de données :
1. Dans le tableau de bord {{site.data.keyword.Bluemix_notm}}, dans l'onglet **Connexions** de la page Détails du service de votre service {{site.data.keyword.Db2_on_Cloud_long_notm}}, cliquez sur le bouton **Créer une connexion**.
2. Sélectionnez l'application {{site.data.keyword.Bluemix_notm}} à utiliser avec votre base de données {{site.data.keyword.Db2_on_Cloud_short}} comme source de données, puis cliquez sur le bouton **Connecter**.
3. Mettez à jour le code de votre application pour qu'il extraie les détails et les données d'identification de la base de données à partir de la variable d'environnement `VCAP_SERVICES` :

    **Exemple sans `VCAP_SERVICES`**

    ```php
    <?php
    $driver      = "DRIVER={IBM DB2 ODBC DRIVER};";

    $database    = "BLUDB";         # Get these database details from
    $hostname    = "<Host-name>";   # the Connect page of the Db2 on Cloud
    $port        = 50000;           # web console.
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

Voici des liens vers des exemples qui montrent comment se connecter à votre base de données {{site.data.keyword.Db2_on_Cloud_short}} à partir d'applications dans différents langages :
{: shortdesc}

   * [.NET ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:new_window}
<!-- * [JAVA ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_java.html){:new_window} -->
   * [JDBC ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:new_window}
<!-- * [Node.js ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_nodejs.html){:new_window} -->
   * [PHP ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:new_window}
<!-- * [Python ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_python.html){:new_window} -->
<!-- * [{{site.data.keyword.Db2_on_Cloud_short}} samples on GitHub ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/IBM-Bluemix/dashdb-nodejs-helloworld){:new_window} -->

## Vidéo : Introducing Db2 on Cloud
{: #intro_vid}

Regardez cette vidéo pour voir une présentation de {{site.data.keyword.Db2_on_Cloud_short}}.

<iframe class="embed-responsive-item" id="youtubeplayer1" title="Introduction to {{site.data.keyword.Db2_on_Cloud_short}}" type="text/html" width="640" height="390" src="//www.youtube.com/embed/F_ylk44_WOg?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>

## Vidéo : Using REST API to communicate with Db2 on Cloud
{: #vid_api}

Regardez cette vidéo pour connaître les étapes nécessaires à l'utilisation d'une API RESTful pour communiquer avec {{site.data.keyword.Db2_on_Cloud_short}}.

<iframe class="embed-responsive-item" id="youtubeplayer2" title="Using RESTful API to communicate with {{site.data.keyword.Db2_on_Cloud_short}}" type="text/html" width="640" height="390" src="//www.youtube.com/embed/PSNBDwgf9ts?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>

## Vidéo : Integrating Jupyter Notebooks
{: #cognos_vid}

Regardez cette vidéo pour voir comment intégrer des blocs-notes Jupyter à {{site.data.keyword.Db2_on_Cloud_short}}.

<iframe class="embed-responsive-item" id="youtubeplayer3" title="Integrating Jupyter notebooks" type="text/html" width="640" height="390" src="//www.youtube.com/embed/bNfH0Wzx3is?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>


