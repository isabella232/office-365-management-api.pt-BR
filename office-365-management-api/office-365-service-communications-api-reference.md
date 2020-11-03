---
ms.technology: o365-service-communications
ms.TocTitle: Office 365 Service Communications API reference
title: Referência da API de Comunicações de Serviço do Office 365
description: 'Use esta API para acessar os seguintes dados: Obter Serviços, Obter Status Atual, Obter Status Histórico e Obter Mensagens.'
ms.ContentId: d0b9341a-b205-5442-1c20-8fb56407351d
ms.topic: reference (API)
ms.date: ''
localization_priority: Priority
ms.openlocfilehash: 7cd91d9a43090b4731a11df701e0bf1aa340800e
ms.sourcegitcommit: e7f345710dc63003704399419f784c4a9b5fc529
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2020
ms.locfileid: "48830466"
---
# <a name="office-365-service-communications-api-reference"></a><span data-ttu-id="8ca9e-103">Referência da API de Comunicações de Serviço do Office 365</span><span class="sxs-lookup"><span data-stu-id="8ca9e-103">Office 365 Service Communications API reference</span></span>

<span data-ttu-id="8ca9e-104">Você pode usar o API de Comunicações do Serviço do Office 365 V2 para acessar os seguintes dados:</span><span class="sxs-lookup"><span data-stu-id="8ca9e-104">You can use the Office 365 Service Communications API V2 to access the following data:</span></span>

- <span data-ttu-id="8ca9e-105">**Obter Serviços** : obtenha a lista de serviços assinados.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-105">**Get Services** : Get the list of subscribed services.</span></span>

- <span data-ttu-id="8ca9e-106">**Obter Status Atual** : obtenha uma visualização em tempo real dos eventos de manutenção e dos incidentes de serviço.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-106">**Get Current Status** : Get a real-time view of current and ongoing service incidents.</span></span>

- <span data-ttu-id="8ca9e-107">**Obter Status Histórico** : obtenha uma visualização do histórico de incidentes de serviço.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-107">**Get Historical Status** : Get a historical view of service incidents.</span></span>

- <span data-ttu-id="8ca9e-108">**Obter Mensagens** : comunicações do Localizar Incidente e Centro de Mensagens.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-108">**Get Messages** : Find Incident and Message Center communications.</span></span>

<span data-ttu-id="8ca9e-109">Atualmente, a API de Comunicações do Serviço do Office 365 contém dados para os serviços de nuvem do Office 365, Yammer, Dynamics CRM e Microsoft Intune.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-109">Currently, the Office 365 Service Communications API contains data for Office 365, Yammer, Dynamics CRM and Microsoft Intune cloud services.</span></span>

## <a name="the-fundamentals"></a><span data-ttu-id="8ca9e-110">Os conceitos básicos</span><span class="sxs-lookup"><span data-stu-id="8ca9e-110">The fundamentals</span></span>

<span data-ttu-id="8ca9e-111">A URL raiz da API inclui um identificador de locatário que atribui operações a um único locatário:</span><span class="sxs-lookup"><span data-stu-id="8ca9e-111">The root URL of the API includes a tenant identifier that scopes the operations to a single tenant:</span></span>

```http
https://manage.office.com/api/v1.0/{tenant_identifier}/ServiceComms/{operation}
```

<span data-ttu-id="8ca9e-112">A **API de Comunicações do Serviço do Office 365** é um serviço do REST que permite desenvolver soluções usando qualquer linguagem da web e ambiente de hospedagem compatível com os certificados HTTPS e X.509.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-112">The **Office 365 Service Communications API** is a REST service that allows you to develop solutions using any web language and hosting environment that supports HTTPS and X.509 certificates.</span></span> <span data-ttu-id="8ca9e-113">A API depende do **Microsoft Azure Active Directory** e do protocolo **OAuth2** para autorização e autenticação.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-113">The API relies on **Microsoft Azure Active Directory** and the **OAuth2** protocol for authentication and authorization.</span></span> <span data-ttu-id="8ca9e-114">Para acessar a API do seu aplicativo, é preciso primeiro registrá-la no Azure AD e configurá-la com permissões no escopo apropriado.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-114">To access the API from your application, you'll need to first register it in Azure AD and configure it with permissions at the appropriate scope.</span></span> <span data-ttu-id="8ca9e-115">Isso permitirá que seu aplicativo solicite os tokens de acesso do OAuth2 necessários para chamar a API.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-115">This will enable your application to request OAuth2 access tokens necessary for calling the API.</span></span> <span data-ttu-id="8ca9e-116">Saiba mais sobre como registrar e configurar um aplicativo no Azure AD em [Introdução às APIs de Gerenciamento do Office 365](get-started-with-office-365-management-apis.md).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-116">You can find more information about registering and configuring an application in Azure AD at [Office 365 Management APIs getting started](get-started-with-office-365-management-apis.md).</span></span>

