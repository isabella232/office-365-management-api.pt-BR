---
ms.TocTitle: Office 365 Management Activity API frequently asked questions
title: Perguntas frequentes sobre a API de Atividade de Gerenciamento do Office 365
description: Perguntas frequentes sobre como usar a API de Atividade de Gerenciamento do Office 365
ms.ContentId: ''
ms.topic: reference (API)
ms.date: 09/21/2018
ms.openlocfilehash: 8118f44b04beedf33e98edd5ebc63c85b8c0fbc5
ms.sourcegitcommit: a5a60b603acd9a17d7717420e377d5760e08c7da
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2018
ms.locfileid: "27240621"
---
# <a name="office-365-management-activity-api-frequently-asked-questions"></a>Perguntas frequentes sobre a API de Atividade de Gerenciamento do Office 365

#### <a name="what-events-are-audited-for-a-specific-office-365-service"></a>Que eventos são auditados para um serviço específico do Office 365?

A documentação do esquema de API de Atividade de Gerenciamento do Office 365 possui uma lista abrangente de eventos. Para ver mais detalhes, confira o [esquema de API de Atividade de Gerenciamento do Office 365](office-365-management-activity-api-schema.md).

#### <a name="how-do-i-onboard-to-the-management-activity-api"></a>Como faço para integrar a API de Atividade de Gerenciamento?

Para começar a usar a API de Atividade de Gerenciamento do Office 365, confira [ Introdução às APIs de Gerenciamento do Office 365 ](get-started-with-office-365-management-apis.md).
 
#### <a name="what-is-the-throttling-limit-for-the--management-activity-api"></a>O que é a restrição de limitação para a API de Atividade de Gerenciamento?

A restrição de limitação atual é de 60 mil solicitações/minuto por ID do Fornecedor. 

#### <a name="we-want-to-programmatically-capture-all-events-in-all-workloads-what-is-the-most-reliable-way-to-do-this"></a>Queremos capturar programaticamente todos os eventos em todas as cargas de trabalho. Qual é a maneira mais confiável de fazer isso?

Você pode fazer isso usando a API de Atividade de Gerenciamento do Office 365. Também recomendamos que você use o **modelo de pull** devido a problemas de uso de webhooks. Para saber mais, confira a seção "Como usar webhooks" em [ Solucionando problemas da API de Atividade de Gerenciamento do Office 365](troubleshooting-the-office-365-management-activity-api.md#using-webhooks).

#### <a name="is-it-true-that-mailbox-auditing-in-exchange-online-can-only-be-enabled-by-using-powershell"></a>É verdade que a auditoria de caixa de correio do Exchange Online só pode ser habilitada usando o PowerShell?

Sim. No entanto, estamos trabalhando para habilitar a auditoria de caixa de correio por padrão para todas as caixas de correio em uma organização do Office 365. Para saber mais, confira "A auditoria de caixa de correio do Exchange ativada por padrão" no [blog de Segurança, Privacidade e Conformidade da Microsoft](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Exchange-Mailbox-Auditing-will-be-enabled-by-default/ba-p/215171).

#### <a name="are-there-any-differences-in-the-records-that-are-fetched-by-the-management-activity-api-versus-the-records-that-are-returned-by-using-the-audit-log-search-tool-in-the-office-365-security--compliance-center"></a>Há alguma diferença entre os registros buscados pela API de Atividade de Gerenciamento e os registros retornados usando a ferramenta de pesquisa de log de auditoria no Centro de Conformidade e Segurança do Office 365?

Os dados retornados pelos dois métodos são os mesmos. Não ocorre a filtragem. A única diferença é que, com a API, você obtém dados dos últimos sete dias de cada vez. Ao pesquisar o log de auditoria no Centro de Conformidade e Segurança (ou usando o cmdlet [Search-UnifiedAuditLog](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog) correspondente no Exchange Online), é possível obter dados dos últimos 90 dias. 
 
#### <a name="arent-webhook-notifications-more-immediate-after-all-arent-they-event-driven"></a>As notificações do webhook não são mais imediatas? Afinal, elas não são controlados por evento?

Não. As notificações do webhook não são controladas por evento, no sentido de que o evento dispara a notificação. O blob de conteúdo ainda deve ser criado, e é a criação desse conteúdo que aciona a entrega da notificação. Recentemente, o tempo de espera de entrega de notificações ao usar um webhook tem sido maior se comparado à consulta da API diretamente com a operação */content*. Portanto, a API de Atividade de Gerenciamento não deve ser considerada como um sistema de alerta de segurança em tempo real. A Microsoft tem outros produtos para isso. No que diz respeito à segurança, as notificações de eventos da API de Atividade de Gerenciamento podem ser usadas de maneira mais apropriada para determinar padrões de uso por longos períodos.

#### <a name="when-pulling-the-data-from-the-management-activity-api-there-is-sometimes-a-delay-of-more-than-3-to-5-days-why-is-this"></a>Ao extrair os dados da API de Atividade de Gerenciamento, pode ocorrer um atraso de mais de três a cinco dias. Por que isso ocorre?

Às vezes, há situações de interrupção temporária ou outros problemas no serviço do Office 365. Nesses casos, alguns registros de auditoria são descartados, e o serviço tenta preenchê-los. Embora isso ocorra apenas em cerca de 5% a 10% dos registros, esses são os registros que podem gerar atrasos em determinadas situações. Se o atraso for superior a cinco dias, verifique o Painel de Integridade do Serviço no Centro de administração do Office 365. Se necessário, você também pode abrir um tíquete com o [suporte da Microsoft](https://support.office.com/article/contact-support-for-business-products-admin-help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b#ID0EAADAAA=online).

#### <a name="im-encountering-a-throttling-error-in-the-management-activity-api-what-should-i-do"></a>Estou encontrando um erro de limitação na API da Atividade de Gestão. O que devo fazer?

Abra um tíquete com o [Suporte da Microsoft](https://support.office.com/article/contact-support-for-business-products-admin-help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b#ID0EAADAAA=online) e solicite uma nova restrição de limitação, além de incluir uma justificativa comercial para aumentar o limite. Nós avaliaremos a solicitação e, se aceita, aumentaremos a restrição de limitação.

#### <a name="what-happens-if-i-disable-auditing-for-my-office-365-organization-will-i-still-get-events-via-the-management-activty-api"></a>O que acontece se eu desabilitar a auditoria da minha organização no Office 365? Ainda receberei eventos por meio da API da Atividade de Gestão?

Não. A auditoria deve estar habilitada na sua organização para incluir os registros por meio da API de Atividade de Gestão.

