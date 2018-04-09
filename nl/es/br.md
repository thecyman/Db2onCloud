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

# Copia de seguridad y restauración
{: #br}

Para los planes de pago, se realizan copias de seguridad cifradas de la base de datos a diario. Se conserva una copia de seguridad diaria para cada uno de los últimos 14 días.
{: shortdesc}

IBM utiliza las copias de seguridad que se conservan para realizar una recuperación del sistema en el caso de que se produzca un error grave o una pérdida de datos del sistema. Utilice [Time Travel Query ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} para conservar datos históricos para sus propios fines. También puede realizar sus propias exportaciones mediante IBM Data Studio o cualquier herramienta de Db2.

Para guardar sus copias de seguridad en un sitio de almacenamiento remoto, realice una solicitud al equipo de soporte de IBM.

También puede utilizar la [CLI de IBM Lift](https://lift.ng.bluemix.net/){:new_window} para importar datos en {{site.data.keyword.Db2_on_Cloud_short}}.