<span data-ttu-id="8ca9e-117">Todas as solicitações de API exigem um cabeçalho HTTP de Autorização com um token de acesso de JWT do OAuth2 obtido do Azure AD contendo a solicitação **ServiceHealth.Read** e o identificador do locatário deve corresponder ao identificador do locatário na URL raiz.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-117">All API requests require an Authorization HTTP header that has a valid OAuth2 JWT access token obtained from Azure AD that contains the **ServiceHealth.Read** claim; and the tenant identifier must match the tenant identifier in the root URL.</span></span>

```json
Authorization: Bearer {OAuth2 token}
```

### <a name="request-headers"></a><span data-ttu-id="8ca9e-118">Cabeçalhos de solicitação</span><span class="sxs-lookup"><span data-stu-id="8ca9e-118">Request headers</span></span>

<span data-ttu-id="8ca9e-119">Estes são os cabeçalhos de solicitação suportados para todas as operações da API de Comunicações do Serviço do Office 365.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-119">These are the supported request headers for all Office 365 Service Communications API operations.</span></span>

|<span data-ttu-id="8ca9e-120">Cabeçalho</span><span class="sxs-lookup"><span data-stu-id="8ca9e-120">Header</span></span>|<span data-ttu-id="8ca9e-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ca9e-121">Description</span></span>|
|:-----|:-----|
|<span data-ttu-id="8ca9e-122">**Aceitação (opcional)**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-122">**Accept (Optional)**</span></span>|<span data-ttu-id="8ca9e-123">Estas são representações aceitas da resposta:</span><span class="sxs-lookup"><span data-stu-id="8ca9e-123">The following are acceptable representations for the response:</span></span><br/><span data-ttu-id="8ca9e-124">**application/json;odata.metadata=full**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-124">**application/json;odata.metadata=full**</span></span><br/><span data-ttu-id="8ca9e-125">**application/json;odata.metadata=minimal**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-125">**application/json;odata.metadata=minimal**</span></span><br/><span data-ttu-id="8ca9e-126">[O padrão se o cabeçalho não for especificado] **application/json;odata.metadata=none**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-126">[The default if header not specified] **application/json;odata.metadata=none**</span></span>|
|<span data-ttu-id="8ca9e-127">**Autorização (obrigatória)**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-127">**Authorization (Required)**</span></span>|<span data-ttu-id="8ca9e-128">Token de autorização (Token do Azure AD do JWT do portador) para a solicitação.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-128">Authorization token (Bearer JWT Azure AD Token) for the request.</span></span>|

<br/>

### <a name="response-headers"></a><span data-ttu-id="8ca9e-129">Cabeçalhos de resposta</span><span class="sxs-lookup"><span data-stu-id="8ca9e-129">Response headers</span></span>

<span data-ttu-id="8ca9e-130">Estes são os cabeçalhos de respostas retornados para todas as operações da API de Comunicações do Serviço do Office 365:</span><span class="sxs-lookup"><span data-stu-id="8ca9e-130">These are the response headers returned for all Office 365 Service Communications API operations:</span></span>

