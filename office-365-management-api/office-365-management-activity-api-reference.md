---
ms.TocTitle: Office 365 Management Activity API reference
title: Referência da API da Atividade de Gerenciamento do Office 365
description: Use a API da Atividade de Gerenciamento do Office 365 para recuperar informações sobre ações e eventos de usuário, administração, sistema e políticas dos logs de atividades do Office 365 e do Azure AD.
ms.ContentId: 52749845-37f8-6076-7ea5-49d9a4055445
ms.topic: reference (API)
ms.date: ''
localization_priority: Priority
ms.openlocfilehash: 48065e1770e485ffa04778d662a170ae14916354
ms.sourcegitcommit: d55928a0d535090fa2dbe94f38c7316d0e52e9a9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2020
ms.locfileid: "44173138"
---
# <a name="office-365-management-activity-api-reference"></a><span data-ttu-id="9ed50-103">Referência da API da Atividade de Gerenciamento do Office 365</span><span class="sxs-lookup"><span data-stu-id="9ed50-103">Office 365 Management Activity API reference</span></span>

<span data-ttu-id="9ed50-104">Use a API da Atividade de Gerenciamento do Office 365 para recuperar informações sobre ações e eventos de usuário, administração, sistema e políticas dos logs de atividades do Office 365 e do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="9ed50-104">Use the Office 365 Management Activity API to retrieve information about user, admin, system, and policy actions and events from Office 365 and Azure AD activity logs.</span></span> 

