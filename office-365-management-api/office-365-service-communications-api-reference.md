---
ms.TocTitle: Office 365 Service Communications API reference (Preview)
title: Referência da API de comunicações de serviço do Office 365 (visualização)
description: 'Use esta API para acessar os seguintes dados: Obter Serviços, Obter Status Atual, Obter Status Histórico e Obter Mensagens.'
ms.ContentId: d0b9341a-b205-5442-1c20-8fb56407351d
ms.topic: reference (API)
ms.date: ''
localization_priority: Priority
ms.openlocfilehash: 986298b87e2583788dca9b11f288743ce5f96b60
ms.sourcegitcommit: 784b581a699c6d0ab7939ea621d5ecbea71925ea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2019
ms.locfileid: "35924809"
---
# <a name="office-365-service-communications-api-reference-preview"></a><span data-ttu-id="a8dfe-103">Referência da API de comunicações de serviço do Office 365 (visualização)</span><span class="sxs-lookup"><span data-stu-id="a8dfe-103">Office 365 Service Communications API reference (preview)</span></span>

> [!NOTE] 
> <span data-ttu-id="a8dfe-104">Esta documentação aborda os recursos que estão atualmente na versão prévia.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-104">This documentation covers features that are currently in preview.</span></span>

<span data-ttu-id="a8dfe-105">Você pode usar o API de Comunicações do Serviço do Office 365 V2 para acessar os seguintes dados:</span><span class="sxs-lookup"><span data-stu-id="a8dfe-105">You can use the Office 365 Service Communications API V2 to access the following data:</span></span>

- <span data-ttu-id="a8dfe-106">**Obter Serviços**: obtenha a lista de serviços assinados.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-106">**Get Services**: Get the list of subscribed services.</span></span>
    
- <span data-ttu-id="a8dfe-107">**Obter Status Atual**: obtenha uma visualização em tempo real dos eventos de manutenção e dos incidentes de serviço em andamento e atuais</span><span class="sxs-lookup"><span data-stu-id="a8dfe-107">**Get Current Status**: Get a real-time view of current and ongoing service incidents and maintenance events</span></span>
    
- <span data-ttu-id="a8dfe-108">**Obter Status Histórico**: obtenha uma visualização do histórico de integridade do serviço, incluindo incidentes de serviço e eventos de manutenção.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-108">**Get Historical Status**: Get a historical view of service health, including service incidents and maintenance events.</span></span>
    
- <span data-ttu-id="a8dfe-109">**Obter Mensagens**: comunicações do Centro de Mensagens, Manutenção Planejada e Localizar Incidente.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-109">**Get Messages**: Find Incident, Planned Maintenance, and Message Center communications.</span></span>
    
<span data-ttu-id="a8dfe-110">Atualmente, a API de Comunicações do Serviço do Office 365 contém os dados dos seguintes serviços: Dynamics CRM, Dynamics Marketing, Exchange Online, Proteção do Exchange Online, Identity Service, Gerenciamento de Dispositivo Móvel, Centro de Administração do Parceiro do Office 365, OneDrive for Business, Parature, OneDrive for Business, Power BI para Office 365, Serviço de Gerenciamento de Direitos, SharePoint Online, Administrador do SHD, Skype for Business, Envolvimento Social e Yammer Enterprise.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-110">Currently, the Office 365 Service Communications API contains data for the following services: Dynamics CRM, Dynamics Marketing, Exchange Online, Exchange Online Protection, Identity Service, Mobile Device Management, Office 365 Partner Admin Center, OneDrive for Business, Parature, OneDrive for Business, Power BI for Office 365, Rights Management Service, SharePoint Online, SHD Admin, Skype for Business, Social Engagement, and Yammer Enterprise.</span></span>

## <a name="the-fundamentals"></a><span data-ttu-id="a8dfe-111">Os conceitos básicos</span><span class="sxs-lookup"><span data-stu-id="a8dfe-111">The fundamentals</span></span>

<span data-ttu-id="a8dfe-112">A URL raiz da API inclui um identificador de locatário que atribui operações a um único locatário:</span><span class="sxs-lookup"><span data-stu-id="a8dfe-112">The root URL of the API includes a tenant identifier that scopes the operations to a single tenant:</span></span>

```http
https://manage.office.com/api/v1.0/{tenant_identifier}/ServiceComms/{operation}
```

<span data-ttu-id="a8dfe-113">A **API de Comunicações do Serviço do Office 365** é um serviço do REST que permite desenvolver soluções usando qualquer linguagem da web e ambiente de hospedagem compatível com os certificados HTTPS e X.509.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-113">The **Office 365 Service Communications API** is a REST service that allows you to develop solutions using any web language and hosting environment that supports HTTPS and X.509 certificates.</span></span> <span data-ttu-id="a8dfe-114">A API depende do **Microsoft Azure Active Directory** e do protocolo **OAuth2** para autorização e autenticação.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-114">The API relies on **Microsoft Azure Active Directory** and the **OAuth2** protocol for authentication and authorization.</span></span> <span data-ttu-id="a8dfe-115">Para acessar a API do seu aplicativo, é preciso primeiro registrá-la no Azure AD e configurá-la com permissões no escopo apropriado.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-115">To access the API from your application, you'll need to first register it in Azure AD and configure it with permissions at the appropriate scope.</span></span> <span data-ttu-id="a8dfe-116">Isso permitirá que seu aplicativo solicite os tokens de acesso do OAuth2 necessários para chamar a API.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-116">This will enable your application to request OAuth2 access tokens necessary for calling the API.</span></span> <span data-ttu-id="a8dfe-117">Saiba mais sobre como registrar e configurar um aplicativo no Azure AD em [Introdução às APIs de Gerenciamento do Office 365](get-started-with-office-365-management-apis.md).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-117">You can find more information about registering and configuring an application in Azure AD at [Office 365 Management APIs getting started](get-started-with-office-365-management-apis.md).</span></span>

