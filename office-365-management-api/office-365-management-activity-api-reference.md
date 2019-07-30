---
ms.TocTitle: Office 365 Management Activity API reference
title: Referência da API da Atividade de Gerenciamento do Office 365
description: Use a API da Atividade de Gerenciamento do Office 365 para recuperar informações sobre ações e eventos de usuário, administração, sistema e políticas dos logs de atividades do Office 365 e do Azure AD.
ms.ContentId: 52749845-37f8-6076-7ea5-49d9a4055445
ms.topic: reference (API)
ms.date: 01/10/2018
localization_priority: Priority
ms.openlocfilehash: d6cdef5f0445ef0fa551be3080d4ce28595a1e9f
ms.sourcegitcommit: 784b581a699c6d0ab7939ea621d5ecbea71925ea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2019
ms.locfileid: "35924823"
---
# <a name="office-365-management-activity-api-reference"></a><span data-ttu-id="3edcf-103">Referência da API da Atividade de Gerenciamento do Office 365</span><span class="sxs-lookup"><span data-stu-id="3edcf-103">Office 365 Management Activity API reference</span></span>

<span data-ttu-id="3edcf-104">Use a API da Atividade de Gerenciamento do Office 365 para recuperar informações sobre ações e eventos de usuário, administração, sistema e políticas dos logs de atividades do Office 365 e do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="3edcf-104">Use the Office 365 Management Activity API to retrieve information about user, admin, system, and policy actions and events from Office 365 and Azure AD activity logs.</span></span> 

<span data-ttu-id="3edcf-105">Você pode usar as ações e os eventos dos logs de auditoria e atividades do Office 365 e do Microsoft Azure Active Directory para criar soluções que forneçam monitoramento, análise e visualização de dados.</span><span class="sxs-lookup"><span data-stu-id="3edcf-105">You can use the actions and events from the Office 365 and Microsoft Azure Active Directory audit and activity logs to create solutions that provide monitoring, analysis, and data visualization.</span></span> <span data-ttu-id="3edcf-106">Essas soluções oferecem às organizações mais visibilidade das ações realizadas em relação a seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-106">These solutions give organizations greater visibility into actions taken on their content.</span></span> <span data-ttu-id="3edcf-107">Essas ações e eventos também estão disponíveis nos Relatórios de Atividades do Office 365.</span><span class="sxs-lookup"><span data-stu-id="3edcf-107">These actions and events are also available in the Office 365 Activity Reports.</span></span> <span data-ttu-id="3edcf-108">Para saber mais, confira [Pesquisar o log de auditoria no Centro de Conformidade e Segurança do Office 365](https://support.office.com/pt-BR/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).</span><span class="sxs-lookup"><span data-stu-id="3edcf-108">For more information, see [Search the audit log in the Office 365 Security & Compliance Center](https://support.office.com/en-us/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c).</span></span>

<span data-ttu-id="3edcf-109">A API da Atividade de Gerenciamento do Office 365 é um serviço Web REST que você pode usar para desenvolver soluções usando qualquer linguagem e ambiente de hospedagem que dê suporte a certificados HTTPS e X.509.</span><span class="sxs-lookup"><span data-stu-id="3edcf-109">The Office 365 Management Activity API is a REST web service that you can use to develop solutions using any language and hosting environment that supports HTTPS and X.509 certificates.</span></span> <span data-ttu-id="3edcf-110">A API depende do Azure AD e do protocolo OAuth2 para autorização e autenticação.</span><span class="sxs-lookup"><span data-stu-id="3edcf-110">The API relies on Azure AD and the OAuth2 protocol for authentication and authorization.</span></span> <span data-ttu-id="3edcf-111">Para acessar a API por meio de seu aplicativo, primeiro será preciso registrá-la no Azure AD e configurá-la com permissões apropriadas.</span><span class="sxs-lookup"><span data-stu-id="3edcf-111">To access the API from your application, you'll need to first register it in Azure AD and configure it with appropriate permissions.</span></span> <span data-ttu-id="3edcf-112">Isso habilitará o aplicativo a solicitar os tokens de acesso OAuth2 necessários para chamar a API.</span><span class="sxs-lookup"><span data-stu-id="3edcf-112">This will enable your application to request the OAuth2 access tokens it needs to call the API.</span></span> <span data-ttu-id="3edcf-113">Para saber mais, confira [Introdução às APIs de Gerenciamento do Office 365](get-started-with-office-365-management-apis.md).</span><span class="sxs-lookup"><span data-stu-id="3edcf-113">For more information, see [Get started with Office 365 Management APIs](get-started-with-office-365-management-apis.md).</span></span>

