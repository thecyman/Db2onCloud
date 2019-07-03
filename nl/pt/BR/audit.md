---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-10"

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

# Auditoria, criação de log e monitoramento
{: #aud-log-mon}

## Auditando
{: #auditing}

É possível criar uma política de auditoria de banco de dados que fornece a capacidade de auditar várias categorias de eventos que são armazenados em tabelas de eventos de auditoria em seu banco de dados. Para obter mais informações, consulte [Diretrizes de política de auditoria ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/audit_policy_guidelines.html){:new_window}.

Também é possível auditar e rastrear mudanças em seu banco de dados usando os métodos a seguir:
* Ao criar um monitor de eventos `CHANGE HISTORY`, é possível consultar a tabela de monitor de eventos para determinar o que foi feito dentro do banco de dados e quem fez isso. Para obter mais informações, consulte [Monitor de eventos `CHANGE HISTORY` ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}.
* O Time Travel Query facilita o armazenamento de todas as mudanças em seus dados e até mesmo consulta seus dados antigos com base em um momento selecionado. Para usar esse método de auditoria, assegure-se de primeiro configurar suas tabelas para suportar o Time Travel Query. Para obter mais informações, consulte [Time Travel Query ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}

Para obter mais informações sobre como auditar e rastrear as mudanças do banco de dados, consulte [Como auditar ou rastrear mudanças? ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}.

## Criando log e monitorando
{: #log_mon}

O monitoramento e a criação de log fazem parte do serviço, no entanto, não são expostos diretamente para o usuário final. Em vez disso, a infraestrutura é usada pela equipe operacional da IBM para tratar de problemas.  

Para ver a disponibilidade do Activity Tracker, consulte o [roteiro ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/db2oncloud-roadmap){:new_window}.

É possível se conectar a um cliente da linha de comando do Db2, como o CLPPlus, para acessar informações detalhadas e diagnósticos.

### Uma visão geral básica:
{: #basic_overview}

Há dois tipos básicos de verificação. Verificações externas de funcionamento/tempo de atividade e monitoramento baseado em métricas. A IBM monitora centenas de métricas e as armazena historicamente. Com base nos valores dessas métricas, os alertas são gerados. Esses alertas são enviados para a equipe de operações da IBM para assegurar que eles sejam vistos e abordados. Além disso, a IBM também envia os logs de diagnósticos e do sistema operacional arquivados para diagnóstico rápido. O {{site.data.keyword.Db2_on_Cloud_short}} está em conformidade com o GDPR e as opções do IBM EU Cloud fornecem um nível ainda mais alto de comprometimento com o GDPR, se necessário.


