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

# Auditando
{: #audit}

A seguir estão os métodos pelos quais é possível auditar a atividade no banco de dados {{site.data.keyword.Db2_on_Cloud_short}}:

* [Monitor de eventos CHANGE HISTORY ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}
* [Time Travel Query ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}
{: shortdesc}

Ao criar um monitor de eventos CHANGE HISTORY, é possível consultar a tabela do monitor de eventos para determinar o que foi feito dentro do banco de dados e por quem. 

O Time Travel Query facilita o armazenamento de todas as mudanças em seus dados e até mesmo consulta seus dados antigos com base em um momento selecionado. Para usar esse método de auditoria, assegure-se de primeiro configurar suas tabelas para suportar o Time Travel Query.

Para obter mais informações sobre esses métodos de auditoria, consulte [Como auditar ou controlar mudanças? ![Ícone de linkexterno](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}.

