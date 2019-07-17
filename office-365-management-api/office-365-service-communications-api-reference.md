---
ms.TocTitle: Office 365 Service Communications API reference (Preview)
title: Referência da API de comunicações de serviço do Office 365 (visualização)
description: 'Use esta API para acessar os seguintes dados: Obter Serviços, Obter Status Atual, Obter Status Histórico e Obter Mensagens.'
ms.ContentId: d0b9341a-b205-5442-1c20-8fb56407351d
ms.topic: reference (API)
ms.date: ''
localization_priority: Priority
ms.openlocfilehash: 6b42efe72931875592c87e78aa9c9cdce11a339b
ms.sourcegitcommit: f823233a1ab116bc83d7ca8cd8ad7c7ea59439fc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "35688169"
---
# <a name="office-365-service-communications-api-reference-preview"></a><span data-ttu-id="fe1c7-103">Referência da API de comunicações de serviço do Office 365 (visualização)</span><span class="sxs-lookup"><span data-stu-id="fe1c7-103">Office 365 Service Communications API reference (preview)</span></span>

> [!NOTE] 
> <span data-ttu-id="fe1c7-104">Esta documentação aborda os recursos que estão atualmente na versão prévia.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-104">This documentation covers features that are currently in preview.</span></span>

<span data-ttu-id="fe1c7-105">Você pode usar o API de Comunicações do Serviço do Office 365 V2 para acessar os seguintes dados:</span><span class="sxs-lookup"><span data-stu-id="fe1c7-105">You can use the Office 365 Service Communications API V2 to access the following data:</span></span>

- <span data-ttu-id="fe1c7-106">**Obter Serviços**: obtenha a lista de serviços assinados.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-106">**Get Services**: Get the list of subscribed services.</span></span>
    
- <span data-ttu-id="fe1c7-107">**Obter Status Atual**: obtenha uma visualização em tempo real dos eventos de manutenção e dos incidentes de serviço em andamento e atuais</span><span class="sxs-lookup"><span data-stu-id="fe1c7-107">**Get Current Status**: Get a real-time view of current and ongoing service incidents and maintenance events</span></span>
    
- <span data-ttu-id="fe1c7-108">**Obter Status Histórico**: obtenha uma visualização do histórico de integridade do serviço, incluindo incidentes de serviço e eventos de manutenção.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-108">**Get Historical Status**: Get a historical view of service health, including service incidents and maintenance events.</span></span>
    
- <span data-ttu-id="fe1c7-109">**Obter Mensagens**: comunicações do Centro de Mensagens, Manutenção Planejada e Localizar Incidente.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-109">**Get Messages**: Find Incident, Planned Maintenance, and Message Center communications.</span></span>
    
<span data-ttu-id="fe1c7-110">Atualmente, a API de Comunicações do Serviço do Office 365 contém os dados dos seguintes serviços: Dynamics CRM, Dynamics Marketing, Exchange Online, Proteção do Exchange Online, Identity Service, Gerenciamento de Dispositivo Móvel, Centro de Administração do Parceiro do Office 365, OneDrive for Business, Parature, OneDrive for Business, Power BI para Office 365, Serviço de Gerenciamento de Direitos, SharePoint Online, Administrador do SHD, Skype for Business, Envolvimento Social e Yammer Enterprise.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-110">Currently, the Office 365 Service Communications API contains data for the following services: Dynamics CRM, Dynamics Marketing, Exchange Online, Exchange Online Protection, Identity Service, Mobile Device Management, Office 365 Partner Admin Center, OneDrive for Business, Parature, OneDrive for Business, Power BI for Office 365, Rights Management Service, SharePoint Online, SHD Admin, Skype for Business, Social Engagement, and Yammer Enterprise.</span></span>

## <a name="the-fundamentals"></a><span data-ttu-id="fe1c7-111">Os conceitos básicos</span><span class="sxs-lookup"><span data-stu-id="fe1c7-111">The fundamentals</span></span>

<span data-ttu-id="fe1c7-112">A URL raiz da API inclui um identificador de locatário que atribui operações a um único locatário:</span><span class="sxs-lookup"><span data-stu-id="fe1c7-112">The root URL of the API includes a tenant identifier that scopes the operations to a single tenant:</span></span>

```http
https://manage.office.com/api/v1.0/{tenant_identifier}/ServiceComms/{operation}
```