<span data-ttu-id="3edcf-114">Para obter informações sobre os dados que a API da Atividade de Gerenciamento do Office 365 retorna, confira [Esquema da API da Atividade de Gerenciamento do Office 365](office-365-management-activity-api-schema.md).</span><span class="sxs-lookup"><span data-stu-id="3edcf-114">For information about the schema of the data that the Office 365 Management Activity API returns, see [Office 365 Management Activity API schema](office-365-management-activity-api-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3edcf-115">Para poder acessar dados por meio da API de Atividade de Gerenciamento do Office 365, habilite o log de auditoria unificado para a sua organização do Office 365.</span><span class="sxs-lookup"><span data-stu-id="3edcf-115">Before you can access data through the Office 365 Management Activity API, you must enable unified audit logging for your Office 365 organization.</span></span> <span data-ttu-id="3edcf-116">Para fazer isso, ative o log de auditoria do Office 365.</span><span class="sxs-lookup"><span data-stu-id="3edcf-116">You do this by turning on the Office 365 audit log.</span></span> <span data-ttu-id="3edcf-117">Para obter instruções, confira [Ativar ou desativar a pesquisa de log de auditoria do Office 365](https://docs.microsoft.com/office365/securitycompliance/turn-audit-log-search-on-or-off).</span><span class="sxs-lookup"><span data-stu-id="3edcf-117">[Turn Office 365 audit log search on or off](https://docs.microsoft.com/office365/securitycompliance/turn-audit-log-search-on-or-off)</span></span>


## <a name="working-with-the-office-365-management-activity-api"></a><span data-ttu-id="3edcf-118">Usar a API da Atividade de Gerenciamento do Office 365</span><span class="sxs-lookup"><span data-stu-id="3edcf-118">Working with the Office 365 Management Activity API</span></span>

<span data-ttu-id="3edcf-119">A API da Atividade de Gerenciamento do Office 365 agrega ações e eventos em blobs de conteúdo específicos de locatário, que são classificados pelo tipo e pela origem de seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-119">The Office 365 Management Activity API aggregates actions and events into tenant-specific content blobs, which are classified by the type and source of the content they contain.</span></span> <span data-ttu-id="3edcf-120">Atualmente, há suporte para estes tipos de conteúdo:</span><span class="sxs-lookup"><span data-stu-id="3edcf-120">Currently, these content types are supported:</span></span>

- <span data-ttu-id="3edcf-121">Audit.AzureActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="3edcf-121">Audit.AzureActiveDirectory</span></span>
    
- <span data-ttu-id="3edcf-122">Audit.Exchange</span><span class="sxs-lookup"><span data-stu-id="3edcf-122">Audit.Exchange</span></span>
    
- <span data-ttu-id="3edcf-123">Audit.SharePoint</span><span class="sxs-lookup"><span data-stu-id="3edcf-123">Audit.SharePoint</span></span>
    
- <span data-ttu-id="3edcf-124">Audit.General (inclui todas as outras cargas de trabalho não incluídas nos tipos de conteúdo anteriores)</span><span class="sxs-lookup"><span data-stu-id="3edcf-124">Audit.General (includes all other workloads not included in the previous content types)</span></span>

- <span data-ttu-id="3edcf-125">DLP.All (apenas eventos DLP para todas as cargas de trabalho)</span><span class="sxs-lookup"><span data-stu-id="3edcf-125">DLP.All (DLP events only for all workloads)</span></span>
    
<span data-ttu-id="3edcf-126">Para saber mais sobre os eventos e as propriedades associados a esses tipos de conteúdo, confira [Esquema de API da Atividade de Gerenciamento do Office 365](office-365-management-activity-api-schema.md).</span><span class="sxs-lookup"><span data-stu-id="3edcf-126">For details about the events and properties associated with these content types, see [Office 365 Management Activity API schema](office-365-management-activity-api-schema.md).</span></span>

<span data-ttu-id="3edcf-127">Para começar a recuperar blobs de conteúdo para um locatário, primeiro você cria uma assinatura para os tipos de conteúdo desejados.</span><span class="sxs-lookup"><span data-stu-id="3edcf-127">To begin retrieving content blobs for a tenant, you first a create subscription to the desired content types.</span></span> <span data-ttu-id="3edcf-128">Se está recuperando blobs de conteúdo para vários locatários, você cria várias assinaturas para cada um dos tipos de conteúdo desejados, uma para cada locatário.</span><span class="sxs-lookup"><span data-stu-id="3edcf-128">If you are retrieving content blobs for multiple tenants, you create multiple subscriptions to each of the desired content types, one for each tenant.</span></span>

<span data-ttu-id="3edcf-129">Após criar uma assinatura, você pode realizar uma sondagem regularmente para descobrir novos blobs de conteúdo que estão disponíveis para download ou pode registrar um ponto de extremidade de webhook com a assinatura, e enviaremos notificações a esse ponto de extremidade quando novos blobs de conteúdo estiverem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="3edcf-129">After you create a subscription, you can poll regularly to discover new content blobs that are available for download, or you can register a webhook endpoint with the subscription and we will send notifications to this endpoint as new content blobs are available.</span></span>


> [!NOTE] 
> <span data-ttu-id="3edcf-130">Quando uma assinatura é criada, pode levar até 12 horas para que os primeiros blobs de conteúdo fiquem disponíveis para essa assinatura.</span><span class="sxs-lookup"><span data-stu-id="3edcf-130">When a subscription is created, it can take up to 12 hours for the first content blobs to become available for that subscription.</span></span> <span data-ttu-id="3edcf-131">Os blobs de conteúdo são criados com a coleta e a agregação de ações e eventos entre vários servidores e data centers.</span><span class="sxs-lookup"><span data-stu-id="3edcf-131">The content blobs are created by collecting and aggregating actions and events across multiple servers and datacenters.</span></span> <span data-ttu-id="3edcf-132">Como resultado desse processo distribuído, as ações e os eventos contidos nos blobs de conteúdo não necessariamente aparecerão na ordem em que ocorreram.</span><span class="sxs-lookup"><span data-stu-id="3edcf-132">As a result of this distributed process, the actions and events contained in the content blobs will not necessarily appear in the order in which they occurred.</span></span> <span data-ttu-id="3edcf-133">Um blob de conteúdo pode ter ações e eventos que ocorreram antes das ações e dos eventos contidos em um blob de conteúdo anterior.</span><span class="sxs-lookup"><span data-stu-id="3edcf-133">One content blob can contain actions and events that occurred prior to the actions and events contained in an earlier content blob.</span></span> <span data-ttu-id="3edcf-134">Estamos trabalhando para reduzir a latência entre a ocorrência de ações e eventos, bem como a respectiva disponibilidade em um blob de conteúdo, mas não podemos garantir que eles apareçam sequencialmente.</span><span class="sxs-lookup"><span data-stu-id="3edcf-134">We are working to decrease the latency between the occurrence of actions and events and their availability within a content blob, but we can't guarantee that they appear sequentially.</span></span>


> [!NOTE] 
> <span data-ttu-id="3edcf-135">Os dados confidenciais de DLP só estão disponíveis na API de feed de atividades para usuários que receberam permissões para "Ler dados confidenciais de DLP".</span><span class="sxs-lookup"><span data-stu-id="3edcf-135">DLP sensitive data is only available in the activity feed API to users that have been granted “Read DLP sensitive data” permissions.</span></span> <span data-ttu-id="3edcf-136">Para saber mais sobre DLP (Prevenção contra Perda de Dados), confira [Visão geral de Políticas de Prevenção contra Perda de Dados](https://support.office.com/pt-BR/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)</span><span class="sxs-lookup"><span data-stu-id="3edcf-136">For more on Data Loss Prevention (DLP) see [Overview of Data Loss Prevention Policies](https://support.office.com/en-us/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)</span></span>

## <a name="activity-api-operations"></a><span data-ttu-id="3edcf-137">Operações de API de atividade</span><span class="sxs-lookup"><span data-stu-id="3edcf-137">Activity API operations</span></span>

<span data-ttu-id="3edcf-138">Todas as operações da API têm como escopo um único locatário, e a URL raiz da API inclui uma ID de locatário que especifica o contexto do locatário.</span><span class="sxs-lookup"><span data-stu-id="3edcf-138">All API operations are scoped to a single tenant and the root URL of the API includes a tenant ID that specifies the tenant context.</span></span> <span data-ttu-id="3edcf-139">A ID de locatário é um GUID.</span><span class="sxs-lookup"><span data-stu-id="3edcf-139">The tenant ID is a GUID.</span></span> <span data-ttu-id="3edcf-140">Para saber mais sobre como obter o GUID, confira [Introdução às APIs de Gerenciamento do Office 365](get-started-with-office-365-management-apis.md).</span><span class="sxs-lookup"><span data-stu-id="3edcf-140">For information about how to get the GUID, see [Get started with Office 365 Management APIs](get-started-with-office-365-management-apis.md).</span></span>


```http
https://manage.office.com/api/v1.0/{tenant_id}/activity/feed/{operation}
```

<span data-ttu-id="3edcf-141">Como as notificações que enviamos a seu webhook incluem a **ID de locatário**, você pode usar o mesmo webhook para receber notificações para todos os locatários.</span><span class="sxs-lookup"><span data-stu-id="3edcf-141">Because the notifications we send to your webhook include the **tenant ID**, you can use the same webhook to receive notifications for all tenants.</span></span>

<span data-ttu-id="3edcf-142">Todas as operações de API exigem um cabeçalho de Autorização HTTP com um token obtido do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="3edcf-142">All API operations require an Authorization HTTP header with an access token obtained from Azure AD.</span></span> <span data-ttu-id="3edcf-143">A ID de locatário no token de acesso deve corresponder à ID de locatário na URL raiz da API, e o token de acesso deve conter a declaração ActivityFeed.Read (isso corresponde à permissão [Ler dados de atividade de uma organização] que você configurou para o aplicativo no Azure AD).</span><span class="sxs-lookup"><span data-stu-id="3edcf-143">The tenant ID in the access token must match the tenant ID in the root URL of the API and the access token must contain the ActivityFeed.Read claim (this corresponds to the permission [Read activity data for an organization] that you configured for you application in Azure AD).</span></span>

```json
Authorization: Bearer eyJ0e...Qa6wg
```

<span data-ttu-id="3edcf-144">A API de Atividade dá suporte às seguintes operações:</span><span class="sxs-lookup"><span data-stu-id="3edcf-144">The Activity API supports the following operations:</span></span>

- <span data-ttu-id="3edcf-145">**Iniciar uma assinatura** para começar a receber notificações e recuperar dados de atividade de um locatário.</span><span class="sxs-lookup"><span data-stu-id="3edcf-145">**Start a subscription** to begin receiving notifications and retrieving activity data for a tenant.</span></span>
    
- <span data-ttu-id="3edcf-146">**Interromper uma assinatura** para descontinuar a recuperação de dados de um locatário.</span><span class="sxs-lookup"><span data-stu-id="3edcf-146">**Stop a subscription** to discontinue retrieving data for a tenant.</span></span>
    
- <span data-ttu-id="3edcf-147">**Listar as assinaturas atuais**</span><span class="sxs-lookup"><span data-stu-id="3edcf-147">**List current subscriptions**</span></span>
    
- <span data-ttu-id="3edcf-148">**Listar o conteúdo disponível** e as URLs de conteúdo correspondentes.</span><span class="sxs-lookup"><span data-stu-id="3edcf-148">**List available content** and the corresponding content URLs.</span></span>
    
- <span data-ttu-id="3edcf-149">**Receber notificações** enviadas por um webhook quando novo conteúdo está disponível.</span><span class="sxs-lookup"><span data-stu-id="3edcf-149">**Receiving notifications** sent by a webhook when new content is available.</span></span>
    
- <span data-ttu-id="3edcf-150">**Recuperar conteúdo** usando a URL de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-150">**Retrieving content** by using the content URL.</span></span>
    
- <span data-ttu-id="3edcf-151">**Listar notificações** enviadas por um webhook.</span><span class="sxs-lookup"><span data-stu-id="3edcf-151">**List notifications** sent by a webhook.</span></span>

- <span data-ttu-id="3edcf-152">**Recuperar nomes amigáveis de recursos** para objetos no feed de dados identificados por guids.</span><span class="sxs-lookup"><span data-stu-id="3edcf-152">**Retrieve resource friendly names** for objects in the data feed identified by guids.</span></span>
    

## <a name="start-a-subscription"></a><span data-ttu-id="3edcf-153">Iniciar uma assinatura</span><span class="sxs-lookup"><span data-stu-id="3edcf-153">Start a subscription</span></span>

<span data-ttu-id="3edcf-154">Essa operação inicia uma assinatura para o tipo de conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-154">This operation starts a subscription to the specified content type.</span></span> <span data-ttu-id="3edcf-155">Se já existir uma assinatura para o tipo de conteúdo especificado, essa operação será usada para:</span><span class="sxs-lookup"><span data-stu-id="3edcf-155">If a subscription to the specified content type already exists, this operation is used to:</span></span>

- <span data-ttu-id="3edcf-156">Atualizar as propriedades de um webhook ativo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-156">Update the properties of an active webhook.</span></span>
    
- <span data-ttu-id="3edcf-157">Habilitar um webhook que foi desabilitado devido a um número excessivo de notificações de falhas.</span><span class="sxs-lookup"><span data-stu-id="3edcf-157">Enable a webhook that was disabled because of excessive failed notifications.</span></span>
    
- <span data-ttu-id="3edcf-158">Habilitar novamente um webhook expirado especificando uma data de término posterior ou nula.</span><span class="sxs-lookup"><span data-stu-id="3edcf-158">Re-enable an expired webhook by specifying a later or null expiration date.</span></span>
    
- <span data-ttu-id="3edcf-159">Remover um webhook.</span><span class="sxs-lookup"><span data-stu-id="3edcf-159">Remove a webhook.</span></span>
    
||<span data-ttu-id="3edcf-160">Assinatura</span><span class="sxs-lookup"><span data-stu-id="3edcf-160">Subscription</span></span>|<span data-ttu-id="3edcf-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="3edcf-161">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="3edcf-162">**Path**</span><span class="sxs-lookup"><span data-stu-id="3edcf-162">**Path**</span></span>| `/subscriptions/start?contentType={ContentType}`||
|<span data-ttu-id="3edcf-163">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="3edcf-163">**Parameters**</span></span>|<span data-ttu-id="3edcf-164">contentType</span><span class="sxs-lookup"><span data-stu-id="3edcf-164">contentType</span></span>|<span data-ttu-id="3edcf-165">Deve ser um tipo de conteúdo válido.</span><span class="sxs-lookup"><span data-stu-id="3edcf-165">Must be a valid content type.</span></span>|
||<span data-ttu-id="3edcf-166">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="3edcf-166">PublisherIdentifier</span></span>|<span data-ttu-id="3edcf-167">O GUID de locatário de codificação de fornecedor para a API.</span><span class="sxs-lookup"><span data-stu-id="3edcf-167">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="3edcf-168">Este **não** é o GUID de aplicativo nem o GUID do cliente que está usando o aplicativo, mas o GUID da empresa que está escrevendo o código.</span><span class="sxs-lookup"><span data-stu-id="3edcf-168">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="3edcf-169">Este parâmetro é usado para limitar a taxa de solicitações.</span><span class="sxs-lookup"><span data-stu-id="3edcf-169">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="3edcf-170">Verifique se este parâmetro foi especificado em todas as solicitações emitidas para obter uma cota dedicada.</span><span class="sxs-lookup"><span data-stu-id="3edcf-170">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="3edcf-171">Todas as solicitações recebidas sem este parâmetro compartilharão a mesma cota.</span><span class="sxs-lookup"><span data-stu-id="3edcf-171">All requests received without this parameter will share the same quota.</span></span>|
|<span data-ttu-id="3edcf-172">**Body**</span><span class="sxs-lookup"><span data-stu-id="3edcf-172">**Body**</span></span>|<span data-ttu-id="3edcf-173">webhook</span><span class="sxs-lookup"><span data-stu-id="3edcf-173">webhook</span></span>|<span data-ttu-id="3edcf-174">Objeto JSON opcional com três propriedades:</span><span class="sxs-lookup"><span data-stu-id="3edcf-174">Optional JSON object with three properties:</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-175"><b>address</b>: ponto de extremidade HTTPS necessário que pode receber notificações.</span><span class="sxs-lookup"><span data-stu-id="3edcf-175"><b>address</b>: Required HTTPS endpoint that can receive notifications.</span></span>  <span data-ttu-id="3edcf-176">Uma mensagem de teste será enviada ao webhook para validá-lo antes da criação da assinatura.</span><span class="sxs-lookup"><span data-stu-id="3edcf-176">A test message will be sent to the webhook to validate the webhook before creating the subscription.</span></span></p></li><li><p><span data-ttu-id="3edcf-177"><b>authId</b>: cadeia de caracteres opcional que é incluída como o cabeçalho WebHook AuthID na notificação enviada ao webhook para identificar e autorizar a origem da solicitação para o webhook.</span><span class="sxs-lookup"><span data-stu-id="3edcf-177"><b>authId</b>: Optional string that will be included as the WebHook-AuthID header in notifications sent to the webhook as a means of identifying and authorizing the source of the request to the webhook.</span></span></p></li><li><p><span data-ttu-id="3edcf-178"><b>expiration</b>: data e hora opcionais que indicam uma data e uma hora após as quais as notificações não devem ser enviadas ao webhook.</span><span class="sxs-lookup"><span data-stu-id="3edcf-178"><b>expiration</b>: Optional datetime that indicates a datetime after which notifications should no longer be sent to the webhook.</span></span></p></li></ul>|
|<span data-ttu-id="3edcf-179">**Response**</span><span class="sxs-lookup"><span data-stu-id="3edcf-179">**Response**</span></span>|<span data-ttu-id="3edcf-180">contentType</span><span class="sxs-lookup"><span data-stu-id="3edcf-180">contentType</span></span>|<span data-ttu-id="3edcf-181">O tipo de conteúdo especificado na chamada.</span><span class="sxs-lookup"><span data-stu-id="3edcf-181">The content type specified in the call.</span></span>|
||<span data-ttu-id="3edcf-182">status</span><span class="sxs-lookup"><span data-stu-id="3edcf-182">status</span></span>|<span data-ttu-id="3edcf-183">O status da assinatura.</span><span class="sxs-lookup"><span data-stu-id="3edcf-183">The status of the subscription.</span></span> <span data-ttu-id="3edcf-184">Se uma assinatura for desabilitada, você não poderá listar nem recuperar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-184">If a subscription is disabled, you will not be able to list or retrieve content.</span></span>|
||<span data-ttu-id="3edcf-185">webhook</span><span class="sxs-lookup"><span data-stu-id="3edcf-185">webhook</span></span>|<span data-ttu-id="3edcf-186">As propriedades de webhook especificadas na chamada, juntamente com o status do webhook.</span><span class="sxs-lookup"><span data-stu-id="3edcf-186">The webhook properties specified in the call together with the status of the webhook.</span></span> <span data-ttu-id="3edcf-187">Se o webhook for desabilitado, você não receberá notificações, mas ainda poderá listar e recuperar conteúdo, desde que a assinatura esteja habilitada.</span><span class="sxs-lookup"><span data-stu-id="3edcf-187">If the webhook is disabled, you will not receive notification, but you will still be able to list and retrieve content, provided the subscription is enabled.</span></span>|

#### <a name="sample-request"></a><span data-ttu-id="3edcf-188">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="3edcf-188">Sample request</span></span>

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


#### <a name="sample-response"></a><span data-ttu-id="3edcf-189">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="3edcf-189">Sample response</span></span>

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


## <a name="webhook-validation"></a><span data-ttu-id="3edcf-190">Validação de webhook</span><span class="sxs-lookup"><span data-stu-id="3edcf-190">Webhook validation</span></span>

<span data-ttu-id="3edcf-191">Quando a operação /start for chamada e um webhook for especificado, enviaremos uma notificação de validação ao endereço de webhook especificado para validar que um ouvinte ativo pode aceitar e processar notificações.</span><span class="sxs-lookup"><span data-stu-id="3edcf-191">When the /start operation is called and a webhook is specified, we will send a validation notification to the specified webhook address to validate that an active listener can accept and process notifications.</span></span> <span data-ttu-id="3edcf-192">Se não recebermos uma resposta HTTP 200 OK, a assinatura não será criada.</span><span class="sxs-lookup"><span data-stu-id="3edcf-192">If we do not receive an HTTP 200 OK response, the subscription will not be created.</span></span> <span data-ttu-id="3edcf-193">Ou então, se /start for chamado para adicionar um webhook a uma assinatura existente, e uma resposta HTTP 200 OK não for recebida, o webhook não será adicionado, e a assinatura permanecerá inalterada.</span><span class="sxs-lookup"><span data-stu-id="3edcf-193">Or, if /start is being called to add a webhook to an existing subscription and a response of HTTP 200 OK is not received, the webhook will not be added and the subscription will remain unchanged.</span></span>

#### <a name="sample-request"></a><span data-ttu-id="3edcf-194">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="3edcf-194">Sample request</span></span>

```json
POST {webhook address}
Content-Type: application/json; charset=utf-8
Webhook-AuthID: (webhook authId, if provided)
Webhook-ValidationCode: (random opaque string)

{
    "validationCode": (random opaque string, same as header)
}

```


#### <a name="sample-response"></a><span data-ttu-id="3edcf-195">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="3edcf-195">Sample response</span></span>

```json

HTTP/1.1 200 OK

```


## <a name="stop-a-subscription"></a><span data-ttu-id="3edcf-196">Interromper uma assinatura</span><span class="sxs-lookup"><span data-stu-id="3edcf-196">Stop a subscription</span></span>

<span data-ttu-id="3edcf-197">Essa operação interrompe uma assinatura para o tipo de conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-197">This operation stops a subscription to the specified content type.</span></span> 

<span data-ttu-id="3edcf-198">Quando uma assinatura for interrompida, você não receberá mais notificações e não poderá recuperar o conteúdo disponível.</span><span class="sxs-lookup"><span data-stu-id="3edcf-198">When a subscription is stopped, you will no longer receive notifications and you will not be able to retrieve available content.</span></span> <span data-ttu-id="3edcf-199">Se a assinatura for reiniciada posteriormente, você terá acesso ao novo conteúdo desse ponto em diante.</span><span class="sxs-lookup"><span data-stu-id="3edcf-199">If the subscription is later restarted, you will have access to new content from that point forward.</span></span> <span data-ttu-id="3edcf-200">Você não poderá recuperar o conteúdo que estava disponível entre o momento em que a assinatura foi interrompida e reiniciada.</span><span class="sxs-lookup"><span data-stu-id="3edcf-200">You will not be able to retrieve content that was available between the time the subscription was stopped and restarted.</span></span>


||<span data-ttu-id="3edcf-201">Assinatura</span><span class="sxs-lookup"><span data-stu-id="3edcf-201">Subscription</span></span>|<span data-ttu-id="3edcf-202">Descrição</span><span class="sxs-lookup"><span data-stu-id="3edcf-202">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="3edcf-203">**Path**</span><span class="sxs-lookup"><span data-stu-id="3edcf-203">**Path**</span></span>| `/subscriptions/stop?contentType={ContentType}`||
|<span data-ttu-id="3edcf-204">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="3edcf-204">**Parameters**</span></span>|<span data-ttu-id="3edcf-205">contentType</span><span class="sxs-lookup"><span data-stu-id="3edcf-205">contentType</span></span>|<span data-ttu-id="3edcf-206">Deve ser um tipo de conteúdo válido.</span><span class="sxs-lookup"><span data-stu-id="3edcf-206">Must be a valid content type.</span></span>|
||<span data-ttu-id="3edcf-207">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="3edcf-207">PublisherIdentifier</span></span>|<span data-ttu-id="3edcf-208">O GUID de locatário de codificação de fornecedor para a API.</span><span class="sxs-lookup"><span data-stu-id="3edcf-208">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="3edcf-209">Este **não** é o GUID de aplicativo nem o GUID do cliente que está usando o aplicativo, mas o GUID da empresa que está escrevendo o código.</span><span class="sxs-lookup"><span data-stu-id="3edcf-209">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="3edcf-210">Este parâmetro é usado para limitar a taxa de solicitações.</span><span class="sxs-lookup"><span data-stu-id="3edcf-210">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="3edcf-211">Verifique se este parâmetro foi especificado em todas as solicitações emitidas para obter uma cota dedicada.</span><span class="sxs-lookup"><span data-stu-id="3edcf-211">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="3edcf-212">Todas as solicitações recebidas sem este parâmetro compartilharão a mesma cota.</span><span class="sxs-lookup"><span data-stu-id="3edcf-212">All requests received without this parameter will share the same quota.</span></span>|
|<span data-ttu-id="3edcf-213">**Body**</span><span class="sxs-lookup"><span data-stu-id="3edcf-213">**Body**</span></span>|<span data-ttu-id="3edcf-214">(vazio)</span><span class="sxs-lookup"><span data-stu-id="3edcf-214">(empty)</span></span>||
|<span data-ttu-id="3edcf-215">**Response**</span><span class="sxs-lookup"><span data-stu-id="3edcf-215">**Response**</span></span>|<span data-ttu-id="3edcf-216">(vazio)</span><span class="sxs-lookup"><span data-stu-id="3edcf-216">(empty)</span></span>|||

#### <a name="sample-request"></a><span data-ttu-id="3edcf-217">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="3edcf-217">Sample request</span></span>

```json
POST {root}/subscriptions/stop?contentType=Audit.SharePoint&PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Authorization: Bearer eyJ0e...Qa6wg

```

#### <a name="sample-response"></a><span data-ttu-id="3edcf-218">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="3edcf-218">Sample response</span></span>

```json
HTTP/1.1 200 OK
```


## <a name="list-current-subscriptions"></a><span data-ttu-id="3edcf-219">Listar as assinaturas atuais</span><span class="sxs-lookup"><span data-stu-id="3edcf-219">List current subscriptions</span></span>

<span data-ttu-id="3edcf-220">Essa operação retorna um conjunto de assinaturas atuais com os webhooks associados.</span><span class="sxs-lookup"><span data-stu-id="3edcf-220">This operation returns a collection of the current subscriptions together with the associated webhooks.</span></span>

||<span data-ttu-id="3edcf-221">Assinatura</span><span class="sxs-lookup"><span data-stu-id="3edcf-221">Subscription</span></span>|<span data-ttu-id="3edcf-222">Descrição</span><span class="sxs-lookup"><span data-stu-id="3edcf-222">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="3edcf-223">**Path**</span><span class="sxs-lookup"><span data-stu-id="3edcf-223">**Path**</span></span>| `/subscriptions/list`||
|<span data-ttu-id="3edcf-224">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="3edcf-224">**Parameters**</span></span>|<span data-ttu-id="3edcf-225">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="3edcf-225">PublisherIdentifier</span></span>|<span data-ttu-id="3edcf-226">O GUID de locatário de codificação de fornecedor para a API.</span><span class="sxs-lookup"><span data-stu-id="3edcf-226">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="3edcf-227">Este **não** é o GUID de aplicativo nem o GUID do cliente que está usando o aplicativo, mas o GUID da empresa que está escrevendo o código.</span><span class="sxs-lookup"><span data-stu-id="3edcf-227">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="3edcf-228">Este parâmetro é usado para limitar a taxa de solicitações.</span><span class="sxs-lookup"><span data-stu-id="3edcf-228">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="3edcf-229">Verifique se este parâmetro foi especificado em todas as solicitações emitidas para obter uma cota dedicada.</span><span class="sxs-lookup"><span data-stu-id="3edcf-229">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="3edcf-230">Todas as solicitações recebidas sem este parâmetro compartilharão a mesma cota.</span><span class="sxs-lookup"><span data-stu-id="3edcf-230">All requests received without this parameter will share the same quota.</span></span>|
|<span data-ttu-id="3edcf-231">**Body**</span><span class="sxs-lookup"><span data-stu-id="3edcf-231">**Body**</span></span>|<span data-ttu-id="3edcf-232">(vazio)</span><span class="sxs-lookup"><span data-stu-id="3edcf-232">(empty)</span></span>||
|<span data-ttu-id="3edcf-233">**Response**</span><span class="sxs-lookup"><span data-stu-id="3edcf-233">**Response**</span></span>|<span data-ttu-id="3edcf-234">Matriz JSON</span><span class="sxs-lookup"><span data-stu-id="3edcf-234">JSON array</span></span>|<span data-ttu-id="3edcf-235">Cada assinatura será representada por um objeto JSON com três propriedades:</span><span class="sxs-lookup"><span data-stu-id="3edcf-235">Each subscription will be represented by a JSON object with three properties:</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-236"><b>contentType</b>: indica o tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-236"><b>contentType</b>: Indicates the content type.</span></span></p></li><li><p><span data-ttu-id="3edcf-237"><b>status</b>: indica o status da assinatura.</span><span class="sxs-lookup"><span data-stu-id="3edcf-237"><b>status</b>: Indicates the status of the subscription.</span></span></p></li><li><p><span data-ttu-id="3edcf-238"><b>webhook</b>: indica o webhook configurado, juntamente com o status (habilitado, desabilitado, expirado) dele.</span><span class="sxs-lookup"><span data-stu-id="3edcf-238"><b>webhook</b>: Indicates the configured webhook, together with the status (enabled, disabled, expired) of the webhook.</span></span>  <span data-ttu-id="3edcf-239">Se uma assinatura não tiver um webhook, a propriedade webhook estará presente, mas com um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-239">If a subscription does not have a webhook, the webhook property will be present but with null value.</span></span></p></li></ul>|


#### <a name="sample-request"></a><span data-ttu-id="3edcf-240">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="3edcf-240">Sample request</span></span>

```json
GET {root}/subscriptions/list?PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Authorization: Bearer eyJ0e...Qa6wg

```

#### <a name="sample-response"></a><span data-ttu-id="3edcf-241">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="3edcf-241">Sample response</span></span>

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


## <a name="list-available-content"></a><span data-ttu-id="3edcf-242">Listar conteúdo disponível</span><span class="sxs-lookup"><span data-stu-id="3edcf-242">List available content</span></span>

<span data-ttu-id="3edcf-243">Essa operação lista o conteúdo atualmente disponível para recuperação para o tipo de conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-243">This operation lists the content currently available for retrieval for the specified content type.</span></span> <span data-ttu-id="3edcf-244">O conteúdo é uma agregação de ações e eventos coletados de vários servidores em vários data centers.</span><span class="sxs-lookup"><span data-stu-id="3edcf-244">The content is an aggregation of actions and events harvested from multiple servers across multiple datacenters.</span></span> <span data-ttu-id="3edcf-245">O conteúdo será listado na ordem em que as agregações se tornarem disponíveis, mas não há garantia de que os eventos e as ações nas agregações sejam sequenciais.</span><span class="sxs-lookup"><span data-stu-id="3edcf-245">The content will be listed in the order in which the aggregations become available, but the events and actions within the aggregations are not guaranteed to be sequential.</span></span> <span data-ttu-id="3edcf-246">Um erro será retornado se o status da assinatura for desabilitado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-246">An error is returned if the subscription status is disabled.</span></span>


||<span data-ttu-id="3edcf-247">Assinatura</span><span class="sxs-lookup"><span data-stu-id="3edcf-247">Subscription</span></span>|<span data-ttu-id="3edcf-248">Descrição</span><span class="sxs-lookup"><span data-stu-id="3edcf-248">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="3edcf-249">**Path**</span><span class="sxs-lookup"><span data-stu-id="3edcf-249">**Path**</span></span>| `/subscriptions/content?contentType={ContentType}&amp;startTime={0}&amp;endTime={1}`||
|<span data-ttu-id="3edcf-250">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="3edcf-250">**Parameters**</span></span>|<span data-ttu-id="3edcf-251">contentType</span><span class="sxs-lookup"><span data-stu-id="3edcf-251">contentType</span></span>|<span data-ttu-id="3edcf-252">Deve ser um tipo de conteúdo válido.</span><span class="sxs-lookup"><span data-stu-id="3edcf-252">Must be a valid content type.</span></span>|
||<span data-ttu-id="3edcf-253">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="3edcf-253">PublisherIdentifier</span></span>|<span data-ttu-id="3edcf-254">O GUID de locatário de codificação de fornecedor para a API.</span><span class="sxs-lookup"><span data-stu-id="3edcf-254">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="3edcf-255">Este **não** é o GUID de aplicativo nem o GUID do cliente que está usando o aplicativo, mas o GUID da empresa que está escrevendo o código.</span><span class="sxs-lookup"><span data-stu-id="3edcf-255">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="3edcf-256">Este parâmetro é usado para limitar a taxa de solicitações.</span><span class="sxs-lookup"><span data-stu-id="3edcf-256">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="3edcf-257">Verifique se este parâmetro foi especificado em todas as solicitações emitidas para obter uma cota dedicada.</span><span class="sxs-lookup"><span data-stu-id="3edcf-257">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="3edcf-258">Todas as solicitações recebidas sem este parâmetro compartilharão a mesma cota.</span><span class="sxs-lookup"><span data-stu-id="3edcf-258">All requests received without this parameter will share the same quota.</span></span>|
||<span data-ttu-id="3edcf-259">startTime endTime</span><span class="sxs-lookup"><span data-stu-id="3edcf-259">startTime endTime</span></span>|<span data-ttu-id="3edcf-260">As datas e horas opcionais (UTC) que indicam o intervalo de tempo do conteúdo a ser retornado, com base em quando o conteúdo foi disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-260">Optional datetimes (UTC) indicating the time range of content to return, based on when the content became available.</span></span> <span data-ttu-id="3edcf-261">O intervalo de tempo é inclusivo em relação a startTime(startTime <= contentCreated) e exclusivo em relação a endTime (contentCreated < endTime). Portanto, intervalos de tempo incrementos e não sobrepostos podem ser usados para percorrer o conteúdo disponível.</span><span class="sxs-lookup"><span data-stu-id="3edcf-261">The time range is inclusive with respect to startTime (startTime <= contentCreated) and exclusive with respect to endTime (contentCreated < endTime), so that non-overlapping, incrementing time intervals can used to page through available content.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-262">AAAA-MM-DD</span><span class="sxs-lookup"><span data-stu-id="3edcf-262">YYYY-MM-DD</span></span></p></li><li><p><span data-ttu-id="3edcf-263">AAAA-MM-DDTHH:MM</span><span class="sxs-lookup"><span data-stu-id="3edcf-263">YYYY-MM-DDTHH:MM</span></span></p></li><li><p><span data-ttu-id="3edcf-264">AAAA-MM-DDTHH:MM:SS</span><span class="sxs-lookup"><span data-stu-id="3edcf-264">YYYY-MM-DDTHH:MM:SS</span></span></p></li></ul><span data-ttu-id="3edcf-265">Ambos devem ser especificados (ou ambos omitidos), não devem estar separados por mais de 24 horas e a hora de início não pode ser mais de sete dias no passado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-265">Both must be specified (or both omitted) and they must be no more than 24 hours apart, with the start time no more than 7 days in the past.</span></span> <span data-ttu-id="3edcf-266">Por padrão, se startTime e endTime forem omitidos, o conteúdo disponível nas últimas 24 horas será retornado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-266">By default, if startTime and endTime are omitted, then the content available in the last 24 hours is returned.</span></span><p><span data-ttu-id="3edcf-267">**OBSERVAÇÃO**: embora seja possível especificar startTime e endTime separados por mais de 24 horas, isso não é recomendável.</span><span class="sxs-lookup"><span data-stu-id="3edcf-267">**NOTE**: Even though it is possible to specify a startTime and endTime more than 24 hours apart, this is not recommended.</span></span> <span data-ttu-id="3edcf-268">Além disso, se você obtiver resultados em resposta a uma solicitação de mais de 24 horas, serão resultados parciais e não deverão ser levados em consideração.</span><span class="sxs-lookup"><span data-stu-id="3edcf-268">Furthermore, if you do get any results in response to a request for more than 24 hours, these could be partial results and should not be taken into account.</span></span> <span data-ttu-id="3edcf-269">A solicitação deve ser emitida com um intervalo de no máximo 24 horas entre startTime e endTime.</span><span class="sxs-lookup"><span data-stu-id="3edcf-269">The request should be issued with an interval of no more than 24 hours between the startTime and endTime.</span></span></p>|
|<span data-ttu-id="3edcf-270">**Response**</span><span class="sxs-lookup"><span data-stu-id="3edcf-270">**Response**</span></span>|<span data-ttu-id="3edcf-271">Matriz JSON</span><span class="sxs-lookup"><span data-stu-id="3edcf-271">JSON array</span></span>|<span data-ttu-id="3edcf-272">O conteúdo disponível será representado por objetos JSON com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="3edcf-272">The available content will be represented by JSON objects with the following properties:</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-273"><b>contentType</b>: indica o tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-273"><b>contentType</b>: Indicates the content type.</span></span></p></li><li><p><span data-ttu-id="3edcf-274"><b>contentId</b>: uma cadeia de caracteres opaca que identifica o conteúdo de forma exclusiva.</span><span class="sxs-lookup"><span data-stu-id="3edcf-274"><b>contentId</b>: An opaque string that uniquely identifies the content.</span></span></p></li><li><p><span data-ttu-id="3edcf-275"><b>contentUri</b>: a URL a ser usada ao recuperar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-275"><b>contentUri</b>: The URL to use when retrieving the content.</span></span></p></li><li><p><span data-ttu-id="3edcf-276"><b>contentCreated</b>: data e hora em que o conteúdo foi disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-276"><b>contentCreated</b>: The datetime when the content was made available.</span></span></p></li><li><p><span data-ttu-id="3edcf-277"><b>contentExpiration</b>: data e hora em que o conteúdo não estará mais disponível para recuperação.</span><span class="sxs-lookup"><span data-stu-id="3edcf-277"><b>contentExpiration</b>: The datetime after which the content will no longer be available for retrieval.</span></span></p></li></ul>|


#### <a name="sample-request"></a><span data-ttu-id="3edcf-278">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="3edcf-278">Sample request</span></span>

```json
GET {root}/subscriptions/content?contentType=Audit.SharePoint&PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Authorization: Bearer eyJ0e...Qa6wg

```

#### <a name="sample-response"></a><span data-ttu-id="3edcf-279">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="3edcf-279">Sample response</span></span>

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


### <a name="pagination"></a><span data-ttu-id="3edcf-280">Paginação</span><span class="sxs-lookup"><span data-stu-id="3edcf-280">Pagination</span></span>

<span data-ttu-id="3edcf-281">Ao ser listado o conteúdo disponível para um intervalo de tempo, o número de resultados retornados é limitado para impedir tempos limite de resposta.</span><span class="sxs-lookup"><span data-stu-id="3edcf-281">When listing available content for a time range, the number of results returned is limited to prevent response timeouts.</span></span> <span data-ttu-id="3edcf-282">Se houver mais resultados no intervalo de tempo especificado do que o máximo que pode ser retornados em uma única resposta, eles serão truncados, e um cabeçalho será adicionado à resposta para indicar a URL a ser usada para recuperar a próxima página de resultados.</span><span class="sxs-lookup"><span data-stu-id="3edcf-282">If there are more results in the specified time range than can be returned in single response, the results will be truncated and a header will be added to the response indicating the URL to use to retrieve the next page of results.</span></span> <span data-ttu-id="3edcf-283">A URL conterá os mesmos parâmetros _startTime_ e _endTime_ especificados na solicitação original, juntamente com um parâmetro que indica a ID interna da próxima página.</span><span class="sxs-lookup"><span data-stu-id="3edcf-283">The URL will contain the same  _startTime_ and _endTime_ parameters that were specified in the original request, together with a parameter indicating the internal ID of the next page.</span></span> <span data-ttu-id="3edcf-284">Se _startTime_ e _endTime_ não tiverem sido especificados na solicitação original, eles serão definidos para refletir o intervalo de 24 horas que precedia a solicitação original.</span><span class="sxs-lookup"><span data-stu-id="3edcf-284">If _startTime_ and _endTime_ were not specified in the original request, they will be set to reflect the 24-hour interval that preceded the original request.</span></span>


```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
NextPageUri: https://manage.office.com/api/v1/{tenant_id}/activity/feed/subscriptions/content?contentType=Audit.SharePoint&amp;startTime=2015-10-01&amp;endTime=2015-10-02&amp;nextPage=2015101900R022885001761

```

<span data-ttu-id="3edcf-285">Para listar todo o conteúdo disponível para um intervalo de tempo especificado, talvez seja necessário recuperar várias páginas até que uma resposta sem o cabeçalho **NextPageUri** seja recebida.</span><span class="sxs-lookup"><span data-stu-id="3edcf-285">To list all available content for a specified time range, you might need to retrieve multiple pages until a response without the **NextPageUri** header is received.</span></span>


## <a name="receiving-notifications"></a><span data-ttu-id="3edcf-286">Receber notificações</span><span class="sxs-lookup"><span data-stu-id="3edcf-286">Receiving notifications</span></span>

<span data-ttu-id="3edcf-287">Notificações são enviadas ao webhook configurado para uma assinatura à medida que novo conteúdo fica disponível.</span><span class="sxs-lookup"><span data-stu-id="3edcf-287">Notifications are sent to the configured webhook for a subscription as new content becomes available.</span></span> <span data-ttu-id="3edcf-288">Como a notificação inclui o identificador de locatário, você pode usar o mesmo webhook para receber notificações para todos os locatários para os quais tem assinaturas.</span><span class="sxs-lookup"><span data-stu-id="3edcf-288">Because the notification includes the tenant identifier, you can use the same webhook to receive notifications for all tenants for which you have subscriptions.</span></span>

<span data-ttu-id="3edcf-289">A notificação é criada como um HTTP POST sobre TLS (TLS 1.0 e versões posteriores) para o endereço do webhook especificado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-289">The notification is made as an HTTP POST over TLS (TLS 1.0 and later versions) to the specified webhook address.</span></span> <span data-ttu-id="3edcf-290">Se a configuração do webhook inclui uma ID de autenticação, a enviamos como um cabeçalho HTTP: Webhook AuthID.</span><span class="sxs-lookup"><span data-stu-id="3edcf-290">If the webhook configuration includes an auth ID, we will send it as an HTTP header: Webhook-AuthID.</span></span> <span data-ttu-id="3edcf-291">Uma resposta diferente de HTTP 200 OK será considerada uma falha, e a notificação será tentada novamente.</span><span class="sxs-lookup"><span data-stu-id="3edcf-291">Any response other than HTTP 200 OK will be considered a failure and the notification will be retried.</span></span> <span data-ttu-id="3edcf-292">Você também pode configurar o webhook para exigir autenticação baseada em certificado de cliente, e faremos a autenticação usando o certificado manage.office.com.</span><span class="sxs-lookup"><span data-stu-id="3edcf-292">You can also configure your webhook to require client certificate-based authentication and we will authenticate using the manage.office.com certificate.</span></span>

<span data-ttu-id="3edcf-293">O corpo da solicitação conterá uma matriz de um ou mais objetos JSON que representam os blobs de conteúdo disponíveis.</span><span class="sxs-lookup"><span data-stu-id="3edcf-293">The body of the request will contain an array of one or more JSON objects that represent the available content blobs.</span></span> <span data-ttu-id="3edcf-294">O número de blobs de conteúdo em cada notificação é limitado para manter o tamanho da notificação relativamente pequeno.</span><span class="sxs-lookup"><span data-stu-id="3edcf-294">The number of content blobs in each notification is limited to keep the size of the notification relatively small.</span></span> <span data-ttu-id="3edcf-295">Como esse limite pode ser alterado, a implementação deve consultar o comprimento da matriz, em vez de esperar um tamanho fixo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-295">Because this limit might change, your implementation should query for the length of the array instead of expecting a fixed size.</span></span> <span data-ttu-id="3edcf-296">Cada objeto incluirá as mesmas propriedades retornadas pela operação /content, juntamente com o GUID do locatário ao qual os dados pertencem e o GUID do aplicativo que criou as assinaturas.</span><span class="sxs-lookup"><span data-stu-id="3edcf-296">Each object will include the same properties returned by the /content operation, together with the GUID of the tenant to which the data belongs and the GUID of your application that created the subscriptions.</span></span> <span data-ttu-id="3edcf-297">Isso permite que o webhook estabeleça o contexto quando está sendo usado com vários locatários e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3edcf-297">This allows the webhook to establish context when it is being used with multiple tenants and applications.</span></span>

- <span data-ttu-id="3edcf-298">**tenantId**: o GUID do locatário ao qual o conteúdo pertence.</span><span class="sxs-lookup"><span data-stu-id="3edcf-298">**tenantId**: The GUID of the tenant to which the content belongs.</span></span>
    
- <span data-ttu-id="3edcf-299">**clientId**: o GUID do aplicativo que criou a assinatura.</span><span class="sxs-lookup"><span data-stu-id="3edcf-299">**clientId**: The GUID of your application that created the subscription.</span></span>
    
- <span data-ttu-id="3edcf-300">**contentType**: indica o tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-300">**contentType**: Indicates the content type.</span></span>
    
- <span data-ttu-id="3edcf-301">**contentId**: uma cadeia de caracteres opaca que identifica o conteúdo de forma exclusiva.</span><span class="sxs-lookup"><span data-stu-id="3edcf-301">**contentId**: An opaque string that uniquely identifies the content.</span></span>
    
- <span data-ttu-id="3edcf-302">**contentUri**: a URL a ser usada ao recuperar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-302">**contentUri**: The URL to use when retrieving the content.</span></span>
    
- <span data-ttu-id="3edcf-303">**contentCreated**: data e hora em que o conteúdo foi disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-303">**contentCreated**: The datetime when the content was made available.</span></span>
    
- <span data-ttu-id="3edcf-304">**contentExpiration**: data e hora em que o conteúdo não estará mais disponível para recuperação.</span><span class="sxs-lookup"><span data-stu-id="3edcf-304">**contentExpiration**: The datetime after which the content will no longer be available for retrieval.</span></span>
    
<span data-ttu-id="3edcf-305">A seguir há um exemplo de uma notificação.</span><span class="sxs-lookup"><span data-stu-id="3edcf-305">The following is an example of a notification.</span></span>

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


## <a name="notification-failure-and-retry"></a><span data-ttu-id="3edcf-306">Falha de notificação e nova tentativa</span><span class="sxs-lookup"><span data-stu-id="3edcf-306">Notification failure and retry</span></span>

<span data-ttu-id="3edcf-307">O sistema de notificação envia notificações à medida que novo conteúdo é disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-307">The notification system sends notifications as new content becomes available.</span></span> <span data-ttu-id="3edcf-308">Se encontramos um número excessivo de falhas ao enviar notificações, o mecanismo de novas tentativas aumentará exponencialmente o tempo entre as novas tentativas.</span><span class="sxs-lookup"><span data-stu-id="3edcf-308">If we encounter excessive failures when sending notifications, our retry mechanism will exponentially increase the time between retries.</span></span> <span data-ttu-id="3edcf-309">Se continuarmos a encontrar falhas, nos reservaremos o direito de desabilitar o webhook e interromper completamente o envio de notificações.</span><span class="sxs-lookup"><span data-stu-id="3edcf-309">If we continue to encounter failures, we reserve the right to disable the webhook and stop sending notifications to it altogether.</span></span> <span data-ttu-id="3edcf-310">A operação /start pode ser usada para reabilitar um webhook desabilitado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-310">The /start operation can be used to re-enable a disabled webhook.</span></span>


## <a name="retrieving-content"></a><span data-ttu-id="3edcf-311">Recuperar conteúdo</span><span class="sxs-lookup"><span data-stu-id="3edcf-311">Retrieving content</span></span>

<span data-ttu-id="3edcf-312">Para recuperar um blob de conteúdo, faça uma solicitação GET em relação ao URI de conteúdo correspondente que está incluído na lista de conteúdo disponível e nas notificações enviadas a um webhook.</span><span class="sxs-lookup"><span data-stu-id="3edcf-312">To retrieve a content blob, make a GET request against the corresponding content URI that is included in the list of available content and in the notifications sent to a webhook.</span></span> <span data-ttu-id="3edcf-313">O conteúdo retornado será um conjunto de mais ações ou eventos no formato JSON.</span><span class="sxs-lookup"><span data-stu-id="3edcf-313">The returned content will be a collection of one more actions or events in JSON format.</span></span>

#### <a name="sample-request"></a><span data-ttu-id="3edcf-314">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="3edcf-314">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/41463f53-8812-40f4-890f-865bf6e35190/activity/feed/audit/301299007231$301299007231$41463f53881240f4890f865bf6e35190aad2015062920$e1c2ab19858a469fb1f1fd097effffc9$04 HTTP/1.1
Authorization: Bearer eyJ0e...Qa6wg
```

#### <a name="sample-response"></a><span data-ttu-id="3edcf-315">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="3edcf-315">Sample response</span></span>

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


## <a name="list-notifications"></a><span data-ttu-id="3edcf-316">Listar notificações</span><span class="sxs-lookup"><span data-stu-id="3edcf-316">List notifications</span></span>

<span data-ttu-id="3edcf-317">Essa operação lista todas as tentativas de notificação para o tipo de conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-317">This operation lists all notification attempts for the specified content type.</span></span> <span data-ttu-id="3edcf-318">Se você não tiver incluído um webhook ao iniciar a assinatura para o tipo de conteúdo, não haverá notificações a serem recuperadas.</span><span class="sxs-lookup"><span data-stu-id="3edcf-318">If you did not include a webhook when starting the subscription to the content type, there will be no notifications to retrieve.</span></span> <span data-ttu-id="3edcf-319">Como repetimos as notificações em caso de falha, essa operação pode retornar várias notificações para o mesmo conteúdo. A ordem em que as notificações são enviadas não necessariamente corresponde à ordem em que o conteúdo foi disponibilizado (especialmente quando há falhas e repetições).</span><span class="sxs-lookup"><span data-stu-id="3edcf-319">Because we retry notifications in the event of failure, this operation can return multiple notifications for the same content, and the order in which the notifications are sent will not necessarily match the order in which the content became available (especially when there are failures and retries).</span></span> 

<span data-ttu-id="3edcf-320">Você pode usar essa operação para ajudar a investigar problemas relacionados a webhooks e notificações, mas não deve usá-la para determinar qual conteúdo está disponível atualmente para recuperação.</span><span class="sxs-lookup"><span data-stu-id="3edcf-320">You can use this operation to help investigate issues related to webhooks and notifications, but you should not use it to determine what content is currently available for retrieval.</span></span> <span data-ttu-id="3edcf-321">Use a operação /content em vez disso.</span><span class="sxs-lookup"><span data-stu-id="3edcf-321">Use the /content operation instead.</span></span> <span data-ttu-id="3edcf-322">Retornaremos um erro se o status de assinatura for desabilitado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-322">We return an error if the subscription status is disabled.</span></span>


||<span data-ttu-id="3edcf-323">Assinatura</span><span class="sxs-lookup"><span data-stu-id="3edcf-323">Subscription</span></span>|<span data-ttu-id="3edcf-324">Descrição</span><span class="sxs-lookup"><span data-stu-id="3edcf-324">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="3edcf-325">**Path**</span><span class="sxs-lookup"><span data-stu-id="3edcf-325">**Path**</span></span>| `/subscriptions/notifications?contentType={ContentType}&amp;startTime={0}&amp;endTime={1}`||
|<span data-ttu-id="3edcf-326">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="3edcf-326">**Parameters**</span></span>|<span data-ttu-id="3edcf-327">contentType</span><span class="sxs-lookup"><span data-stu-id="3edcf-327">contentType</span></span>|<span data-ttu-id="3edcf-328">Deve ser um tipo de conteúdo válido.</span><span class="sxs-lookup"><span data-stu-id="3edcf-328">Must be a valid content type.</span></span>|
||<span data-ttu-id="3edcf-329">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="3edcf-329">PublisherIdentifier</span></span>|<span data-ttu-id="3edcf-330">O GUID de locatário de codificação de fornecedor para a API.</span><span class="sxs-lookup"><span data-stu-id="3edcf-330">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="3edcf-331">Este **não** é o GUID de aplicativo nem o GUID do cliente que está usando o aplicativo, mas o GUID da empresa que está escrevendo o código.</span><span class="sxs-lookup"><span data-stu-id="3edcf-331">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="3edcf-332">Este parâmetro é usado para limitar a taxa de solicitações.</span><span class="sxs-lookup"><span data-stu-id="3edcf-332">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="3edcf-333">Verifique se este parâmetro foi especificado em todas as solicitações emitidas para obter uma cota dedicada.</span><span class="sxs-lookup"><span data-stu-id="3edcf-333">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="3edcf-334">Todas as solicitações recebidas sem este parâmetro compartilharão a mesma cota.</span><span class="sxs-lookup"><span data-stu-id="3edcf-334">All requests received without this parameter will share the same quota.</span></span>|
||<span data-ttu-id="3edcf-335">startTime endTime</span><span class="sxs-lookup"><span data-stu-id="3edcf-335">startTime endTime</span></span>|<span data-ttu-id="3edcf-336">Datas e horas opcionais (UTC) que indicam o intervalo de tempo do conteúdo a ser retornado, com base em quando o conteúdo foi disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-336">Optional datetimes (UTC) that indicate the time range of content to return, based on when the content became available.</span></span> <span data-ttu-id="3edcf-337">O intervalo de tempo é inclusivo em relação a _startTime_ ( _startTime_ <= contentCreated) e exclusivo em relação a _endTime_ (_contentCreated_ < endTime). Portanto, intervalos de tempo incrementos e não sobrepostos podem ser usados para percorrer o conteúdo disponível.</span><span class="sxs-lookup"><span data-stu-id="3edcf-337">The time range is inclusive with respect to  _startTime_ ( _startTime_ <= contentCreated) and exclusive with respect to _endTime_ (_contentCreated_ < endTime), so that non-overlapping, incrementing time intervals can used to page through available content.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-338">AAAA-MM-DD</span><span class="sxs-lookup"><span data-stu-id="3edcf-338">YYYY-MM-DD</span></span></p></li><li><p><span data-ttu-id="3edcf-339">AAAA-MM-DDTHH:MM</span><span class="sxs-lookup"><span data-stu-id="3edcf-339">YYYY-MM-DDTHH:MM</span></span></p></li><li><p><span data-ttu-id="3edcf-340">AAAA-MM-DDTHH:MM:SS</span><span class="sxs-lookup"><span data-stu-id="3edcf-340">YYYY-MM-DDTHH:MM:SS</span></span></p></li></ul><span data-ttu-id="3edcf-341">Ambos devem ser especificados (ou ambos omitidos), não devem estar separados por mais de 24 horas e a hora de início não pode ser mais de sete dias no passado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-341">Both must be specified (or both omitted) and they must be no more than 24 hours apart, with the start time no more than 7 days in the past.</span></span> <span data-ttu-id="3edcf-342">Por padrão, se _startTime_ e _endTime_ forem omitidos, o conteúdo disponível nas últimas 24 horas será retornado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-342">By default, if  _startTime_ and _endTime_ are omitted, the content available in the last 24 hours is returned.</span></span>|
|<span data-ttu-id="3edcf-343">**Response**</span><span class="sxs-lookup"><span data-stu-id="3edcf-343">**Response**</span></span>|<span data-ttu-id="3edcf-344">Matriz JSON</span><span class="sxs-lookup"><span data-stu-id="3edcf-344">JSON array</span></span>|<span data-ttu-id="3edcf-345">As notificações serão representadas por objetos JSON com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="3edcf-345">The notifications will be represented by JSON objects with the following properties:</span></span> <ul><li><span data-ttu-id="3edcf-346">**contentType**: indica o tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-346">**contentType**: indicates the content type.</span></span></li><li><span data-ttu-id="3edcf-347">**contentId**: uma cadeia de caracteres opaca que identifica o conteúdo de forma exclusiva.</span><span class="sxs-lookup"><span data-stu-id="3edcf-347">**contentId**: an opaque string that uniquely identifies the content.</span></span></li><li><span data-ttu-id="3edcf-348">**contentUri**: a URL a ser usada ao recuperar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3edcf-348">**contentUri**: the URL to use when retrieving the content.</span></span> </li><li><span data-ttu-id="3edcf-349">**contentCreated**: data e hora em que o conteúdo foi disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-349">**contentCreated**: the datetime when the content was made available.</span></span></li><li><span data-ttu-id="3edcf-350">**contentExpiration**: data e hora em que o conteúdo não estará mais disponível para recuperação.</span><span class="sxs-lookup"><span data-stu-id="3edcf-350">**contentExpiration**: the datetime after which the content will no longer be available for retrieval.</span></span></li><li><span data-ttu-id="3edcf-351">**contentCreated**: data e hora em que o conteúdo foi disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-351">**notificationSent**: the datetime when the notification was sent.</span></span></li><li><span data-ttu-id="3edcf-352">**notificationStatus**: indica o êxito ou a falha da tentativa de notificação.</span><span class="sxs-lookup"><span data-stu-id="3edcf-352">**notificationStatus**: indicates the success or failure of the notification attempt.</span></span></li></ul>|

#### <a name="sample-request"></a><span data-ttu-id="3edcf-353">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="3edcf-353">Sample request</span></span>

```json
GET {root}/subscriptions/notifications?contentType=Audit.SharePoint&PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Authorization: Bearer eyJ0e...Qa6wg

```

#### <a name="sample-response"></a><span data-ttu-id="3edcf-354">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="3edcf-354">Sample response</span></span>

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


### <a name="pagination"></a><span data-ttu-id="3edcf-355">Paginação</span><span class="sxs-lookup"><span data-stu-id="3edcf-355">Pagination</span></span>

<span data-ttu-id="3edcf-356">Ao ser listado o histórico de notificações para um intervalo de tempo, o número de resultados retornados é limitado para impedir tempos limite de resposta.</span><span class="sxs-lookup"><span data-stu-id="3edcf-356">When listing notification history for a time range, the number of results returned is limited to prevent response timeouts.</span></span> <span data-ttu-id="3edcf-357">Se houver mais resultados no intervalo de tempo especificado do que o máximo que pode ser retornados em uma única resposta, eles serão truncados, e um cabeçalho será adicionado à resposta para indicar a URL a ser usada para recuperar a próxima página de resultados.</span><span class="sxs-lookup"><span data-stu-id="3edcf-357">If there are more results in the specified time range than can be returned in a single response, the results are truncated and a header is added to the response indicating the URL to use to retrieve the next page of results.</span></span> <span data-ttu-id="3edcf-358">A URL conterá os mesmos parâmetros _startTime_ e _endTime_ especificados na solicitação original, juntamente com um parâmetro que indica a ID interna da próxima página.</span><span class="sxs-lookup"><span data-stu-id="3edcf-358">The URL will contain the same  _startTime_ and _endTime_ parameters that were specified in the original request, together with a parameter indicating the internal ID of the next page.</span></span> <span data-ttu-id="3edcf-359">Se _startTime_ e _endTime_ não tiverem sido especificados na solicitação original, eles serão definidos para refletir o intervalo de 24 horas que precedia a solicitação original.</span><span class="sxs-lookup"><span data-stu-id="3edcf-359">If _startTime_ and _endTime_ were not specified in the original request, they will be set to reflect the 24-hour interval that preceded the original request.</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
NextPageUrl: https://manage.office.com/api/v1/{tenant_id}/activity/feed/subscriptions/content?contentType=Audit.SharePoint&amp;startTime=2015-10-01&amp;endTime=2015-10-02&amp;nextPage=2015101900R022885001761

```

<span data-ttu-id="3edcf-360">Para listar todo o conteúdo disponível para um intervalo de tempo especificado, talvez seja necessário recuperar várias páginas até que uma resposta sem o cabeçalho **NextPageUri** seja recebida.</span><span class="sxs-lookup"><span data-stu-id="3edcf-360">To list all available content for a specified time range, you might need to retrieve multiple pages until a response without the **NextPageUrl** header is received.</span></span>

## <a name="retrieve-resource-friendly-names"></a><span data-ttu-id="3edcf-361">Recuperar nomes amigáveis de recursos</span><span class="sxs-lookup"><span data-stu-id="3edcf-361">Retrieve resource friendly names</span></span>

<span data-ttu-id="3edcf-362">Essa operação recupera nomes amigáveis de recursos para objetos no feed de dados identificados por guids.</span><span class="sxs-lookup"><span data-stu-id="3edcf-362">This operation retrieves friendly names for objects in the data feed identified by guids.</span></span> <span data-ttu-id="3edcf-363">No momento, "DlpSensitiveType" é o único objeto com suporte.</span><span class="sxs-lookup"><span data-stu-id="3edcf-363">Currently "DlpSensitiveType" is the only supported object.</span></span> 


||<span data-ttu-id="3edcf-364">Assinatura</span><span class="sxs-lookup"><span data-stu-id="3edcf-364">Subscription</span></span>|<span data-ttu-id="3edcf-365">Descrição</span><span class="sxs-lookup"><span data-stu-id="3edcf-365">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="3edcf-366">**Path**</span><span class="sxs-lookup"><span data-stu-id="3edcf-366">**Path**</span></span>| `/resources/dlpSensitiveTypes`||
|<span data-ttu-id="3edcf-367">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="3edcf-367">**Parameters**</span></span>|<span data-ttu-id="3edcf-368">PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="3edcf-368">PublisherIdentifier</span></span>|<span data-ttu-id="3edcf-369">O GUID de locatário de codificação de fornecedor para a API.</span><span class="sxs-lookup"><span data-stu-id="3edcf-369">The tenant GUID of the vendor coding against the API.</span></span> <span data-ttu-id="3edcf-370">Este **não** é o GUID de aplicativo nem o GUID do cliente que está usando o aplicativo, mas o GUID da empresa que está escrevendo o código.</span><span class="sxs-lookup"><span data-stu-id="3edcf-370">This is **not** the application GUID or the GUID of the customer using the application, but the GUID of the company writing the code.</span></span> <span data-ttu-id="3edcf-371">Este parâmetro é usado para limitar a taxa de solicitações.</span><span class="sxs-lookup"><span data-stu-id="3edcf-371">This parameter is used for throttling the request rate.</span></span> <span data-ttu-id="3edcf-372">Verifique se este parâmetro foi especificado em todas as solicitações emitidas para obter uma cota dedicada.</span><span class="sxs-lookup"><span data-stu-id="3edcf-372">Make sure this parameter is specified in all issued requests to get a dedicated quota.</span></span> <span data-ttu-id="3edcf-373">Todas as solicitações recebidas sem este parâmetro compartilharão a mesma cota.</span><span class="sxs-lookup"><span data-stu-id="3edcf-373">All requests received without this parameter will share the same quota.</span></span>|
|<span data-ttu-id="3edcf-374">**Cabeçalhos**</span><span class="sxs-lookup"><span data-stu-id="3edcf-374">**Headers**</span></span>|<span data-ttu-id="3edcf-375">Accept-Language</span><span class="sxs-lookup"><span data-stu-id="3edcf-375">Accept-Language</span></span>|<span data-ttu-id="3edcf-376">Cabeçalho para especificar o idioma desejado para nomes traduzidos.</span><span class="sxs-lookup"><span data-stu-id="3edcf-376">Header to specify the desired language for localized names.</span></span> <span data-ttu-id="3edcf-377">Por exemplo, use "pt-BR" para português ou "es" para espanhol.</span><span class="sxs-lookup"><span data-stu-id="3edcf-377">For example, use "en-US" for English or "es" for Spanish.</span></span> <span data-ttu-id="3edcf-378">O idioma padrão (en-US) será retornado se esse cabeçalho não estiver presente.</span><span class="sxs-lookup"><span data-stu-id="3edcf-378">The default language (en-US) will be returned if this header is not present.</span></span>|
|<span data-ttu-id="3edcf-379">**Body**</span><span class="sxs-lookup"><span data-stu-id="3edcf-379">**Body**</span></span>|<span data-ttu-id="3edcf-380">(vazio)</span><span class="sxs-lookup"><span data-stu-id="3edcf-380">(empty)</span></span>||
|<span data-ttu-id="3edcf-381">**Response**</span><span class="sxs-lookup"><span data-stu-id="3edcf-381">**Response**</span></span>|<span data-ttu-id="3edcf-382">Matriz JSON</span><span class="sxs-lookup"><span data-stu-id="3edcf-382">JSON array</span></span>|<span data-ttu-id="3edcf-383">O conteúdo disponível será representado por objetos JSON com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="3edcf-383">The available content will be represented by JSON objects with the following properties:</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-384"><b>ID</b>: indica o guid do tipo de informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="3edcf-384"><b>id</b>: Indicates the guid of the sensitive information type.</span></span></p></li><li><p><span data-ttu-id="3edcf-385"><b>name</b>: o nome amigável do tipo de informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="3edcf-385"><b>name</b>: The friendly name of the sensitive information type.</span></span></p></li></ul>|

#### <a name="sample-request"></a><span data-ttu-id="3edcf-386">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="3edcf-386">Sample request</span></span>

```json
GET {root}/resources/dlpSensitiveTypes?PublisherIdentifier=46b472a7-c68e-4adf-8ade-3db49497518e
Authorization: Bearer eyJ0e...Qa6wg
Accept-Language: {language code} 

```

#### <a name="sample-response"></a><span data-ttu-id="3edcf-387">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="3edcf-387">Sample response</span></span>

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

## <a name="api-throttling"></a><span data-ttu-id="3edcf-388">Limitação de API</span><span class="sxs-lookup"><span data-stu-id="3edcf-388">API throttling</span></span>

<span data-ttu-id="3edcf-389">Cada codificação de fornecedor em relação à API tem uma cota dedicada de solicitação de limitação de 60K por minuto.</span><span class="sxs-lookup"><span data-stu-id="3edcf-389">Each vendor coding against the API has a dedicated quota for request throttling at 60K per minute.</span></span> <span data-ttu-id="3edcf-390">Para obter a cota dedicada, especifique o parâmetro PublisherIdentifier em todas as solicitações.</span><span class="sxs-lookup"><span data-stu-id="3edcf-390">To get the dedicated quota, specify the parameter PublisherIdentifier in all your requests.</span></span> <span data-ttu-id="3edcf-391">Solicitações com o mesmo PublisherIdentifier compartilharão a mesma cota.</span><span class="sxs-lookup"><span data-stu-id="3edcf-391">Requests with the same PublisherIdentifier will share the same quota.</span></span> <span data-ttu-id="3edcf-392">Todas as solicitações sem PublisherIdentifier especificado compartilharão a mesma cota que GUID 00000000-0000-0000-0000-000000000000.</span><span class="sxs-lookup"><span data-stu-id="3edcf-392">All requests without the PublisherIdentifier specified will share the same quota as GUID 00000000-0000-0000-0000-000000000000.</span></span>

<span data-ttu-id="3edcf-393">Se o Office 365 precisar reverter o escalonamento para você em determinados problemas, verifique se a assinatura do locatário cujo GUID é usado como o PublisherIdentifier está atualizada com as informações de contato corretas.</span><span class="sxs-lookup"><span data-stu-id="3edcf-393">If Office 365 needs to reverse escalate to you in certain issues, make sure the subscription for the tenant whose GUID is used as your PublisherIdentifier is current and updated with the correct contact information.</span></span> <span data-ttu-id="3edcf-394">Não há requisitos de assinatura para esse locatário.</span><span class="sxs-lookup"><span data-stu-id="3edcf-394">There is no subscription requirement for this tenant.</span></span>

<span data-ttu-id="3edcf-395">Para clientes que estão desenvolvendo suas próprias soluções usando essa API, é recomendável usar seu próprio GUID de locatário para evitar a concorrência causada por uma cota compartilhada limitada.</span><span class="sxs-lookup"><span data-stu-id="3edcf-395">For customers who are developing their own solutions using this API, we recommend using your own tenant GUID to avoid competition caused by a limited shared quota.</span></span>

> [!NOTE] 
> <span data-ttu-id="3edcf-396">Embora cada fornecedor possa enviar até 60K solicitações por minuto, a Microsoft não pode garantir uma taxa de resposta.</span><span class="sxs-lookup"><span data-stu-id="3edcf-396">Even though each publisher can submit up to 60K requests per minute, Microsoft cannot guarantee a response rate.</span></span> <span data-ttu-id="3edcf-397">A taxa de resposta depende de vários fatores, como o desempenho do sistema do cliente, a capacidade e a velocidade da rede.</span><span class="sxs-lookup"><span data-stu-id="3edcf-397">The response rate depends on various factors, such as client system performance, network capacity, and network speed.</span></span>  <span data-ttu-id="3edcf-398">Um fornecedor pode enviar até 60 mil solicitações por minuto, mas não deve esperar receber respostas a todas as 60 mil solicitações nesse mesmo minuto.</span><span class="sxs-lookup"><span data-stu-id="3edcf-398">A publisher can submit up to 60K requests per minute, but should not expect to receive responses for all 60K requests within that same minute.</span></span> <span data-ttu-id="3edcf-399">Se um fornecedor quiser avaliar o desempenho de um aplicativo cliente, deverá fazer isso em cada ambiente diferente em que planeja executar o aplicativo cliente, pois os resultados variarão entre os ambientes.</span><span class="sxs-lookup"><span data-stu-id="3edcf-399">If anything, should a publisher want to benchmark a client application, they should do so in each different environment that they are planning on running the client application in because results will vary from environment to environment.</span></span>

## <a name="errors"></a><span data-ttu-id="3edcf-400">Erros</span><span class="sxs-lookup"><span data-stu-id="3edcf-400">Errors</span></span>

<span data-ttu-id="3edcf-401">Quando o serviço encontrar um erro, relatará o código de resposta do erro ao chamador, usando a sintaxe de código de erro HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="3edcf-401">When the service encounters an error, it will report the error response code to the caller, using standard HTTP error-code syntax.</span></span> <span data-ttu-id="3edcf-402">.</span><span class="sxs-lookup"><span data-stu-id="3edcf-402"></span></span> <span data-ttu-id="3edcf-403">Informações adicionais são incluídas no corpo da chamada com falha como um único objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="3edcf-403">Additional information is included in the body of the failed call as a single JSON object.</span></span> <span data-ttu-id="3edcf-404">Um exemplo de um corpo de erro JSON completo é mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="3edcf-404">An example of a full JSON error body is shown below:</span></span> 

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
|<span data-ttu-id="3edcf-405">Código</span><span class="sxs-lookup"><span data-stu-id="3edcf-405">Code</span></span>|<span data-ttu-id="3edcf-406">Mensagem</span><span class="sxs-lookup"><span data-stu-id="3edcf-406">Message</span></span>|
|<span data-ttu-id="3edcf-407">AF10001</span><span class="sxs-lookup"><span data-stu-id="3edcf-407">AF10001</span></span>|<span data-ttu-id="3edcf-408">O conjunto de permissões ({0}) enviadas na solicitação não incluía a permissão esperada **ActivityFeed.Read**.</span><span class="sxs-lookup"><span data-stu-id="3edcf-408">The permission set ({0}) sent in the request did not include the expected permission **ActivityFeed.Read**.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-409">{0} = o conjunto de permissões no token de acesso.</span><span class="sxs-lookup"><span data-stu-id="3edcf-409">{0} = the permission set in the access token.</span></span></p></li></ul>|
|<span data-ttu-id="3edcf-410">AF20001</span><span class="sxs-lookup"><span data-stu-id="3edcf-410">AF20001</span></span>|<span data-ttu-id="3edcf-411">Parâmetro ausente: {0}.</span><span class="sxs-lookup"><span data-stu-id="3edcf-411">Missing parameter: {0}.</span></span> <ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-412">{0} = nome do parâmetro ausente.</span><span class="sxs-lookup"><span data-stu-id="3edcf-412">{0} = the name of the missing parameter.</span></span></p></li></ul>|
|<span data-ttu-id="3edcf-413">AF20002</span><span class="sxs-lookup"><span data-stu-id="3edcf-413">AF20002</span></span>|<span data-ttu-id="3edcf-414">Tipo de parâmetro inválido: {0}.</span><span class="sxs-lookup"><span data-stu-id="3edcf-414">Invalid parameter type: {0}.</span></span> <span data-ttu-id="3edcf-415">Tipo esperado: {1}</span><span class="sxs-lookup"><span data-stu-id="3edcf-415">Expected type: {1}</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-416">{0} = nome do parâmetro inválido.</span><span class="sxs-lookup"><span data-stu-id="3edcf-416">{0} = the name of the invalid parameter.</span></span></p></li><li><p><span data-ttu-id="3edcf-417">{1} = tipo esperado (int, datetime, guid).</span><span class="sxs-lookup"><span data-stu-id="3edcf-417">{1} = the expected type (int, datetime, guid).</span></span></p></li></ul>|
|<span data-ttu-id="3edcf-418">AF20003</span><span class="sxs-lookup"><span data-stu-id="3edcf-418">AF20003</span></span>|<span data-ttu-id="3edcf-419">A expiração de {0} fornecida está definida como data e hora anteriores.</span><span class="sxs-lookup"><span data-stu-id="3edcf-419">Expiration {0} provided is set to past date and time.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-420">{0} = a expiração passada na chamada à API.</span><span class="sxs-lookup"><span data-stu-id="3edcf-420">{0} = the expiration passed in the API call.</span></span></p></li></ul>|
|<span data-ttu-id="3edcf-421">AF20010</span><span class="sxs-lookup"><span data-stu-id="3edcf-421">AF20010</span></span>|<span data-ttu-id="3edcf-422">A ID de locatário passada na URL ({0}) não correspondia à ID de locatário passada no token de acesso ({1}).</span><span class="sxs-lookup"><span data-stu-id="3edcf-422">The tenant ID passed in the URL ({0}) does not match the tenant ID passed in the access token ({1}).</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-423">{0} = ID de locatário passada na URL</span><span class="sxs-lookup"><span data-stu-id="3edcf-423">{0} = tenant ID passed in the URL</span></span></p></li><li><p><span data-ttu-id="3edcf-424">{1} = ID de locatário passada no token de acesso</span><span class="sxs-lookup"><span data-stu-id="3edcf-424">{1} = tenant ID passed in the access token</span></span></p></li></ul>|
|<span data-ttu-id="3edcf-425">AF20011</span><span class="sxs-lookup"><span data-stu-id="3edcf-425">AF20011</span></span>|<span data-ttu-id="3edcf-426">A ID de locatário especificada ({0}) não existe no sistema ou foi excluída.</span><span class="sxs-lookup"><span data-stu-id="3edcf-426">Specified tenant ID ({0}) does not exist in the system or has been deleted.</span></span> <ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p>   <span data-ttu-id="3edcf-427">{0} = ID de locatário passada na URL</span><span class="sxs-lookup"><span data-stu-id="3edcf-427">{0} = tenant ID passed in the URL</span></span></p></li></ul>|
|<span data-ttu-id="3edcf-428">AF20012</span><span class="sxs-lookup"><span data-stu-id="3edcf-428">AF20012</span></span>|<span data-ttu-id="3edcf-429">A ID de locatário especificada ({0}) está configurada incorretamente no sistema.</span><span class="sxs-lookup"><span data-stu-id="3edcf-429">Specified tenant ID ({0}) is incorrectly configured in the system.</span></span> <ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p>    <span data-ttu-id="3edcf-430">{0} = ID de locatário passada na URL</span><span class="sxs-lookup"><span data-stu-id="3edcf-430">{0} = tenant ID passed in the URL</span></span></p></li></ul>|
|<span data-ttu-id="3edcf-431">AF20013</span><span class="sxs-lookup"><span data-stu-id="3edcf-431">AF20013</span></span>|<span data-ttu-id="3edcf-432">A ID de locatário passada na URL ({0}) não é um GUID válido.</span><span class="sxs-lookup"><span data-stu-id="3edcf-432">The tenant ID passed in the URL ({0}) is not a valid GUID.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p> <span data-ttu-id="3edcf-433">{0} = ID de locatário passada na URL</span><span class="sxs-lookup"><span data-stu-id="3edcf-433">{0} = tenant ID passed in the URL</span></span></p></li></ul>|
|<span data-ttu-id="3edcf-434">AF20020</span><span class="sxs-lookup"><span data-stu-id="3edcf-434">AF20020</span></span>|<span data-ttu-id="3edcf-435">O tipo de conteúdo especificado não é válido.</span><span class="sxs-lookup"><span data-stu-id="3edcf-435">The specified content type is not valid.</span></span>|
|<span data-ttu-id="3edcf-436">AF20021</span><span class="sxs-lookup"><span data-stu-id="3edcf-436">AF20021</span></span>|<span data-ttu-id="3edcf-437">O ponto de extremidade de webhook {{0}) não pôde ser validado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-437">The webhook endpoint {{0}) could not be validated.</span></span> <span data-ttu-id="3edcf-438">{1}</span><span class="sxs-lookup"><span data-stu-id="3edcf-438"></span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-439">{0} = endereço de webhook.</span><span class="sxs-lookup"><span data-stu-id="3edcf-439">{0} = webhook address.</span></span></p></li><li><p><span data-ttu-id="3edcf-440">{1} = "O ponto de extremidade não retornou HTTP 200."</span><span class="sxs-lookup"><span data-stu-id="3edcf-440">{1} = "The endpoint did not return HTTP 200."</span></span> <span data-ttu-id="3edcf-441">ou "O endereço deve começar com HTTPS."</span><span class="sxs-lookup"><span data-stu-id="3edcf-441">or "The address must begin with HTTPS."</span></span></p></li></ul>|
|<span data-ttu-id="3edcf-442">AF20022</span><span class="sxs-lookup"><span data-stu-id="3edcf-442">AF20022</span></span>|<span data-ttu-id="3edcf-443">Nenhuma assinatura foi encontrada para o tipo de conteúdo específico.</span><span class="sxs-lookup"><span data-stu-id="3edcf-443">No subscription found for the specified content type.</span></span>|
|<span data-ttu-id="3edcf-444">AF20023</span><span class="sxs-lookup"><span data-stu-id="3edcf-444">AF20023</span></span>|<span data-ttu-id="3edcf-445">A assinatura foi desabilitada por {0}.</span><span class="sxs-lookup"><span data-stu-id="3edcf-445">The subscription was disabled by {0}.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-446">{0} = "administrador de locatário" ou "administrador de serviço"</span><span class="sxs-lookup"><span data-stu-id="3edcf-446">{0} = "a tenant admin" or "a service admin"</span></span></p></li></ul>|
|<span data-ttu-id="3edcf-447">AF20030</span><span class="sxs-lookup"><span data-stu-id="3edcf-447">AF20030</span></span>|<span data-ttu-id="3edcf-448">A hora de início e a hora de término devem ser especificadas (ou omitidas) e devem ser separadas por um valor menor ou igual a 24 horas, com a hora de início no máximo sete dias no passado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-448">Start time and end time must both be specified (or both omitted) and must be less than or equal to 24 hours apart, with the start time no more than 7 days in the past.</span></span>|
|<span data-ttu-id="3edcf-449">AF20031</span><span class="sxs-lookup"><span data-stu-id="3edcf-449">AF20031</span></span>|<span data-ttu-id="3edcf-450">Entrada de NextPage inválida: {0}.</span><span class="sxs-lookup"><span data-stu-id="3edcf-450">Invalid nextPage Input: {0}.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-451">{0} = o indicador de próxima página passado na URL</span><span class="sxs-lookup"><span data-stu-id="3edcf-451">{0} = the next page indicator passed in the URL</span></span></p></li></ul>|
|<span data-ttu-id="3edcf-452">AF20050</span><span class="sxs-lookup"><span data-stu-id="3edcf-452">AF20050</span></span>|<span data-ttu-id="3edcf-453">O conteúdo especificado ({0}) não existe.</span><span class="sxs-lookup"><span data-stu-id="3edcf-453">The specified content ({0}) does not exist.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-454">{0} = id de recurso ou URL de recurso</span><span class="sxs-lookup"><span data-stu-id="3edcf-454">{0} = resource id or resource URL</span></span></p></li></ul>|
|<span data-ttu-id="3edcf-455">AF20051</span><span class="sxs-lookup"><span data-stu-id="3edcf-455">AF20051</span></span>|<span data-ttu-id="3edcf-456">O conteúdo solicitado com a chave {0} já expirou.</span><span class="sxs-lookup"><span data-stu-id="3edcf-456">Content requested with the key {0} has already expired.</span></span> <span data-ttu-id="3edcf-457">Conteúdo com mais de sete dias não pode ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="3edcf-457">Content older than 7 days cannot be retrieved.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-458">• {0} = id de recurso ou URL de recurso</span><span class="sxs-lookup"><span data-stu-id="3edcf-458">•    {0} = resource id or resource URL</span></span></p></li></ul>|
|<span data-ttu-id="3edcf-459">AF20052</span><span class="sxs-lookup"><span data-stu-id="3edcf-459">AF20052</span></span>|<span data-ttu-id="3edcf-460">A ID de conteúdo {0} na URL é inválida.</span><span class="sxs-lookup"><span data-stu-id="3edcf-460">Content ID {0} in the URL is invalid.</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-461">{0} = id de recurso ou URL de recurso</span><span class="sxs-lookup"><span data-stu-id="3edcf-461">{0} = resource id or resource URL</span></span></p></li></ul>|
|<span data-ttu-id="3edcf-462">AF20053</span><span class="sxs-lookup"><span data-stu-id="3edcf-462">AF20053</span></span>|<span data-ttu-id="3edcf-463">Apenas um idioma pode estar presente no cabeçalho Accept-Language.</span><span class="sxs-lookup"><span data-stu-id="3edcf-463">Only one language may be present in the Accept-Language header.</span></span>|
|<span data-ttu-id="3edcf-464">AF20054</span><span class="sxs-lookup"><span data-stu-id="3edcf-464">AF20054</span></span>|<span data-ttu-id="3edcf-465">Sintaxe inválida no cabeçalho Accept-Language.</span><span class="sxs-lookup"><span data-stu-id="3edcf-465">Invalid syntax in Accept-Language header.</span></span>|
|<span data-ttu-id="3edcf-466">AF429</span><span class="sxs-lookup"><span data-stu-id="3edcf-466">AF429</span></span>|<span data-ttu-id="3edcf-467">Muitas solicitações.</span><span class="sxs-lookup"><span data-stu-id="3edcf-467">Too many requests.</span></span> <span data-ttu-id="3edcf-468">Method={0}, PublisherId={1}</span><span class="sxs-lookup"><span data-stu-id="3edcf-468">Method={0}, PublisherId={1}</span></span><ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p><span data-ttu-id="3edcf-469">{0} = Método HTTP</span><span class="sxs-lookup"><span data-stu-id="3edcf-469">{0} = HTTP Method</span></span></p></li><li><p><span data-ttu-id="3edcf-470">{1} = GUID de locatário usado como PublisherIdentifier</span><span class="sxs-lookup"><span data-stu-id="3edcf-470">{1} = Tenant GUID used as PublisherIdentifier</span></span></p></li></ul>|
|<span data-ttu-id="3edcf-471">AF50000</span><span class="sxs-lookup"><span data-stu-id="3edcf-471">AF50000</span></span>|<span data-ttu-id="3edcf-472">Erro interno.</span><span class="sxs-lookup"><span data-stu-id="3edcf-472">An internal error occurred.</span></span> <span data-ttu-id="3edcf-473">Repita a solicitação.</span><span class="sxs-lookup"><span data-stu-id="3edcf-473">Retry the request.</span></span>|