<span data-ttu-id="9ed50-105">Você pode usar as ações e os eventos dos logs de auditoria e atividades do Office 365 e do Microsoft Azure Active Directory para criar soluções que forneçam monitoramento, análise e visualização de dados.</span><span class="sxs-lookup"><span data-stu-id="9ed50-105">You can use the actions and events from the Office 365 and Microsoft Azure Active Directory audit and activity logs to create solutions that provide monitoring, analysis, and data visualization.</span></span> <span data-ttu-id="9ed50-106">Essas soluções oferecem às organizações mais visibilidade das ações realizadas em relação a seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="9ed50-106">These solutions give organizations greater visibility into actions taken on their content.</span></span> <span data-ttu-id="9ed50-107">Essas ações e eventos também estão disponíveis nos Relatórios de Atividades do Office 365.</span><span class="sxs-lookup"><span data-stu-id="9ed50-107">These actions and events are also available in the Office 365 Activity Reports.</span></span> <span data-ttu-id="9ed50-108">Para saber mais, confira [Pesquisar o log de auditoria no Centro de Conformidade e Segurança do Office 365](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).</span><span class="sxs-lookup"><span data-stu-id="9ed50-108">For more information, see [Search the audit log in the Office 365 Security & Compliance Center](https://support.office.com/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).</span></span>

<span data-ttu-id="9ed50-109">A API da Atividade de Gerenciamento do Office 365 é um serviço Web REST que você pode usar para desenvolver soluções usando qualquer linguagem e ambiente de hospedagem que dê suporte a certificados HTTPS e X.509.</span><span class="sxs-lookup"><span data-stu-id="9ed50-109">The Office 365 Management Activity API is a REST web service that you can use to develop solutions using any language and hosting environment that supports HTTPS and X.509 certificates.</span></span> <span data-ttu-id="9ed50-110">A API depende do Azure AD e do protocolo OAuth2 para autorização e autenticação.</span><span class="sxs-lookup"><span data-stu-id="9ed50-110">The API relies on Azure AD and the OAuth2 protocol for authentication and authorization.</span></span> <span data-ttu-id="9ed50-111">Para acessar a API por meio de seu aplicativo, primeiro será preciso registrá-la no Azure AD e configurá-la com permissões apropriadas.</span><span class="sxs-lookup"><span data-stu-id="9ed50-111">To access the API from your application, you'll need to first register it in Azure AD and configure it with appropriate permissions.</span></span> <span data-ttu-id="9ed50-112">Isso habilitará o aplicativo a solicitar os tokens de acesso OAuth2 necessários para chamar a API.</span><span class="sxs-lookup"><span data-stu-id="9ed50-112">This will enable your application to request the OAuth2 access tokens it needs to call the API.</span></span> <span data-ttu-id="9ed50-113">Para saber mais, confira [Introdução às APIs de Gerenciamento do Office 365](get-started-with-office-365-management-apis.md).</span><span class="sxs-lookup"><span data-stu-id="9ed50-113">For more information, see [Get started with Office 365 Management APIs](get-started-with-office-365-management-apis.md).</span></span>

<span data-ttu-id="9ed50-114">Para obter informações sobre os dados que a API da Atividade de Gerenciamento do Office 365 retorna, confira [Esquema da API da Atividade de Gerenciamento do Office 365](office-365-management-activity-api-schema.md).</span><span class="sxs-lookup"><span data-stu-id="9ed50-114">For information about the data that the Office 365 Management Activity API returns, see [Office 365 Management Activity API schema](office-365-management-activity-api-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ed50-115">Para poder acessar dados por meio da API de Atividade de Gerenciamento do Office 365, habilite o log de auditoria unificado para a sua organização do Office 365.</span><span class="sxs-lookup"><span data-stu-id="9ed50-115">Before you can access data through the Office 365 Management Activity API, you must enable unified audit logging for your Office 365 organization.</span></span> <span data-ttu-id="9ed50-116">Para fazer isso, ative o log de auditoria do Office 365.</span><span class="sxs-lookup"><span data-stu-id="9ed50-116">You do this by turning on the Office 365 audit log.</span></span> <span data-ttu-id="9ed50-117">Para obter instruções, confira [Ativar ou desativar a pesquisa de log de auditoria do Office 365](https://docs.microsoft.com/office365/securitycompliance/turn-audit-log-search-on-or-off).</span><span class="sxs-lookup"><span data-stu-id="9ed50-117">For instructions, see [Turn Office 365 audit log search on or off](https://docs.microsoft.com/office365/securitycompliance/turn-audit-log-search-on-or-off).</span></span>


## <a name="working-with-the-office-365-management-activity-api"></a><span data-ttu-id="9ed50-118">Usar a API da Atividade de Gerenciamento do Office 365</span><span class="sxs-lookup"><span data-stu-id="9ed50-118">Working with the Office 365 Management Activity API</span></span>

<span data-ttu-id="9ed50-119">A API da Atividade de Gerenciamento do Office 365 agrega ações e eventos em blobs de conteúdo específicos de locatário, que são classificados pelo tipo e pela origem de seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="9ed50-119">The Office 365 Management Activity API aggregates actions and events into tenant-specific content blobs, which are classified by the type and source of the content they contain.</span></span> <span data-ttu-id="9ed50-120">Atualmente, há suporte para estes tipos de conteúdo:</span><span class="sxs-lookup"><span data-stu-id="9ed50-120">Currently, these content types are supported:</span></span>

- <span data-ttu-id="9ed50-121">Audit.AzureActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="9ed50-121">Audit.AzureActiveDirectory</span></span>
    
- <span data-ttu-id="9ed50-122">Audit.Exchange</span><span class="sxs-lookup"><span data-stu-id="9ed50-122">Audit.Exchange</span></span>
    
- <span data-ttu-id="9ed50-123">Audit.SharePoint</span><span class="sxs-lookup"><span data-stu-id="9ed50-123">Audit.SharePoint</span></span>
    
- <span data-ttu-id="9ed50-124">Audit.General (inclui todas as outras cargas de trabalho não incluídas nos tipos de conteúdo anteriores)</span><span class="sxs-lookup"><span data-stu-id="9ed50-124">Audit.General (includes all other workloads not included in the previous content types)</span></span>

- <span data-ttu-id="9ed50-125">DLP.All (apenas eventos DLP para todas as cargas de trabalho)</span><span class="sxs-lookup"><span data-stu-id="9ed50-125">DLP.All (DLP events only for all workloads)</span></span>
    
<span data-ttu-id="9ed50-126">Para saber mais sobre os eventos e as propriedades associados a esses tipos de conteúdo, confira [Esquema de API da Atividade de Gerenciamento do Office 365](office-365-management-activity-api-schema.md).</span><span class="sxs-lookup"><span data-stu-id="9ed50-126">For details about the events and properties associated with these content types, see [Office 365 Management Activity API schema](office-365-management-activity-api-schema.md).</span></span>

<span data-ttu-id="9ed50-127">Para começar a recuperar blobs de conteúdo para um locatário, primeiro você cria uma assinatura para os tipos de conteúdo desejados.</span><span class="sxs-lookup"><span data-stu-id="9ed50-127">To begin retrieving content blobs for a tenant, you first a create subscription to the desired content types.</span></span> <span data-ttu-id="9ed50-128">Se está recuperando blobs de conteúdo para vários locatários, você cria várias assinaturas para cada um dos tipos de conteúdo desejados, uma para cada locatário.</span><span class="sxs-lookup"><span data-stu-id="9ed50-128">If you are retrieving content blobs for multiple tenants, you create multiple subscriptions to each of the desired content types, one for each tenant.</span></span>

<span data-ttu-id="9ed50-129">Após criar uma assinatura, você pode realizar uma sondagem regularmente para descobrir novos blobs de conteúdo que estão disponíveis para download ou pode registrar um ponto de extremidade de webhook com a assinatura, e enviaremos notificações a esse ponto de extremidade quando novos blobs de conteúdo estiverem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9ed50-129">After you create a subscription, you can poll regularly to discover new content blobs that are available for download, or you can register a webhook endpoint with the subscription and we will send notifications to this endpoint as new content blobs are available.</span></span>


> [!NOTE] 
> <span data-ttu-id="9ed50-130">Quando uma assinatura é criada, pode levar até 12 horas para que os primeiros blobs de conteúdo fiquem disponíveis para essa assinatura.</span><span class="sxs-lookup"><span data-stu-id="9ed50-130">When a subscription is created, it can take up to 12 hours for the first content blobs to become available for that subscription.</span></span> <span data-ttu-id="9ed50-131">Os blobs de conteúdo são criados com a coleta e a agregação de ações e eventos entre vários servidores e data centers.</span><span class="sxs-lookup"><span data-stu-id="9ed50-131">The content blobs are created by collecting and aggregating actions and events across multiple servers and datacenters.</span></span> <span data-ttu-id="9ed50-132">Como resultado desse processo distribuído, as ações e os eventos contidos nos blobs de conteúdo não necessariamente aparecerão na ordem em que ocorreram.</span><span class="sxs-lookup"><span data-stu-id="9ed50-132">As a result of this distributed process, the actions and events contained in the content blobs will not necessarily appear in the order in which they occurred.</span></span> <span data-ttu-id="9ed50-133">Um blob de conteúdo pode ter ações e eventos que ocorreram antes das ações e dos eventos contidos em um blob de conteúdo anterior.</span><span class="sxs-lookup"><span data-stu-id="9ed50-133">One content blob can contain actions and events that occurred prior to the actions and events contained in an earlier content blob.</span></span> <span data-ttu-id="9ed50-134">Estamos trabalhando para reduzir a latência entre a ocorrência de ações e eventos, bem como a respectiva disponibilidade em um blob de conteúdo, mas não podemos garantir que eles apareçam sequencialmente.</span><span class="sxs-lookup"><span data-stu-id="9ed50-134">We are working to decrease the latency between the occurrence of actions and events and their availability within a content blob, but we can't guarantee that they appear sequentially.</span></span>


> [!NOTE] 
> <span data-ttu-id="9ed50-135">Os dados confidenciais de DLP só estão disponíveis na API de feed de atividades para usuários que receberam permissões para "Ler dados confidenciais de DLP".</span><span class="sxs-lookup"><span data-stu-id="9ed50-135">DLP sensitive data is only available in the activity feed API to users that have been granted “Read DLP sensitive data” permissions.</span></span> <span data-ttu-id="9ed50-136">Para saber mais sobre DLP (Prevenção contra Perda de Dados), confira [Visão geral de Políticas de Prevenção contra Perda de Dados](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)</span><span class="sxs-lookup"><span data-stu-id="9ed50-136">For more on Data Loss Prevention (DLP) see [Overview of Data Loss Prevention Policies](https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)</span></span>

## <a name="activity-api-operations"></a><span data-ttu-id="9ed50-137">Operações de API de atividade</span><span class="sxs-lookup"><span data-stu-id="9ed50-137">Activity API operations</span></span>

<span data-ttu-id="9ed50-138">Todas as operações da API têm como escopo um único locatário, e a URL raiz da API inclui uma ID de locatário que especifica o contexto do locatário.</span><span class="sxs-lookup"><span data-stu-id="9ed50-138">All API operations are scoped to a single tenant and the root URL of the API includes a tenant ID that specifies the tenant context.</span></span> <span data-ttu-id="9ed50-139">A ID de locatário é um GUID.</span><span class="sxs-lookup"><span data-stu-id="9ed50-139">The tenant ID is a GUID.</span></span> <span data-ttu-id="9ed50-140">Para saber mais sobre como obter o GUID, confira [Introdução às APIs de Gerenciamento do Office 365](get-started-with-office-365-management-apis.md).</span><span class="sxs-lookup"><span data-stu-id="9ed50-140">For information about how to get the GUID, see [Get started with Office 365 Management APIs](get-started-with-office-365-management-apis.md).</span></span> 

<span data-ttu-id="9ed50-141">Como as notificações que enviamos a seu webhook incluem a ID de locatário, você pode usar o mesmo webhook para receber notificações para todos os locatários.</span><span class="sxs-lookup"><span data-stu-id="9ed50-141">Because the notifications we send to your webhook include the tenant ID, you can use the same webhook to receive notifications for all tenants.</span></span>

<span data-ttu-id="9ed50-142">A URL do ponto de extremidade da API que você usa é baseada no tipo de plano de assinatura do Microsoft 365 ou Office 365 para sua organização.</span><span class="sxs-lookup"><span data-stu-id="9ed50-142">The URL for the API endpoint that you use is based on the type of Microsoft 365 or Office 365 subscription plan for your organization.</span></span>

<span data-ttu-id="9ed50-143">**Plano empresarial e plano governamental GCC**</span><span class="sxs-lookup"><span data-stu-id="9ed50-143">**Enterprise plan and GCC government plan**</span></span>

```http
https://manage.office.com/api/v1.0/{tenant_id}/activity/feed/{operation}
```

<span data-ttu-id="9ed50-144">**Plano de alto governo GCC**</span><span class="sxs-lookup"><span data-stu-id="9ed50-144">**GCC High government plan**</span></span>

```http
https://manage.office365.us/api/v1.0/{tenant_id}/activity/feed/{operation}
```

<span data-ttu-id="9ed50-145">**Plano governamental DoD**</span><span class="sxs-lookup"><span data-stu-id="9ed50-145">**DoD government plan**</span></span>

```http
https://manage.protection.apps.mil/api/v1.0/{tenant_id}/activity/feed/{operation}
```

<span data-ttu-id="9ed50-146">Todas as operações de API exigem um cabeçalho de Autorização HTTP com um token obtido do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="9ed50-146">All API operations require an Authorization HTTP header with an access token obtained from Azure AD.</span></span> <span data-ttu-id="9ed50-147">A ID de locatário no token de acesso deve corresponder à ID de locatário na URL raiz da API, e o token de acesso deve conter a declaração ActivityFeed.Read (isso corresponde à permissão [Ler dados de atividade de uma organização] que você configurou para o aplicativo no Azure AD).</span><span class="sxs-lookup"><span data-stu-id="9ed50-147">The tenant ID in the access token must match the tenant ID in the root URL of the API and the access token must contain the ActivityFeed.Read claim (this corresponds to the permission [Read activity data for an organization] that you configured for you application in Azure AD).</span></span>

```json
Authorization: Bearer eyJ0e...Qa6wg
```

<span data-ttu-id="9ed50-148">A API de Atividade dá suporte às seguintes operações:</span><span class="sxs-lookup"><span data-stu-id="9ed50-148">The Activity API supports the following operations:</span></span>

- <span data-ttu-id="9ed50-149">**Iniciar uma assinatura** para começar a receber notificações e recuperar dados de atividade de um locatário.</span><span class="sxs-lookup"><span data-stu-id="9ed50-149">**Start a subscription** to begin receiving notifications and retrieving activity data for a tenant.</span></span>
    
- <span data-ttu-id="9ed50-150">**Interromper uma assinatura** para descontinuar a recuperação de dados de um locatário.</span><span class="sxs-lookup"><span data-stu-id="9ed50-150">**Stop a subscription** to discontinue retrieving data for a tenant.</span></span>
    
- <span data-ttu-id="9ed50-151">**Listar as assinaturas atuais**</span><span class="sxs-lookup"><span data-stu-id="9ed50-151">**List current subscriptions**</span></span>
    
- <span data-ttu-id="9ed50-152">**Listar o conteúdo disponível** e as URLs de conteúdo correspondentes.</span><span class="sxs-lookup"><span data-stu-id="9ed50-152">**List available content** and the corresponding content URLs.</span></span>
    
- <span data-ttu-id="9ed50-153">**Receber notificações** enviadas por um webhook quando novo conteúdo está disponível.</span><span class="sxs-lookup"><span data-stu-id="9ed50-153">**Receiving notifications** sent by a webhook when new content is available.</span></span>
    
- <span data-ttu-id="9ed50-154">**Recuperar conteúdo** usando a URL de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="9ed50-154">**Retrieving content** by using the content URL.</span></span>
    
- <span data-ttu-id="9ed50-155">**Listar notificações** enviadas por um webhook.</span><span class="sxs-lookup"><span data-stu-id="9ed50-155">**List notifications** sent by a webhook.</span></span>

- <span data-ttu-id="9ed50-156">**Recuperar nomes amigáveis de recursos** para objetos no feed de dados identificados por guids.</span><span class="sxs-lookup"><span data-stu-id="9ed50-156">**Retrieve resource friendly names** for objects in the data feed identified by guids.</span></span>
    

## <a name="start-a-subscription"></a><span data-ttu-id="9ed50-157">Iniciar uma assinatura</span><span class="sxs-lookup"><span data-stu-id="9ed50-157">Start a subscription</span></span>

<span data-ttu-id="9ed50-158">Essa operação inicia uma assinatura para o tipo de conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-158">This operation starts a subscription to the specified content type.</span></span> <span data-ttu-id="9ed50-159">Se já existir uma assinatura para o tipo de conteúdo especificado, essa operação será usada para:</span><span class="sxs-lookup"><span data-stu-id="9ed50-159">If a subscription to the specified content type already exists, this operation is used to:</span></span>

- <span data-ttu-id="9ed50-160">Atualizar as propriedades de um webhook ativo.</span><span class="sxs-lookup"><span data-stu-id="9ed50-160">Update the properties of an active webhook.</span></span>
    
- <span data-ttu-id="9ed50-161">Habilitar um webhook que foi desabilitado devido a um número excessivo de notificações de falhas.</span><span class="sxs-lookup"><span data-stu-id="9ed50-161">Enable a webhook that was disabled because of excessive failed notifications.</span></span>
    
- <span data-ttu-id="9ed50-162">Habilitar novamente um webhook expirado especificando uma data de término posterior ou nula.</span><span class="sxs-lookup"><span data-stu-id="9ed50-162">Re-enable an expired webhook by specifying a later or null expiration date.</span></span>
    
- <span data-ttu-id="9ed50-163">Remover um webhook.</span><span class="sxs-lookup"><span data-stu-id="9ed50-163">Remove a webhook.</span></span>
    
||<span data-ttu-id="9ed50-164">Assinatura</span><span class="sxs-lookup"><span data-stu-id="9ed50-164">Subscription</span></span>|<span data-ttu-id="9ed50-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ed50-165">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="9ed50-166">**Path**</span><span class="sxs-lookup"><span data-stu-id="9ed50-166">**Path**</span></span>| `/subscriptions/start?contentType={ContentType}`||
|<span data-ttu-id="9ed50-167">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="9ed50-167">**Parameters**</span></span>|<span data-ttu-id="9ed50-168">contentType</span><span class="sxs-lookup"><span data-stu-id="9ed50-168">contentType</span></span>|<span data-ttu-id="9ed50-169">Deve ser um tipo de conteúdo válido.</span><span class="sxs-lookup"><span data-stu-id="9ed50-169">Must be a valid content type.</span></span>|
||<span data-ttu-id="9ed50-170">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="9ed50-170">PublisherIdentifier</span></span>|<span data-ttu-id="9ed50-171">O GUID de locatário de codificação de fornecedor para a API.</span><span class="sxs-lookup"><span data-stu-id="9ed50-171">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="9ed50-172">Este **não** é o GUID de aplicativo nem o GUID do cliente que está usando o aplicativo, mas o GUID da empresa que está escrevendo o código.</span><span class="sxs-lookup"><span data-stu-id="9ed50-172">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="9ed50-173">Este parâmetro é usado para limitar a taxa de solicitações.</span><span class="sxs-lookup"><span data-stu-id="9ed50-173">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="9ed50-174">Verifique se este parâmetro foi especificado em todas as solicitações emitidas para obter uma cota dedicada.</span><span class="sxs-lookup"><span data-stu-id="9ed50-174">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="9ed50-175">Todas as solicitações recebidas sem este parâmetro compartilharão a mesma cota.</span><span class="sxs-lookup"><span data-stu-id="9ed50-175">All requests received without this parameter will share the same quota.</span></span>|
|<span data-ttu-id="9ed50-176">**Body**</span><span class="sxs-lookup"><span data-stu-id="9ed50-176">**Body**</span></span>|<span data-ttu-id="9ed50-177">webhook</span><span class="sxs-lookup"><span data-stu-id="9ed50-177">webhook</span></span>|<span data-ttu-id="9ed50-178">Objeto JSON opcional com três propriedades:</span><span class="sxs-lookup"><span data-stu-id="9ed50-178">Optional JSON object with three properties:</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-179"><b>address</b>: ponto de extremidade HTTPS necessário que pode receber notificações.</span><span class="sxs-lookup"><span data-stu-id="9ed50-179"><b>address</b>: Required HTTPS endpoint that can receive notifications.</span></span>  <span data-ttu-id="9ed50-180">Uma mensagem de teste será enviada ao webhook para validá-lo antes da criação da assinatura.</span><span class="sxs-lookup"><span data-stu-id="9ed50-180">A test message will be sent to the webhook to validate the webhook before creating the subscription.</span></span></p></li><li><p><span data-ttu-id="9ed50-181"><b>authId</b>: cadeia de caracteres opcional que é incluída como o cabeçalho WebHook AuthID na notificação enviada ao webhook para identificar e autorizar a origem da solicitação para o webhook.</span><span class="sxs-lookup"><span data-stu-id="9ed50-181"><b>authId</b>: Optional string that will be included as the WebHook-AuthID header in notifications sent to the webhook as a means of identifying and authorizing the source of the request to the webhook.</span></span></p></li><li><p><span data-ttu-id="9ed50-182"><b>expiration</b>: data e hora opcionais que indicam uma data e uma hora após as quais as notificações não devem ser enviadas ao webhook.</span><span class="sxs-lookup"><span data-stu-id="9ed50-182"><b>expiration</b>: Optional datetime that indicates a datetime after which notifications should no longer be sent to the webhook.</span></span></p></li></ul>|
|<span data-ttu-id="9ed50-183">**Response**</span><span class="sxs-lookup"><span data-stu-id="9ed50-183">**Response**</span></span>|<span data-ttu-id="9ed50-184">contentType</span><span class="sxs-lookup"><span data-stu-id="9ed50-184">contentType</span></span>|<span data-ttu-id="9ed50-185">O tipo de conteúdo especificado na chamada.</span><span class="sxs-lookup"><span data-stu-id="9ed50-185">The content type specified in the call.</span></span>|
||<span data-ttu-id="9ed50-186">status</span><span class="sxs-lookup"><span data-stu-id="9ed50-186">status</span></span>|<span data-ttu-id="9ed50-187">O status da assinatura.</span><span class="sxs-lookup"><span data-stu-id="9ed50-187">The status of the subscription.</span></span> <span data-ttu-id="9ed50-188">Se uma assinatura for desabilitada, você não poderá listar nem recuperar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="9ed50-188">If a subscription is disabled, you will not be able to list or retrieve content.</span></span>|
||<span data-ttu-id="9ed50-189">webhook</span><span class="sxs-lookup"><span data-stu-id="9ed50-189">webhook</span></span>|<span data-ttu-id="9ed50-190">As propriedades de webhook especificadas na chamada, juntamente com o status do webhook.</span><span class="sxs-lookup"><span data-stu-id="9ed50-190">The webhook properties specified in the call together with the status of the webhook.</span></span> <span data-ttu-id="9ed50-191">Se o webhook for desabilitado, você não receberá notificações, mas ainda poderá listar e recuperar conteúdo, desde que a assinatura esteja habilitada.</span><span class="sxs-lookup"><span data-stu-id="9ed50-191">If the webhook is disabled, you will not receive notification, but you will still be able to list and retrieve content, provided the subscription is enabled.</span></span>|

#### <a name="sample-request"></a><span data-ttu-id="9ed50-192">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="9ed50-192">Sample request</span></span>

```json
POST {root}/subscriptions/start?contentType=Audit.SharePoint&PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Content-Type: application/json; utf-8
Authorization: Bearer eyJ0e...Qa6wg

{
    "webhook" : {
        "address": "https://webhook.myapp.com/o365/",
        "authId": "o365activityapinotification",
        "expiration": ""
    }
}

```


#### <a name="sample-response"></a><span data-ttu-id="9ed50-193">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="9ed50-193">Sample response</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
    "contentType": "Audit.SharePoint",
    "status": "enabled",
    "webhook": {
        "status": "enabled",
        "address":  "https://webhook.myapp.com/o365/",
        "authId": "o365activityapinotification",
        "expiration": null
    }
}

```


## <a name="webhook-validation"></a><span data-ttu-id="9ed50-194">Validação de webhook</span><span class="sxs-lookup"><span data-stu-id="9ed50-194">Webhook validation</span></span>

<span data-ttu-id="9ed50-195">Quando a operação /start for chamada e um webhook for especificado, enviaremos uma notificação de validação ao endereço de webhook especificado para validar que um ouvinte ativo pode aceitar e processar notificações.</span><span class="sxs-lookup"><span data-stu-id="9ed50-195">When the /start operation is called and a webhook is specified, we will send a validation notification to the specified webhook address to validate that an active listener can accept and process notifications.</span></span> <span data-ttu-id="9ed50-196">Se não recebermos uma resposta HTTP 200 OK, a assinatura não será criada.</span><span class="sxs-lookup"><span data-stu-id="9ed50-196">If we do not receive an HTTP 200 OK response, the subscription will not be created.</span></span> <span data-ttu-id="9ed50-197">Ou então, se /start for chamado para adicionar um webhook a uma assinatura existente, e uma resposta HTTP 200 OK não for recebida, o webhook não será adicionado, e a assinatura permanecerá inalterada.</span><span class="sxs-lookup"><span data-stu-id="9ed50-197">Or, if /start is being called to add a webhook to an existing subscription and a response of HTTP 200 OK is not received, the webhook will not be added and the subscription will remain unchanged.</span></span>

#### <a name="sample-request"></a><span data-ttu-id="9ed50-198">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="9ed50-198">Sample request</span></span>

```json
POST {webhook address}
Content-Type: application/json; charset=utf-8
Webhook-AuthID: (webhook authId, if provided)
Webhook-ValidationCode: (random opaque string)

{
    "validationCode": (random opaque string, same as header)
}

```


#### <a name="sample-response"></a><span data-ttu-id="9ed50-199">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="9ed50-199">Sample response</span></span>

```json

HTTP/1.1 200 OK

```


## <a name="stop-a-subscription"></a><span data-ttu-id="9ed50-200">Interromper uma assinatura</span><span class="sxs-lookup"><span data-stu-id="9ed50-200">Stop a subscription</span></span>

<span data-ttu-id="9ed50-201">Essa operação interrompe uma assinatura para o tipo de conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-201">This operation stops a subscription to the specified content type.</span></span> 

<span data-ttu-id="9ed50-202">Quando uma assinatura for interrompida, você não receberá mais notificações e não poderá recuperar o conteúdo disponível.</span><span class="sxs-lookup"><span data-stu-id="9ed50-202">When a subscription is stopped, you will no longer receive notifications and you will not be able to retrieve available content.</span></span> <span data-ttu-id="9ed50-203">Se a assinatura for reiniciada posteriormente, você terá acesso ao novo conteúdo desse ponto em diante.</span><span class="sxs-lookup"><span data-stu-id="9ed50-203">If the subscription is later restarted, you will have access to new content from that point forward.</span></span> <span data-ttu-id="9ed50-204">Você não poderá recuperar o conteúdo que estava disponível entre o momento em que a assinatura foi interrompida e reiniciada.</span><span class="sxs-lookup"><span data-stu-id="9ed50-204">You will not be able to retrieve content that was available between the time the subscription was stopped and restarted.</span></span>


||<span data-ttu-id="9ed50-205">Assinatura</span><span class="sxs-lookup"><span data-stu-id="9ed50-205">Subscription</span></span>|<span data-ttu-id="9ed50-206">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ed50-206">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="9ed50-207">**Path**</span><span class="sxs-lookup"><span data-stu-id="9ed50-207">**Path**</span></span>| `/subscriptions/stop?contentType={ContentType}`||
|<span data-ttu-id="9ed50-208">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="9ed50-208">**Parameters**</span></span>|<span data-ttu-id="9ed50-209">contentType</span><span class="sxs-lookup"><span data-stu-id="9ed50-209">contentType</span></span>|<span data-ttu-id="9ed50-210">Deve ser um tipo de conteúdo válido.</span><span class="sxs-lookup"><span data-stu-id="9ed50-210">Must be a valid content type.</span></span>|
||<span data-ttu-id="9ed50-211">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="9ed50-211">PublisherIdentifier</span></span>|<span data-ttu-id="9ed50-212">O GUID de locatário de codificação de fornecedor para a API.</span><span class="sxs-lookup"><span data-stu-id="9ed50-212">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="9ed50-213">Este **não** é o GUID de aplicativo nem o GUID do cliente que está usando o aplicativo, mas o GUID da empresa que está escrevendo o código.</span><span class="sxs-lookup"><span data-stu-id="9ed50-213">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="9ed50-214">Este parâmetro é usado para limitar a taxa de solicitações.</span><span class="sxs-lookup"><span data-stu-id="9ed50-214">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="9ed50-215">Verifique se este parâmetro foi especificado em todas as solicitações emitidas para obter uma cota dedicada.</span><span class="sxs-lookup"><span data-stu-id="9ed50-215">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="9ed50-216">Todas as solicitações recebidas sem este parâmetro compartilharão a mesma cota.</span><span class="sxs-lookup"><span data-stu-id="9ed50-216">All requests received without this parameter will share the same quota.</span></span>|
|<span data-ttu-id="9ed50-217">**Body**</span><span class="sxs-lookup"><span data-stu-id="9ed50-217">**Body**</span></span>|<span data-ttu-id="9ed50-218">(vazio)</span><span class="sxs-lookup"><span data-stu-id="9ed50-218">(empty)</span></span>||
|<span data-ttu-id="9ed50-219">**Response**</span><span class="sxs-lookup"><span data-stu-id="9ed50-219">**Response**</span></span>|<span data-ttu-id="9ed50-220">(vazio)</span><span class="sxs-lookup"><span data-stu-id="9ed50-220">(empty)</span></span>|||

#### <a name="sample-request"></a><span data-ttu-id="9ed50-221">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="9ed50-221">Sample request</span></span>

```json
POST {root}/subscriptions/stop?contentType=Audit.SharePoint&PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Authorization: Bearer eyJ0e...Qa6wg

```

#### <a name="sample-response"></a><span data-ttu-id="9ed50-222">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="9ed50-222">Sample response</span></span>

```json
HTTP/1.1 200 OK
```


## <a name="list-current-subscriptions"></a><span data-ttu-id="9ed50-223">Listar as assinaturas atuais</span><span class="sxs-lookup"><span data-stu-id="9ed50-223">List current subscriptions</span></span>

<span data-ttu-id="9ed50-224">Essa operação retorna um conjunto de assinaturas atuais com os webhooks associados.</span><span class="sxs-lookup"><span data-stu-id="9ed50-224">This operation returns a collection of the current subscriptions together with the associated webhooks.</span></span>

||<span data-ttu-id="9ed50-225">Assinatura</span><span class="sxs-lookup"><span data-stu-id="9ed50-225">Subscription</span></span>|<span data-ttu-id="9ed50-226">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ed50-226">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="9ed50-227">**Path**</span><span class="sxs-lookup"><span data-stu-id="9ed50-227">**Path**</span></span>| `/subscriptions/list`||
|<span data-ttu-id="9ed50-228">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="9ed50-228">**Parameters**</span></span>|<span data-ttu-id="9ed50-229">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="9ed50-229">PublisherIdentifier</span></span>|<span data-ttu-id="9ed50-230">O GUID de locatário de codificação de fornecedor para a API.</span><span class="sxs-lookup"><span data-stu-id="9ed50-230">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="9ed50-231">Este **não** é o GUID de aplicativo nem o GUID do cliente que está usando o aplicativo, mas o GUID da empresa que está escrevendo o código.</span><span class="sxs-lookup"><span data-stu-id="9ed50-231">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="9ed50-232">Este parâmetro é usado para limitar a taxa de solicitações.</span><span class="sxs-lookup"><span data-stu-id="9ed50-232">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="9ed50-233">Verifique se este parâmetro foi especificado em todas as solicitações emitidas para obter uma cota dedicada.</span><span class="sxs-lookup"><span data-stu-id="9ed50-233">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="9ed50-234">Todas as solicitações recebidas sem este parâmetro compartilharão a mesma cota.</span><span class="sxs-lookup"><span data-stu-id="9ed50-234">All requests received without this parameter will share the same quota.</span></span>|
|<span data-ttu-id="9ed50-235">**Body**</span><span class="sxs-lookup"><span data-stu-id="9ed50-235">**Body**</span></span>|<span data-ttu-id="9ed50-236">(vazio)</span><span class="sxs-lookup"><span data-stu-id="9ed50-236">(empty)</span></span>||
|<span data-ttu-id="9ed50-237">**Response**</span><span class="sxs-lookup"><span data-stu-id="9ed50-237">**Response**</span></span>|<span data-ttu-id="9ed50-238">Matriz JSON</span><span class="sxs-lookup"><span data-stu-id="9ed50-238">JSON array</span></span>|<span data-ttu-id="9ed50-239">Cada assinatura será representada por um objeto JSON com três propriedades:</span><span class="sxs-lookup"><span data-stu-id="9ed50-239">Each subscription will be represented by a JSON object with three properties:</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-240"><b>contentType</b>: indica o tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="9ed50-240"><b>contentType</b>: Indicates the content type.</span></span></p></li><li><p><span data-ttu-id="9ed50-241"><b>status</b>: indica o status da assinatura.</span><span class="sxs-lookup"><span data-stu-id="9ed50-241"><b>status</b>: Indicates the status of the subscription.</span></span></p></li><li><p><span data-ttu-id="9ed50-242"><b>webhook</b>: indica o webhook configurado, juntamente com o status (habilitado, desabilitado, expirado) dele.</span><span class="sxs-lookup"><span data-stu-id="9ed50-242"><b>webhook</b>: Indicates the configured webhook, together with the status (enabled, disabled, expired) of the webhook.</span></span>  <span data-ttu-id="9ed50-243">Se uma assinatura não tiver um webhook, a propriedade webhook estará presente, mas com um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="9ed50-243">If a subscription does not have a webhook, the webhook property will be present but with null value.</span></span></p></li></ul>|


#### <a name="sample-request"></a><span data-ttu-id="9ed50-244">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="9ed50-244">Sample request</span></span>

```json
GET {root}/subscriptions/list?PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Authorization: Bearer eyJ0e...Qa6wg

```

#### <a name="sample-response"></a><span data-ttu-id="9ed50-245">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="9ed50-245">Sample response</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "contentType" : "Audit.SharePoint",
        "status": "enabled",
        "webhook": {
            "status": "enabled",
            "address": "https://webhook.myapp.com/o365/",
            "authId": "o365activityapinotification",
            "expiration": null
        }
    },

    ...

    {
        "contentType": "Audit.Exchange",
        "webhook": null
    }
]

```


## <a name="list-available-content"></a><span data-ttu-id="9ed50-246">Listar conteúdo disponível</span><span class="sxs-lookup"><span data-stu-id="9ed50-246">List available content</span></span>

<span data-ttu-id="9ed50-247">Essa operação lista o conteúdo atualmente disponível para recuperação para o tipo de conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-247">This operation lists the content currently available for retrieval for the specified content type.</span></span> <span data-ttu-id="9ed50-248">O conteúdo é uma agregação de ações e eventos coletados de vários servidores em vários data centers.</span><span class="sxs-lookup"><span data-stu-id="9ed50-248">The content is an aggregation of actions and events harvested from multiple servers across multiple datacenters.</span></span> <span data-ttu-id="9ed50-249">O conteúdo será listado na ordem em que as agregações se tornarem disponíveis, mas não há garantia de que os eventos e as ações nas agregações sejam sequenciais.</span><span class="sxs-lookup"><span data-stu-id="9ed50-249">The content will be listed in the order in which the aggregations become available, but the events and actions within the aggregations are not guaranteed to be sequential.</span></span> <span data-ttu-id="9ed50-250">Um erro será retornado se o status da assinatura for desabilitado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-250">An error is returned if the subscription status is disabled.</span></span>


||<span data-ttu-id="9ed50-251">Assinatura</span><span class="sxs-lookup"><span data-stu-id="9ed50-251">Subscription</span></span>|<span data-ttu-id="9ed50-252">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ed50-252">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="9ed50-253">**Path**</span><span class="sxs-lookup"><span data-stu-id="9ed50-253">**Path**</span></span>| `/subscriptions/content?contentType={ContentType}&amp;startTime={0}&amp;endTime={1}`||
|<span data-ttu-id="9ed50-254">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="9ed50-254">**Parameters**</span></span>|<span data-ttu-id="9ed50-255">contentType</span><span class="sxs-lookup"><span data-stu-id="9ed50-255">contentType</span></span>|<span data-ttu-id="9ed50-256">Deve ser um tipo de conteúdo válido.</span><span class="sxs-lookup"><span data-stu-id="9ed50-256">Must be a valid content type.</span></span>|
||<span data-ttu-id="9ed50-257">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="9ed50-257">PublisherIdentifier</span></span>|<span data-ttu-id="9ed50-258">O GUID de locatário de codificação de fornecedor para a API.</span><span class="sxs-lookup"><span data-stu-id="9ed50-258">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="9ed50-259">Este **não** é o GUID de aplicativo nem o GUID do cliente que está usando o aplicativo, mas o GUID da empresa que está escrevendo o código.</span><span class="sxs-lookup"><span data-stu-id="9ed50-259">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="9ed50-260">Este parâmetro é usado para limitar a taxa de solicitações.</span><span class="sxs-lookup"><span data-stu-id="9ed50-260">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="9ed50-261">Verifique se este parâmetro foi especificado em todas as solicitações emitidas para obter uma cota dedicada.</span><span class="sxs-lookup"><span data-stu-id="9ed50-261">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="9ed50-262">Todas as solicitações recebidas sem este parâmetro compartilharão a mesma cota.</span><span class="sxs-lookup"><span data-stu-id="9ed50-262">All requests received without this parameter will share the same quota.</span></span>|
||<span data-ttu-id="9ed50-263">startTime endTime</span><span class="sxs-lookup"><span data-stu-id="9ed50-263">startTime endTime</span></span>|<span data-ttu-id="9ed50-264">As datas e horas opcionais (UTC) que indicam o intervalo de tempo do conteúdo a ser retornado, com base em quando o conteúdo foi disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-264">Optional datetimes (UTC) indicating the time range of content to return, based on when the content became available.</span></span> <span data-ttu-id="9ed50-265">O intervalo de tempo é inclusivo em relação a startTime(startTime <= contentCreated) e exclusivo em relação a endTime (contentCreated < endTime). Portanto, intervalos de tempo incrementos e não sobrepostos podem ser usados para percorrer o conteúdo disponível.</span><span class="sxs-lookup"><span data-stu-id="9ed50-265">The time range is inclusive with respect to startTime (startTime <= contentCreated) and exclusive with respect to endTime (contentCreated < endTime), so that non-overlapping, incrementing time intervals can used to page through available content.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-266">AAAA-MM-DD</span><span class="sxs-lookup"><span data-stu-id="9ed50-266">YYYY-MM-DD</span></span></p></li><li><p><span data-ttu-id="9ed50-267">AAAA-MM-DDTHH:MM</span><span class="sxs-lookup"><span data-stu-id="9ed50-267">YYYY-MM-DDTHH:MM</span></span></p></li><li><p><span data-ttu-id="9ed50-268">AAAA-MM-DDTHH:MM:SS</span><span class="sxs-lookup"><span data-stu-id="9ed50-268">YYYY-MM-DDTHH:MM:SS</span></span></p></li></ul><span data-ttu-id="9ed50-269">Ambos devem ser especificados (ou ambos omitidos), não devem estar separados por mais de 24 horas e a hora de início não pode ser mais de sete dias no passado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-269">Both must be specified (or both omitted) and they must be no more than 24 hours apart, with the start time no more than 7 days in the past.</span></span> <span data-ttu-id="9ed50-270">Por padrão, se startTime e endTime forem omitidos, o conteúdo disponível nas últimas 24 horas será retornado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-270">By default, if startTime and endTime are omitted, then the content available in the last 24 hours is returned.</span></span><p><span data-ttu-id="9ed50-271">**OBSERVAÇÃO**: embora seja possível especificar startTime e endTime separados por mais de 24 horas, isso não é recomendável.</span><span class="sxs-lookup"><span data-stu-id="9ed50-271">**NOTE**: Even though it is possible to specify a startTime and endTime more than 24 hours apart, this is not recommended.</span></span> <span data-ttu-id="9ed50-272">Além disso, se você obtiver resultados em resposta a uma solicitação de mais de 24 horas, serão resultados parciais e não deverão ser levados em consideração.</span><span class="sxs-lookup"><span data-stu-id="9ed50-272">Furthermore, if you do get any results in response to a request for more than 24 hours, these could be partial results and should not be taken into account.</span></span> <span data-ttu-id="9ed50-273">A solicitação deve ser emitida com um intervalo de no máximo 24 horas entre startTime e endTime.</span><span class="sxs-lookup"><span data-stu-id="9ed50-273">The request should be issued with an interval of no more than 24 hours between the startTime and endTime.</span></span></p>|
|<span data-ttu-id="9ed50-274">**Response**</span><span class="sxs-lookup"><span data-stu-id="9ed50-274">**Response**</span></span>|<span data-ttu-id="9ed50-275">Matriz JSON</span><span class="sxs-lookup"><span data-stu-id="9ed50-275">JSON array</span></span>|<span data-ttu-id="9ed50-276">O conteúdo disponível será representado por objetos JSON com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="9ed50-276">The available content will be represented by JSON objects with the following properties:</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-277"><b>contentType</b>: indica o tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="9ed50-277"><b>contentType</b>: Indicates the content type.</span></span></p></li><li><p><span data-ttu-id="9ed50-278"><b>contentId</b>: uma cadeia de caracteres opaca que identifica o conteúdo de forma exclusiva.</span><span class="sxs-lookup"><span data-stu-id="9ed50-278"><b>contentId</b>: An opaque string that uniquely identifies the content.</span></span></p></li><li><p><span data-ttu-id="9ed50-279"><b>contentUri</b>: a URL a ser usada ao recuperar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="9ed50-279"><b>contentUri</b>: The URL to use when retrieving the content.</span></span></p></li><li><p><span data-ttu-id="9ed50-280"><b>contentCreated</b>: data e hora em que o conteúdo foi disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-280"><b>contentCreated</b>: The datetime when the content was made available.</span></span></p></li><li><p><span data-ttu-id="9ed50-281"><b>contentExpiration</b>: data e hora em que o conteúdo não estará mais disponível para recuperação.</span><span class="sxs-lookup"><span data-stu-id="9ed50-281"><b>contentExpiration</b>: The datetime after which the content will no longer be available for retrieval.</span></span></p></li></ul>|


#### <a name="sample-request"></a><span data-ttu-id="9ed50-282">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="9ed50-282">Sample request</span></span>

```json
GET {root}/subscriptions/content?contentType=Audit.SharePoint&PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Authorization: Bearer eyJ0e...Qa6wg

```

#### <a name="sample-response"></a><span data-ttu-id="9ed50-283">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="9ed50-283">Sample response</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "contentType": "Audit.SharePoint",
        "contentId": "492638008028$492638008028$f28ab78ad40140608012736e373933ebspo2015043022$4a81a7c326fc4aed89c62e6039ab833b$04",
        "contentUri": "https://manage.office.com/api/v1.0/f28ab78a-d401-4060-8012-736e373933eb/activity/feed/audit/492638008028$492638008028$f28ab78ad40140608012736e373933ebspo2015043022$4a81a7c326fc4aed89c62e6039ab833b$04",
        "contentCreated": "2015-05-23T17:35:00.000Z",
        "contentExpiration": "2015-05-30T17:35:00.000Z"
    },
    ...
]

