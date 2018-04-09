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

# Alta disponibilidade (HA)
{: #ha}

Os planos de alta disponibilidade do {{site.data.keyword.Db2_on_Cloud_short}} têm excelentes características de
disponibilidade com um SLA de 99,99% .
{: shortdesc}

Os planos padrão de alta disponibilidade <!-- without a DR node -->fornecem failover contínuo e atualizações
contínuas. Eles são gerenciados para você usando nova rota do cliente automática (ACR) e IPs móveis.

A alta disponibilidade com um nó de recuperação de desastre externo está atualmente em beta fechado. Entre em contato com seu
representante IBM para saber como participar do beta fechado. Com o nó externo DR, é possível sincronizar rapidamente seus dados em tempo real para um nó de banco de dados em um local externo de sua escolha. 
O {{site.data.keyword.Db2_on_Cloud_short}} usa a tecnologia do DB2 High Availability Disaster Recovery (HADR) no modo ASYNC para atingir o recurso externo do nó DR e fornece Read on Standy no nó de recuperação de desastre.
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->