|<span data-ttu-id="8ca9e-131">Cabeçalho</span><span class="sxs-lookup"><span data-stu-id="8ca9e-131">Header</span></span>|<span data-ttu-id="8ca9e-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ca9e-132">Description</span></span>|
|:-----|:-----|
|<span data-ttu-id="8ca9e-133">**Content-Length**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-133">**Content-Length**</span></span>|<span data-ttu-id="8ca9e-134">O comprimento do corpo da resposta.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-134">The length of the response body.</span></span>|
|<span data-ttu-id="8ca9e-135">**Content-Type**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-135">**Content-Type**</span></span>|<span data-ttu-id="8ca9e-136">Representação da resposta:</span><span class="sxs-lookup"><span data-stu-id="8ca9e-136">Representation of the response:</span></span><br/><span data-ttu-id="8ca9e-137">**application/json**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-137">**application/json**</span></span><br/><span data-ttu-id="8ca9e-138">**application/json;odata.metadata=full**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-138">**application/json;odata.metadata=full**</span></span><br/><span data-ttu-id="8ca9e-139">**application/json;odata.metadata=minimal**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-139">**application/json;odata.metadata=minimal**</span></span><br/><span data-ttu-id="8ca9e-140">**application/json;odata.metadata=none**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-140">**application/json;odata.metadata=none**</span></span><br/><span data-ttu-id="8ca9e-141">**odata.streaming=true**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-141">**odata.streaming=true**</span></span>|
|<span data-ttu-id="8ca9e-142">**Cache-Control**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-142">**Cache-Control**</span></span>|<span data-ttu-id="8ca9e-143">Usado para especificar as diretivas que todos os mecanismos de cache devem seguir ao longo da cadeia de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-143">Used to specify directives that all caching mechanisms along the request/response chain must obey.</span></span>|
|<span data-ttu-id="8ca9e-144">**Pragma**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-144">**Pragma**</span></span>|<span data-ttu-id="8ca9e-145">Comportamentos específicos de implementação.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-145">Implementation-specific behaviors.</span></span>|
|<span data-ttu-id="8ca9e-146">**Expires**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-146">**Expires**</span></span>|<span data-ttu-id="8ca9e-147">Quando o cliente deve fazer o recurso expirar.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-147">When the client should make the resource expire.</span></span>|
|<span data-ttu-id="8ca9e-148">**X-Activity-Id**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-148">**X-Activity-Id**</span></span>|<span data-ttu-id="8ca9e-149">O ID de atividade gerado pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-149">The server-generated activity Id.</span></span>|
|<span data-ttu-id="8ca9e-150">**OData-Version**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-150">**OData-Version**</span></span>|<span data-ttu-id="8ca9e-151">O OData Versão (4.0) com suporte.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-151">The supported OData Version (4.0).</span></span>|
|<span data-ttu-id="8ca9e-152">**Date**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-152">**Date**</span></span>|<span data-ttu-id="8ca9e-153">A data em UTC de quando a resposta foi enviada do servidor.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-153">The date in UTC when the response was sent from the server.</span></span>|
|<span data-ttu-id="8ca9e-154">**X-Time-Taken**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-154">**X-Time-Taken**</span></span>|<span data-ttu-id="8ca9e-155">O tempo que foi necessário para gerar a resposta (ms).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-155">The time it took to generate the response (ms).</span></span>|
|<span data-ttu-id="8ca9e-156">**X-Instance-Name**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-156">**X-Instance-Name**</span></span>|<span data-ttu-id="8ca9e-157">O identificador da instância do Azure usado para gerar a resposta (para fins de depuração).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-157">The identifier of the Azure instance used to generate the response (for debugging purposes).</span></span>|
|<span data-ttu-id="8ca9e-158">**Server**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-158">**Server**</span></span>|<span data-ttu-id="8ca9e-159">O servidor usado para gerar a resposta (para fins de depuração).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-159">The server used to generate the response (for debugging purposes).</span></span>|
|<span data-ttu-id="8ca9e-160">**X-ASPNET-Version**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-160">**X-ASPNET-Version**</span></span>|<span data-ttu-id="8ca9e-161">A versão do ASP.Net usada pelo servidor que gerou a resposta (para fins de depuração).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-161">The version of ASP.Net used by the server that generated the response (for debugging purposes).</span></span>|
|<span data-ttu-id="8ca9e-162">**X-Powered-By**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-162">**X-Powered-By**</span></span>|<span data-ttu-id="8ca9e-163">As tecnologias usadas no servidor que gerou a resposta (para fins de depuração).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-163">The technologies used in the server that generated the response (for debugging purposes).</span></span>|
|||