```


### <a name="pagination"></a><span data-ttu-id="9ed50-284">Paginação</span><span class="sxs-lookup"><span data-stu-id="9ed50-284">Pagination</span></span>

<span data-ttu-id="9ed50-285">Ao ser listado o conteúdo disponível para um intervalo de tempo, o número de resultados retornados é limitado para impedir tempos limite de resposta.</span><span class="sxs-lookup"><span data-stu-id="9ed50-285">When listing available content for a time range, the number of results returned is limited to prevent response timeouts.</span></span> <span data-ttu-id="9ed50-286">Se houver mais resultados no intervalo de tempo especificado do que o máximo que pode ser retornados em uma única resposta, eles serão truncados, e um cabeçalho será adicionado à resposta para indicar a URL a ser usada para recuperar a próxima página de resultados.</span><span class="sxs-lookup"><span data-stu-id="9ed50-286">If there are more results in the specified time range than can be returned in single response, the results will be truncated and a header will be added to the response indicating the URL to use to retrieve the next page of results.</span></span> <span data-ttu-id="9ed50-287">A URL conterá os mesmos parâmetros _startTime_ e _endTime_ especificados na solicitação original, juntamente com um parâmetro que indica a ID interna da próxima página.</span><span class="sxs-lookup"><span data-stu-id="9ed50-287">The URL will contain the same  _startTime_ and _endTime_ parameters that were specified in the original request, together with a parameter indicating the internal ID of the next page.</span></span> <span data-ttu-id="9ed50-288">Se _startTime_ e _endTime_ não tiverem sido especificados na solicitação original, eles serão definidos para refletir o intervalo de 24 horas que precedia a solicitação original.</span><span class="sxs-lookup"><span data-stu-id="9ed50-288">If _startTime_ and _endTime_ were not specified in the original request, they will be set to reflect the 24-hour interval that preceded the original request.</span></span>


```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
NextPageUri: https://manage.office.com/api/v1/{tenant_id}/activity/feed/subscriptions/content?contentType=Audit.SharePoint&amp;startTime=2015-10-01&amp;endTime=2015-10-02&amp;nextPage=2015101900R022885001761

