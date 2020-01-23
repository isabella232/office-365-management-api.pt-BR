---
ms.TocTitle: Office 365 Management APIs overview
title: Visão geral das APIs de Gerenciamento do Office 365
description: Oferecem uma plataforma de extensibilidade única para todas as tarefas de gerenciamento de clientes e de parceiros do Office 365, incluindo comunicações do serviço, segurança, conformidade, relatórios e auditoria.
ms.ContentId: 4fca85f9-efa6-3b4b-b10d-a07cb31f803f
ms.topic: reference (API)
ms.date: 09/28/2016
localization_priority: Priority
ms.openlocfilehash: 88b7e590d769699ed186d7cecaf80e162d79a095
ms.sourcegitcommit: 36d0167805d24bbb3e2cf1a02d0f011270cc31cb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/22/2020
ms.locfileid: "41263279"
---
# <a name="office-365-management-apis-overview"></a><span data-ttu-id="95e29-103">Visão geral das APIs de Gerenciamento do Office 365</span><span class="sxs-lookup"><span data-stu-id="95e29-103">Office 365 Management APIs overview</span></span>

<span data-ttu-id="95e29-104">As APIs de Gerenciamento do Office 365 oferecem uma plataforma de extensibilidade única para todas as tarefas de gerenciamento de clientes e de parceiros do Office 365, incluindo comunicações de serviço, segurança, conformidade, relatórios e auditoria.</span><span class="sxs-lookup"><span data-stu-id="95e29-104">The Office 365 Management APIs provide a single extensibility platform for all Office 365 customers' and partners' management tasks, including service communications, security, compliance, reporting, and auditing.</span></span> <span data-ttu-id="95e29-105">Todas as APIs de Gerenciamento do Office 365 são consistentes no design e na implementação com o pacote atual de APIs REST do Office 365, usando abordagens comuns de padrões da indústria, incluindo OAuth v2, OData v4 e JSON.</span><span class="sxs-lookup"><span data-stu-id="95e29-105">All of the Office 365 Management APIs are consistent in design and implementation with the current suite of Office 365 REST APIs, using common industry-standard approaches, including OAuth v2, OData v4, and JSON.</span></span> <span data-ttu-id="95e29-106">Como em outras APIs do Office 365, os aplicativos são registrados no Azure Active Directory, oferecendo aos desenvolvedores uma forma consistente de autenticar e autorizar os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="95e29-106">Like the other Office 365 APIs, applications are registered in Azure Active Directory, giving developers a consistent way to authenticate and authorize their apps.</span></span>