<span data-ttu-id="fe1c7-113">A **API de Comunicações do Serviço do Office 365** é um serviço do REST que permite desenvolver soluções usando qualquer linguagem da web e ambiente de hospedagem compatível com os certificados HTTPS e X.509.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-113">The **Office 365 Service Communications API** is a REST service that allows you to develop solutions using any web language and hosting environment that supports HTTPS and X.509 certificates.</span></span> <span data-ttu-id="fe1c7-114">A API depende do **Microsoft Azure Active Directory** e do protocolo **OAuth2** para autorização e autenticação.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-114">The API relies on **Microsoft Azure Active Directory** and the **OAuth2** protocol for authentication and authorization.</span></span> <span data-ttu-id="fe1c7-115">Para acessar a API do seu aplicativo, é preciso primeiro registrá-la no Azure AD e configurá-la com permissões no escopo apropriado.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-115">To access the API from your application, you'll need to first register it in Azure AD and configure it with permissions at the appropriate scope.</span></span> <span data-ttu-id="fe1c7-116">Isso permitirá que seu aplicativo solicite os tokens de acesso do OAuth2 necessários para chamar a API.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-116">This will enable your application to request OAuth2 access tokens necessary for calling the API.</span></span> <span data-ttu-id="fe1c7-117">Saiba mais sobre como registrar e configurar um aplicativo no Azure AD em [Introdução às APIs de Gerenciamento do Office 365](get-started-with-office-365-management-apis.md).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-117">You can find more information about registering and configuring an application in Azure AD at [Office 365 Management APIs getting started](get-started-with-office-365-management-apis.md).</span></span>

<span data-ttu-id="fe1c7-118">Todas as solicitações de API exigem um cabeçalho HTTP de Autorização com um token de acesso de JWT do OAuth2 obtido do Azure AD contendo a solicitação **ServiceHealth.Read** e o identificador do locatário deve corresponder ao identificador do locatário na URL raiz.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-118">All API requests require an Authorization HTTP header that has a valid OAuth2 JWT access token obtained from Azure AD that contains the **ServiceHealth.Read** claim; and the tenant identifier must match the tenant identifier in the root URL.</span></span>

```json
Authorization: Bearer {OAuth2 token}
```

<span data-ttu-id="fe1c7-119">**Cabeçalhos da Solicitação**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-119">**Request headers**</span></span>

<span data-ttu-id="fe1c7-120">Estes são os cabeçalhos de solicitação suportados para todas as operações da API de Comunicações do Serviço do Office 365.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-120">These are the supported request headers for all Office 365 Service Communications API operations.</span></span>

|<span data-ttu-id="fe1c7-121">Cabeçalho</span><span class="sxs-lookup"><span data-stu-id="fe1c7-121">Header</span></span>|<span data-ttu-id="fe1c7-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe1c7-122">Description</span></span>|
|:-----|:-----|
|<span data-ttu-id="fe1c7-123">**Aceitação (opcional)**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-123">**Accept (Optional)**</span></span>|<span data-ttu-id="fe1c7-124">Estas são representações aceitas da resposta:</span><span class="sxs-lookup"><span data-stu-id="fe1c7-124">The following are acceptable representations for the response:</span></span><br/><span data-ttu-id="fe1c7-125">**application/json;odata.metadata=full**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-125">**application/json;odata.metadata=full**</span></span><br/><span data-ttu-id="fe1c7-126">**application/json;odata.metadata=minimal**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-126">**application/json;odata.metadata=minimal**</span></span><br/><span data-ttu-id="fe1c7-127">[O padrão se o cabeçalho não for especificado] **application/json;odata.metadata=none**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-127">[The default if header not specified] **application/json;odata.metadata=none**</span></span>|
|<span data-ttu-id="fe1c7-128">**Autorização (obrigatória)**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-128">**Authorization (Required)**</span></span>|<span data-ttu-id="fe1c7-129">Token de autorização (Token do Azure AD do JWT do portador) para a solicitação.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-129">Authorization token (Bearer JWT Azure AD Token) for the request.</span></span>|


<br/>

<span data-ttu-id="fe1c7-130">**Cabeçalhos de respostas**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-130">**Response headers**</span></span>