```

<span data-ttu-id="9ed50-289">Para listar todo o conteúdo disponível para um intervalo de tempo especificado, talvez seja necessário recuperar várias páginas até que uma resposta sem o cabeçalho **NextPageUri** seja recebida.</span><span class="sxs-lookup"><span data-stu-id="9ed50-289">To list all available content for a specified time range, you might need to retrieve multiple pages until a response without the **NextPageUri** header is received.</span></span>


## <a name="receiving-notifications"></a><span data-ttu-id="9ed50-290">Receber notificações</span><span class="sxs-lookup"><span data-stu-id="9ed50-290">Receiving notifications</span></span>

<span data-ttu-id="9ed50-291">Notificações são enviadas ao webhook configurado para uma assinatura à medida que novo conteúdo fica disponível.</span><span class="sxs-lookup"><span data-stu-id="9ed50-291">Notifications are sent to the configured webhook for a subscription as new content becomes available.</span></span> <span data-ttu-id="9ed50-292">Como a notificação inclui o identificador de locatário, você pode usar o mesmo webhook para receber notificações para todos os locatários para os quais tem assinaturas.</span><span class="sxs-lookup"><span data-stu-id="9ed50-292">Because the notification includes the tenant identifier, you can use the same webhook to receive notifications for all tenants for which you have subscriptions.</span></span>

<span data-ttu-id="9ed50-293">A notificação é criada como um HTTP POST sobre TLS (TLS 1.0 e versões posteriores) para o endereço do webhook especificado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-293">The notification is made as an HTTP POST over TLS (TLS 1.0 and later versions) to the specified webhook address.</span></span> <span data-ttu-id="9ed50-294">Se a configuração do webhook inclui uma ID de autenticação, a enviamos como um cabeçalho HTTP: Webhook AuthID.</span><span class="sxs-lookup"><span data-stu-id="9ed50-294">If the webhook configuration includes an auth ID, we will send it as an HTTP header: Webhook-AuthID.</span></span> <span data-ttu-id="9ed50-295">Uma resposta diferente de HTTP 200 OK será considerada uma falha, e a notificação será tentada novamente.</span><span class="sxs-lookup"><span data-stu-id="9ed50-295">Any response other than HTTP 200 OK will be considered a failure and the notification will be retried.</span></span> <span data-ttu-id="9ed50-296">Você também pode configurar o webhook para exigir autenticação baseada em certificado de cliente, e faremos a autenticação usando o certificado manage.office.com.</span><span class="sxs-lookup"><span data-stu-id="9ed50-296">You can also configure your webhook to require client certificate-based authentication and we will authenticate using the manage.office.com certificate.</span></span>

<span data-ttu-id="9ed50-297">O corpo da solicitação conterá uma matriz de um ou mais objetos JSON que representam os blobs de conteúdo disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9ed50-297">The body of the request will contain an array of one or more JSON objects that represent the available content blobs.</span></span> <span data-ttu-id="9ed50-298">O número de blobs de conteúdo em cada notificação é limitado para manter o tamanho da notificação relativamente pequeno.</span><span class="sxs-lookup"><span data-stu-id="9ed50-298">The number of content blobs in each notification is limited to keep the size of the notification relatively small.</span></span> <span data-ttu-id="9ed50-299">Como esse limite pode ser alterado, a implementação deve consultar o comprimento da matriz, em vez de esperar um tamanho fixo.</span><span class="sxs-lookup"><span data-stu-id="9ed50-299">Because this limit might change, your implementation should query for the length of the array instead of expecting a fixed size.</span></span> <span data-ttu-id="9ed50-300">Cada objeto incluirá as mesmas propriedades retornadas pela operação /content, juntamente com o GUID do locatário ao qual os dados pertencem e o GUID do aplicativo que criou as assinaturas.</span><span class="sxs-lookup"><span data-stu-id="9ed50-300">Each object will include the same properties returned by the /content operation, together with the GUID of the tenant to which the data belongs and the GUID of your application that created the subscriptions.</span></span> <span data-ttu-id="9ed50-301">Isso permite que o webhook estabeleça o contexto quando está sendo usado com vários locatários e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9ed50-301">This allows the webhook to establish context when it is being used with multiple tenants and applications.</span></span>

- <span data-ttu-id="9ed50-302">**tenantId**: o GUID do locatário ao qual o conteúdo pertence.</span><span class="sxs-lookup"><span data-stu-id="9ed50-302">**tenantId**: The GUID of the tenant to which the content belongs.</span></span>
    
- <span data-ttu-id="9ed50-303">**clientId**: o GUID do aplicativo que criou a assinatura.</span><span class="sxs-lookup"><span data-stu-id="9ed50-303">**clientId**: The GUID of your application that created the subscription.</span></span>
    
- <span data-ttu-id="9ed50-304">**contentType**: indica o tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="9ed50-304">**contentType**: Indicates the content type.</span></span>
    
- <span data-ttu-id="9ed50-305">**contentId**: uma cadeia de caracteres opaca que identifica o conteúdo de forma exclusiva.</span><span class="sxs-lookup"><span data-stu-id="9ed50-305">**contentId**: An opaque string that uniquely identifies the content.</span></span>
    
- <span data-ttu-id="9ed50-306">**contentUri**: a URL a ser usada ao recuperar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="9ed50-306">**contentUri**: The URL to use when retrieving the content.</span></span>
    
- <span data-ttu-id="9ed50-307">**contentCreated**: data e hora em que o conteúdo foi disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-307">**contentCreated**: The datetime when the content was made available.</span></span>
    
- <span data-ttu-id="9ed50-308">**contentExpiration**: data e hora em que o conteúdo não estará mais disponível para recuperação.</span><span class="sxs-lookup"><span data-stu-id="9ed50-308">**contentExpiration**: The datetime after which the content will no longer be available for retrieval.</span></span>
    
<span data-ttu-id="9ed50-309">A seguir há um exemplo de uma notificação.</span><span class="sxs-lookup"><span data-stu-id="9ed50-309">The following is an example of a notification.</span></span>

```json
POST https://webhook.myapp.com/o365/ 
Content-Type: application/json; utf-8
Webhook-AuthID: o365activityapinotification