<br/>

<span data-ttu-id="8ca9e-164">Estas são as operações da API de Comunicações do Serviço do Office 365.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-164">Following are the Office 365 Service Communications API operations.</span></span>

## <a name="get-services"></a><span data-ttu-id="8ca9e-165">Obter Serviços</span><span class="sxs-lookup"><span data-stu-id="8ca9e-165">Get Services</span></span>

<span data-ttu-id="8ca9e-166">Retorna a lista de serviços assinados.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-166">Returns the list of subscribed services.</span></span>

|<span data-ttu-id="8ca9e-167">Informações</span><span class="sxs-lookup"><span data-stu-id="8ca9e-167">Information</span></span>|<span data-ttu-id="8ca9e-168">Fornecer manutenção</span><span class="sxs-lookup"><span data-stu-id="8ca9e-168">Service</span></span>|<span data-ttu-id="8ca9e-169">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ca9e-169">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="8ca9e-170">**Caminho**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-170">**Path**</span></span>| `/Services`||
|<span data-ttu-id="8ca9e-171">**Query-option**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-171">**Query-option**</span></span>|<span data-ttu-id="8ca9e-172">$select</span><span class="sxs-lookup"><span data-stu-id="8ca9e-172">$select</span></span>|<span data-ttu-id="8ca9e-173">Escolha um subconjunto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-173">Pick a subset of properties.</span></span>|
|<span data-ttu-id="8ca9e-174">**Resposta**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-174">**Response**</span></span>|<span data-ttu-id="8ca9e-175">Lista de entidades "Service"</span><span class="sxs-lookup"><span data-stu-id="8ca9e-175">List of "Service" entities</span></span>|<span data-ttu-id="8ca9e-176">A entidade "Service" contém "Id" (cadeia de caracteres), "DisplayName" (cadeia de caracteres) e "FeatureNames" (lista de cadeias de caracteres).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-176">"Service" entity contains "Id" (String), "DisplayName" (String), and "FeatureNames" (list of Strings).</span></span>|
||||

### <a name="sample-request"></a><span data-ttu-id="8ca9e-177">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="8ca9e-177">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/Services 
Authorization: Bearer {AAD_Bearer_JWT_Token}

