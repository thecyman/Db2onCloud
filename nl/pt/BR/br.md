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

# Backup e restauração
{: #br}

Para planos pagos, backups criptografados do banco de dados são feitos diariamente. Um backup diário é mantido para cada um
dos últimos 14 dias.
{: shortdesc}

Os backups retidos são usados pela IBM para fins de recuperação do sistema no caso de um desastre ou perda do sistema. Use o
[Time Travel
Query ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} para manter dados históricos para suas próprias finalidades. Além disso, também é possível executar as suas próprias exportações usando o IBM Data Studio ou qualquer ferramenta DB2.

Para armazenar seus backups externos em um site de armazenamento remoto, faça uma solicitação ao suporte IBM.

Também é possível usar o [IBM Lift CLI](https://lift.ng.bluemix.net/){:new_window} para importar
dados para o {{site.data.keyword.Db2_on_Cloud_short}}.
