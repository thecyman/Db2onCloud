---

copyright:
  years: 2014, 2018
lastupdated: "2018-11-01"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}

# Recursos e especificações
{: #overview}

Os recursos e as especificações do {{site.data.keyword.Db2_on_Cloud_long}} são resumidos aqui para sua conveniência.
{: shortdesc}

| Categoria | Recurso | Suportado? | Comentários |
|----------|---------|------------|----------|
| Geral | Db2 AESE | S | Db2 v11.1.3.3 |
|  | Leitura em espera | S | Somente nó DR externo |
|  | Atualizações contínuas automáticas | S | Com planos de HA |
|  | Opções de localização de data center | S | [Localizações ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/db2oncloud-locations){:new_window}. Consulte também: Implementação e durações de ajuste de escala. |
|  | BLU na memória | S | O padrão é linha, especifique `CREATE TABLE..AS COL` para o BLU |
|  | Activity Tracker | [No roteiro ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | Acesso raiz fornecido | N | Use o Db2 hospedado se o acesso raiz for necessário |
|  |  |  |  |
| Alta disponibilidade e replicação | DR externo | S | - |
|  | Alta disponibilidade (2 nós em 1 zona) | S | 99,99% de tempo de atividade do SLA |
|  | Diferentes zonas no mesmo data center | [No roteiro ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | Captura de dados de mudança (CDC) | S | - |
|  | Uso como HADR das instalações | N | Usar o CDC. Para obter informações, consulte [Como posso migrar ou sincronizar dados do Db2 para o Db2 on Cloud? ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/questions/426111/how-can-i-migrate-from-db2-to-db2-on-cloud/){:new_window} |
|  | Failover autônomo - HA | S | - |
|  | Failover autônomo - DR externo | N | Usar botão ou API |
|  | O IP se move com o failover | S | Apenas HA local; não HADR externo |
|  |  |  |  |
| Políticas de manutenção e SLAs | Planos de alta disponibilidade | 99,99% | - |
|  | Planos de servidor único | 99,5% | - |
|  | Nó de DR externo | 99,5% | Deve-se usar HA local adicional para alcançar 99,99% |
|  | Política de manutenção | S | [Ler detalhes ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/questions/439146/where-can-i-find-detail-about-maintenance-and-noti.html){:new_window} |
|  |  |  |  |
| Conformidades de segurança | Pronto para o HIPAA | S | Todos os planos pagos, incluindo o Flex. Deve-se solicitar o modo HIPAA do suporte IBM. |
|  | HITRUST  | [No roteiro ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/db2oncloud-roadmap){:new_window} |O Db2 hospedado pode ser usado hoje para HITRUST |
|  | Organização internacional para normatização (ISO)  | S | ISO 27001, 27002, 27017 e 27018 |
|  | Service Organization Controls (SOC) | S | SOC 2 Tipo 2 |
|  | GDPR | S | - |
|  | Nuvem da UE | S | Usar a região de Frankfurt. Suporte fornecido fisicamente na UE. |
|  | Lista completa de conformidades | S | [Conformidades de segurança ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SS6NHC/com.ibm.swg.im.dashdb.security.doc/doc/compliances.html){:new_window} |
|  |  |  |  |
| Backup e restauração | Backups diários | S | 14 dias de backups diários |
|  | Recuperação self-serve point-in-time | Disponível em 15 de novembro de 2018 | - |
|  | Backups mantidos externos | Por encomenda | A partir de 1º de dezembro de 2018, o externo será o padrão  |
|  | Manter backup por até 10 anos | Por encomenda | A partir de 1º de dezembro de 2018. Requer chamado de suporte. |
|  | Consultar dados antigos sem restauração | S | Deve-se configurar o [Time Travel Query ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} |
|  |  |  |  |
| Rede, segurança e VMs | Máquina virtual de único locatário | S | Todos os planos pagos, incluindo o Flex, são VMs de único locatário ou bare metal. |
|  | ICIAE | S | Solicitar ao suporte IBM. Se o ICIAE estiver sendo solicitado para um ambiente de serviço existente, os dados deverão ser migrados para o ambiente ICIAE pelo suporte IBM. |
|  | VPN | S | Solicitar ao suporte IBM |
|  | Criptografia em disco | S | -  |
|  | Conexões SSL/TLS | S | -  |
|  | Whitelisting de IP | Alguns | Disponível no nível do usuário do Db2. Para o nível de rede, considere o ICIAE ou semelhante. |
|  | KeyProtect (traga a sua própria chave) | [No roteiro ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | Serviço MIS/interconectado | [No roteiro ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  |  |  |  |
| Precificação e compra | Descontos de BYOL | S | [Comunicado ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/db2oncloud-byol){:new_window} |
|  | Disponível por meio do IBM Cloud | S | Assinatura e pré-pago |
|  | Disponível por meio de pedido de cotação de software | S | Todos os planos, incluindo o Flex. [Peças e detalhes. ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/db2oncloud-parts-public){:new_window}|
|  | Faturamento diário | S | O faturamento para os planos Flex é baseado no uso diário de pico. Por exemplo, se você escalar de 2 a 8 núcleos para uma hora de um dia, será faturado por 8 núcleos para apenas este dia e 2 núcleos para todos os outros dias do mês. |
|  | Faturamento por hora | [No roteiro ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - | 
|  | Métrica de atribuição de preço principal | Mensal | Os preços são declarados em termos mensais (por exemplo, US$ 189 por mês). Um preço mensal rateado é baseado no número de dias de serviço ativado durante o mês em que o serviço foi finalizado. [Exemplos](plans_pricing.html) |
|  |  |  |  |
| Implementação e durações de ajuste de escala | Dallas | **Implementar**: < 5 minutos. **Escalar**: < 45 minutos. | Plano Flex apenas, dependendo do inventário |
| | Outros do sul dos Estados Unidos | **Implementar**: 1 dia. **Escalar**: 8 horas. | Algumas localizações são mais curtas do que outras |
| | Frankfurt e Londres | **Implementar**: < 5 minutos. **Escalar**: 2 horas. | Plano Flex apenas, dependendo do inventário |
| | Outros da UE | **Implementar**: 3 a 5 dias. **Escalar**: 1 a 2 dias. | Algumas localizações são mais curtas do que outras |
| | Sydney | **Implementar**: < 1 hora. **Escalar**: 2 horas. | Plano Flex apenas, dependendo do inventário |
| | Outros da AP | **Implementar**: 3 a 5 dias. **Escalar**: 3 a 5 dias. | Algumas localizações são mais curtas do que outras. Volumes inferiores na AP resultam em tempos de fornecimento de infraestrutura mais lentos. |
{: caption="Tabela 1. Recursos e especificações suportados no Db2 on Cloud" caption-side="top"}