```

### <a name="sample-response"></a><span data-ttu-id="8ca9e-178">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="8ca9e-178">Sample response</span></span>

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

## <a name="get-current-status"></a><span data-ttu-id="8ca9e-179">Obter Status Atual</span><span class="sxs-lookup"><span data-stu-id="8ca9e-179">Get Current Status</span></span>

<span data-ttu-id="8ca9e-180">Retorna o status do serviço das últimas 24 horas.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-180">Returns the status of the service from the previous 24 hours.</span></span>

> [!NOTE] 
> <span data-ttu-id="8ca9e-181">A resposta do serviço conterá o status e quaisquer incidentes ocorridos dentro das últimas 24 horas.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-181">The service response will contain the status and any incidents within the previous 24 hours.</span></span> <span data-ttu-id="8ca9e-182">O valor StatusDate ou StatusTime retornado estará exatamente 24 horas no passado.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-182">The StatusDate or StatusTime value returned will be exactly 24 hours in the past.</span></span> <span data-ttu-id="8ca9e-183">Para obter a última atualização para um determinado incidente, use a funcionalidade de Obter Mensagens e leia o valor de LastUpdatedTime no registro de resposta que corresponde à ID do incidente.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-183">To get the last update for a particular incident, use the Get Messages functionality and read the LastUpdatedTime value from the response record that matches your incident ID.</span></span> <br/>

<br/>

|<span data-ttu-id="8ca9e-184">Informações</span><span class="sxs-lookup"><span data-stu-id="8ca9e-184">Information</span></span>|<span data-ttu-id="8ca9e-185">Fornecer manutenção</span><span class="sxs-lookup"><span data-stu-id="8ca9e-185">Service</span></span>|<span data-ttu-id="8ca9e-186">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ca9e-186">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="8ca9e-187">**Caminho**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-187">**Path**</span></span>| `/CurrentStatus`||
|<span data-ttu-id="8ca9e-188">**Filtro**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-188">**Filter**</span></span>|<span data-ttu-id="8ca9e-189">Carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="8ca9e-189">Workload</span></span>|<span data-ttu-id="8ca9e-190">Filtrar por carga de trabalho (cadeia de caracteres, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-190">Filter by workload (String, default: all).</span></span>|
|<span data-ttu-id="8ca9e-191">**Query-option**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-191">**Query-option**</span></span>|<span data-ttu-id="8ca9e-192">$select</span><span class="sxs-lookup"><span data-stu-id="8ca9e-192">$select</span></span>|<span data-ttu-id="8ca9e-193">Escolha um subconjunto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-193">Pick a subset of properties.</span></span>|
|<span data-ttu-id="8ca9e-194">**Resposta**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-194">**Response**</span></span>|<span data-ttu-id="8ca9e-195">Lista de entidades "WorkloadStatus".</span><span class="sxs-lookup"><span data-stu-id="8ca9e-195">List of "WorkloadStatus" entities.</span></span>|<span data-ttu-id="8ca9e-196">A entidade "WorkloadStatus" contém "Id" (cadeia de caracteres), "Workload" (cadeia de caracteres), "StatusTime"(DateTimeOffset), "WorkloadDisplayName" (cadeia de caracteres), "Status" (cadeia de caracteres), "IncidentIds" (lista de cadeias de caracteres) e FeatureGroupStatusCollection (lista de "FeatureStatus").</span><span class="sxs-lookup"><span data-stu-id="8ca9e-196">"WorkloadStatus" entity contains "Id" (String), "Workload" (String), "StatusTime"(DateTimeOffset), "WorkloadDisplayName" (String), "Status" (String), "IncidentIds" (list of Strings), and FeatureGroupStatusCollection (list of "FeatureStatus").</span></span><br/><br/><span data-ttu-id="8ca9e-197">A entidade "FeatureStatus" contém "Feature" (cadeia de caracteres), "FeatureGroupDisplayName" (cadeia de cadeia de caracteres) e "FeatureStatus" (cadeia de caracteres).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-197">"FeatureStatus" entity contains "Feature" (String), "FeatureGroupDisplayName" (String), and "FeatureStatus" (String).</span></span>|
||||

### <a name="sample-request"></a><span data-ttu-id="8ca9e-198">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="8ca9e-198">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/CurrentStatus
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

### <a name="sample-response"></a><span data-ttu-id="8ca9e-199">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="8ca9e-199">Sample response</span></span>

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

### <a name="status-definitions"></a><span data-ttu-id="8ca9e-200">Definições de status</span><span class="sxs-lookup"><span data-stu-id="8ca9e-200">Status definitions</span></span>

<span data-ttu-id="8ca9e-201">As definições de status incluem os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="8ca9e-201">The status definitions include the following values:</span></span>

- <span data-ttu-id="8ca9e-202">Investigando</span><span class="sxs-lookup"><span data-stu-id="8ca9e-202">Investigating</span></span>
- <span data-ttu-id="8ca9e-203">ServiceDegradation</span><span class="sxs-lookup"><span data-stu-id="8ca9e-203">ServiceDegradation</span></span>
- <span data-ttu-id="8ca9e-204">ServiceInterruption</span><span class="sxs-lookup"><span data-stu-id="8ca9e-204">ServiceInterruption</span></span>
- <span data-ttu-id="8ca9e-205">RestoringService</span><span class="sxs-lookup"><span data-stu-id="8ca9e-205">RestoringService</span></span>
- <span data-ttu-id="8ca9e-206">ExtendedRecovery</span><span class="sxs-lookup"><span data-stu-id="8ca9e-206">ExtendedRecovery</span></span>
- <span data-ttu-id="8ca9e-207">InvestigationSuspended</span><span class="sxs-lookup"><span data-stu-id="8ca9e-207">InvestigationSuspended</span></span>
- <span data-ttu-id="8ca9e-208">ServiceRestored</span><span class="sxs-lookup"><span data-stu-id="8ca9e-208">ServiceRestored</span></span>
- <span data-ttu-id="8ca9e-209">FalsePositive</span><span class="sxs-lookup"><span data-stu-id="8ca9e-209">FalsePositive</span></span>
- <span data-ttu-id="8ca9e-210">PostIncidentReportPublished</span><span class="sxs-lookup"><span data-stu-id="8ca9e-210">PostIncidentReportPublished</span></span>
- <span data-ttu-id="8ca9e-211">ServiceOperational</span><span class="sxs-lookup"><span data-stu-id="8ca9e-211">ServiceOperational</span></span>

<span data-ttu-id="8ca9e-212">Para uma descrição dessas definições de status, consulte [Como verificar a saúde dos serviços do Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/view-service-health#status-definitions).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-212">For a description of these status definitions, see [How to check Microsoft 365 service health](https://docs.microsoft.com/microsoft-365/enterprise/view-service-health#status-definitions).</span></span>

## <a name="get-historical-status"></a><span data-ttu-id="8ca9e-213">Obter Status Histórico</span><span class="sxs-lookup"><span data-stu-id="8ca9e-213">Get Historical Status</span></span>

<span data-ttu-id="8ca9e-214">Retorna o status histórico do serviço, por dia, durante um determinado intervalo.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-214">Returns the historical status of the service, by day, over a certain time range.</span></span>

|<span data-ttu-id="8ca9e-215">Informações</span><span class="sxs-lookup"><span data-stu-id="8ca9e-215">Information</span></span>|<span data-ttu-id="8ca9e-216">Fornecer manutenção</span><span class="sxs-lookup"><span data-stu-id="8ca9e-216">Service</span></span>|<span data-ttu-id="8ca9e-217">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ca9e-217">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="8ca9e-218">**Caminho**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-218">**Path**</span></span>| `/HistoricalStatus`||
|<span data-ttu-id="8ca9e-219">**Filtros**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-219">**Filters**</span></span>|<span data-ttu-id="8ca9e-220">Carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="8ca9e-220">Workload</span></span>|<span data-ttu-id="8ca9e-221">Filtrar por carga de trabalho (cadeia de caracteres, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-221">Filter by workload (String, default: all).</span></span>|
||<span data-ttu-id="8ca9e-222">StatusTime</span><span class="sxs-lookup"><span data-stu-id="8ca9e-222">StatusTime</span></span>|<span data-ttu-id="8ca9e-223">Filtrar por dias maiores que StatusTime (DateTimeOffset, padrão: ge CurrentTime, 7 dias).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-223">Filter by days greater than StatusTime (DateTimeOffset, default: ge CurrentTime - 7 days).</span></span>|
|<span data-ttu-id="8ca9e-224">**Query-option**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-224">**Query-option**</span></span>|<span data-ttu-id="8ca9e-225">$select</span><span class="sxs-lookup"><span data-stu-id="8ca9e-225">$select</span></span>|<span data-ttu-id="8ca9e-226">Escolha um subconjunto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-226">Pick a subset of properties.</span></span>|
|<span data-ttu-id="8ca9e-227">**Resposta**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-227">**Response**</span></span>|<span data-ttu-id="8ca9e-228">Lista de entidades "WorkloadStatus".</span><span class="sxs-lookup"><span data-stu-id="8ca9e-228">List of "WorkloadStatus" entities.</span></span>|<span data-ttu-id="8ca9e-229">A entidade "WorkloadStatus" contém "Id" (cadeia de caracteres), "Workload" (cadeia de caracteres), "StatusTime"(DateTimeOffset), "WorkloadDisplayName" (cadeia de caracteres), "Status" (cadeia de caracteres), "IncidentIds" (lista de cadeias de caracteres) e FeatureGroupStatusCollection (lista de "FeatureStatus").</span><span class="sxs-lookup"><span data-stu-id="8ca9e-229">"WorkloadStatus" entity contains "Id" (String), "Workload" (String), "StatusTime"(DateTimeOffset), "WorkloadDisplayName" (String), "Status" (String), "IncidentIds" (list of Strings), and FeatureGroupStatusCollection (list of "FeatureStatus").</span></span><br/><br/><span data-ttu-id="8ca9e-230">A entidade "FeatureStatus" contém "Feature" (cadeia de caracteres), "FeatureGroupDisplayName" (cadeia de cadeia de caracteres) e "FeatureStatus" (cadeia de caracteres).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-230">"FeatureStatus" entity contains "Feature" (String), "FeatureGroupDisplayName" (String), and "FeatureStatus" (String).</span></span>|
||||

### <a name="sample-request"></a><span data-ttu-id="8ca9e-231">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="8ca9e-231">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/HistoricalStatus
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

### <a name="sample-response"></a><span data-ttu-id="8ca9e-232">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="8ca9e-232">Sample response</span></span>

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

## <a name="get-messages"></a><span data-ttu-id="8ca9e-233">Obter Mensagens</span><span class="sxs-lookup"><span data-stu-id="8ca9e-233">Get Messages</span></span>

<span data-ttu-id="8ca9e-234">Retorna as mensagens sobre o serviço de um determinado intervalo de tempo.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-234">Returns the messages about the service over a certain time range.</span></span> <span data-ttu-id="8ca9e-235">Use o tipo de filtro para filtrar as mensagens por "Centro de Mensagens", "Manutenção Planejada" ou "Incidente de Serviço".</span><span class="sxs-lookup"><span data-stu-id="8ca9e-235">Use the type filter to filter for "Service Incident", "Planned Maintenance", or "Message Center" messages.</span></span>

|<span data-ttu-id="8ca9e-236">Informações</span><span class="sxs-lookup"><span data-stu-id="8ca9e-236">Information</span></span>|<span data-ttu-id="8ca9e-237">Fornecer manutenção</span><span class="sxs-lookup"><span data-stu-id="8ca9e-237">Service</span></span>|<span data-ttu-id="8ca9e-238">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ca9e-238">Description</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="8ca9e-239">**Caminho**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-239">**Path**</span></span>| `/Messages`||
|<span data-ttu-id="8ca9e-240">**Filtros**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-240">**Filters**</span></span>|<span data-ttu-id="8ca9e-241">Carga de trabalho</span><span class="sxs-lookup"><span data-stu-id="8ca9e-241">Workload</span></span>|<span data-ttu-id="8ca9e-242">Filtrar por carga de trabalho (cadeia de caracteres, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-242">Filter by workload (String, default: all).</span></span>|
||<span data-ttu-id="8ca9e-243">StartTime</span><span class="sxs-lookup"><span data-stu-id="8ca9e-243">StartTime</span></span>|<span data-ttu-id="8ca9e-244">Filtrar por Hora de Início (DateTimeOffset, padrão: ge CurrentTime – 7 dias).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-244">Filter by Start Time (DateTimeOffset, default: ge CurrentTime - 7 days).</span></span>|
||<span data-ttu-id="8ca9e-245">EndTime</span><span class="sxs-lookup"><span data-stu-id="8ca9e-245">EndTime</span></span>|<span data-ttu-id="8ca9e-246">Filtrar por Hora de Término (DateTimeOffset, padrão: le CurrentTime).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-246">Filter by End Time (DateTimeOffset, default: le CurrentTime).</span></span>|
||<span data-ttu-id="8ca9e-247">MessageType</span><span class="sxs-lookup"><span data-stu-id="8ca9e-247">MessageType</span></span>|<span data-ttu-id="8ca9e-248">Filtrar por Tipo de Mensagem (Cadeia de caracteres, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-248">Filter by MessageType (String, default: all).</span></span>|
||<span data-ttu-id="8ca9e-249">Id</span><span class="sxs-lookup"><span data-stu-id="8ca9e-249">Id</span></span>|<span data-ttu-id="8ca9e-250">Filtrar por Id (Cadeia de caracteres, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-250">Filter by Id (String, default: all).</span></span>|
|<span data-ttu-id="8ca9e-251">**Query-option**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-251">**Query-option**</span></span>|<span data-ttu-id="8ca9e-252">$select</span><span class="sxs-lookup"><span data-stu-id="8ca9e-252">$select</span></span>|<span data-ttu-id="8ca9e-253">Escolha um subconjunto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-253">Pick a subset of properties.</span></span>|
||<span data-ttu-id="8ca9e-254">$top</span><span class="sxs-lookup"><span data-stu-id="8ca9e-254">$top</span></span>|<span data-ttu-id="8ca9e-255">Escolha o número máximo de resultados (padrão e máx. $top=100).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-255">Pick the top number of results (default and max $top=100).</span></span>|
||<span data-ttu-id="8ca9e-256">$skip</span><span class="sxs-lookup"><span data-stu-id="8ca9e-256">$skip</span></span>|<span data-ttu-id="8ca9e-257">Ignorar o número de resultados (padrão: $skip=0).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-257">Skip number of results (default: $skip=0).</span></span>|
|<span data-ttu-id="8ca9e-258">**Resposta**</span><span class="sxs-lookup"><span data-stu-id="8ca9e-258">**Response**</span></span>|<span data-ttu-id="8ca9e-259">Lista de entidades de "Mensagem".</span><span class="sxs-lookup"><span data-stu-id="8ca9e-259">List of "Message" entities.</span></span>|<span data-ttu-id="8ca9e-260">A entidade "Message" contém "Id" (cadeia de caracteres), "StartTime" (DateTimeOffset), "EndTime" (DateTimeOffset), "Status" (cadeia de caracteres), "Messages" (lista da entidade "MessagHistory"), "LastUpdatedTime" (DateTimeOffset), "Workload" (cadeia de caracteres), "WorkloadDisplayName" (cadeia de caracteres), "Feature" (cadeia de caracteres), "FeatureDisplayName" (cadeia de caracteres), "MessageType" (Enum, padrão: todos).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-260">"Message" entity contains "Id" (String), "StartTime" (DateTimeOffset), "EndTime" (DateTimeOffset), "Status" (String), "Messages" (list of "MessageHistory" entity), "LastUpdatedTime" (DateTimeOffset), "Workload" (String), "WorkloadDisplayName" (String), "Feature" (String), "FeatureDisplayName" (String), "MessageType" (Enum, default: all).</span></span><br/><br/><span data-ttu-id="8ca9e-261">A entidade "MessageHistory" contém "PublishedTime" (DateTimeOffset), "MessageText" (cadeia de caracteres).</span><span class="sxs-lookup"><span data-stu-id="8ca9e-261">"MessageHistory" entity contains "PublishedTime" (DateTimeOffset), "MessageText" (String).</span></span>|
||||

### <a name="sample-request"></a><span data-ttu-id="8ca9e-262">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="8ca9e-262">Sample request</span></span>

```json
GET https://manage.office.com/api/v1.0/contoso.com/ServiceComms/Messages
Authorization: Bearer {AAD_Bearer_JWT_Token}
```

### <a name="sample-response"></a><span data-ttu-id="8ca9e-263">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="8ca9e-263">Sample response</span></span>

```json
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


## <a name="errors"></a><span data-ttu-id="8ca9e-264">Erros</span><span class="sxs-lookup"><span data-stu-id="8ca9e-264">Errors</span></span>

<span data-ttu-id="8ca9e-265">Quando o serviço encontra um erro, ele relata o código de resposta do erro ao chamador, usando a sintaxe de código de erro HTTP padrão.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-265">When the service encounters an error, it reports the error response code to the caller, using standard HTTP error-code syntax.</span></span> <span data-ttu-id="8ca9e-266">Conforme descrito na [especificação OData V4](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html), as informações adicionais são incluídas no corpo da chamada que falhou como um único objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="8ca9e-266">As per [OData V4 specification](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html), additional information is included in the body of the failed call as a single JSON object.</span></span> <span data-ttu-id="8ca9e-267">Este é um exemplo de um corpo de erro JSON completo:</span><span class="sxs-lookup"><span data-stu-id="8ca9e-267">The following is an example of a full JSON error body:</span></span>


```json
{ 
    "error":{ 
        "code":"AF5000.  An internal server error occurred.",
        "message": "Retry the request." 
    } 
}
```