<span data-ttu-id="a8dfe-118">Todas as solicitações de API exigem um cabeçalho HTTP de Autorização com um token de acesso de JWT do OAuth2 obtido do Azure AD contendo a solicitação **ServiceHealth.Read** e o identificador do locatário deve corresponder ao identificador do locatário na URL raiz.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-118">All API requests require an Authorization HTTP header that has a valid OAuth2 JWT access token obtained from Azure AD that contains the **ServiceHealth.Read** claim; and the tenant identifier must match the tenant identifier in the root URL.</span></span>

```json
Authorization: Bearer {OAuth2 token}
```

### <a name="request-headers"></a><span data-ttu-id="a8dfe-119">Cabeçalhos de solicitação</span><span class="sxs-lookup"><span data-stu-id="a8dfe-119">Request headers</span></span>

<span data-ttu-id="a8dfe-120">Estes são os cabeçalhos de solicitação suportados para todas as operações da API de Comunicações do Serviço do Office 365.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-120">These are the supported request headers for all Office 365 Service Communications API operations.</span></span>

|<span data-ttu-id="a8dfe-121">Cabeçalho</span><span class="sxs-lookup"><span data-stu-id="a8dfe-121">Header</span></span>|<span data-ttu-id="a8dfe-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8dfe-122">Description</span></span>|
|:-----|:-----|
|<span data-ttu-id="a8dfe-123">**Aceitação (opcional)**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-123">**Accept (Optional)**</span></span>|<span data-ttu-id="a8dfe-124">Estas são representações aceitas da resposta:</span><span class="sxs-lookup"><span data-stu-id="a8dfe-124">The following are acceptable representations for the response:</span></span><br/><span data-ttu-id="a8dfe-125">**application/json;odata.metadata=full**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-125">**application/json;odata.metadata=full**</span></span><br/><span data-ttu-id="a8dfe-126">**application/json;odata.metadata=minimal**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-126">**application/json;odata.metadata=minimal**</span></span><br/><span data-ttu-id="a8dfe-127">[O padrão se o cabeçalho não for especificado] **application/json;odata.metadata=none**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-127">[The default if header not specified] **application/json;odata.metadata=none**</span></span>|
|<span data-ttu-id="a8dfe-128">**Autorização (obrigatória)**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-128">**Authorization (Required)**</span></span>|<span data-ttu-id="a8dfe-129">Token de autorização (Token do Azure AD do JWT do portador) para a solicitação.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-129">Authorization token (Bearer JWT Azure AD Token) for the request.</span></span>|


<br/>

### <a name="response-headers"></a><span data-ttu-id="a8dfe-130">Cabeçalhos de resposta</span><span class="sxs-lookup"><span data-stu-id="a8dfe-130">Response headers</span></span>

<span data-ttu-id="a8dfe-131">Estes são os cabeçalhos de respostas retornados para todas as operações da API de Comunicações do Serviço do Office 365:</span><span class="sxs-lookup"><span data-stu-id="a8dfe-131">These are the response headers returned for all Office 365 Service Communications API operations:</span></span>