[
    {
        "tenantId": "{GUID}"
        "clientId": "{GUID}"
        "contentType": "Audit.SharePoint",
        "contentId": "492638008028$492638008028$f28ab78ad40140608012736e373933ebspo2015043022$4a81a7c326fc4aed89c62e6039ab833b$04",
        "contentUri": "https://manage.office.com/api/v1.0/f28ab78a-d401-4060-8012-736e373933eb/activity/feed/audit/492638008028$492638008028$f28ab78ad40140608012736e373933ebspo2015043022$4a81a7c326fc4aed89c62e6039ab833b$04",
        "contentCreated": "2015-05-23T17:35:00.000Z",
        "contentExpiration": "2015-05-30T17:35:00.000Z"
    },
    ...
]

```


## <a name="notification-failure-and-retry"></a><span data-ttu-id="9ed50-310">Falha de notificação e nova tentativa</span><span class="sxs-lookup"><span data-stu-id="9ed50-310">Notification failure and retry</span></span>

<span data-ttu-id="9ed50-311">O sistema de notificação envia notificações à medida que novo conteúdo é disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-311">The notification system sends notifications as new content becomes available.</span></span> <span data-ttu-id="9ed50-312">Se encontramos um número excessivo de falhas ao enviar notificações, o mecanismo de novas tentativas aumentará exponencialmente o tempo entre as novas tentativas.</span><span class="sxs-lookup"><span data-stu-id="9ed50-312">If we encounter excessive failures when sending notifications, our retry mechanism will exponentially increase the time between retries.</span></span> <span data-ttu-id="9ed50-313">Se continuarmos a encontrar falhas, nos reservaremos o direito de desabilitar o webhook e interromper completamente o envio de notificações.</span><span class="sxs-lookup"><span data-stu-id="9ed50-313">If we continue to encounter failures, we reserve the right to disable the webhook and stop sending notifications to it altogether.</span></span> <span data-ttu-id="9ed50-314">A operação /start pode ser usada para reabilitar um webhook desabilitado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-314">The /start operation can be used to re-enable a disabled webhook.</span></span>


## <a name="retrieving-content"></a><span data-ttu-id="9ed50-315">Recuperar conteúdo</span><span class="sxs-lookup"><span data-stu-id="9ed50-315">Retrieving content</span></span>

<span data-ttu-id="9ed50-316">Para recuperar um blob de conteúdo, faça uma solicitação GET em relação ao URI de conteúdo correspondente que está incluído na lista de conteúdo disponível e nas notificações enviadas a um webhook.</span><span class="sxs-lookup"><span data-stu-id="9ed50-316">To retrieve a content blob, make a GET request against the corresponding content URI that is included in the list of available content and in the notifications sent to a webhook.</span></span> <span data-ttu-id="9ed50-317">O conteúdo retornado será um conjunto de mais ações ou eventos no formato JSON.</span><span class="sxs-lookup"><span data-stu-id="9ed50-317">The returned content will be a collection of one more actions or events in JSON format.</span></span>

#### <a name="sample-request"></a><span data-ttu-id="9ed50-318">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="9ed50-318">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/41463f53-8812-40f4-890f-865bf6e35190/activity/feed/audit/301299007231$301299007231$41463f53881240f4890f865bf6e35190aad2015062920$e1c2ab19858a469fb1f1fd097effffc9$04 HTTP/1.1
Authorization: Bearer eyJ0e...Qa6wg
```

#### <a name="sample-response"></a><span data-ttu-id="9ed50-319">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="9ed50-319">Sample response</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "CreationTime": "2015-06-29T20:03:19",
        "Id": "80c76bd2-9d81-4c57-a97a-accfc3443dca",
        "Operation": "PasswordLogonInitialAuthUsingPassword",
        "OrganizationId": "41463f53-8812-40f4-890f-865bf6e35190",
        "RecordType": 9,
        "ResultStatus": "failed",
        "UserKey": "1153977025279851686@contoso.onmicrosoft.com",
        "UserType": 0,
        "Workload": "AzureActiveDirectory",
        "ClientIP": "134.170.188.221",
        "ObjectId": "admin@contoso.onmicrosoft.com",
        "UserId": "admin@contoso.onmicrosoft.com",
        "AzureActiveDirectoryEventType": 0,
        "ExtendedProperties": [
            {
                "Name": "LoginError",
                "Value": "-2147217390;PP_E_BAD_PASSWORD;The entered and stored passwords do not match."
            }
        ],
        "Client": "Exchange",
        "LoginStatus": -2147217390,
        "UserDomain": "contoso.onmicrosoft.com"
    },
    {
        "CreationTime": "2015-06-29T20:03:34",
        "Id": "4e655d3f-35fa-42e0-b050-264b2d255c7a",
        "Operation": "PasswordLogonInitialAuthUsingPassword",
        "OrganizationId": "41463f53-8812-40f4-890f-865bf6e35190",
        "RecordType": 9,
        "ResultStatus": "success",
        "UserKey": "1153977025279851686@contoso.onmicrosoft.com",
        "UserType": 0,
        "Workload": "AzureActiveDirectory",
        "ClientIP": "134.170.188.221",
        "ObjectId": "admin@contoso.onmicrosoft.com",
        "UserId": "admin@contoso.onmicrosoft.com",
        "AzureActiveDirectoryEventType": 0,
        "Client": "Exchange",
        "LoginStatus": 0,
        "UserDomain": "contoso.onmicrosoft.com"
    },
    {
        "CreationTime": "2015-06-29T20:04:55",
        "Id": "b567caf0-088e-4c1c-a4ea-633a1e3d66c8",
        "Operation": "Add User.",
        "OrganizationId": "41463f53-8812-40f4-890f-865bf6e35190",
        "RecordType": 8,
        "ResultStatus": "success",
        "UserKey": "1003BFFD8EC47CA6@contoso.onmicrosoft.com",
        "UserType": 0,
        "Workload": "AzureActiveDirectory",
        "ObjectId": "user001@contoso.onmicrosoft.com",
        "UserId": "admin@contoso.onmicrosoft.com",
        "AzureActiveDirectoryEventType": 0,
        "Actor": [
            {
                "ID": "1cef1fdb-ff52-48c4-8e4e-dfb5ea83d357",
                "Type": 2
            },
            {
                "ID": "admin@contoso.onmicrosoft.com",
                "Type": 5
            },
            {
                "ID": "1003BFFD8EC47CA6",
                "Type": 3
            }
        ],
        "ActorContextId": "41463f53-8812-40f4-890f-865bf6e35190",
        "InterSystemsId": "c2ced078-ad57-4079-a743-5c37f5284790",
        "IntraSystemId": "d1497f7e-15b4-49aa-83ad-11a17ca4a2f4",
        "Target": [
            {
                "ID": "user001@contoso.onmicrosoft.com",
                "Type": 5
            },
            {
                "ID": "10037FFE91510806",
                "Type": 3
            }
        ],
        "TargetContextId": "41463f53-8812-40f4-890f-865bf6e35190"
    }
]

