---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-02"

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

# Políticas de manutenção e notificação
{: #maint_note_pol}

As políticas de manutenção e notificação para o serviço {{site.data.keyword.Db2_on_Cloud_long}} podem ser localizadas nas descrições de serviço do [{{site.data.keyword.Bluemix_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/software/sla/sladb.nsf/sla/bm?OpenDocument){:new_window}. Termos adicionais de serviço, especificamente para o {{site.data.keyword.Db2_on_Cloud_short}} podem ser localizados procurando na categoria **SDs adicionais com encargos**. 

Estar familiarizado com nossas políticas pode ajudar a planejar e programar suas cargas de trabalho para que elas sejam resilientes à manutenção do sistema.
{: shortdesc}

## Política de manutenção
{: #maintenance}

Efetivo a partir de 27 de março de 2018, no caso em que a manutenção programada do sistema deve ser feita para o serviço {{site.data.keyword.Db2_on_Cloud_short}}, os principais data centers (Londres, Dallas e Sydney) são atualizados em dias separados da semana comercial. Todos os outros data centers são atualizados simultaneamente em um dia da semana que não coincida com os data centers principais. A Tabela 1 mostra um exemplo de um planejamento de manutenção do sistema do {{site.data.keyword.Db2_on_Cloud_short}}.

| Datacenter | Exemplo de um planejamento de manutenção possível |
|-------------|-----------------------------|
| Londres | Segunda-feira |
| Dallas | Terça-feira |
| Sydney | Quarta-feira |
| Todas as outras | Quinta |
{: caption="Tabela 1. Exemplo de um planejamento de manutenção do sistema" caption-side="top"}

A tabela não é um planejamento de manutenção do sistema oficial, mas um exemplo de um planejamento de manutenção
possível que demonstra como a manutenção pode ser feita em dias diferentes para uma determinada atualização.
{: note}

## Política de notificação
{: #notification}

Efetivo a partir de 27 de março de 2018, a notificação é enviada dois dias úteis antes de qualquer manutenção planejada do sistema que possa impactar seu serviço {{site.data.keyword.Db2_on_Cloud_short}}. 

A política de notificação do {{site.data.keyword.Db2_on_Cloud_short}} exclui o caso em que devemos abordar, de forma oportuna, qualquer vulnerabilidade de segurança que consideramos ser um problema de nível de emergência e sensível ao tempo. Nesse caso, uma antecedência de pelo menos 24 horas é fornecida, conforme estipulado nas descrições de serviço do {{site.data.keyword.Bluemix_notm}}.