<span data-ttu-id="fe1c7-131">Estes são os cabeçalhos de respostas retornados para todas as operações da API de Comunicações do Serviço do Office 365:</span><span class="sxs-lookup"><span data-stu-id="fe1c7-131">These are the response headers returned for all Office 365 Service Communications API operations:</span></span>

|<span data-ttu-id="fe1c7-132">Cabeçalho</span><span class="sxs-lookup"><span data-stu-id="fe1c7-132">Header</span></span>|<span data-ttu-id="fe1c7-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe1c7-133">Description</span></span>|
|:-----|:-----|
|<span data-ttu-id="fe1c7-134">**Content-Length**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-134">**Content-Length**</span></span>|<span data-ttu-id="fe1c7-135">O comprimento do corpo da resposta.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-135">The length of the response body.</span></span>|
|<span data-ttu-id="fe1c7-136">**Content-Type**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-136">**Content-Type**</span></span>|<span data-ttu-id="fe1c7-137">Representação da resposta:</span><span class="sxs-lookup"><span data-stu-id="fe1c7-137">Representation of the response:</span></span><br/><span data-ttu-id="fe1c7-138">**application/json**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-138">**application/json**</span></span><br/><span data-ttu-id="fe1c7-139">**application/json;odata.metadata=full**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-139">**application/json;odata.metadata=full**</span></span><br/><span data-ttu-id="fe1c7-140">**application/json;odata.metadata=minimal**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-140">**application/json;odata.metadata=minimal**</span></span><br/><span data-ttu-id="fe1c7-141">**application/json;odata.metadata=none**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-141">**application/json;odata.metadata=none**</span></span><br/><span data-ttu-id="fe1c7-142">**odata.streaming=true**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-142">**odata.streaming=true**</span></span>|
|<span data-ttu-id="fe1c7-143">**Cache-Control**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-143">**Cache-Control**</span></span>|<span data-ttu-id="fe1c7-144">Usado para especificar as diretivas que todos os mecanismos de cache devem seguir ao longo da cadeia de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-144">Used to specify directives that all caching mechanisms along the request/response chain must obey.</span></span>|
|<span data-ttu-id="fe1c7-145">**Pragma**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-145">**Pragma**</span></span>|<span data-ttu-id="fe1c7-146">Comportamentos específicos de implementação.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-146">Implementation-specific behaviors.</span></span>|
|<span data-ttu-id="fe1c7-147">**Expires**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-147">**Expires**</span></span>|<span data-ttu-id="fe1c7-148">Quando o cliente deve fazer o recurso expirar.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-148">When the client should make the resource expire.</span></span>|
|<span data-ttu-id="fe1c7-149">**X-Activity-Id**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-149">**X-Activity-Id**</span></span>|<span data-ttu-id="fe1c7-150">O ID de atividade gerado pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-150">The server-generated activity Id.</span></span>|
|<span data-ttu-id="fe1c7-151">**OData-Version**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-151">**OData-Version**</span></span>|<span data-ttu-id="fe1c7-152">O OData Versão (4.0) com suporte.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-152">The supported OData Version (4.0).</span></span>|
|<span data-ttu-id="fe1c7-153">**Date**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-153">**Date**</span></span>|<span data-ttu-id="fe1c7-154">A data em UTC de quando a resposta foi enviada do servidor.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-154">The date in UTC when the response was sent from the server.</span></span>|
|<span data-ttu-id="fe1c7-155">**X-Time-Taken**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-155">**X-Time-Taken**</span></span>|<span data-ttu-id="fe1c7-156">O tempo que foi necessário para gerar a resposta (ms).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-156">The time it took to generate the response (ms).</span></span>|
|<span data-ttu-id="fe1c7-157">**X-Instance-Name**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-157">**X-Instance-Name**</span></span>|<span data-ttu-id="fe1c7-158">O identificador da instância do Azure usado para gerar a resposta (para fins de depuração).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-158">The identifier of the Azure instance used to generate the response (for debugging purposes).</span></span>|
|<span data-ttu-id="fe1c7-159">**Server**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-159">**Server**</span></span>|<span data-ttu-id="fe1c7-160">O servidor usado para gerar a resposta (para fins de depuração).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-160">The server used to generate the response (for debugging purposes).</span></span>|
|<span data-ttu-id="fe1c7-161">**X-ASPNET-Version**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-161">**X-ASPNET-Version**</span></span>|<span data-ttu-id="fe1c7-162">A versão do ASP.Net usada pelo servidor que gerou a resposta (para fins de depuração).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-162">The version of ASP.Net used by the server that generated the response (for debugging purposes).</span></span>|
|<span data-ttu-id="fe1c7-163">**X-Powered-By**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-163">**X-Powered-By**</span></span>|<span data-ttu-id="fe1c7-164">As tecnologias usadas no servidor que gerou a resposta (para fins de depuração).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-164">The technologies used in the server that generated the response (for debugging purposes).</span></span>|
|||