```


## <a name="list-notifications"></a><span data-ttu-id="9ed50-320">Listar notificações</span><span class="sxs-lookup"><span data-stu-id="9ed50-320">List notifications</span></span>

<span data-ttu-id="9ed50-321">Essa operação lista todas as tentativas de notificação para o tipo de conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-321">This operation lists all notification attempts for the specified content type.</span></span> <span data-ttu-id="9ed50-322">Se você não tiver incluído um webhook ao iniciar a assinatura para o tipo de conteúdo, não haverá notificações a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="9ed50-322">If you did not include a webhook when starting the subscription to the content type, there will be no notifications to retrieve.</span></span> <span data-ttu-id="9ed50-323">Como repetimos as notificações em caso de falha, essa operação pode retornar várias notificações para o mesmo conteúdo. A ordem em que as notificações são enviadas não necessariamente corresponde à ordem em que o conteúdo foi disponibilizado (especialmente quando há falhas e repetições).</span><span class="sxs-lookup"><span data-stu-id="9ed50-323">Because we retry notifications in the event of failure, this operation can return multiple notifications for the same content, and the order in which the notifications are sent will not necessarily match the order in which the content became available (especially when there are failures and retries).</span></span> 

<span data-ttu-id="9ed50-324">Você pode usar essa operação para ajudar a investigar problemas relacionados a webhooks e notificações, mas não deve usá-la para determinar qual conteúdo está disponível atualmente para recuperação.</span><span class="sxs-lookup"><span data-stu-id="9ed50-324">You can use this operation to help investigate issues related to webhooks and notifications, but you should not use it to determine what content is currently available for retrieval.</span></span> <span data-ttu-id="9ed50-325">Use a operação /content em vez disso.</span><span class="sxs-lookup"><span data-stu-id="9ed50-325">Use the /content operation instead.</span></span> <span data-ttu-id="9ed50-326">Retornaremos um erro se o status de assinatura for desabilitado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-326">We return an error if the subscription status is disabled.</span></span>


||<span data-ttu-id="9ed50-327">Assinatura</span><span class="sxs-lookup"><span data-stu-id="9ed50-327">Subscription</span></span>|<span data-ttu-id="9ed50-328">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ed50-328">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="9ed50-329">**Path**</span><span class="sxs-lookup"><span data-stu-id="9ed50-329">**Path**</span></span>| `/subscriptions/notifications?contentType={ContentType}&amp;startTime={0}&amp;endTime={1}`||
|<span data-ttu-id="9ed50-330">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="9ed50-330">**Parameters**</span></span>|<span data-ttu-id="9ed50-331">contentType</span><span class="sxs-lookup"><span data-stu-id="9ed50-331">contentType</span></span>|<span data-ttu-id="9ed50-332">Deve ser um tipo de conteúdo válido.</span><span class="sxs-lookup"><span data-stu-id="9ed50-332">Must be a valid content type.</span></span>|
||<span data-ttu-id="9ed50-333">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="9ed50-333">PublisherIdentifier</span></span>|<span data-ttu-id="9ed50-334">O GUID de locatário de codificação de fornecedor para a API.</span><span class="sxs-lookup"><span data-stu-id="9ed50-334">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="9ed50-335">Este **não** é o GUID de aplicativo nem o GUID do cliente que está usando o aplicativo, mas o GUID da empresa que está escrevendo o código.</span><span class="sxs-lookup"><span data-stu-id="9ed50-335">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="9ed50-336">Este parâmetro é usado para limitar a taxa de solicitações.</span><span class="sxs-lookup"><span data-stu-id="9ed50-336">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="9ed50-337">Verifique se este parâmetro foi especificado em todas as solicitações emitidas para obter uma cota dedicada.</span><span class="sxs-lookup"><span data-stu-id="9ed50-337">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="9ed50-338">Todas as solicitações recebidas sem este parâmetro compartilharão a mesma cota.</span><span class="sxs-lookup"><span data-stu-id="9ed50-338">All requests received without this parameter will share the same quota.</span></span>|
||<span data-ttu-id="9ed50-339">startTime endTime</span><span class="sxs-lookup"><span data-stu-id="9ed50-339">startTime endTime</span></span>|<span data-ttu-id="9ed50-340">Datas e horas opcionais (UTC) que indicam o intervalo de tempo do conteúdo a ser retornado, com base em quando o conteúdo foi disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-340">Optional datetimes (UTC) that indicate the time range of content to return, based on when the content became available.</span></span> <span data-ttu-id="9ed50-341">O intervalo de tempo é inclusivo em relação a _startTime_ ( _startTime_ <= contentCreated) e exclusivo em relação a _endTime_ (_contentCreated_ < endTime). Portanto, intervalos de tempo incrementos e não sobrepostos podem ser usados para percorrer o conteúdo disponível.</span><span class="sxs-lookup"><span data-stu-id="9ed50-341">The time range is inclusive with respect to  _startTime_ ( _startTime_ <= contentCreated) and exclusive with respect to _endTime_ (_contentCreated_ < endTime), so that non-overlapping, incrementing time intervals can used to page through available content.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-342">AAAA-MM-DD</span><span class="sxs-lookup"><span data-stu-id="9ed50-342">YYYY-MM-DD</span></span></p></li><li><p><span data-ttu-id="9ed50-343">AAAA-MM-DDTHH:MM</span><span class="sxs-lookup"><span data-stu-id="9ed50-343">YYYY-MM-DDTHH:MM</span></span></p></li><li><p><span data-ttu-id="9ed50-344">AAAA-MM-DDTHH:MM:SS</span><span class="sxs-lookup"><span data-stu-id="9ed50-344">YYYY-MM-DDTHH:MM:SS</span></span></p></li></ul><span data-ttu-id="9ed50-345">Ambos devem ser especificados (ou ambos omitidos), não devem estar separados por mais de 24 horas e a hora de início não pode ser mais de sete dias no passado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-345">Both must be specified (or both omitted) and they must be no more than 24 hours apart, with the start time no more than 7 days in the past.</span></span> <span data-ttu-id="9ed50-346">Por padrão, se _startTime_ e _endTime_ forem omitidos, o conteúdo disponível nas últimas 24 horas será retornado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-346">By default, if  _startTime_ and _endTime_ are omitted, the content available in the last 24 hours is returned.</span></span>|
|<span data-ttu-id="9ed50-347">**Response**</span><span class="sxs-lookup"><span data-stu-id="9ed50-347">**Response**</span></span>|<span data-ttu-id="9ed50-348">Matriz JSON</span><span class="sxs-lookup"><span data-stu-id="9ed50-348">JSON array</span></span>|<span data-ttu-id="9ed50-349">As notificações serão representadas por objetos JSON com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="9ed50-349">The notifications will be represented by JSON objects with the following properties:</span></span> <ul><li><span data-ttu-id="9ed50-350">**contentType**: indica o tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="9ed50-350">**contentType**: indicates the content type.</span></span></li><li><span data-ttu-id="9ed50-351">**contentId**: uma cadeia de caracteres opaca que identifica o conteúdo de forma exclusiva.</span><span class="sxs-lookup"><span data-stu-id="9ed50-351">**contentId**: an opaque string that uniquely identifies the content.</span></span></li><li><span data-ttu-id="9ed50-352">**contentUri**: a URL a ser usada ao recuperar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="9ed50-352">**contentUri**: the URL to use when retrieving the content.</span></span> </li><li><span data-ttu-id="9ed50-353">**contentCreated**: data e hora em que o conteúdo foi disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-353">**contentCreated**: the datetime when the content was made available.</span></span></li><li><span data-ttu-id="9ed50-354">**contentExpiration**: data e hora em que o conteúdo não estará mais disponível para recuperação.</span><span class="sxs-lookup"><span data-stu-id="9ed50-354">**contentExpiration**: the datetime after which the content will no longer be available for retrieval.</span></span></li><li><span data-ttu-id="9ed50-355">**contentCreated**: data e hora em que o conteúdo foi disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-355">**notificationSent**: the datetime when the notification was sent.</span></span></li><li><span data-ttu-id="9ed50-356">**notificationStatus**: indica o êxito ou a falha da tentativa de notificação.</span><span class="sxs-lookup"><span data-stu-id="9ed50-356">**notificationStatus**: indicates the success or failure of the notification attempt.</span></span></li></ul>|

#### <a name="sample-request"></a><span data-ttu-id="9ed50-357">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="9ed50-357">Sample request</span></span>

```json
GET {root}/subscriptions/notifications?contentType=Audit.SharePoint&PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Authorization: Bearer eyJ0e...Qa6wg

```

#### <a name="sample-response"></a><span data-ttu-id="9ed50-358">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="9ed50-358">Sample response</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

[
    {
        "contentType": "Audit.SharePoint",
        "contentId": "492638008028$492638008028$f28ab78ad40140608012736e373933ebspo2015043022$4a81a7c326fc4aed89c62e6039ab833b$04",
        "contentUri": "https://manage.office.com/api/v1.0/f28ab78a-d401-4060-8012-736e373933eb/activity/feed/audit/492638008028$492638008028$f28ab78ad40140608012736e373933ebspo2015043022$4a81a7c326fc4aed89c62e6039ab833b$04",
        "contentCreated": "2015-05-23T17:35:00.000Z",
        "contentExpiration": "2015-05-30T17:35:00.000Z",
        "notificationSent": "2015-05-23T17:36:00.000Z",
        "notificationStatus": "success"

    },
    ...
]

```


### <a name="pagination"></a><span data-ttu-id="9ed50-359">Paginação</span><span class="sxs-lookup"><span data-stu-id="9ed50-359">Pagination</span></span>

<span data-ttu-id="9ed50-360">Ao ser listado o histórico de notificações para um intervalo de tempo, o número de resultados retornados é limitado para impedir tempos limite de resposta.</span><span class="sxs-lookup"><span data-stu-id="9ed50-360">When listing notification history for a time range, the number of results returned is limited to prevent response timeouts.</span></span> <span data-ttu-id="9ed50-361">Se houver mais resultados no intervalo de tempo especificado do que o máximo que pode ser retornados em uma única resposta, eles serão truncados, e um cabeçalho será adicionado à resposta para indicar a URL a ser usada para recuperar a próxima página de resultados.</span><span class="sxs-lookup"><span data-stu-id="9ed50-361">If there are more results in the specified time range than can be returned in a single response, the results are truncated and a header is added to the response indicating the URL to use to retrieve the next page of results.</span></span> <span data-ttu-id="9ed50-362">A URL conterá os mesmos parâmetros _startTime_ e _endTime_ especificados na solicitação original, juntamente com um parâmetro que indica a ID interna da próxima página.</span><span class="sxs-lookup"><span data-stu-id="9ed50-362">The URL will contain the same  _startTime_ and _endTime_ parameters that were specified in the original request, together with a parameter indicating the internal ID of the next page.</span></span> <span data-ttu-id="9ed50-363">Se _startTime_ e _endTime_ não tiverem sido especificados na solicitação original, eles serão definidos para refletir o intervalo de 24 horas que precedia a solicitação original.</span><span class="sxs-lookup"><span data-stu-id="9ed50-363">If _startTime_ and _endTime_ were not specified in the original request, they will be set to reflect the 24-hour interval that preceded the original request.</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
NextPageUrl: https://manage.office.com/api/v1/{tenant_id}/activity/feed/subscriptions/content?contentType=Audit.SharePoint&amp;startTime=2015-10-01&amp;endTime=2015-10-02&amp;nextPage=2015101900R022885001761