|<span data-ttu-id="a8dfe-132">Cabeçalho</span><span class="sxs-lookup"><span data-stu-id="a8dfe-132">Header</span></span>|<span data-ttu-id="a8dfe-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8dfe-133">Description</span></span>|
|:-----|:-----|
|<span data-ttu-id="a8dfe-134">**Content-Length**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-134">**Content-Length**</span></span>|<span data-ttu-id="a8dfe-135">O comprimento do corpo da resposta.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-135">The length of the response body.</span></span>|
|<span data-ttu-id="a8dfe-136">**Content-Type**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-136">**Content-Type**</span></span>|<span data-ttu-id="a8dfe-137">Representação da resposta:</span><span class="sxs-lookup"><span data-stu-id="a8dfe-137">Representation of the response:</span></span><br/><span data-ttu-id="a8dfe-138">**application/json**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-138">**application/json**</span></span><br/><span data-ttu-id="a8dfe-139">**application/json;odata.metadata=full**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-139">**application/json;odata.metadata=full**</span></span><br/><span data-ttu-id="a8dfe-140">**application/json;odata.metadata=minimal**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-140">**application/json;odata.metadata=minimal**</span></span><br/><span data-ttu-id="a8dfe-141">**application/json;odata.metadata=none**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-141">**application/json;odata.metadata=none**</span></span><br/><span data-ttu-id="a8dfe-142">**odata.streaming=true**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-142">**odata.streaming=true**</span></span>|
|<span data-ttu-id="a8dfe-143">**Cache-Control**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-143">**Cache-Control**</span></span>|<span data-ttu-id="a8dfe-144">Usado para especificar as diretivas que todos os mecanismos de cache devem seguir ao longo da cadeia de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-144">Used to specify directives that all caching mechanisms along the request/response chain must obey.</span></span>|
|<span data-ttu-id="a8dfe-145">**Pragma**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-145">**Pragma**</span></span>|<span data-ttu-id="a8dfe-146">Comportamentos específicos de implementação.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-146">Implementation-specific behaviors.</span></span>|
|<span data-ttu-id="a8dfe-147">**Expires**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-147">**Expires**</span></span>|<span data-ttu-id="a8dfe-148">Quando o cliente deve fazer o recurso expirar.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-148">When the client should make the resource expire.</span></span>|
|<span data-ttu-id="a8dfe-149">**X-Activity-Id**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-149">**X-Activity-Id**</span></span>|<span data-ttu-id="a8dfe-150">O ID de atividade gerado pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-150">The server-generated activity Id.</span></span>|
|<span data-ttu-id="a8dfe-151">**OData-Version**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-151">**OData-Version**</span></span>|<span data-ttu-id="a8dfe-152">O OData Versão (4.0) com suporte.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-152">The supported OData Version (4.0).</span></span>|
|<span data-ttu-id="a8dfe-153">**Date**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-153">**Date**</span></span>|<span data-ttu-id="a8dfe-154">A data em UTC de quando a resposta foi enviada do servidor.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-154">The date in UTC when the response was sent from the server.</span></span>|
|<span data-ttu-id="a8dfe-155">**X-Time-Taken**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-155">**X-Time-Taken**</span></span>|<span data-ttu-id="a8dfe-156">O tempo que foi necessário para gerar a resposta (ms).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-156">The time it took to generate the response (ms).</span></span>|
|<span data-ttu-id="a8dfe-157">**X-Instance-Name**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-157">**X-Instance-Name**</span></span>|<span data-ttu-id="a8dfe-158">O identificador da instância do Azure usado para gerar a resposta (para fins de depuração).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-158">The identifier of the Azure instance used to generate the response (for debugging purposes).</span></span>|
|<span data-ttu-id="a8dfe-159">**Server**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-159">**Server**</span></span>|<span data-ttu-id="a8dfe-160">O servidor usado para gerar a resposta (para fins de depuração).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-160">The server used to generate the response (for debugging purposes).</span></span>|
|<span data-ttu-id="a8dfe-161">**X-ASPNET-Version**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-161">**X-ASPNET-Version**</span></span>|<span data-ttu-id="a8dfe-162">A versão do ASP.Net usada pelo servidor que gerou a resposta (para fins de depuração).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-162">The version of ASP.Net used by the server that generated the response (for debugging purposes).</span></span>|
|<span data-ttu-id="a8dfe-163">**X-Powered-By**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-163">**X-Powered-By**</span></span>|<span data-ttu-id="a8dfe-164">As tecnologias usadas no servidor que gerou a resposta (para fins de depuração).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-164">The technologies used in the server that generated the response (for debugging purposes).</span></span>|
|||

<br/>

<span data-ttu-id="a8dfe-165">Estas são as operações da API de Comunicações do Serviço do Office 365.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-165">Following are the Office 365 Service Communications API operations.</span></span>


## <a name="get-services"></a><span data-ttu-id="a8dfe-166">Obter Serviços</span><span class="sxs-lookup"><span data-stu-id="a8dfe-166">Get Services</span></span>

<span data-ttu-id="a8dfe-167">Retorna a lista de serviços assinados.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-167">Returns the list of subscribed services.</span></span>

||<span data-ttu-id="a8dfe-168">Serviço</span><span class="sxs-lookup"><span data-stu-id="a8dfe-168">Service</span></span>|<span data-ttu-id="a8dfe-169">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8dfe-169">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="a8dfe-170">**Caminho**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-170">**Path**</span></span>| `/Services`||
|<span data-ttu-id="a8dfe-171">**Query-option**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-171">**Query-option**</span></span>|<span data-ttu-id="a8dfe-172">$select</span><span class="sxs-lookup"><span data-stu-id="a8dfe-172">$select</span></span>|<span data-ttu-id="a8dfe-173">Escolha um subconjunto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-173">Pick a subset of properties.</span></span>|
|<span data-ttu-id="a8dfe-174">**Resposta**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-174">**Response**</span></span>|<span data-ttu-id="a8dfe-175">Lista de entidades "Service"</span><span class="sxs-lookup"><span data-stu-id="a8dfe-175">List of "Service" entities</span></span>|<span data-ttu-id="a8dfe-176">A entidade "Service" contém "Id" (cadeia de caracteres), "DisplayName" (cadeia de caracteres) e "FeatureNames" (lista de cadeias de caracteres).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-176">"Service" entity contains "Id" (String), "DisplayName" (String), and "FeatureNames" (list of Strings).</span></span>|
||||

### <a name="sample-request"></a><span data-ttu-id="a8dfe-177">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="a8dfe-177">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/Services 
Authorization: Bearer {AAD_Bearer_JWT_Token}