<br/>

<span data-ttu-id="fe1c7-165">Estas são as operações da API de Comunicações do Serviço do Office 365.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-165">Following are the Office 365 Service Communications API operations.</span></span>


## <a name="get-services"></a><span data-ttu-id="fe1c7-166">Obter Serviços</span><span class="sxs-lookup"><span data-stu-id="fe1c7-166">Get Services</span></span>

<span data-ttu-id="fe1c7-167">Retorna a lista de serviços assinados.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-167">Returns the list of subscribed services.</span></span>

||<span data-ttu-id="fe1c7-168">Serviço</span><span class="sxs-lookup"><span data-stu-id="fe1c7-168">Service</span></span>|<span data-ttu-id="fe1c7-169">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe1c7-169">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="fe1c7-170">**Caminho**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-170">**Path**</span></span>| `/Services`||
|<span data-ttu-id="fe1c7-171">**Query-option**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-171">**Query-option**</span></span>|<span data-ttu-id="fe1c7-172">$select</span><span class="sxs-lookup"><span data-stu-id="fe1c7-172">$select</span></span>|<span data-ttu-id="fe1c7-173">Escolha um subconjunto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-173">Pick a subset of properties.</span></span>|
|<span data-ttu-id="fe1c7-174">**Resposta**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-174">**Response**</span></span>|<span data-ttu-id="fe1c7-175">Lista de entidades "Service"</span><span class="sxs-lookup"><span data-stu-id="fe1c7-175">List of "Service" entities</span></span>|<span data-ttu-id="fe1c7-176">A entidade "Service" contém "Id" (cadeia de caracteres), "DisplayName" (cadeia de caracteres) e "FeatureNames" (lista de cadeias de caracteres).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-176">"Service" entity contains "Id" (String), "DisplayName" (String), and "FeatureNames" (list of Strings).</span></span>|
||||

#### <a name="sample-request"></a><span data-ttu-id="fe1c7-177">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="fe1c7-177">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/Services 
Authorization: Bearer {AAD_Bearer_JWT_Token}