```

<span data-ttu-id="9ed50-364">Para listar todo o conteúdo disponível para um intervalo de tempo especificado, talvez seja necessário recuperar várias páginas até que uma resposta sem o cabeçalho **NextPageUri** seja recebida.</span><span class="sxs-lookup"><span data-stu-id="9ed50-364">To list all available content for a specified time range, you might need to retrieve multiple pages until a response without the **NextPageUrl** header is received.</span></span>

## <a name="retrieve-resource-friendly-names"></a><span data-ttu-id="9ed50-365">Recuperar nomes amigáveis de recursos</span><span class="sxs-lookup"><span data-stu-id="9ed50-365">Retrieve resource friendly names</span></span>

<span data-ttu-id="9ed50-366">Essa operação recupera nomes amigáveis de recursos para objetos no feed de dados identificados por guids.</span><span class="sxs-lookup"><span data-stu-id="9ed50-366">This operation retrieves friendly names for objects in the data feed identified by guids.</span></span> <span data-ttu-id="9ed50-367">No momento, "DlpSensitiveType" é o único objeto com suporte.</span><span class="sxs-lookup"><span data-stu-id="9ed50-367">Currently "DlpSensitiveType" is the only supported object.</span></span> 


||<span data-ttu-id="9ed50-368">Assinatura</span><span class="sxs-lookup"><span data-stu-id="9ed50-368">Subscription</span></span>|<span data-ttu-id="9ed50-369">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ed50-369">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="9ed50-370">**Path**</span><span class="sxs-lookup"><span data-stu-id="9ed50-370">**Path**</span></span>| `/resources/dlpSensitiveTypes`||
|<span data-ttu-id="9ed50-371">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="9ed50-371">**Parameters**</span></span>|<span data-ttu-id="9ed50-372">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="9ed50-372">PublisherIdentifier</span></span>|<span data-ttu-id="9ed50-373">O GUID de locatário de codificação de fornecedor para a API.</span><span class="sxs-lookup"><span data-stu-id="9ed50-373">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="9ed50-374">Este **não** é o GUID de aplicativo nem o GUID do cliente que está usando o aplicativo, mas o GUID da empresa que está escrevendo o código.</span><span class="sxs-lookup"><span data-stu-id="9ed50-374">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="9ed50-375">Este parâmetro é usado para limitar a taxa de solicitações.</span><span class="sxs-lookup"><span data-stu-id="9ed50-375">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="9ed50-376">Verifique se este parâmetro foi especificado em todas as solicitações emitidas para obter uma cota dedicada.</span><span class="sxs-lookup"><span data-stu-id="9ed50-376">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="9ed50-377">Todas as solicitações recebidas sem este parâmetro compartilharão a mesma cota.</span><span class="sxs-lookup"><span data-stu-id="9ed50-377">All requests received without this parameter will share the same quota.</span></span>|
|<span data-ttu-id="9ed50-378">**Cabeçalhos**</span><span class="sxs-lookup"><span data-stu-id="9ed50-378">**Headers**</span></span>|<span data-ttu-id="9ed50-379">Accept-Language</span><span class="sxs-lookup"><span data-stu-id="9ed50-379">Accept-Language</span></span>|<span data-ttu-id="9ed50-380">Cabeçalho para especificar o idioma desejado para nomes traduzidos.</span><span class="sxs-lookup"><span data-stu-id="9ed50-380">Header to specify the desired language for localized names.</span></span> <span data-ttu-id="9ed50-381">Por exemplo, use "pt-BR" para português ou "es" para espanhol.</span><span class="sxs-lookup"><span data-stu-id="9ed50-381">For example, use "en-US" for English or "es" for Spanish.</span></span> <span data-ttu-id="9ed50-382">O idioma padrão (en-US) será retornado se esse cabeçalho não estiver presente.</span><span class="sxs-lookup"><span data-stu-id="9ed50-382">The default language (en-US) will be returned if this header is not present.</span></span>|
|<span data-ttu-id="9ed50-383">**Body**</span><span class="sxs-lookup"><span data-stu-id="9ed50-383">**Body**</span></span>|<span data-ttu-id="9ed50-384">(vazio)</span><span class="sxs-lookup"><span data-stu-id="9ed50-384">(empty)</span></span>||
|<span data-ttu-id="9ed50-385">**Response**</span><span class="sxs-lookup"><span data-stu-id="9ed50-385">**Response**</span></span>|<span data-ttu-id="9ed50-386">Matriz JSON</span><span class="sxs-lookup"><span data-stu-id="9ed50-386">JSON array</span></span>|<span data-ttu-id="9ed50-387">O conteúdo disponível será representado por objetos JSON com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="9ed50-387">The available content will be represented by JSON objects with the following properties:</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-388"><b>ID</b>: indica o guid do tipo de informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="9ed50-388"><b>id</b>: Indicates the guid of the sensitive information type.</span></span></p></li><li><p><span data-ttu-id="9ed50-389"><b>name</b>: o nome amigável do tipo de informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="9ed50-389"><b>name</b>: The friendly name of the sensitive information type.</span></span></p></li></ul>|

#### <a name="sample-request"></a><span data-ttu-id="9ed50-390">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="9ed50-390">Sample request</span></span>

```json
GET {root}/resources/dlpSensitiveTypes?PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Authorization: Bearer eyJ0e...Qa6wg
Accept-Language: {language code} 

```

#### <a name="sample-response"></a><span data-ttu-id="9ed50-391">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="9ed50-391">Sample response</span></span>

```json
HTTP/1.1 200 OK

[
    {
        "id": "50842eb7-edc8-4019-85dd-5a5c1f2bb085",
        "name": "CreditCardNumber"
    }, 
    {
        "id": "0e9b3178-9678-47dd-a509-37222ca96b42",
        "name": "EUDebitCardNumber"
    }, 
    ...
    {
    }
]

```

## <a name="api-throttling"></a><span data-ttu-id="9ed50-392">Limitação de API</span><span class="sxs-lookup"><span data-stu-id="9ed50-392">API throttling</span></span>

<span data-ttu-id="9ed50-393">As organizações que acessam logs de auditoria por meio da API da Atividade de Gestão do Office 365 foram restritas pelos limites no nível do editor.</span><span class="sxs-lookup"><span data-stu-id="9ed50-393">Organizations that access auditing logs through the Office 365 Management Activity API were restricted by throttling limits at the publisher level.</span></span> <span data-ttu-id="9ed50-394">Isso significa que, para um Publisher obter dados em nome de vários clientes, o limite foi compartilhado por todos esses clientes.</span><span class="sxs-lookup"><span data-stu-id="9ed50-394">This means that for a publisher pulling data on behalf of multiple customers, the limit was shared by all those customers.</span></span>

<span data-ttu-id="9ed50-395">Estamos migrando do limite no nível do editor para um limite no nível do locatário.</span><span class="sxs-lookup"><span data-stu-id="9ed50-395">We're moving from a publisher-level limit to a tenant-level limit.</span></span> <span data-ttu-id="9ed50-396">O resultado é que todas as organizações terão sua própria cota de largura de banda totalmente alocada para acessar os dados de auditoria.</span><span class="sxs-lookup"><span data-stu-id="9ed50-396">The result is that each organization will get their own fully allocated bandwidth quota to access their auditing data.</span></span> <span data-ttu-id="9ed50-397">Todas as organizações alocam inicialmente uma linha de base de 2.000 solicitações por minuto.</span><span class="sxs-lookup"><span data-stu-id="9ed50-397">All organizations are initially allocated a baseline of 2,000 requests per minute.</span></span> <span data-ttu-id="9ed50-398">Esse não é um limite estático e predefinido, mas está modelado em uma combinação de fatores, incluindo o número de assentos da organização e que as organizações do Office 365 e do Microsoft 365 E5 terão aproximadamente o dobro de largura de banda quanto organizações que não são do E5.</span><span class="sxs-lookup"><span data-stu-id="9ed50-398">This is not a static, predefined limit but is modeled on a combination of factors including the number of seats in the organization and that Office 365 and Microsoft 365 E5 organizations will get approximately twice as much bandwidth as non-E5 organizations.</span></span> <span data-ttu-id="9ed50-399">Também haverá limite máximo quanto à largura de banda para proteger a integridade do serviço.</span><span class="sxs-lookup"><span data-stu-id="9ed50-399">There will also be cap on the maximum bandwidth to protect the health of the service.</span></span>

<span data-ttu-id="9ed50-400">Para saber mais, confira a seção "acesso de largura de banda alta à API da Atividade de Gestão do Office 365" em [Auditoria avançada no Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/advanced-audit#high-bandwidth-access-to-the-office-365-management-activity-api).</span><span class="sxs-lookup"><span data-stu-id="9ed50-400">For more information, see the "High-bandwidth access to the Office 365 Management Activity API" section in [Advanced audit in Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/advanced-audit#high-bandwidth-access-to-the-office-365-management-activity-api).</span></span>

> [!NOTE] 
> <span data-ttu-id="9ed50-401">Embora cada locatário possa enviar inicialmente até 2 mil solicitações por minuto, a Microsoft não pode garantir uma taxa de resposta.</span><span class="sxs-lookup"><span data-stu-id="9ed50-401">Even though each tenant can initially submit up to 2,000 requests per minute, Microsoft cannot guarantee a response rate.</span></span> <span data-ttu-id="9ed50-402">A taxa de resposta depende de vários fatores, como o desempenho do sistema do cliente, a capacidade e a velocidade da rede.</span><span class="sxs-lookup"><span data-stu-id="9ed50-402">The response rate depends on various factors, such as client system performance, network capacity, and network speed.</span></span> 

## <a name="errors"></a><span data-ttu-id="9ed50-403">Erros</span><span class="sxs-lookup"><span data-stu-id="9ed50-403">Errors</span></span>

<span data-ttu-id="9ed50-404">Quando o serviço encontrar um erro, relatará o código de resposta do erro ao chamador, usando a sintaxe de código de erro HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="9ed50-404">When the service encounters an error, it will report the error response code to the caller, using standard HTTP error-code syntax.</span></span> <span data-ttu-id="9ed50-405">.</span><span class="sxs-lookup"><span data-stu-id="9ed50-405">.</span></span> <span data-ttu-id="9ed50-406">Informações adicionais são incluídas no corpo da chamada com falha como um único objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="9ed50-406">Additional information is included in the body of the failed call as a single JSON object.</span></span> <span data-ttu-id="9ed50-407">Um exemplo de um corpo de erro JSON completo é mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="9ed50-407">An example of a full JSON error body is shown below:</span></span> 

```json

{ 
    "error":{ 
        "code":"AF50000",
        "message": "An internal server error occurred. Retry the request."
    } 
}