```

### <a name="sample-response"></a><span data-ttu-id="a8dfe-178">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="a8dfe-178">Sample response</span></span>

```json
{
    "value": [
        {
            "Id": "Exchange",
            "DisplayName": "Exchange Online",
            "FeatureNames": [
                "Sign-in",
                "E-Mail and calendar access",
                "E-Mail timely delivery",
                "Management and Provisioning",
                "Voice mail"
            ]
        },
        {
            "Id": "Lync",
            "DisplayName": "Lync Online",
            "FeatureNames": [
                "Audio and Video",
                "Federation",
                "Management and Provisioning",
                "Sign-In",
                "All Features",
                "Dial-In Conferencing",
                "Online Meetings",
                "Instant Messaging",
                "Presence",
                "Mobility"
            ]
        }
    ]
}
```


## <a name="get-current-status"></a><span data-ttu-id="a8dfe-179">Obter Status Atual</span><span class="sxs-lookup"><span data-stu-id="a8dfe-179">Get Current Status</span></span>

<span data-ttu-id="a8dfe-180">Retorna o status do serviço das últimas 24 horas.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-180">Returns the status of the service over the previous 24 hours.</span></span>

> [!NOTE] 
> <span data-ttu-id="a8dfe-181">A resposta do serviço conterá o status e quaisquer incidentes ocorridos dentro das últimas 24 horas.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-181">The service response will contain the status and any incidents within the previous 24 hours.</span></span> <span data-ttu-id="a8dfe-182">O valor StatusDate ou StatusTime retornado estará exatamente 24 horas no passado.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-182">The StatusDate or StatusTime value returned will be exactly 24 hours in the past.</span></span> <span data-ttu-id="a8dfe-183">Para obter a última atualização para um determinado incidente, use a funcionalidade de Obter Mensagens e leia o valor de LastUpdatedTime no registro de resposta que corresponde à ID do incidente.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-183">To get the last update for a particular incident, use the Get Messages functionality and read the LastUpdatedTime value from the response record that matches your incident ID.</span></span> <br/>

<br/>

||<span data-ttu-id="a8dfe-184">Serviço</span><span class="sxs-lookup"><span data-stu-id="a8dfe-184">Service</span></span>|<span data-ttu-id="a8dfe-185">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8dfe-185">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="a8dfe-186">**Caminho**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-186">**Path**</span></span>| `/CurrentStatus`||
|<span data-ttu-id="a8dfe-187">**Filtro**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-187">**Filter**</span></span>|<span data-ttu-id="a8dfe-188">Carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="a8dfe-188">Workload</span></span>|<span data-ttu-id="a8dfe-189">Filtrar por carga de trabalho (cadeia de caracteres, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-189">Filter by workload (String, default: all).</span></span>|
|<span data-ttu-id="a8dfe-190">**Query-option**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-190">**Query-option**</span></span>|<span data-ttu-id="a8dfe-191">$select</span><span class="sxs-lookup"><span data-stu-id="a8dfe-191">$select</span></span>|<span data-ttu-id="a8dfe-192">Escolha um subconjunto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-192">Pick a subset of properties.</span></span>|
|<span data-ttu-id="a8dfe-193">**Resposta**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-193">**Response**</span></span>|<span data-ttu-id="a8dfe-194">Lista de entidades "WorkloadStatus".</span><span class="sxs-lookup"><span data-stu-id="a8dfe-194">List of "WorkloadStatus" entities.</span></span>|<span data-ttu-id="a8dfe-195">A entidade "WorkloadStatus" contém "Id" (cadeia de caracteres), "Workload" (cadeia de caracteres), "StatusTime"(DateTimeOffset), "WorkloadDisplayName" (cadeia de caracteres), "Status" (cadeia de caracteres), "IncidentIds" (lista de cadeias de caracteres) e FeatureGroupStatusCollection (lista de "FeatureStatus").</span><span class="sxs-lookup"><span data-stu-id="a8dfe-195">"WorkloadStatus" entity contains "Id" (String), "Workload" (String), "StatusTime"(DateTimeOffset), "WorkloadDisplayName" (String), "Status" (String), "IncidentIds" (list of Strings), and FeatureGroupStatusCollection (list of "FeatureStatus").</span></span><br/><br/><span data-ttu-id="a8dfe-196">A entidade "FeatureStatus" contém "Feature" (cadeia de caracteres), "FeatureGroupDisplayName" (cadeia de cadeia de caracteres) e "FeatureStatus" (cadeia de caracteres).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-196">"FeatureStatus" entity contains "Feature" (String), "FeatureGroupDisplayName" (String), and "FeatureStatus" (String).</span></span>|
||||

### <a name="sample-request"></a><span data-ttu-id="a8dfe-197">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="a8dfe-197">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/CurrentStatus
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

### <a name="sample-response"></a><span data-ttu-id="a8dfe-198">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="a8dfe-198">Sample response</span></span>

```json
{
    "value": [
        {
            "Id": "Exchange",
            "Workload": "Exchange",
            "StatusDate": "2015-04-11T00:00:00Z",
            "WorkloadDisplayName": "Exchange Online",
            "Status": "ServiceOperational",
            "IncidentIds": [],
            "FeatureGroupStatusCollection": [
                {
                    "Feature": "Signin",
                    "FeatureGroupDisplayName": "Sign-in",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Access",
                    "FeatureGroupDisplayName": "E-Mail and calendar access",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Delivery",
                    "FeatureGroupDisplayName": "E-Mail timely delivery",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Provisioning",
                    "FeatureGroupDisplayName": "Management and Provisioning",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "UnifiedMessaging",
                    "FeatureGroupDisplayName": "Voice mail",
                    "FeatureStatus": "ServiceOperational"
                }
            ]
        },
        {
            "Id": "Lync",
            "Workload": "Lync",
            "StatusDate": "2015-04-11T00:00:00Z",
            "WorkloadDisplayName": "Lync Online",
            "Status": "ServiceOperational",
            "IncidentIds": [],
            "FeatureGroupStatusCollection": [
                {
                    "Feature": "AudioVideo",
                    "FeatureGroupDisplayName": "Audio and Video",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Federation",
                    "FeatureGroupDisplayName": "Federation",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "ManagementandProvisioning",
                    "FeatureGroupDisplayName": "Management and Provisioning",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Sign-In",
                    "FeatureGroupDisplayName": "Sign-In",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "All",
                    "FeatureGroupDisplayName": "All Features",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "DialInConferencing",
                    "FeatureGroupDisplayName": "Dial-In Conferencing",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "OnlineMeetings",
                    "FeatureGroupDisplayName": "Online Meetings",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "InstantMessaging",
                    "FeatureGroupDisplayName": "Instant Messaging",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Presence",
                    "FeatureGroupDisplayName": "Presence",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Mobility",
                    "FeatureGroupDisplayName": "Mobility",
                    "FeatureStatus": "ServiceOperational"
                }
            ]
        }
    ]
}
```

### <a name="status-definitions"></a><span data-ttu-id="a8dfe-199">Definições de status</span><span class="sxs-lookup"><span data-stu-id="a8dfe-199">Status definitions</span></span>

<span data-ttu-id="a8dfe-200">As definições de status incluem os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="a8dfe-200">The status definitions include the following values:</span></span> 

- <span data-ttu-id="a8dfe-201">Investigando</span><span class="sxs-lookup"><span data-stu-id="a8dfe-201">Investigating</span></span>
- <span data-ttu-id="a8dfe-202">ServiceDegradation</span><span class="sxs-lookup"><span data-stu-id="a8dfe-202">ServiceDegradation</span></span>
- <span data-ttu-id="a8dfe-203">ServiceInterruption</span><span class="sxs-lookup"><span data-stu-id="a8dfe-203">ServiceInterruption</span></span> 
- <span data-ttu-id="a8dfe-204">RestoringService</span><span class="sxs-lookup"><span data-stu-id="a8dfe-204">RestoringService</span></span>
- <span data-ttu-id="a8dfe-205">ExtendedRecovery</span><span class="sxs-lookup"><span data-stu-id="a8dfe-205">ExtendedRecovery</span></span>
- <span data-ttu-id="a8dfe-206">ServiceRestored</span><span class="sxs-lookup"><span data-stu-id="a8dfe-206">ServiceRestored</span></span>
- <span data-ttu-id="a8dfe-207">PostIncidentReportPublished</span><span class="sxs-lookup"><span data-stu-id="a8dfe-207">PostIncidentReportPublished</span></span> 
- <span data-ttu-id="a8dfe-208">VerifyingService</span><span class="sxs-lookup"><span data-stu-id="a8dfe-208">VerifyingService</span></span>
- <span data-ttu-id="a8dfe-209">ServiceOperational</span><span class="sxs-lookup"><span data-stu-id="a8dfe-209">ServiceOperational</span></span>

<span data-ttu-id="a8dfe-210">Para obter uma lista atualizada e uma descrição dessas definições de status, confira [Como verificar a integridade do serviço do Office 365](https://docs.microsoft.com/office365/enterprise/view-service-health#status-definitions).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-210">For an up-to-date list and description of these status definitions, see [How to check Office 365 service health](https://docs.microsoft.com/office365/enterprise/view-service-health#status-definitions).</span></span>


## <a name="get-historical-status"></a><span data-ttu-id="a8dfe-211">Obter Status Histórico</span><span class="sxs-lookup"><span data-stu-id="a8dfe-211">Get Historical Status</span></span>

<span data-ttu-id="a8dfe-212">Retorna o status histórico do serviço, por dia, durante um determinado intervalo.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-212">Returns the historical status of the service, by day, over a certain time range.</span></span>

||<span data-ttu-id="a8dfe-213">Serviço</span><span class="sxs-lookup"><span data-stu-id="a8dfe-213">Service</span></span>|<span data-ttu-id="a8dfe-214">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8dfe-214">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="a8dfe-215">**Caminho**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-215">**Path**</span></span>| `/HistoricalStatus`||
|<span data-ttu-id="a8dfe-216">**Filtros**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-216">**Filters**</span></span>|<span data-ttu-id="a8dfe-217">Carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="a8dfe-217">Workload</span></span>|<span data-ttu-id="a8dfe-218">Filtrar por carga de trabalho (cadeia de caracteres, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-218">Filter by workload (String, default: all).</span></span>|
||<span data-ttu-id="a8dfe-219">StatusTime</span><span class="sxs-lookup"><span data-stu-id="a8dfe-219">StatusTime</span></span>|<span data-ttu-id="a8dfe-220">Filtrar por dias maiores que StatusTime (DateTimeOffset, padrão: ge CurrentTime, 7 dias).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-220">Filter by days greater than StatusTime (DateTimeOffset, default: ge CurrentTime - 7 days).</span></span>|
|<span data-ttu-id="a8dfe-221">**Query-option**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-221">**Query-option**</span></span>|<span data-ttu-id="a8dfe-222">$select</span><span class="sxs-lookup"><span data-stu-id="a8dfe-222">$select</span></span>|<span data-ttu-id="a8dfe-223">Escolha um subconjunto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-223">Pick a subset of properties.</span></span>|
|<span data-ttu-id="a8dfe-224">**Resposta**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-224">**Response**</span></span>|<span data-ttu-id="a8dfe-225">Lista de entidades "WorkloadStatus".</span><span class="sxs-lookup"><span data-stu-id="a8dfe-225">List of "WorkloadStatus" entities.</span></span>|<span data-ttu-id="a8dfe-226">A entidade "WorkloadStatus" contém "Id" (cadeia de caracteres), "Workload" (cadeia de caracteres), "StatusTime"(DateTimeOffset), "WorkloadDisplayName" (cadeia de caracteres), "Status" (cadeia de caracteres), "IncidentIds" (lista de cadeias de caracteres) e FeatureGroupStatusCollection (lista de "FeatureStatus").</span><span class="sxs-lookup"><span data-stu-id="a8dfe-226">"WorkloadStatus" entity contains "Id" (String), "Workload" (String), "StatusTime"(DateTimeOffset), "WorkloadDisplayName" (String), "Status" (String), "IncidentIds" (list of Strings), and FeatureGroupStatusCollection (list of "FeatureStatus").</span></span><br/><br/><span data-ttu-id="a8dfe-227">A entidade "FeatureStatus" contém "Feature" (cadeia de caracteres), "FeatureGroupDisplayName" (cadeia de cadeia de caracteres) e "FeatureStatus" (cadeia de caracteres).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-227">"FeatureStatus" entity contains "Feature" (String), "FeatureGroupDisplayName" (String), and "FeatureStatus" (String).</span></span>|
||||

### <a name="sample-request"></a><span data-ttu-id="a8dfe-228">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="a8dfe-228">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/HistoricalStatus
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

### <a name="sample-response"></a><span data-ttu-id="a8dfe-229">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="a8dfe-229">Sample response</span></span>

```json
{
    "value": [
        {
            "Id": "Exchange",
            "Workload": "Exchange",
            "StatusDate": "2015-04-11T00:00:00Z",
            "WorkloadDisplayName": "Exchange Online",
            "Status": "ServiceOperational",
            "IncidentIds": [],
            "FeatureGroupStatusCollection": [
                {
                    "Feature": "Signin",
                    "FeatureGroupDisplayName": "Sign-in",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Access",
                    "FeatureGroupDisplayName": "E-Mail and calendar access",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Delivery",
                    "FeatureGroupDisplayName": "E-Mail timely delivery",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Provisioning",
                    "FeatureGroupDisplayName": "Management and Provisioning",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "UnifiedMessaging",
                    "FeatureGroupDisplayName": "Voice mail",
                    "FeatureStatus": "ServiceOperational"
                }
            ]
        },
        {
            "Id": "Exchange",
            "Workload": "Exchange",
            "StatusDate": "2015-04-10T00:00:00Z",
            "WorkloadDisplayName": "Exchange Online",
            "Status": "InformationAvailable",
            "IncidentIds": [
                "EX20870"
            ],
            "FeatureGroupStatusCollection": [
                {
                    "Feature": "Signin",
                    "FeatureGroupDisplayName": "Sign-in",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Access",
                    "FeatureGroupDisplayName": "E-Mail and calendar access",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Delivery",
                    "FeatureGroupDisplayName": "E-Mail timely delivery",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "Provisioning",
                    "FeatureGroupDisplayName": "Management and Provisioning",
                    "FeatureStatus": "ServiceOperational"
                },
                {
                    "Feature": "UnifiedMessaging",
                    "FeatureGroupDisplayName": "Voice mail",
                    "FeatureStatus": "InformationAvailable"
                }
            ]
        }
    ]
}
```

## <a name="get-messages"></a><span data-ttu-id="a8dfe-230">Obter Mensagens</span><span class="sxs-lookup"><span data-stu-id="a8dfe-230">Get Messages</span></span>

<span data-ttu-id="a8dfe-231">Retorna as mensagens sobre o serviço de um determinado intervalo de tempo.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-231">Returns the messages about the service over a certain time range.</span></span> <span data-ttu-id="a8dfe-232">Use o tipo de filtro para filtrar as mensagens por "Centro de Mensagens", "Manutenção Planejada" ou "Incidente de Serviço".</span><span class="sxs-lookup"><span data-stu-id="a8dfe-232">Use the type filter to filter for "Service Incident", "Planned Maintenance", or "Message Center" messages.</span></span>

||<span data-ttu-id="a8dfe-233">Serviço</span><span class="sxs-lookup"><span data-stu-id="a8dfe-233">Service</span></span>|<span data-ttu-id="a8dfe-234">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8dfe-234">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="a8dfe-235">**Caminho**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-235">**Path**</span></span>| `/Messages`||
|<span data-ttu-id="a8dfe-236">**Filtros**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-236">**Filters**</span></span>|<span data-ttu-id="a8dfe-237">Carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="a8dfe-237">Workload</span></span>|<span data-ttu-id="a8dfe-238">Filtrar por carga de trabalho (cadeia de caracteres, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-238">Filter by workload (String, default: all).</span></span>|
||<span data-ttu-id="a8dfe-239">StartTime</span><span class="sxs-lookup"><span data-stu-id="a8dfe-239">StartTime</span></span>|<span data-ttu-id="a8dfe-240">Filtrar por Hora de Início (DateTimeOffset, padrão: ge CurrentTime – 7 dias).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-240">Filter by Start Time (DateTimeOffset, default: ge CurrentTime - 7 days).</span></span>|
||<span data-ttu-id="a8dfe-241">EndTime</span><span class="sxs-lookup"><span data-stu-id="a8dfe-241">EndTime</span></span>|<span data-ttu-id="a8dfe-242">Filtrar por Hora de Término (DateTimeOffset, padrão: le CurrentTime).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-242">Filter by End Time (DateTimeOffset, default: le CurrentTime).</span></span>|
||<span data-ttu-id="a8dfe-243">MessageType</span><span class="sxs-lookup"><span data-stu-id="a8dfe-243">MessageType</span></span>|<span data-ttu-id="a8dfe-244">Filtrar por Tipo de Mensagem (Cadeia de caracteres, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-244">Filter by MessageType (String, default: all).</span></span>|
||<span data-ttu-id="a8dfe-245">ID</span><span class="sxs-lookup"><span data-stu-id="a8dfe-245">ID</span></span>|<span data-ttu-id="a8dfe-246">Filtrar por ID (Cadeia de caracteres, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-246">Filter by ID (String, default: all).</span></span>|
|<span data-ttu-id="a8dfe-247">**Query-option**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-247">**Query-option**</span></span>|<span data-ttu-id="a8dfe-248">$select</span><span class="sxs-lookup"><span data-stu-id="a8dfe-248">$select</span></span>|<span data-ttu-id="a8dfe-249">Escolha um subconjunto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-249">Pick a subset of properties.</span></span>|
||<span data-ttu-id="a8dfe-250">$top</span><span class="sxs-lookup"><span data-stu-id="a8dfe-250">$top</span></span>|<span data-ttu-id="a8dfe-251">Escolha o número máximo de resultados (padrão e máx. $top=100).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-251">Pick the top number of results (default and max $top=100).</span></span>|
||<span data-ttu-id="a8dfe-252">$skip</span><span class="sxs-lookup"><span data-stu-id="a8dfe-252">$skip</span></span>|<span data-ttu-id="a8dfe-253">Ignorar o número de resultados (padrão: $skip=0).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-253">Skip number of results (default: $skip=0).</span></span>|
|<span data-ttu-id="a8dfe-254">**Resposta**</span><span class="sxs-lookup"><span data-stu-id="a8dfe-254">**Response**</span></span>|<span data-ttu-id="a8dfe-255">Lista de entidades de "Mensagem".</span><span class="sxs-lookup"><span data-stu-id="a8dfe-255">List of "Message" entities.</span></span>|<span data-ttu-id="a8dfe-256">A entidade "Message" contém "Id" (cadeia de caracteres), "StartTime" (DateTimeOffset), "EndTime" (DateTimeOffset), "Status" (cadeia de caracteres), "Messages" (lista da entidade "MessagHistory"), "LastUpdatedTime" (DateTimeOffset), "Workload" (cadeia de caracteres), "WorkloadDisplayName" (cadeia de caracteres), "Feature" (cadeia de caracteres), "FeatureDisplayName" (cadeia de caracteres), "MessageType" (Enum, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-256">"Message" entity contains "Id" (String), "StartTime" (DateTimeOffset), "EndTime" (DateTimeOffset), "Status" (String), "Messages" (list of "MessageHistory" entity), "LastUpdatedTime" (DateTimeOffset), "Workload" (String), "WorkloadDisplayName" (String), "Feature" (String), "FeatureDisplayName" (String), "MessageType" (Enum, default: all).</span></span><br/><br/><span data-ttu-id="a8dfe-257">A entidade "MessageHistory" contém "PublishedTime" (DateTimeOffset), "MessageText" (cadeia de caracteres).</span><span class="sxs-lookup"><span data-stu-id="a8dfe-257">"MessageHistory" entity contains "PublishedTime" (DateTimeOffset), "MessageText" (String).</span></span>|
||||

### <a name="sample-request"></a><span data-ttu-id="a8dfe-258">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="a8dfe-258">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/Messages
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

### <a name="sample-response"></a><span data-ttu-id="a8dfe-259">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="a8dfe-259">Sample response</span></span>

```json
{
 {
    "value": [
        {
            "Id": "EX20119",
            "Name": "EX20119",
            "Title": null,
            "StartTime": "2015-04-01T22:25:00Z",
            "EndTime": "2015-04-07T21:48:00Z",
            "Status": "Service restored",
            "Messages": [
                {
                    "PublishedTime": "2015-04-01T22:34:28.76Z",
                    "MessageText": "Current Status: Engineers are investigating an issue in which some customers may be experiencing problems accessing or using Exchange Online services or features. This event is actively being investigated. More information will be provided shortly."
                },
                {
                    "PublishedTime": "2015-04-03T18:45:32.56Z",
                    "MessageText": "Current Status: Engineers are implementing a fix within the affected infrastructure to remediate Exchange Online archive access issues. \n\nUser Experience: Affected users are unable to access online archives when using Outlook Web App (OWA). As a workaround, users may be able to access online archives via the Outlook client.\n\nCustomer Impact: Customer impact appears to be limited at this time. This issue only affects hybrid customers.\n\nPreliminary Root Cause: As part of our ongoing work, an updated certificate was deployed to the infrastructure; however, a caching issue has caused the infrastructure to use an expired certificate which is causing archive access issues.  \n\nNext Update by: Monday, April 6, 2015, at 9:00 PM UTC\n"
                },
                {
                    "PublishedTime": "2015-04-06T21:17:34.007Z",
                    "MessageText": "Current Status: Deployment of the fix is almost complete. Engineers are monitoring service health to ensure the issue has been remediated. \n\nUser Experience: Affected users are unable to access online archives when using Outlook Web App (OWA). As a workaround, users may be able to access online archives via the Outlook client. \n\nCustomer Impact: Customer impact appears to be limited at this time. This issue only affects hybrid customers.\n\nPreliminary Root Cause: As part of our ongoing work, an updated certificate was deployed to the infrastructure; however, a caching issue has caused the infrastructure to use an expired certificate which is causing archive access issues. \n\nNext Update by: Tuesday, April 7, 2015, at 10:00 PM UTC "
                },
                {
                    "PublishedTime": "2015-04-08T21:54:49.06Z",
                    "MessageText": "Final Status: Engineers have implemented a fix which remediated end-user impact. \r\n\r\nUser Experience: Affected users were unable to access online archives when using Outlook Web App (OWA).\r\n\r\nCustomer Impact: Customer impact appears to have been limited. This issue only affected hybrid customers.\r\n\r\nIncident Start Time: Monday, March 30, 2015, at 9:28 AM UTC\r\n\r\nIncident End Time: Tuesday, April 7, 2015, at 8:00 PM UTC\r\n\r\nPreliminary Root Cause: As part of our ongoing work, an updated certificate was deployed to the infrastructure; however, a caching issue has caused the infrastructure to use an expired certificate which is causing archive access issues.  \r\n\r\nNext Steps: The following is a list of known action item(s) associated with this incident. As part of the Office 365 problem management process, additional engineering actions may be identified to improve the overall service.\r\n- Action: Review the monitoring infrastructure for improvements as this event was reported by customers before an alert prompted a high priority investigation. \r\n\r\nA post-incident report will be available on the Service Health Dashboard within five business days."
                }
            ],
            "LastUpdatedTime": "2015-04-08T21:54:49.55Z",
            "Workload": "Exchange Online",
            "WorkloadDisplayName": "Exchange",
            "Feature": "Access",
            "FeatureDisplayName": "E-Mail and calendar access"
        },
        {
            "Id": "EX20789",
            "Name": "EX20789",
            "Title": null,
            "StartTime": "2015-04-06T20:00:00Z",
            "EndTime": "2015-04-07T23:00:00Z",
            "Status": "Service restored",
            "Messages": [
                {
                    "PublishedTime": "2015-04-07T23:26:44.643Z",
                    "MessageText": "Final Status: Engineers have validated that the deployed fix has resolved the issue and that service is restored.\r\n\r\nUser Experience: Affected users were unable to send or receive email while using Exchange Web Services (EWS) on their mobile devices.\r\n\r\nCustomer Impact: Customer impact appeared to be limited during this event. This issue was only affecting customers that use third-party Mobile Device Management software from Good Technology. As a workaround to provide immediate relief from impact, engineers implemented a configuration change for customers who reported this issue to Microsoft Support.\r\n\r\nIncident Start Time: Wednesday, April 1, 2015, at 2:00 PM UTC\r\n\r\nIncident End Time: Tuesday, April 7, 2015, at 10:00 PM UTC\r\n\r\nPreliminary Root Cause: As part of our ongoing efforts to improve service resiliency, an update was deployed to the infrastructure that facilitates connections from multiple Exchange Online protocols to mailbox databases. The update, however, contained a code issue that caused connectivity issues in some scenarios. \r\n\r\nNext Steps: The following is a list of known action item(s) associated with this incident. As part of the Office 365 problem management process, additional engineering actions may be identified to improve the overall service.\r\n- Action: Review the infrastructure update process to prevent reoccurrences of this scenario.\r\n\r\nPlease consider this service notification the final update on the event."
               }
            ],
            "LastUpdatedTime": "2015-04-07T23:26:45.08Z",
            "Workload": "Exchange Online",
            "WorkloadDisplayName": "Exchange",
            "Feature": "Access",
            "FeatureDisplayName": "E-Mail and calendar access"
        }
    ]
}
```


## <a name="errors"></a><span data-ttu-id="a8dfe-260">Erros</span><span class="sxs-lookup"><span data-stu-id="a8dfe-260">Errors</span></span>

<span data-ttu-id="a8dfe-261">Quando o serviço encontra um erro, ele relata o código de resposta do erro ao chamador, usando a sintaxe de código de erro HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-261">When the service encounters an error, it reports the error response code to the caller, using standard HTTP error-code syntax.</span></span> <span data-ttu-id="a8dfe-262">Conforme descrito na [especificação OData V4](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html), as informações adicionais são incluídas no corpo da chamada que falhou como um único objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="a8dfe-262">As per [OData V4 specification](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html), additional information is included in the body of the failed call as a single JSON object.</span></span> <span data-ttu-id="a8dfe-263">Este é um exemplo de um corpo de erro JSON completo:</span><span class="sxs-lookup"><span data-stu-id="a8dfe-263">The following is an example of a full JSON error body:</span></span>


```json
{ 
    "error":{ 
        "code":"AF5000.  An internal server error occurred.",
        "message": "Retry the request." 
    } 
}
```