```

#### <a name="sample-response"></a><span data-ttu-id="fe1c7-178">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="fe1c7-178">Sample response</span></span>

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


## <a name="get-current-status"></a><span data-ttu-id="fe1c7-179">Obter Status Atual</span><span class="sxs-lookup"><span data-stu-id="fe1c7-179">Get Current Status</span></span>

<span data-ttu-id="fe1c7-180">Retorna o status do serviço das últimas 24 horas.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-180">Returns the status of the service over the previous 24 hours.</span></span>

> [!NOTE] 
> <span data-ttu-id="fe1c7-181">A resposta do serviço conterá o status e quaisquer incidentes ocorridos dentro das últimas 24 horas.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-181">The service response will contain the status and any incidents within the previous 24 hours.</span></span> <span data-ttu-id="fe1c7-182">O valor StatusDate ou StatusTime retornado estará exatamente 24 horas no passado, a menos que haja um status mais recente disponível.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-182">The StatusDate or StatusTime value returned will be exactly 24 hours in the past, unless a more recent status is available.</span></span> <span data-ttu-id="fe1c7-183">Se um serviço recebeu uma atualização de status nas últimas 24 horas, o horário da última atualização será retornado.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-183">If a service has received a status update within the last 24 hours, the time of the latest update will be returned instead.</span></span>

||<span data-ttu-id="fe1c7-184">Serviço</span><span class="sxs-lookup"><span data-stu-id="fe1c7-184">Service</span></span>|<span data-ttu-id="fe1c7-185">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe1c7-185">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="fe1c7-186">**Caminho**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-186">**Path**</span></span>| `/CurrentStatus`||
|<span data-ttu-id="fe1c7-187">**Filtro**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-187">**Filter**</span></span>|<span data-ttu-id="fe1c7-188">Carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="fe1c7-188">Workload</span></span>|<span data-ttu-id="fe1c7-189">Filtrar por carga de trabalho (cadeia de caracteres, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-189">Filter by workload (String, default: all).</span></span>|
|<span data-ttu-id="fe1c7-190">**Query-option**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-190">**Query-option**</span></span>|<span data-ttu-id="fe1c7-191">$select</span><span class="sxs-lookup"><span data-stu-id="fe1c7-191">$select</span></span>|<span data-ttu-id="fe1c7-192">Escolha um subconjunto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-192">Pick a subset of properties.</span></span>|
|<span data-ttu-id="fe1c7-193">**Resposta**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-193">**Response**</span></span>|<span data-ttu-id="fe1c7-194">Lista de entidades "WorkloadStatus".</span><span class="sxs-lookup"><span data-stu-id="fe1c7-194">List of "WorkloadStatus" entities.</span></span>|<span data-ttu-id="fe1c7-195">A entidade "WorkloadStatus" contém "Id" (cadeia de caracteres), "Workload" (cadeia de caracteres), "StatusTime"(DateTimeOffset), "WorkloadDisplayName" (cadeia de caracteres), "Status" (cadeia de caracteres), "IncidentIds" (lista de cadeias de caracteres) e FeatureGroupStatusCollection (lista de "FeatureStatus").</span><span class="sxs-lookup"><span data-stu-id="fe1c7-195">"WorkloadStatus" entity contains "Id" (String), "Workload" (String), "StatusTime"(DateTimeOffset), "WorkloadDisplayName" (String), "Status" (String), "IncidentIds" (list of Strings), and FeatureGroupStatusCollection (list of "FeatureStatus").</span></span><br/><br/><span data-ttu-id="fe1c7-196">A entidade "FeatureStatus" contém "Feature" (cadeia de caracteres), "FeatureGroupDisplayName" (cadeia de cadeia de caracteres) e "FeatureStatus" (cadeia de caracteres).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-196">"FeatureStatus" entity contains "Feature" (String), "FeatureGroupDisplayName" (String), and "FeatureStatus" (String).</span></span>|
||||

#### <a name="sample-request"></a><span data-ttu-id="fe1c7-197">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="fe1c7-197">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/CurrentStatus
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

#### <a name="sample-response"></a><span data-ttu-id="fe1c7-198">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="fe1c7-198">Sample response</span></span>

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
#### <a name="status-definitions"></a><span data-ttu-id="fe1c7-199">Definições de status</span><span class="sxs-lookup"><span data-stu-id="fe1c7-199">Status definitions</span></span>

|<span data-ttu-id="fe1c7-200">**Status**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-200">**Status**</span></span>|<span data-ttu-id="fe1c7-201">**Definição**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-201">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="fe1c7-202">**Investigando**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-202">**Investigating**</span></span> | <span data-ttu-id="fe1c7-203">Estamos cientes de um possível problema e reunindo mais informações sobre o que está acontecendo e o escopo de impacto.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-203">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span> |
|<span data-ttu-id="fe1c7-204">**ServiceDegradation**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-204">**ServiceDegradation**</span></span> | <span data-ttu-id="fe1c7-p103">Confirmamos que existe um problema que pode afetar o uso de um serviço ou recurso. Talvez você veja esse status se um serviço apresentar um desempenho mais lento do que o normal, se houver interrupções intermitentes ou se um recurso não estiver funcionando, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-p103">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span> |
|<span data-ttu-id="fe1c7-207">**ServiceInterruption**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-207">**ServiceInterruption**</span></span> | <span data-ttu-id="fe1c7-p104">Você verá esse status se determinarmos que um problema afeta a capacidade dos usuários de acessar o serviço. Neste caso, a questão é significativa e pode ser reproduzida de forma consistente.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-p104">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span> |
|<span data-ttu-id="fe1c7-210">**RestoringService**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-210">**RestoringService**</span></span> | <span data-ttu-id="fe1c7-211">A causa do problema foi identificada, sabemos quais ações corretivas devem ser tomadas e estamos no processo de retomar o estado de integridade do serviço.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-211">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span> |
|<span data-ttu-id="fe1c7-212">**ExtendedRecovery**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-212">**ExtendedRecovery**</span></span> | <span data-ttu-id="fe1c7-p105">Esse status indica que uma ação corretiva está em andamento para restaurar o serviço para a maioria dos usuários, mas levará algum tempo para alcançar todos os sistemas afetados. Você também poderá ver esse status se tivermos feito uma correção temporária para reduzir o impacto enquanto aguardamos para aplicar uma correção permanente.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-p105">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span> |
|<span data-ttu-id="fe1c7-215">**InvestigationSuspended**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-215">**InvestigationSuspended**</span></span> | <span data-ttu-id="fe1c7-p106">Se a nossa investigação detalhada de um problema potencial resultar em uma solicitação de informações adicionais de clientes para nos permitir investigar mais, você verá esse status. Se precisarmos de você para prosseguir, informaremos quais dados ou logs precisamos.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-p106">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span> |
|<span data-ttu-id="fe1c7-218">**ServiceRestored**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-218">**ServiceRestored**</span></span> | <span data-ttu-id="fe1c7-p107">Confirmamos que a ação corretiva solucionou o problema subjacente, e o serviço foi restaurado para um estado íntegro. Para descobrir o que deu errado, confira os detalhes do problema.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-p107">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span> |
|<span data-ttu-id="fe1c7-221">**PostIncidentReportPublished**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-221">**PostIncidentReportPublished**</span></span> | <span data-ttu-id="fe1c7-222">Publicamos um relatório pós-incidente para um problema específico que inclui as informações da causa raiz e as próximas etapas para garantir que um problema semelhante não ocorra.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-222">We’ve published a Post Incident Report for a specific issue that includes root cause information and next steps to ensure a similar issue doesn’t reoccur.</span></span> |
|||

> [!NOTE] 
> <span data-ttu-id="fe1c7-223">Para saber mais sobre a integridade do serviço do Office 365, visite[como verificar a integridade do serviço do Office 365](https://docs.microsoft.com/office365/enterprise/view-service-health).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-223">For more information on Office 365 service health please visit [How to check Office 365 service health](https://docs.microsoft.com/office365/enterprise/view-service-health).</span></span>

## <a name="get-historical-status"></a><span data-ttu-id="fe1c7-224">Obter Status Histórico</span><span class="sxs-lookup"><span data-stu-id="fe1c7-224">Get Historical Status</span></span>

<span data-ttu-id="fe1c7-225">Retorna o status histórico do serviço, por dia, durante um determinado intervalo.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-225">Returns the historical status of the service, by day, over a certain time range.</span></span>

||<span data-ttu-id="fe1c7-226">Serviço</span><span class="sxs-lookup"><span data-stu-id="fe1c7-226">Service</span></span>|<span data-ttu-id="fe1c7-227">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe1c7-227">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="fe1c7-228">**Caminho**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-228">**Path**</span></span>| `/HistoricalStatus`||
|<span data-ttu-id="fe1c7-229">**Filtros**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-229">**Filters**</span></span>|<span data-ttu-id="fe1c7-230">Carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="fe1c7-230">Workload</span></span>|<span data-ttu-id="fe1c7-231">Filtrar por carga de trabalho (cadeia de caracteres, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-231">Filter by workload (String, default: all).</span></span>|
||<span data-ttu-id="fe1c7-232">StatusTime</span><span class="sxs-lookup"><span data-stu-id="fe1c7-232">StatusTime</span></span>|<span data-ttu-id="fe1c7-233">Filtrar por dias maiores que StatusTime (DateTimeOffset, padrão: ge CurrentTime, 7 dias).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-233">Filter by days greater than StatusTime (DateTimeOffset, default: ge CurrentTime - 7 days).</span></span>|
|<span data-ttu-id="fe1c7-234">**Query-option**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-234">**Query-option**</span></span>|<span data-ttu-id="fe1c7-235">$select</span><span class="sxs-lookup"><span data-stu-id="fe1c7-235">$select</span></span>|<span data-ttu-id="fe1c7-236">Escolha um subconjunto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-236">Pick a subset of properties.</span></span>|
|<span data-ttu-id="fe1c7-237">**Resposta**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-237">**Response**</span></span>|<span data-ttu-id="fe1c7-238">Lista de entidades "WorkloadStatus".</span><span class="sxs-lookup"><span data-stu-id="fe1c7-238">List of "WorkloadStatus" entities.</span></span>|<span data-ttu-id="fe1c7-239">A entidade "WorkloadStatus" contém "Id" (cadeia de caracteres), "Workload" (cadeia de caracteres), "StatusTime"(DateTimeOffset), "WorkloadDisplayName" (cadeia de caracteres), "Status" (cadeia de caracteres), "IncidentIds" (lista de cadeias de caracteres) e FeatureGroupStatusCollection (lista de "FeatureStatus").</span><span class="sxs-lookup"><span data-stu-id="fe1c7-239">"WorkloadStatus" entity contains "Id" (String), "Workload" (String), "StatusTime"(DateTimeOffset), "WorkloadDisplayName" (String), "Status" (String), "IncidentIds" (list of Strings), and FeatureGroupStatusCollection (list of "FeatureStatus").</span></span><br/><br/><span data-ttu-id="fe1c7-240">A entidade "FeatureStatus" contém "Feature" (cadeia de caracteres), "FeatureGroupDisplayName" (cadeia de cadeia de caracteres) e "FeatureStatus" (cadeia de caracteres).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-240">"FeatureStatus" entity contains "Feature" (String), "FeatureGroupDisplayName" (String), and "FeatureStatus" (String).</span></span>|
||||

#### <a name="sample-request"></a><span data-ttu-id="fe1c7-241">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="fe1c7-241">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/HistoricalStatus
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

#### <a name="sample-response"></a><span data-ttu-id="fe1c7-242">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="fe1c7-242">Sample response</span></span>

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


## <a name="get-messages"></a><span data-ttu-id="fe1c7-243">Obter Mensagens</span><span class="sxs-lookup"><span data-stu-id="fe1c7-243">Get Messages</span></span>

<span data-ttu-id="fe1c7-244">Retorna as mensagens sobre o serviço de um determinado intervalo de tempo.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-244">Returns the messages about the service over a certain time range.</span></span> <span data-ttu-id="fe1c7-245">Use o tipo de filtro para filtrar as mensagens por "Centro de Mensagens", "Manutenção Planejada" ou "Incidente de Serviço".</span><span class="sxs-lookup"><span data-stu-id="fe1c7-245">Use the type filter to filter for "Service Incident", "Planned Maintenance", or "Message Center" messages.</span></span>

||<span data-ttu-id="fe1c7-246">Serviço</span><span class="sxs-lookup"><span data-stu-id="fe1c7-246">Service</span></span>|<span data-ttu-id="fe1c7-247">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe1c7-247">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="fe1c7-248">**Caminho**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-248">**Path**</span></span>| `/Messages`||
|<span data-ttu-id="fe1c7-249">**Filtros**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-249">**Filters**</span></span>|<span data-ttu-id="fe1c7-250">Carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="fe1c7-250">Workload</span></span>|<span data-ttu-id="fe1c7-251">Filtrar por carga de trabalho (cadeia de caracteres, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-251">Filter by workload (String, default: all).</span></span>|
||<span data-ttu-id="fe1c7-252">StartTime</span><span class="sxs-lookup"><span data-stu-id="fe1c7-252">StartTime</span></span>|<span data-ttu-id="fe1c7-253">Filtrar por Hora de Início (DateTimeOffset, padrão: ge CurrentTime – 7 dias).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-253">Filter by Start Time (DateTimeOffset, default: ge CurrentTime - 7 days).</span></span>|
||<span data-ttu-id="fe1c7-254">EndTime</span><span class="sxs-lookup"><span data-stu-id="fe1c7-254">EndTime</span></span>|<span data-ttu-id="fe1c7-255">Filtrar por Hora de Término (DateTimeOffset, padrão: le CurrentTime).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-255">Filter by End Time (DateTimeOffset, default: le CurrentTime).</span></span>|
||<span data-ttu-id="fe1c7-256">MessageType</span><span class="sxs-lookup"><span data-stu-id="fe1c7-256">MessageType</span></span>|<span data-ttu-id="fe1c7-257">Filtrar por Tipo de Mensagem (Cadeia de caracteres, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-257">Filter by MessageType (String, default: all).</span></span>|
||<span data-ttu-id="fe1c7-258">ID</span><span class="sxs-lookup"><span data-stu-id="fe1c7-258">ID</span></span>|<span data-ttu-id="fe1c7-259">Filtrar por ID (Cadeia de caracteres, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-259">Filter by ID (String, default: all).</span></span>|
|<span data-ttu-id="fe1c7-260">**Query-option**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-260">**Query-option**</span></span>|<span data-ttu-id="fe1c7-261">$select</span><span class="sxs-lookup"><span data-stu-id="fe1c7-261">$select</span></span>|<span data-ttu-id="fe1c7-262">Escolha um subconjunto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-262">Pick a subset of properties.</span></span>|
||<span data-ttu-id="fe1c7-263">$top</span><span class="sxs-lookup"><span data-stu-id="fe1c7-263">$top</span></span>|<span data-ttu-id="fe1c7-264">Escolha o número máximo de resultados (padrão e máx. $top=100).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-264">Pick the top number of results (default and max $top=100).</span></span>|
||<span data-ttu-id="fe1c7-265">$skip</span><span class="sxs-lookup"><span data-stu-id="fe1c7-265">$skip</span></span>|<span data-ttu-id="fe1c7-266">Ignorar o número de resultados (padrão: $skip=0).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-266">Skip number of results (default: $skip=0).</span></span>|
|<span data-ttu-id="fe1c7-267">**Resposta**</span><span class="sxs-lookup"><span data-stu-id="fe1c7-267">**Response**</span></span>|<span data-ttu-id="fe1c7-268">Lista de entidades de "Mensagem".</span><span class="sxs-lookup"><span data-stu-id="fe1c7-268">List of "Message" entities.</span></span>|<span data-ttu-id="fe1c7-269">A entidade "Message" contém "Id" (cadeia de caracteres), "StartTime" (DateTimeOffset), "EndTime" (DateTimeOffset), "Status" (cadeia de caracteres), "Messages" (lista da entidade "MessagHistory"), "LastUpdatedTime" (DateTimeOffset), "Workload" (cadeia de caracteres), "WorkloadDisplayName" (cadeia de caracteres), "Feature" (cadeia de caracteres), "FeatureDisplayName" (cadeia de caracteres), "MessageType" (Enum, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-269">"Message" entity contains "Id" (String), "StartTime" (DateTimeOffset), "EndTime" (DateTimeOffset), "Status" (String), "Messages" (list of "MessageHistory" entity), "LastUpdatedTime" (DateTimeOffset), "Workload" (String), "WorkloadDisplayName" (String), "Feature" (String), "FeatureDisplayName" (String), "MessageType" (Enum, default: all).</span></span><br/><br/><span data-ttu-id="fe1c7-270">A entidade "MessageHistory" contém "PublishedTime" (DateTimeOffset), "MessageText" (cadeia de caracteres).</span><span class="sxs-lookup"><span data-stu-id="fe1c7-270">"MessageHistory" entity contains "PublishedTime" (DateTimeOffset), "MessageText" (String).</span></span>|
||||

#### <a name="sample-request"></a><span data-ttu-id="fe1c7-271">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="fe1c7-271">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/Messages
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

#### <a name="sample-response"></a><span data-ttu-id="fe1c7-272">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="fe1c7-272">Sample response</span></span>

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


## <a name="errors"></a><span data-ttu-id="fe1c7-273">Erros</span><span class="sxs-lookup"><span data-stu-id="fe1c7-273">Errors</span></span>

<span data-ttu-id="fe1c7-274">Quando o serviço encontra um erro, ele relata o código de resposta do erro ao chamador, usando a sintaxe de código de erro HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-274">When the service encounters an error, it reports the error response code to the caller, using standard HTTP error-code syntax.</span></span> <span data-ttu-id="fe1c7-275">Conforme descrito na [especificação OData V4](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html), as informações adicionais são incluídas no corpo da chamada que falhou como um único objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="fe1c7-275">As per [OData V4 specification](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html), additional information is included in the body of the failed call as a single JSON object.</span></span> <span data-ttu-id="fe1c7-276">Este é um exemplo de um corpo de erro JSON completo:</span><span class="sxs-lookup"><span data-stu-id="fe1c7-276">The following is an example of a full JSON error body:</span></span>


```json

{ 
    "error":{ 
        "code":"AF5000.  An internal server error occurred.",
        "message": "Retry the request." 
    } 
}
```