```


|||
|:-----|:-----|
|<span data-ttu-id="9ed50-408">Código</span><span class="sxs-lookup"><span data-stu-id="9ed50-408">Code</span></span>|<span data-ttu-id="9ed50-409">Mensagem</span><span class="sxs-lookup"><span data-stu-id="9ed50-409">Message</span></span>|
|<span data-ttu-id="9ed50-410">AF10001</span><span class="sxs-lookup"><span data-stu-id="9ed50-410">AF10001</span></span>|<span data-ttu-id="9ed50-411">O conjunto de permissões ({0}) enviadas na solicitação não incluía a permissão esperada **ActivityFeed.Read**.</span><span class="sxs-lookup"><span data-stu-id="9ed50-411">The permission set ({0}) sent in the request did not include the expected permission **ActivityFeed.Read**.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-412">{0} = o conjunto de permissões no token de acesso.</span><span class="sxs-lookup"><span data-stu-id="9ed50-412">{0} = the permission set in the access token.</span></span></p></li></ul>|
|<span data-ttu-id="9ed50-413">AF20001</span><span class="sxs-lookup"><span data-stu-id="9ed50-413">AF20001</span></span>|<span data-ttu-id="9ed50-414">Parâmetro ausente: {0}.</span><span class="sxs-lookup"><span data-stu-id="9ed50-414">Missing parameter: {0}.</span></span> <ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-415">{0} = nome do parâmetro ausente.</span><span class="sxs-lookup"><span data-stu-id="9ed50-415">{0} = the name of the missing parameter.</span></span></p></li></ul>|
|<span data-ttu-id="9ed50-416">AF20002</span><span class="sxs-lookup"><span data-stu-id="9ed50-416">AF20002</span></span>|<span data-ttu-id="9ed50-417">Tipo de parâmetro inválido: {0}.</span><span class="sxs-lookup"><span data-stu-id="9ed50-417">Invalid parameter type: {0}.</span></span> <span data-ttu-id="9ed50-418">Tipo esperado: {1}</span><span class="sxs-lookup"><span data-stu-id="9ed50-418">Expected type: {1}</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-419">{0} = nome do parâmetro inválido.</span><span class="sxs-lookup"><span data-stu-id="9ed50-419">{0} = the name of the invalid parameter.</span></span></p></li><li><p><span data-ttu-id="9ed50-420">{1} = tipo esperado (int, datetime, guid).</span><span class="sxs-lookup"><span data-stu-id="9ed50-420">{1} = the expected type (int, datetime, guid).</span></span></p></li></ul>|
|<span data-ttu-id="9ed50-421">AF20003</span><span class="sxs-lookup"><span data-stu-id="9ed50-421">AF20003</span></span>|<span data-ttu-id="9ed50-422">A expiração de {0} fornecida está definida como data e hora anteriores.</span><span class="sxs-lookup"><span data-stu-id="9ed50-422">Expiration {0} provided is set to past date and time.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-423">{0} = a expiração passada na chamada à API.</span><span class="sxs-lookup"><span data-stu-id="9ed50-423">{0} = the expiration passed in the API call.</span></span></p></li></ul>|
|<span data-ttu-id="9ed50-424">AF20010</span><span class="sxs-lookup"><span data-stu-id="9ed50-424">AF20010</span></span>|<span data-ttu-id="9ed50-425">A ID de locatário passada na URL ({0}) não correspondia à ID de locatário passada no token de acesso ({1}).</span><span class="sxs-lookup"><span data-stu-id="9ed50-425">The tenant ID passed in the URL ({0}) does not match the tenant ID passed in the access token ({1}).</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-426">{0} = ID de locatário passada na URL</span><span class="sxs-lookup"><span data-stu-id="9ed50-426">{0} = tenant ID passed in the URL</span></span></p></li><li><p><span data-ttu-id="9ed50-427">{1} = ID de locatário passada no token de acesso</span><span class="sxs-lookup"><span data-stu-id="9ed50-427">{1} = tenant ID passed in the access token</span></span></p></li></ul>|
|<span data-ttu-id="9ed50-428">AF20011</span><span class="sxs-lookup"><span data-stu-id="9ed50-428">AF20011</span></span>|<span data-ttu-id="9ed50-429">A ID de locatário especificada ({0}) não existe no sistema ou foi excluída.</span><span class="sxs-lookup"><span data-stu-id="9ed50-429">Specified tenant ID ({0}) does not exist in the system or has been deleted.</span></span> <ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p>   <span data-ttu-id="9ed50-430">{0} = ID de locatário passada na URL</span><span class="sxs-lookup"><span data-stu-id="9ed50-430">{0} = tenant ID passed in the URL</span></span></p></li></ul>|
|<span data-ttu-id="9ed50-431">AF20012</span><span class="sxs-lookup"><span data-stu-id="9ed50-431">AF20012</span></span>|<span data-ttu-id="9ed50-432">A ID de locatário especificada ({0}) está configurada incorretamente no sistema.</span><span class="sxs-lookup"><span data-stu-id="9ed50-432">Specified tenant ID ({0}) is incorrectly configured in the system.</span></span> <ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p>    <span data-ttu-id="9ed50-433">{0} = ID de locatário passada na URL</span><span class="sxs-lookup"><span data-stu-id="9ed50-433">{0} = tenant ID passed in the URL</span></span></p></li></ul>|
|<span data-ttu-id="9ed50-434">AF20013</span><span class="sxs-lookup"><span data-stu-id="9ed50-434">AF20013</span></span>|<span data-ttu-id="9ed50-435">A ID de locatário passada na URL ({0}) não é um GUID válido.</span><span class="sxs-lookup"><span data-stu-id="9ed50-435">The tenant ID passed in the URL ({0}) is not a valid GUID.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p> <span data-ttu-id="9ed50-436">{0} = ID de locatário passada na URL</span><span class="sxs-lookup"><span data-stu-id="9ed50-436">{0} = tenant ID passed in the URL</span></span></p></li></ul>|
|<span data-ttu-id="9ed50-437">AF20020</span><span class="sxs-lookup"><span data-stu-id="9ed50-437">AF20020</span></span>|<span data-ttu-id="9ed50-438">O tipo de conteúdo especificado não é válido.</span><span class="sxs-lookup"><span data-stu-id="9ed50-438">The specified content type is not valid.</span></span>|
|<span data-ttu-id="9ed50-439">AF20021</span><span class="sxs-lookup"><span data-stu-id="9ed50-439">AF20021</span></span>|<span data-ttu-id="9ed50-440">O ponto de extremidade de webhook {{0}) não pôde ser validado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-440">The webhook endpoint {{0}) could not be validated.</span></span> <span data-ttu-id="9ed50-441">{1}</span><span class="sxs-lookup"><span data-stu-id="9ed50-441">{1}</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-442">{0} = endereço de webhook.</span><span class="sxs-lookup"><span data-stu-id="9ed50-442">{0} = webhook address.</span></span></p></li><li><p><span data-ttu-id="9ed50-443">{1} = "O ponto de extremidade não retornou HTTP 200."</span><span class="sxs-lookup"><span data-stu-id="9ed50-443">{1} = "The endpoint did not return HTTP 200."</span></span> <span data-ttu-id="9ed50-444">ou "O endereço deve começar com HTTPS."</span><span class="sxs-lookup"><span data-stu-id="9ed50-444">or "The address must begin with HTTPS."</span></span></p></li></ul>|
|<span data-ttu-id="9ed50-445">AF20022</span><span class="sxs-lookup"><span data-stu-id="9ed50-445">AF20022</span></span>|<span data-ttu-id="9ed50-446">Nenhuma assinatura foi encontrada para o tipo de conteúdo específico.</span><span class="sxs-lookup"><span data-stu-id="9ed50-446">No subscription found for the specified content type.</span></span>|
|<span data-ttu-id="9ed50-447">AF20023</span><span class="sxs-lookup"><span data-stu-id="9ed50-447">AF20023</span></span>|<span data-ttu-id="9ed50-448">A assinatura foi desabilitada por {0}.</span><span class="sxs-lookup"><span data-stu-id="9ed50-448">The subscription was disabled by {0}.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-449">{0} = "administrador de locatário" ou "administrador de serviço"</span><span class="sxs-lookup"><span data-stu-id="9ed50-449">{0} = "a tenant admin" or "a service admin"</span></span></p></li></ul>|
|<span data-ttu-id="9ed50-450">AF20030</span><span class="sxs-lookup"><span data-stu-id="9ed50-450">AF20030</span></span>|<span data-ttu-id="9ed50-451">A hora de início e a hora de término devem ser especificadas (ou omitidas) e devem ser separadas por um valor menor ou igual a 24 horas, com a hora de início no máximo sete dias no passado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-451">Start time and end time must both be specified (or both omitted) and must be less than or equal to 24 hours apart, with the start time no more than 7 days in the past.</span></span>|
|<span data-ttu-id="9ed50-452">AF20031</span><span class="sxs-lookup"><span data-stu-id="9ed50-452">AF20031</span></span>|<span data-ttu-id="9ed50-453">Entrada de NextPage inválida: {0}.</span><span class="sxs-lookup"><span data-stu-id="9ed50-453">Invalid nextPage Input: {0}.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-454">{0} = o indicador de próxima página passado na URL</span><span class="sxs-lookup"><span data-stu-id="9ed50-454">{0} = the next page indicator passed in the URL</span></span></p></li></ul>|
|<span data-ttu-id="9ed50-455">AF20050</span><span class="sxs-lookup"><span data-stu-id="9ed50-455">AF20050</span></span>|<span data-ttu-id="9ed50-456">O conteúdo especificado ({0}) não existe.</span><span class="sxs-lookup"><span data-stu-id="9ed50-456">The specified content ({0}) does not exist.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-457">{0} = id de recurso ou URL de recurso</span><span class="sxs-lookup"><span data-stu-id="9ed50-457">{0} = resource id or resource URL</span></span></p></li></ul>|
|<span data-ttu-id="9ed50-458">AF20051</span><span class="sxs-lookup"><span data-stu-id="9ed50-458">AF20051</span></span>|<span data-ttu-id="9ed50-459">O conteúdo solicitado com a chave {0} já expirou.</span><span class="sxs-lookup"><span data-stu-id="9ed50-459">Content requested with the key {0} has already expired.</span></span> <span data-ttu-id="9ed50-460">Conteúdo com mais de sete dias não pode ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="9ed50-460">Content older than 7 days cannot be retrieved.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-461">• {0} = id de recurso ou URL de recurso</span><span class="sxs-lookup"><span data-stu-id="9ed50-461">•    {0} = resource id or resource URL</span></span></p></li></ul>|
|<span data-ttu-id="9ed50-462">AF20052</span><span class="sxs-lookup"><span data-stu-id="9ed50-462">AF20052</span></span>|<span data-ttu-id="9ed50-463">A ID de conteúdo {0} na URL é inválida.</span><span class="sxs-lookup"><span data-stu-id="9ed50-463">Content ID {0} in the URL is invalid.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-464">{0} = id de recurso ou URL de recurso</span><span class="sxs-lookup"><span data-stu-id="9ed50-464">{0} = resource id or resource URL</span></span></p></li></ul>|
|<span data-ttu-id="9ed50-465">AF20053</span><span class="sxs-lookup"><span data-stu-id="9ed50-465">AF20053</span></span>|<span data-ttu-id="9ed50-466">Apenas um idioma pode estar presente no cabeçalho Accept-Language.</span><span class="sxs-lookup"><span data-stu-id="9ed50-466">Only one language may be present in the Accept-Language header.</span></span>|
|<span data-ttu-id="9ed50-467">AF20054</span><span class="sxs-lookup"><span data-stu-id="9ed50-467">AF20054</span></span>|<span data-ttu-id="9ed50-468">Sintaxe inválida no cabeçalho Accept-Language.</span><span class="sxs-lookup"><span data-stu-id="9ed50-468">Invalid syntax in Accept-Language header.</span></span>|
|<span data-ttu-id="9ed50-469">AF429</span><span class="sxs-lookup"><span data-stu-id="9ed50-469">AF429</span></span>|<span data-ttu-id="9ed50-470">Muitas solicitações.</span><span class="sxs-lookup"><span data-stu-id="9ed50-470">Too many requests.</span></span> <span data-ttu-id="9ed50-471">Method={0}, PublisherId={1}</span><span class="sxs-lookup"><span data-stu-id="9ed50-471">Method={0}, PublisherId={1}</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="9ed50-472">{0} = Método HTTP</span><span class="sxs-lookup"><span data-stu-id="9ed50-472">{0} = HTTP Method</span></span></p></li><li><p><span data-ttu-id="9ed50-473">{1} = GUID de locatário usado como PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="9ed50-473">{1} = Tenant GUID used as PublisherIdentifier</span></span></p></li></ul>|
|<span data-ttu-id="9ed50-474">AF50000</span><span class="sxs-lookup"><span data-stu-id="9ed50-474">AF50000</span></span>|<span data-ttu-id="9ed50-475">Erro interno.</span><span class="sxs-lookup"><span data-stu-id="9ed50-475">An internal error occurred.</span></span> <span data-ttu-id="9ed50-476">Repita a solicitação.</span><span class="sxs-lookup"><span data-stu-id="9ed50-476">Retry the request.</span></span>|