<span data-ttu-id="95e29-107">Publique suas dúvidas sobre as APIs de Gerenciamento do Office 365 no [Stack Overflow](http://stackoverflow.com/tags/office365) usando a tag [office365].</span><span class="sxs-lookup"><span data-stu-id="95e29-107">If you have questions about the Office 365 Management APIs, post your question on [Stack Overflow](http://stackoverflow.com/tags/office365), using the [office365] tag.</span></span>

## <a name="office-365-service-communications-api-preview"></a><span data-ttu-id="95e29-108">API de Comunicações do Serviço do Office 365 (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="95e29-108">Office 365 Service Communications API (preview)</span></span>

<span data-ttu-id="95e29-109">A API de Comunicações do Serviço do Office 365 foi lançada no modo de visualização.</span><span class="sxs-lookup"><span data-stu-id="95e29-109">The Office 365 Service Communications API has been released in preview mode.</span></span> <span data-ttu-id="95e29-110">Ela substitui a API de Comunicações do Serviço do Office 365 para fornecer informações sobre a integridade do serviço para parceiros e administradores de locatários.</span><span class="sxs-lookup"><span data-stu-id="95e29-110">It replaces the Office 365 Service Communications API to provide service health information to tenant administrators and partners.</span></span> <span data-ttu-id="95e29-111">Ao contrário da versão anterior, a nova API de Comunicações do Serviço fornece uma experiência coesa na plataforma, com as APIs REST criadas de forma consistentemente, incluindo a nomenclatura da URL, o formato de dados e a autenticação.</span><span class="sxs-lookup"><span data-stu-id="95e29-111">Unlike the previous version, the new Service Communications API delivers a cohesive platform experience, with REST APIs built in a consistent fashion including URL naming, data format, and authentication.</span></span>

<span data-ttu-id="95e29-112">Os novos recursos são adicionados somente para a nova versão da API, incentivando a adoção antecipada por clientes herdados.</span><span class="sxs-lookup"><span data-stu-id="95e29-112">New features are only added to the new version of the API, encouraging early adoption by legacy customers.</span></span> <span data-ttu-id="95e29-113">Quando o Anúncio Geral da API de Comunicações do Serviço do Office 365 foi feito, a versão anterior da API de Comunicações do Serviço iniciou um período de substituição.</span><span class="sxs-lookup"><span data-stu-id="95e29-113">When the General Announcement of Office 365 Service Communications API was made, the older version of the Service Communications API began a period of deprecation.</span></span> 

<span data-ttu-id="95e29-114">Confira a referência de operações em [Referência da API de Comunicações do Serviço do Office 365 (versão prévia)](office-365-service-communications-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="95e29-114">For the operations reference, see [Office 365 Service Communications API reference (preview)](office-365-service-communications-api-reference.md).</span></span>


## <a name="office-365-management-activity-api"></a><span data-ttu-id="95e29-115">API da Atividade de Gerenciamento do Office 365</span><span class="sxs-lookup"><span data-stu-id="95e29-115">Office 365 Management Activity API</span></span>

<span data-ttu-id="95e29-116">A API da Atividade de Gerenciamento do Office 365 fornece informações sobre várias ações e eventos de usuário, administração, sistema e políticas dos logs de atividades do Office 365 e do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="95e29-116">The Office 365 Management Activity API provides information about various user, admin, system, and policy actions and events from Office 365 and Azure Active Directory activity logs.</span></span> <span data-ttu-id="95e29-117">Clientes e parceiros podem usar essa informação para aprimorar ou criar novas soluções de monitoramento de conformidade, segurança e operações para empresas.</span><span class="sxs-lookup"><span data-stu-id="95e29-117">Customers and partners can use this information to create new or enhance existing operations, security, and compliance-monitoring solutions for the enterprise.</span></span> 

<span data-ttu-id="95e29-118">Confira referências de operações em [Referência da API da Atividade de Gerenciamento do Office 365](office-365-management-activity-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="95e29-118">For the operations reference, see [Office 365 Management Activity API reference](office-365-management-activity-api-reference.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="95e29-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="95e29-119">See also</span></span>

- [<span data-ttu-id="95e29-120">Introdução às APIs de Gerenciamento do Office 365</span><span class="sxs-lookup"><span data-stu-id="95e29-120">Get started with Office 365 Management APIs</span></span>](get-started-with-office-365-management-apis.md)
- [<span data-ttu-id="95e29-121">Esquema da API da Atividade de Gerenciamento do Office 365</span><span class="sxs-lookup"><span data-stu-id="95e29-121">Office 365 Management Activity API schema</span></span>](office-365-management-activity-api-schema.md)
- [<span data-ttu-id="95e29-122">Solução de problemas da API da Atividade de Gerenciamento do Office 365</span><span class="sxs-lookup"><span data-stu-id="95e29-122">Troubleshooting the Office 365 Management Activity API</span></span>](troubleshooting-the-office-365-management-activity-api.md)
- [<span data-ttu-id="95e29-123">APIs REST do Office 365</span><span class="sxs-lookup"><span data-stu-id="95e29-123">Office 365 REST APIs</span></span>](https://docs.microsoft.com/previous-versions/office/office-365-api/how-to/platform-development-overview)

