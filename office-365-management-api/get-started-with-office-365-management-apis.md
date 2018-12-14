---
ms.TocTitle: Get started with Office 365 Management APIs
title: Introdução às APIs de Gerenciamento do Office 365
description: As APIs usam o Azure AD para fornecer serviços de autenticação que você pode usar para conceder direitos de acesso a esses serviços para o seu aplicativo.
ms.ContentId: 74137c9a-29e0-b588-6122-26f4d2c5e3fc
ms.topic: reference (API)
ms.date: 09/05/2018
ms.openlocfilehash: 87abfbe89f60710dc6c9981fa57bde4238790b1f
ms.sourcegitcommit: 525c0d0e78cc44ea8cb6a4bdce1858cb4ef91d57
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "25834762"
---
# <a name="get-started-with-office-365-management-apis"></a><span data-ttu-id="49bd9-103">Introdução às APIs de Gerenciamento do Office 365</span><span class="sxs-lookup"><span data-stu-id="49bd9-103">Get started with Office 365 APIs in apps</span></span>

<span data-ttu-id="49bd9-104">Quando você cria um aplicativo que precisa de acesso a serviços protegidos, como as APIs de Gerenciamento do Office 365, é necessário criar uma maneira de informar ao serviço se o aplicativo tem direito de acesso.</span><span class="sxs-lookup"><span data-stu-id="49bd9-104">When you create an application that needs access to the Office 365 API services, you need to provide a way to let the service know your application has rights to access it.</span></span> <span data-ttu-id="49bd9-105">As APIs de Gerenciamento do Office 365 usam o Azure AD para fornecer serviços de autenticação que você pode usar para conceder direitos de acesso a esses serviços para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="49bd9-105">The Office 365 APIs use Azure AD to provide authentication services that you can use to grant rights for the application to access those services.</span></span> 

<span data-ttu-id="49bd9-106">Há quatro etapas principais:</span><span class="sxs-lookup"><span data-stu-id="49bd9-106">There are four key steps:</span></span>

1. <span data-ttu-id="49bd9-107">**Registrar seu aplicativo no Azure AD**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-107">\*\*\*\* Register your application in Azure Active Directory</span></span> <span data-ttu-id="49bd9-108">Para permitir que seu aplicativo acesse as APIs de Gerenciamento do Office 365, é necessário registrá-lo no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="49bd9-108">To allow your application access to the Office 365 APIs, you need to register your application with Azure AD.</span></span> <span data-ttu-id="49bd9-109">Isso permite que você estabeleça uma identidade para o aplicativo e especifique os níveis de permissão necessários para acessar as APIs.</span><span class="sxs-lookup"><span data-stu-id="49bd9-109">This allows you to establish an identity for your application and specify the permission levels it needs to access the APIs.</span></span>
    
2. <span data-ttu-id="49bd9-110">**Obter o consentimento do administrador do locatário do Office 365**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-110">**Get Office 365 tenant admin consent**.</span></span> <span data-ttu-id="49bd9-111">Um administrador do locatário do Office 365 deve conceder explicitamente o consentimento para permitir que seu aplicativo acesse os dados de locatário por meio das APIs de Gerenciamento do Office 365.</span><span class="sxs-lookup"><span data-stu-id="49bd9-111">An Office 365 tenant admin must explicitly grant consent to allow your application to access their tenant data by means of the Office 365 Management APIs.</span></span> <span data-ttu-id="49bd9-112">O processo de consentimento é uma experiência no navegador que exige que o administrador do locatário entre na **IU de consentimento do Azure AD** e analise as permissões de acesso que seu aplicativo está solicitando e conceda ou negue a solicitação.</span><span class="sxs-lookup"><span data-stu-id="49bd9-112">The consent process is a browser-based experience that requires the tenant admin to sign in to the **Azure AD consent UI** and review the access permissions that your application is requesting, and then either grant or deny the request.</span></span> <span data-ttu-id="49bd9-113">Após o consentimento, a IU redireciona o usuário de volta ao aplicativo com um código de autorização na URL.</span><span class="sxs-lookup"><span data-stu-id="49bd9-113">After consent is granted, the UI redirects the user back to your application with an authorization code in the URL.</span></span> <span data-ttu-id="49bd9-114">O aplicativo faz uma chamada de serviço a serviço ao Azure AD para trocar esse código de autorização por um token de acesso, que contém informações sobre o administrador do locatário e seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="49bd9-114">Your application makes a service-to-service call to Azure AD to exchange this authorization code for an access token, which contains information about both the tenant admin and your application.</span></span> <span data-ttu-id="49bd9-115">A ID do locatário deve ser extraída do token de acesso e armazenada para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="49bd9-115">The tenant ID must be extracted from the access token and stored for future use.</span></span>
    
3. <span data-ttu-id="49bd9-116">**Solicitar tokens de acesso do Azure AD**.Usando as credenciais do aplicativo, conforme definidas no Azure AD, seu aplicativo solicita tokens de acesso adicionais para um locatário autorizado continuamente, sem a necessidade de mais interação do administrador do locatário.</span><span class="sxs-lookup"><span data-stu-id="49bd9-116">\*\*\*\* Request and acquire an access token from Azure AD</span></span> Using your application's credentials as configured in Azure AD, your application requests additional access tokens for a consented tenant on an ongoing basis, without the need for further tenant admin interaction. <span data-ttu-id="49bd9-118">Esses tokens de acesso são chamados de tokens somente aplicativo porque não incluem informações sobre o administrador do locatário.</span><span class="sxs-lookup"><span data-stu-id="49bd9-118">These access tokens are called app-only tokens because they do not include information about the tenant admin.</span></span>
    
4. <span data-ttu-id="49bd9-119">**Chamar as APIs de Gerenciamento do Office 365**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-119">**Call the Office 365 Management APIs**.</span></span> <span data-ttu-id="49bd9-120">Os tokens de acesso somente aplicativo são passados ​​para as APIs de Gerenciamento do Office 365 para autenticar e autorizar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="49bd9-120">The app-only access tokens are passed to the Office 365 Management APIs to authenticate and authorize your application.</span></span>
    
<span data-ttu-id="49bd9-121">O diagrama a seguir mostra a sequência de solicitações de consentimento e token de acesso.</span><span class="sxs-lookup"><span data-stu-id="49bd9-121">The following diagram shows the sequence of consent and access token requests.</span></span>


![Fluxo de autorizações de introdução às APIs de Gerenciamento](images/authorization-flow.png)


## <a name="register-your-application-in-azure-ad"></a><span data-ttu-id="49bd9-123">Registrar seu aplicativo no Azure AD</span><span class="sxs-lookup"><span data-stu-id="49bd9-123">Register your application in Azure Active Directory</span></span>

<span data-ttu-id="49bd9-124">As APIs de Gerenciamento do Office 365 usam o Azure AD para fornecer autenticação segura aos dados de locatário do Office 365.</span><span class="sxs-lookup"><span data-stu-id="49bd9-124">The Office 365 API services use Azure AD to provide secure authentication to users' Office 365 data.</span></span> <span data-ttu-id="49bd9-125">Para acessar as APIs de Gerenciamento do Office 365, é preciso registrar seu aplicativo no Azure AD e, como parte da configuração, especificar os níveis de permissão necessários para o aplicativo acessar as APIs.</span><span class="sxs-lookup"><span data-stu-id="49bd9-125">To access the Office 365 Management APIs, you need to register your app in Azure AD, and as part of the configuration, you will specify the permission levels your app needs to access the APIs.</span></span>


### <a name="prerequisites"></a><span data-ttu-id="49bd9-126">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="49bd9-126">Prerequisites</span></span>

<span data-ttu-id="49bd9-127">Para registrar seu aplicativo no Azure AD, você precisa de uma assinatura do Office 365 e de uma assinatura do Azure que tenha sido associada à assinatura do Office 365.</span><span class="sxs-lookup"><span data-stu-id="49bd9-127">To register your app in Azure AD, you need a subscription to Office 365 and a subscription to Azure that has been associated with your Office 365 subscription.</span></span> <span data-ttu-id="49bd9-128">Você pode usar assinaturas de avaliação do Office 365 e do Azure para começar.</span><span class="sxs-lookup"><span data-stu-id="49bd9-128">You can use trial subscriptions to both Office 365 and Azure to get started.</span></span> <span data-ttu-id="49bd9-129">Confira mais detalhes em [Bem-vindo ao Programa para Desenvolvedores do Office 365](https://docs.microsoft.com/pt-BR/office/developer-program/office-365-developer-program).</span><span class="sxs-lookup"><span data-stu-id="49bd9-129">For more information, see [Join the Office 365 Developer Program](https://docs.microsoft.com/pt-BR/office/developer-program/office-365-developer-program).</span></span>


### <a name="use-the-azure-management-portal-to-register-your-application-in-azure-ad"></a><span data-ttu-id="49bd9-130">Use o Portal de Gerenciamento do Azure para registrar seu aplicativo no Azure AD</span><span class="sxs-lookup"><span data-stu-id="49bd9-130">Use the Azure Management Portal to register your application in Azure AD</span></span>

<span data-ttu-id="49bd9-131">Depois de ter um locatário da Microsoft com as assinaturas adequadas, você poderá registrar seu aplicativo no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="49bd9-131">After you have a Microsoft tenant with the proper subscriptions, you can register your application in Azure AD.</span></span>

1. <span data-ttu-id="49bd9-132">Entre no [Portal de Gerenciamento do Azure](https://manage.windowsazure.com/), usando as credenciais do seu locatário da Microsoft que tem a assinatura do Office 365 que você quer usar.</span><span class="sxs-lookup"><span data-stu-id="49bd9-132">Sign into the [Azure management portal](https://manage.windowsazure.com/), using the credential of your Microsoft tenant that has the subscription to Office 365 you wish to use.</span></span> <span data-ttu-id="49bd9-133">Você também pode acessar o Portal de Gerenciamento do Azure por meio de um link que aparece no painel de navegação esquerdo no [Portal de Administração do Office](https://portal.office.com/).</span><span class="sxs-lookup"><span data-stu-id="49bd9-133">You can also access the Azure Management Portal via a link that appears in the left navigation pane in the [Office admin portal](https://portal.office.com/).</span></span>
    
2. <span data-ttu-id="49bd9-134">No painel de navegação esquerdo, escolha Active Directory (1).</span><span class="sxs-lookup"><span data-stu-id="49bd9-134">In the left navigation panel, choose Active Directory (1).</span></span> <span data-ttu-id="49bd9-135">A guia Diretório (2) deve estar selecionada. Selecione o nome do diretório (3).</span><span class="sxs-lookup"><span data-stu-id="49bd9-135">Make sure the Directory tab is selected, and then click on the directory name.</span></span>
    
   ![Página de inscrição do Office 365](images/o365-sign-up-page.png)
    
    
3. <span data-ttu-id="49bd9-137">Na página do diretório, selecione **Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-137">On the directory page, select Applications.</span></span> <span data-ttu-id="49bd9-138">O Azure AD exibe uma lista dos aplicativos instalados atualmente na sua locação.</span><span class="sxs-lookup"><span data-stu-id="49bd9-138">Azure AD displays a list of the applications currently installed in your tenancy.</span></span>
    
4. <span data-ttu-id="49bd9-139">Escolha **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-139">Choose **Add**.</span></span>
    
   ![Página do Administrador do Office 365](images/o365-admin-page.png)
    
    
5. <span data-ttu-id="49bd9-141">Selecione **Adicionar um aplicativo que minha organização esteja desenvolvendo**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-141">Select **Add an application my organization is developing**.</span></span>
    
6. <span data-ttu-id="49bd9-142">Insira o **NOME** do seu aplicativo e especifique o **Tipo** como APLICATIVO WEB E/OU API WEB.</span><span class="sxs-lookup"><span data-stu-id="49bd9-142">Enter the **NAME** of your application and specify the **Type** as WEB APPLICATION AND/OR WEB API.</span></span>
    
7. <span data-ttu-id="49bd9-143">Insira as propriedades apropriadas do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="49bd9-143">Enter the appropriate App properties:</span></span>
    
   - <span data-ttu-id="49bd9-144">**URL DE ENTRADA**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-144">Sign-on URL</span></span> <span data-ttu-id="49bd9-145">A URL em que os usuários podem entrar e usar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="49bd9-145">The Sign-on URL is the address of a web page where users can sign in and use your app.</span></span> <span data-ttu-id="49bd9-146">Você pode alterar isso mais tarde, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="49bd9-146">You can change this later as needed.</span></span>
    
   - <span data-ttu-id="49bd9-147">**URI DA ID DO APLICATIVO**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-147">App ID URI</span></span> <span data-ttu-id="49bd9-148">O URI usado como um identificador lógico exclusivo para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="49bd9-148">The URI used as a unique logical identifier for your app.</span></span> <span data-ttu-id="49bd9-149">O URI deve estar em um domínio personalizado verificado para que um usuário externo conceda ao seu aplicativo acesso aos dados no Windows Azure AD.</span><span class="sxs-lookup"><span data-stu-id="49bd9-149">The URI must be in a verified custom domain for an external user to grant your app access to their data in Windows Azure AD.</span></span> <span data-ttu-id="49bd9-150">Por exemplo, se o locatário da Microsoft é **contoso.onmicrosoft.com**, o URI da ID do aplicativo pode ser **https://app.contoso.onmicrosoft.com**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-150">For example, if your Microsoft tenant is **contoso.onmicrosoft.com**, the APP ID URI could be **https://app.contoso.onmicrosoft.com**.</span></span>
    
8. <span data-ttu-id="49bd9-151">Seu aplicativo agora está registrado no Azure AD e recebeu uma ID de cliente.</span><span class="sxs-lookup"><span data-stu-id="49bd9-151">Your app is now registered with Azure AD, and has been assigned a client ID.</span></span> <span data-ttu-id="49bd9-152">No entanto, há vários aspectos importantes do aplicativo a serem configurados.</span><span class="sxs-lookup"><span data-stu-id="49bd9-152">However, there are several important aspects of your app left to configure.</span></span>
    

### <a name="configure-your-application-properties-in-azure-ad"></a><span data-ttu-id="49bd9-153">Configurar as propriedades do aplicativo no Azure AD</span><span class="sxs-lookup"><span data-stu-id="49bd9-153">Configure your application properties in Azure AD</span></span>

<span data-ttu-id="49bd9-154">Agora que seu aplicativo está registrado, há várias propriedades importantes que você deve especificar para determinar como ele funciona no Azure AD e como os administradores de locatário darão o consentimento para permitir que o aplicativo acesse seus dados usando as APIs de Gerenciamento do Office 365.</span><span class="sxs-lookup"><span data-stu-id="49bd9-154">Now that your application is registered, there are several important properties you must specify that determine how your application functions within Azure AD and how tenant admins will grant consent to allow your application to access their data by using the Office 365 Management APIs.</span></span>

<span data-ttu-id="49bd9-155">Confira mais informações sobre a configuração do aplicativo do Azure AD em geral em [Propriedades do Objeto do Aplicativo](https://docs.microsoft.com/pt-BR/azure/active-directory/develop/active-directory-application-objects).</span><span class="sxs-lookup"><span data-stu-id="49bd9-155">For more information about Azure AD application configuration in general, see [Application Object Properties](https://docs.microsoft.com/pt-BR/azure/active-directory/develop/active-directory-application-objects).</span></span>


1. <span data-ttu-id="49bd9-156">**ID DO CLIENTE**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-156">Client ID</span></span> <span data-ttu-id="49bd9-157">Esse valor é gerado automaticamente pelo Azure AD.</span><span class="sxs-lookup"><span data-stu-id="49bd9-157">This value is automatically generated by Azure AD.</span></span> <span data-ttu-id="49bd9-158">Seu aplicativo usará esse valor ao solicitar o consentimento dos administradores do locatário e ao solicitar tokens somente aplicativo do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="49bd9-158">Your application will use this value when requesting consent from tenant admins and when requesting app-only tokens from Azure AD.</span></span>
    
2. <span data-ttu-id="49bd9-159">**O APLICATIVO É MULTILOCATÁRIO**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-159">**APPLICATION IS MULTI-TENANT**.</span></span> <span data-ttu-id="49bd9-160">Essa propriedade deve ser definida como **SIM** para permitir que os administradores de locatários deem consentimento para que o aplicativo acesse seus dados usando as APIs de Gerenciamento do Office 365.</span><span class="sxs-lookup"><span data-stu-id="49bd9-160">This property must be set to **YES** to allow tenant admins to grant consent to your app to access their data by using the Office 365 Management APIs.</span></span> <span data-ttu-id="49bd9-161">Se essa propriedade for definida como **NÃO**, seu aplicativo só poderá acessar os dados do seu próprio locatário.</span><span class="sxs-lookup"><span data-stu-id="49bd9-161">If this property is set to **NO**, your application will only be able to access your own tenant's data.</span></span>
    
3. <span data-ttu-id="49bd9-162">**URL DE RESPOSTA**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-162">Reply URL</span></span> <span data-ttu-id="49bd9-163">Esta é a URL para a qual um administrador de locatários será redirecionado após dar o consentimento para que o aplicativo acesse seus dados usando as APIs de Gerenciamento do Office 365.</span><span class="sxs-lookup"><span data-stu-id="49bd9-163">This is the URL that a tenant admin will be redirected to after granting consent to allow your application to access their data by using the Office 365 Management APIs.</span></span> <span data-ttu-id="49bd9-164">Você pode configurar várias URLs de resposta, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="49bd9-164">You can configure multiple reply URLs as needed.</span></span> <span data-ttu-id="49bd9-165">O Azure define automaticamente a primeira para corresponder à URL de logon especificada quando você criou o aplicativo, mas é possível alterar esse valor conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="49bd9-165">Azure automatically sets the first one to match the sign-on URL you specified when you created the application, but you can change this value as needed.</span></span>
    
<span data-ttu-id="49bd9-166">Escolha **Salvar** depois de fazer uma alteração nessas propriedades.</span><span class="sxs-lookup"><span data-stu-id="49bd9-166">Be sure to choose **Save** after making any changes to these properties.</span></span>


### <a name="generate-a-new-key-for-your-application"></a><span data-ttu-id="49bd9-167">Gerar uma nova chave para o aplicativo</span><span class="sxs-lookup"><span data-stu-id="49bd9-167">Generate a new app secret for your web application</span></span>

<span data-ttu-id="49bd9-168">Chaves, também conhecidas como segredos do cliente, são usadas ao trocar um código de autorização para um token de acesso.</span><span class="sxs-lookup"><span data-stu-id="49bd9-168">Keys, also known as client secrets, are used when exchanging an authorization code for an access token.</span></span>


1. <span data-ttu-id="49bd9-169">No Portal de Gerenciamento do Azure, selecione seu aplicativo e escolha **Configurar** no menu superior.</span><span class="sxs-lookup"><span data-stu-id="49bd9-169">In the Azure Management Portal, select your application and choose **Configure** in the top menu.</span></span> <span data-ttu-id="49bd9-170">Role para baixo até **chaves**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-170">Scroll down to **keys**.</span></span>
    
2. <span data-ttu-id="49bd9-171">Selecione a duração da chave e escolha **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-171">Select the duration for your key, and choose **Save**.</span></span>
    
   ![Página de assinatura do Azure](images/azure-subscription-page.png)
    
    
3. <span data-ttu-id="49bd9-173">O Azure exibe o segredo do aplicativo somente depois de salvá-lo.</span><span class="sxs-lookup"><span data-stu-id="49bd9-173">Azure displays the app secret only after saving it.</span></span> <span data-ttu-id="49bd9-174">Selecione o ícone da área de transferência para copiar o segredo do cliente para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="49bd9-174">Click the Clipboard icon to copy the client secret to the Clipboard.</span></span>
    
   ![Página do portal do Azure](images/azure-portal-page.png)

   > [!IMPORTANT] 
   > <span data-ttu-id="49bd9-176">O Azure só exibe o segredo do cliente no momento em que você o gera.</span><span class="sxs-lookup"><span data-stu-id="49bd9-176">Important Azure only displays the client secret at the time you initially generate it.</span></span> <span data-ttu-id="49bd9-177">Não é possível retornar a essa página e recuperar o segredo do cliente mais tarde.</span><span class="sxs-lookup"><span data-stu-id="49bd9-177">You cannot navigate back to this page and retrieve the client secret later.</span></span>

### <a name="configure-an-x509-certificate-to-enable-service-to-service-calls"></a><span data-ttu-id="49bd9-178">Configurar um certificado X.509 para habilitar as chamadas de serviço a serviço</span><span class="sxs-lookup"><span data-stu-id="49bd9-178">Configure an X.509 certificate to enable service-to-service calls</span></span>

<span data-ttu-id="49bd9-179">Um aplicativo que está sendo executado em segundo plano, como um daemon ou serviço, pode usar credenciais de cliente para solicitar tokens de acesso somente aplicativo sem solicitar repetidamente o consentimento do administrador do locatário após o consentimento inicial.</span><span class="sxs-lookup"><span data-stu-id="49bd9-179">An application that is running in the background, such as a daemon or service, can use client credentials to request app-only access tokens without repeatedly requesting consent from the tenant admin after initial consent is granted.</span></span> 

<span data-ttu-id="49bd9-180">Confira mais informações em [Chamadas de serviço a serviço usando credenciais do cliente](https://msdn.microsoft.com/pt-BR/library/azure/dn645543.aspx).</span><span class="sxs-lookup"><span data-stu-id="49bd9-180">For details about the authentication flow, see [Service to Service Calls Using Client Credentials](https://msdn.microsoft.com/pt-BR/library/azure/dn645543.aspx).</span></span>

<span data-ttu-id="49bd9-181">Você deve configurar um certificado X.509 com seu aplicativo para ser usado como credencial de cliente ao solicitar tokens de acesso somente aplicativo do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="49bd9-181">You must configure an X.509 certificate with your application to be used as client credentials when requesting app-only access tokens from Azure AD.</span></span> <span data-ttu-id="49bd9-182">Há duas etapas para o processo:</span><span class="sxs-lookup"><span data-stu-id="49bd9-182">There are two main components to the IRM migration process:</span></span>

- <span data-ttu-id="49bd9-183">Obter um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="49bd9-183">Obtain an X.509 certificate.</span></span> <span data-ttu-id="49bd9-184">Você pode usar um certificado autoassinado ou um certificado emitido pela autoridade de certificação confiável publicamente.</span><span class="sxs-lookup"><span data-stu-id="49bd9-184">You can use a self-signed certificate or a certificate issued by publicly trusted certificate authority.</span></span>
    
- <span data-ttu-id="49bd9-185">Modificar o manifesto do seu aplicativo para incluir a impressão digital e a chave pública do seu certificado.</span><span class="sxs-lookup"><span data-stu-id="49bd9-185">Modify your application manifest to include the thumbprint and public key of your certificate.</span></span>
    
<span data-ttu-id="49bd9-186">As instruções a seguir mostram como usar a ferramenta _makecert_ do Visual Studio ou do Windows SDK para gerar um certificado autoassinado e exportar a chave pública para um arquivo codificado em base64.</span><span class="sxs-lookup"><span data-stu-id="49bd9-186">The following instructions show you how to use the Visual Studio or Windows SDK _makecert_ tool to generate a self-signed certificate and export the public key to a base64-encoded file.</span></span>


1. <span data-ttu-id="49bd9-187">Na linha de comando, execute o seguinte:</span><span class="sxs-lookup"><span data-stu-id="49bd9-187">On the command line, run the following command:</span></span>
    
   ```
    makecert -r -pe -n "CN=MyCompanyName MyAppName Cert" -b 03/15/2015 -e 03/15/2017 -ss my -len 2048
   ```

   > [!NOTE] 
   > <span data-ttu-id="49bd9-188">Quando você estiver gerando o certificado X.509, verifique se o tamanho da chave é pelo menos 2048.</span><span class="sxs-lookup"><span data-stu-id="49bd9-188">When you are generating the X.509 certificate, make sure the key length is at least 2048.</span></span> <span data-ttu-id="49bd9-189">Comprimentos de chave mais curtos não são aceitos como chaves válidas.</span><span class="sxs-lookup"><span data-stu-id="49bd9-189">Shorter key length are not accepted as valid keys.</span></span>

2. <span data-ttu-id="49bd9-190">Abra o snap-in do MMC dos Certificados e conecte-se à sua conta de usuário.</span><span class="sxs-lookup"><span data-stu-id="49bd9-190">Open the Certificates management console snap-in and connect to your user account.</span></span> 
    
3. <span data-ttu-id="49bd9-191">Localize o novo certificado na pasta Pessoal e exporte a chave pública para um arquivo codificado em base64 (por exemplo, nomedaminhaempresa.cer).</span><span class="sxs-lookup"><span data-stu-id="49bd9-191">Find the new certificate in the Personal folder and export the public key to a base64-encoded file (for example, mycompanyname.cer).</span></span> <span data-ttu-id="49bd9-192">O aplicativo usará esse certificado para se comunicar com o Azure AD, portanto, mantenha o acesso à chave privada também.</span><span class="sxs-lookup"><span data-stu-id="49bd9-192">Your application will use this certificate to communicate with Azure AD, so make sure you retain access to the private key as well.</span></span>
    
   > [!NOTE] 
   > <span data-ttu-id="49bd9-193">Você pode usar o Windows PowerShell para extrair a chave pública codificada por impressão digital e base64.</span><span class="sxs-lookup"><span data-stu-id="49bd9-193">You can use Windows PowerShell to extract the thumbprint and base64-encoded public key.</span></span> <span data-ttu-id="49bd9-194">Outras plataformas fornecem ferramentas semelhantes para recuperar propriedades de certificados.</span><span class="sxs-lookup"><span data-stu-id="49bd9-194">Other platforms provide similar tools to retrieve properties of certificates.</span></span>

4. <span data-ttu-id="49bd9-195">No prompt do Windows PowerShell, digite e execute o seguinte:</span><span class="sxs-lookup"><span data-stu-id="49bd9-195">From the Windows PowerShell prompt, type and run the following cmdlets:</span></span>
    
   ```powershell
    $cer = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2
    $cer.Import("mycer.cer")
    $bin = $cer.GetRawCertData()
    $base64Value = [System.Convert]::ToBase64String($bin)
    $bin = $cer.GetCertHash()
    $base64Thumbprint = [System.Convert]::ToBase64String($bin)
    $keyid = [System.Guid]::NewGuid().ToString()
   ```

5. <span data-ttu-id="49bd9-196">Armazene os valores para `$base64Thumbprint`, `$base64Value` e `$keyid` a serem usados ​​quando você atualizar o manifesto do aplicativo no próximo conjunto de etapas.</span><span class="sxs-lookup"><span data-stu-id="49bd9-196">Store the values for `$base64Thumbprint`, `$base64Value`, and `$keyid` to be used when you update your application manifest in the next set of steps.</span></span>
    
   <span data-ttu-id="49bd9-197">Usando os valores extraídos do certificado e da ID de chave gerada, você deve atualizar o manifesto do seu aplicativo no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="49bd9-197">Using the values extracted from the certificate and the generated key ID, you must now update your application manifest in Azure AD.</span></span>
    
6. <span data-ttu-id="49bd9-198">No Portal de Gerenciamento do Azure, selecione seu aplicativo e escolha **Configurar** no menu superior.</span><span class="sxs-lookup"><span data-stu-id="49bd9-198">In the Azure Management Portal, select your application and choose **Configure** in the top menu.</span></span>
    
7. <span data-ttu-id="49bd9-199">Na barra de comandos, escolha **Gerenciar Manifesto** e depois **Baixar Manifesto**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-199">In the command bar, choose **Manage manifest**, and then choose **Download Manifest**.</span></span>
    
   ![Exibição de certificado da linha de comando](images/command-line-certificate-display.png)
    
    
8. <span data-ttu-id="49bd9-201">Abra o manifesto baixado para edição e substitua a propriedade vazia KeyCredentials pelo seguinte JSON:</span><span class="sxs-lookup"><span data-stu-id="49bd9-201">Open the downloaded file for editing and replace the empty KeyCredentials property with the following JSON:</span></span>
    
   ```json
      "keyCredentials": [
        {
            "customKeyIdentifier" : "$base64Thumbprint_from_above",
            "keyId": "$keyid_from_above",
            "type": "AsymmetricX509Cert",
            "usage": "Verify",
            "value": "$base64Value_from_above"
        }
    ],
   ```


   > [!NOTE] 
   > <span data-ttu-id="49bd9-202">A propriedade [KeyCredentials](https://msdn.microsoft.com/library/azure/ad/graph/api/entity-and-complex-type-reference#KeyCredentialType) é uma coleção, possibilitando o upload de vários certificados X.509 para cenários de sobreposição ou a exclusão de certificados para cenários de comprometimento.</span><span class="sxs-lookup"><span data-stu-id="49bd9-202">The [KeyCredentials](https://msdn.microsoft.com/library/azure/ad/graph/api/entity-and-complex-type-reference#KeyCredentialType) property is a collection, making it possible to upload multiple X.509 certificates for rollover scenarios or delete certificates for compromise scenarios.</span></span>

9. <span data-ttu-id="49bd9-203">Salve suas alterações e faça o upload do manifesto atualizado escolhendo **Gerenciar Manifesto** na barra de comandos, escolhendo **Carregar Manifesto**, navegando até o arquivo de manifesto atualizado e selecionando-o.</span><span class="sxs-lookup"><span data-stu-id="49bd9-203">Save your changes, and upload the updated app manifest file by clicking **Manage manifest** in the command bar, selecting **Upload manifest**, browsing to your updated manifest file and then selecting it.</span></span>
    

### <a name="specify-the-permissions-your-app-requires-to-access-the-office-365-management-apis"></a><span data-ttu-id="49bd9-204">Especificar as permissões que o aplicativo requer para acessar as APIs de Gerenciamento do Office 365</span><span class="sxs-lookup"><span data-stu-id="49bd9-204">Specify the permissions your app requires to access the Office 365 Management APIs</span></span>

<span data-ttu-id="49bd9-205">Por fim, você precisa especificar exatamente quais permissões seu aplicativo requer das APIs de Gerenciamento do Office 365.</span><span class="sxs-lookup"><span data-stu-id="49bd9-205">Finally, you'll need to specify exactly what permissions your app requires of the Office 365 APIs.</span></span> <span data-ttu-id="49bd9-206">Para isso, adicione acesso às APIs de Gerenciamento do Office 365 ao seu aplicativo e especifique as permissões necessárias.</span><span class="sxs-lookup"><span data-stu-id="49bd9-206">To do so, you add access to the Office 365 service containing the API you require to your app, and then specify the permission(s) you need from the APIs in that service.</span></span>


1. <span data-ttu-id="49bd9-207">No Portal de Gerenciamento do Azure, selecione seu aplicativo e escolha **Configurar** no menu superior.</span><span class="sxs-lookup"><span data-stu-id="49bd9-207">In the Azure Management Portal, select your application and choose **Configure** in the top menu.</span></span> <span data-ttu-id="49bd9-208">Role a tela até \*\*Permissões para outros aplicativos \*\* e escolha **Adicionar aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-208">Scroll down to the **permissions to other applications** section and click the **Add application** button.</span></span>
    
   ![Página do Azure AD](images/azure-ad-page.png)
    
    
2. <span data-ttu-id="49bd9-210">Selecione **APIs de Gerenciamento do Office 365** (1) para que isso apareça na coluna **Selecionada** (2) e depois a marca de seleção no canto inferior direito (3) para salvar sua alteração e retornar à página de configuração principal do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="49bd9-210">Select the **Office 365 Management APIs** (1) so that it appears in the **Selected** column (2), and then select the check mark in the lower right (3) to save your selection and return to the main configuration page for your application.</span></span>
    
   ![Página de aplicativos do Azure AD](images/azure-ad-apps-page.png)
    
    
3. <span data-ttu-id="49bd9-212">Agora, as APIs de Gerenciamento do Office aparecem na lista de aplicativos para os quais seu aplicativo requer permissões.</span><span class="sxs-lookup"><span data-stu-id="49bd9-212">The Office Management APIs now appear in the list of applications to which your application requires permissions.</span></span> <span data-ttu-id="49bd9-213">Em **Permissões de Aplicativo** e **Permissões Delegadas**, selecione as permissões que seu aplicativo requer.</span><span class="sxs-lookup"><span data-stu-id="49bd9-213">Under both **Application Permissions** and **Delegated Permissions**, select the permissions your application requires.</span></span> <span data-ttu-id="49bd9-214">Confira mais detalhes sobre cada permissão na referência da API específica.</span><span class="sxs-lookup"><span data-stu-id="49bd9-214">Refer to the specific API reference for more details about each permission.</span></span>  

   > [!NOTE] 
   > <span data-ttu-id="49bd9-215">Atualmente, há quatro permissões não usadas relacionadas a relatórios de atividades e informações sobre ameaças que serão removidas no futuro.</span><span class="sxs-lookup"><span data-stu-id="49bd9-215">There are currently four unused permissions related to activity reports and threat intelligence that will be removed in the future.</span></span> <span data-ttu-id="49bd9-216">Não selecione essas permissões porque elas são desnecessárias.</span><span class="sxs-lookup"><span data-stu-id="49bd9-216">Do not select any of these permissions because they are unnecessary.</span></span>
    
   ![Adicionar uma caixa de diálogo do aplicativo](images/add-an-application-dialog.png)
    
    
4. <span data-ttu-id="49bd9-218">Escolha **Salvar** para salvar a configuração.</span><span class="sxs-lookup"><span data-stu-id="49bd9-218">Choose **Save** to save the rule.</span></span>
    

## <a name="get-office-365-tenant-admin-consent"></a><span data-ttu-id="49bd9-219">Obter o consentimento do administrador do locatário do Office 365</span><span class="sxs-lookup"><span data-stu-id="49bd9-219">Get Office 365 tenant admin consent</span></span>

<span data-ttu-id="49bd9-220">Agora que o aplicativo está configurado com as permissões necessárias para usar as APIs de Gerenciamento do Office 365, um administrador de locatário deve conceder explicitamente ao seu aplicativo essas permissões para acessar os dados de seus locatários usando as APIs.</span><span class="sxs-lookup"><span data-stu-id="49bd9-220">Now that your application is configured with the permissions it needs to use the Office 365 Management APIs, a tenant admin must explicitly grant your application these permissions in order to access their tenant's data by using the APIs.</span></span> <span data-ttu-id="49bd9-221">Para dar o consentimento, o administrador do locatário deve entrar no Azure AD usando a seguinte URL especialmente criada, em que eles podem revisar as permissões solicitadas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="49bd9-221">To grant consent, the tenant admin must sign in to Azure AD by using the following specially constructed URL, where they can review your application's requested permissions.</span></span> <span data-ttu-id="49bd9-222">Esta etapa não é necessária ao usar as APIs para acessar dados de seu próprio locatário.</span><span class="sxs-lookup"><span data-stu-id="49bd9-222">This step is not required when using the APIs to access data from your own tenant.</span></span>


```http
https://login.windows.net/common/oauth2/authorize?response_type=code&resource=https%3A%2F%2Fmanage.office.com&client_id={your_client_id}&redirect_uri={your_redirect_url }
```

<span data-ttu-id="49bd9-223">A URL de redirecionamento deve corresponder ou ser um subcaminho em uma das URLs de resposta configuradas para seu aplicativo no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="49bd9-223">The redirect URL must match or be a sub-path under one of the Reply URLs configured for your application in Azure AD.</span></span>

<span data-ttu-id="49bd9-224">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="49bd9-224">For example:</span></span>

```http
https://login.windows.net/common/oauth2/authorize?response_type=code&resource=https%3A%2F%2Fmanage.office.com&client_id=2d4d11a2-f814-46a7-890a-274a72a7309e&redirect_uri=http%3A%2F%2Fwww.mycompany.com%2Fmyapp%2F
```

<span data-ttu-id="49bd9-225">Você pode testar a URL de consentimento colando-a em um navegador e entrando usando as credenciais de um administrador do Office 365 para um locatário que não seja o usado para registrar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="49bd9-225">You can test the consent URL by pasting it into a browser and signing in using the credentials of an Office 365 admin for a tenant other than the tenant that you used to register the application.</span></span> <span data-ttu-id="49bd9-226">Você verá a solicitação para conceder ao seu aplicativo permissão para usar as APIs de Gerenciamento do Office.</span><span class="sxs-lookup"><span data-stu-id="49bd9-226">You will see the request to grant your application permission to use the Office Management APIs.</span></span>


![Página adicionada do aplicativo Azure AD](images/azure-ad-app-added-page.png)

<span data-ttu-id="49bd9-228">Depois de escolher **Aceitar**, você será redirecionado para a página especificada, e haverá um código na cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="49bd9-228">After choosing **Accept**, you are redirected to the specified page, and there will be a code in the query string.</span></span> 

<span data-ttu-id="49bd9-229">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="49bd9-229">For example:</span></span>

```http
http://www.mycompany.com/myapp/?code=AAABAAAAvPM1KaPlrEqdFSB...
```

<span data-ttu-id="49bd9-230">Seu aplicativo usa esse código de autorização para obter um token de acesso do Azure AD, do qual a ID do locatário pode ser extraída.</span><span class="sxs-lookup"><span data-stu-id="49bd9-230">Your application uses this authorization code to obtain an access token from Azure AD, from which the tenant ID can be extracted.</span></span> <span data-ttu-id="49bd9-231">Depois de extrair e armazenar a ID do locatário, você poderá obter os tokens de acesso subsequentes sem exigir que o administrador do locatário se conecte.</span><span class="sxs-lookup"><span data-stu-id="49bd9-231">After you have extracted and stored the tenant ID, you can obtain subsequent access tokens without requiring the tenant admin to sign in.</span></span>


## <a name="request-access-tokens-from-azure-ad"></a><span data-ttu-id="49bd9-232">Solicitar tokens de acesso do Azure AD</span><span class="sxs-lookup"><span data-stu-id="49bd9-232">Request and acquire an access token from Azure AD</span></span>

<span data-ttu-id="49bd9-233">Há dois métodos para solicitar tokens de acesso do Azure AD:</span><span class="sxs-lookup"><span data-stu-id="49bd9-233">There are two methods for requesting access tokens from Azure AD:</span></span>

- <span data-ttu-id="49bd9-234">O [Fluxo de Concessão do Código de Autorização](https://msdn.microsoft.com/en-us/library/azure/dn645542.aspx) envolve um administrador do locatário que dá o consentimento explícito, que retorna um código de autorização para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="49bd9-234">The [Authorization Code Grant Flow](https://msdn.microsoft.com/en-us/library/azure/dn645542.aspx) involves a tenant admin granting explicit consent, which returns an authorization code to your application.</span></span> <span data-ttu-id="49bd9-235">Seu aplicativo então troca o código de autorização por um token de acesso.</span><span class="sxs-lookup"><span data-stu-id="49bd9-235">Your application then exchanges the authorization code for an access token.</span></span> <span data-ttu-id="49bd9-236">Este método é necessário para obter o consentimento inicial de que seu aplicativo precisa para acessar os dados do locatário usando a API, e esse primeiro token de acesso é necessário para obter e armazenar o ID do locatário.</span><span class="sxs-lookup"><span data-stu-id="49bd9-236">This method is required to obtain the initial consent that your application needs to access the tenant data by using the API, and this first access token is needed in order to obtain and store the tenant ID.</span></span>
    
- <span data-ttu-id="49bd9-237">O [Fluxo de Concessão de Credenciais do Cliente](https://msdn.microsoft.com/pt-BR/library/azure/dn645543.aspx) permite que seu aplicativo solicite tokens de acesso subsequentes à medida que os antigos expirem, sem exigir que o administrador do locatário faça login e dê explicitamente o consentimento.</span><span class="sxs-lookup"><span data-stu-id="49bd9-237">The [Client Credentials Grant Flow](https://msdn.microsoft.com/pt-BR/library/azure/dn645543.aspx) allows your application to request subsequent access tokens as old ones expire, without requiring the tenant admin to sign in and explicitly grant consent.</span></span> <span data-ttu-id="49bd9-238">Esse método deve ser usado para aplicativos que são executados continuamente em segundo plano chamando as APIs depois que o consentimento inicial do administrador do locatário é dado.</span><span class="sxs-lookup"><span data-stu-id="49bd9-238">This method must be used for applications that run continuously in the background calling the APIs once the initial tenant admin consent has been granted.</span></span>
    

### <a name="request-an-access-token-using-the-authorization-code"></a><span data-ttu-id="49bd9-239">Solicitar um token de acesso usando o código de autorização</span><span class="sxs-lookup"><span data-stu-id="49bd9-239">Request an access token using the authorization code</span></span>

<span data-ttu-id="49bd9-240">Depois que um administrador de locatário der o consentimento, seu aplicativo receberá um código de autorização como um parâmetro de string de consulta quando o Azure AD redirecionar o administrador do locatário para a URL designada.</span><span class="sxs-lookup"><span data-stu-id="49bd9-240">After a tenant admin grants consent, your application receives an authorization code as a query string parameter when Azure AD redirects the tenant admin to your designated URL.</span></span>

```http
http://www.mycompany.com/myapp/?code=AAABAAAAvPM1KaPlrEqdFSB...
```

<span data-ttu-id="49bd9-241">Seu aplicativo faz um HTTP REST POST para o Azure AD para trocar o código de autorização de um token de acesso.</span><span class="sxs-lookup"><span data-stu-id="49bd9-241">Your application makes an HTTP REST POST to Azure AD to exchange the authorization code for an access token.</span></span> <span data-ttu-id="49bd9-242">Como a ID do locatário ainda não é conhecida, o POST será para o ponto de extremidade "comum", que não possui a ID do locatário incorporada à URL:</span><span class="sxs-lookup"><span data-stu-id="49bd9-242">Because the tenant ID is not yet known, the POST will be to the "common" endpoint, which does not have the tenant ID embedded in the URL:</span></span>

```http
https://login.windows.net/common/oauth2/token
```

<span data-ttu-id="49bd9-243">O corpo do POST contém o seguinte:</span><span class="sxs-lookup"><span data-stu-id="49bd9-243">The body of the POST contains the following:</span></span>

```json
resource=https%3A%2F%2Fmanage.office.com&amp;client_id=a6099727-6b7b-482c-b509-1df309acc563 &amp;redirect_uri= http%3A%2F%2Fwww.mycompany.com%2Fmyapp%2F &amp;client_secret={your_client_key}&amp;grant_type=authorization_code&amp;code= AAABAAAAvPM1KaPlrEqdFSB...
```

#### <a name="sample-request"></a><span data-ttu-id="49bd9-244">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="49bd9-244">Sample request</span></span>

```json
POST https://login.windows.net/common/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.windows.net
Content-Length: 944

resource=https%3A%2F%2Fmanage.office.com&amp;client_id=a6099727-6b7b-482c-b509-1df309acc563 &amp;redirect_uri= http%3A%2F%2Fwww.mycompany.com%2Fmyapp%2F &amp;client_secret={your_client_key}&amp;grant_type=authorization_code&amp;code=AAABAAAAvPM1KaPlrEqdFSB...
```

<br/>

<span data-ttu-id="49bd9-245">O corpo da resposta incluirá várias propriedades, inclusive o token de acesso.</span><span class="sxs-lookup"><span data-stu-id="49bd9-245">The body of the response will include several properties, including the access token.</span></span> 

#### <a name="sample-response"></a><span data-ttu-id="49bd9-246">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="49bd9-246">Sample response</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Content-Length: 3265

{"expires_in":"3599","token_type":"Bearer","scope":"ActivityFeed.Read ActivityReports.Read ServiceHealth.Read","expires_on":"1438290275","not_before":"1438286375","resource":"https://manage.office.com","access_token":"eyJ0eX...","refresh_token":"AAABAAA...","id_token":"eyJ0eXAi..."}
```

<span data-ttu-id="49bd9-247">O token de acesso retornado é um token JWT que inclui informações sobre o administrador que deu o consentimento e o aplicativo que está solicitando acesso.</span><span class="sxs-lookup"><span data-stu-id="49bd9-247">The access token that is returned is a JWT token that includes information about both the admin that granted consent and the application requesting access.</span></span> <span data-ttu-id="49bd9-248">A seguir temos um exemplo de um token não codificado.</span><span class="sxs-lookup"><span data-stu-id="49bd9-248">The following shows an example of an un-encoded token.</span></span> <span data-ttu-id="49bd9-249">O aplicativo deve extrair a ID de locatário "tid" desse token e armazená-la para que ela possa ser usada para solicitar tokens de acesso adicionais à medida que eles expiram, sem interação administrativa posterior.</span><span class="sxs-lookup"><span data-stu-id="49bd9-249">Your application must extract the tenant ID "tid" from this token and store it so that it can be used to request additional access tokens as they expire, without further admin interaction.</span></span>

#### <a name="sample-token"></a><span data-ttu-id="49bd9-250">Token de amostra</span><span class="sxs-lookup"><span data-stu-id="49bd9-250">Sample token</span></span>

```json
{
  "aud": "https://manage.office.com",
  "iss": "https://sts.windows.net/41463f53-8812-40f4-890f-865bf6e35190/",
  "iat": 1427246416,
  "nbf": 1427246416,
  "exp": 1427250316,
  "ver": "1.0",
  "tid": "41463f53-8812-40f4-890f-865bf6e35190",
  "amr": [
    "pwd"
  ],
  "oid": "1cef1fdb-ff52-48c4-8e4e-dfb5ea83d357",
  "upn": "admin@contoso.onmicrosoft.com",
  "puid": "1003BFFD8EC47CA6",
  "sub": "7XpD5OWAXM1OWmKiVKh1FOkKXV4N3OSRol6mz1pxxhU",
  "given_name": "John",
  "family_name": "Doe",
  "name": "Contoso, Inc.",
  "unique_name": "admin@contoso.onmicrosoft.com",
  "appid": "a6099727-6b7b-482c-b509-1df309acc563",
  "appidacr": "1",
  "scp": "ActivityFeed.Read ServiceHealth.Read",
  "acr": "1"
}
```


### <a name="request-an-access-token-by-using-client-credentials"></a><span data-ttu-id="49bd9-251">Solicitar um token de acesso usando credenciais de cliente</span><span class="sxs-lookup"><span data-stu-id="49bd9-251">Request an access token by using client credentials</span></span>

<span data-ttu-id="49bd9-252">Depois que a ID do locatário é conhecida, seu aplicativo pode fazer chamadas de serviço a serviço ao Azure AD para solicitar tokens de acesso adicionais à medida que eles expiram.</span><span class="sxs-lookup"><span data-stu-id="49bd9-252">After the tenant ID is known, your application can make service-to-service calls to Azure AD to request additional access tokens as they expire.</span></span> <span data-ttu-id="49bd9-253">Esses tokens incluem informações apenas sobre o aplicativo solicitante e não sobre o administrador que originalmente deu o consentimento.</span><span class="sxs-lookup"><span data-stu-id="49bd9-253">These tokens include information only about the requesting application and not about the admin that originally granted consent.</span></span> <span data-ttu-id="49bd9-254">Chamadas de serviço a serviço requerem que seu aplicativo use um certificado X.509 para criar uma declaração de cliente na forma de um token de portador JWT assinado em SHA256 codificado em base64.</span><span class="sxs-lookup"><span data-stu-id="49bd9-254">Service-to-service calls require that your application use an X.509 certificate to create client assertion in the form of a base64-encoded, SHA256 signed JWT bearer token.</span></span>

<span data-ttu-id="49bd9-255">Quando desenvolve seu aplicativo no .NET, você pode usar a [Biblioteca de Autenticação do Azure AD (ADAL)](https://docs.microsoft.com/pt-BR/azure/active-directory/develop/active-directory-authentication-libraries) para criar declarações de clientes.</span><span class="sxs-lookup"><span data-stu-id="49bd9-255">When you are developing your application in .NET, you can use the [Azure AD Authentication Library (ADAL)](https://docs.microsoft.com/pt-BR/azure/active-directory/develop/active-directory-authentication-libraries) to create client assertions.</span></span> <span data-ttu-id="49bd9-256">Outras plataformas de desenvolvimento devem ter bibliotecas semelhantes.</span><span class="sxs-lookup"><span data-stu-id="49bd9-256">Other development platforms should have similar libraries.</span></span>

<span data-ttu-id="49bd9-257">Um token JWT não codificado consiste em um cabeçalho e o conteúdo com as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="49bd9-257">An un-encoded JWT token consists of a header and payload that have the following properties.</span></span>

```json
HEADER:

{
  "alg": "RS256",
  "x5t": "{thumbprint of your X.509 certificate used to sign the token",
}

PAYLOAD:

{
  "aud": "https://login.windows.net/{tenantid}/oauth2/token",
  "iss": "{your app client ID}",
  "sub": "{your app client ID}"
  "jti": "{random GUID}",
  "nbf": {epoch time, before which the token is not valid},
  "exp": {epoch time, after which the token is not valid},
}

```

#### <a name="sample-jwt-token"></a><span data-ttu-id="49bd9-258">Token JWT de amostra</span><span class="sxs-lookup"><span data-stu-id="49bd9-258">Sample JWT token</span></span>


```json
HEADER:

{
  "alg": "RS256",
  "x5t": "YyfshJC3rPQ-kpGo5dUaiY5t3iU",
}

PAYLOAD:

{
  "aud": "https://login.windows.net/41463f53-8812-40f4-890f-865bf6e35190/oauth2/token",
  "iss": "a6099727-6b7b-482c-b509-1df309acc563",
  "sub": "a6099727-6b7b-482c-b509-1df309acc563"
  "jti": "0ce254c4-81b1-4a2e-8436-9a8c3b49dfb9",
  "nbf": 1427248048,
  "exp": 1427248648,
}
```

<span data-ttu-id="49bd9-259">A asserção do cliente é então passada para o Azure AD como parte de uma chamada de serviço a serviço para solicitar um token de acesso.</span><span class="sxs-lookup"><span data-stu-id="49bd9-259">The client assertion is then passed to Azure AD as part of a service-to-service call to request an access token.</span></span> <span data-ttu-id="49bd9-260">Ao usar as credenciais do cliente para solicitar um token de acesso, use um HTTP POST para um ponto de extremidade específico do locatário, onde a ID do locatário previamente extraída e armazenada é incorporada na URL.</span><span class="sxs-lookup"><span data-stu-id="49bd9-260">When using client credentials to request an access token, use an HTTP POST to a tenant-specific endpoint, where the previously extracted and stored tenant ID is embedded in the URL.</span></span>


```http
https://login.windows.net/{tenantid}/oauth2/token
```

<span data-ttu-id="49bd9-261">O corpo do POST contém o seguinte:</span><span class="sxs-lookup"><span data-stu-id="49bd9-261">The body of the POST contains the following:</span></span>


```json
resource=https%3A%2F%2Fmanage.office.com&amp;client_id={your_app_client_id}&amp;grant_type=client_credentials&amp;client_assertion_type=urn%3Aietf%3Aparams%3Aoauth%3Aclient-assertion-type%3Ajwt-bearer&amp;client_assertion={encoded_signed_JWT_token}
```

#### <a name="sample-request"></a><span data-ttu-id="49bd9-262">Solicitação de amostra</span><span class="sxs-lookup"><span data-stu-id="49bd9-262">Sample request</span></span>

```json
POST https://login.windows.net/41463f53-8812-40f4-890f-865bf6e35190/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.windows.net
Content-Length: 994

resource=https%3A%2F%2Fmanage.office.com&amp;client_id= a6099727-6b7b-482c-b509-1df309acc563&amp;grant_type=client_credentials &amp;client_assertion_type=urn%3Aietf%3Aparams%3Aoauth%3Aclient-assertion-type%3Ajwt-bearer&amp;client_assertion=eyJhbGciOiJSUzI1NiIsIng1dCI6Ill5ZnNoSkMzclBRLWtwR281ZFVhaVk1dDNpVSJ9.eyJhdWQiOiJodHRwczpcL1wvbG9naW4ud2luZG93cy5uZXRcLzQxNDYzZjUzLTg4MTItNDBmNC04OTBmLTg2NWJmNmUzNTE5MFwvb2F1dGgyXC90b2tlbiIsImV4cCI6MTQyNzI0ODY0OCwiaXNzIjoiYTYwOTk3MjctNmI3Yi00ODJjLWI1MDktMWRmMzA5YWNjNTYzIiwianRpIjoiMGNlMjU0YzQtODFiMS00YTJlLTg0MzYtOWE4YzNiNDlkZmI5IiwibmJmIjoxNDI3MjQ4MDQ4LCJzdWIiOiJhNjA5OTcyNy02YjdiLTQ4MmMtYjUwOS0xZGYzMDlhY2M1NjMifQ.vfDrmCjiXgoj2JrTkwyOpr-NOeQTzlXQcGlKGNpLLe0oh4Zvjdcim5C7E0UbI3Z2yb9uKQdx9G7GeqS-gVc9kNV_XSSNP4wEQj3iYNKpf_JD2ikUVIWBkOg41BiTuknRJAYOMjiuBE2a6Wyk-vPCs_JMd7Sr-N3LiNZ-TjluuVzWHfok_HWz_wH8AzdoMF3S0HtrjNd9Ld5eI7MVMt4OTpRfh-Syofi7Ow0HN07nKT5FYeC_ThBpGiIoODnMQQtDA2tM7D3D6OlLQRgLfI8ir73PVXWL7V7Zj2RcOiooIeXx38dvuSwYreJYtdphmrDBZ2ehqtduzUZhaHL1iDvLlw
```

<span data-ttu-id="49bd9-263">A resposta será a mesma de antes, mas o token não terá as mesmas propriedades porque não contém propriedades do administrador que deu o consentimento.</span><span class="sxs-lookup"><span data-stu-id="49bd9-263">The response will be the same as before, but the token will not have the same properties, because it does not contain properties of the admin that granted consent.</span></span> 

#### <a name="sample-response"></a><span data-ttu-id="49bd9-264">Resposta de amostra</span><span class="sxs-lookup"><span data-stu-id="49bd9-264">Sample response</span></span>

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Content-Length: 1276

{"token_type":"Bearer","expires_in":"3599","expires_on":"1431659094","not_before":"1431655194","resource":"https://manage.office.com","access_token":"eyJ0eXAiOiJKV1QiL..."}
```

#### <a name="sample-access-token"></a><span data-ttu-id="49bd9-265">Token de acesso de amostra</span><span class="sxs-lookup"><span data-stu-id="49bd9-265">Sample access token</span></span>

```json
{
  "aud": "https://manage.office.com",
  "iss": "https://sts.windows.net/41463f53-8812-40f4-890f-865bf6e35190/",
  "iat": 1431655194,
  "nbf": 1431655194,
  "exp": 1431659094,
  "ver": "1.0",
  "tid": "41463f53-8812-40f4-890f-865bf6e35190",
  "roles": [
    "ServiceHealth.Read",
    "ActivityFeed.Read"
  ],
  "oid": "67cb0334-e242-4783-8028-0f39132fb5ad",
  "sub": "67cb0334-e242-4783-8028-0f39132fb5ad",
  "idp": "https://sts.windows.net/41463f53-8812-40f4-890f-865bf6e35190/",
  "appid": "a6099727-6b7b-482c-b509-1df309acc563",
  "appidacr": "1"
}
```


## <a name="build-your-app"></a><span data-ttu-id="49bd9-266">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="49bd9-266">Build your app</span></span>

<span data-ttu-id="49bd9-267">Agora que você registrou o aplicativo no Azure AD e o configurou com as permissões necessárias, está pronto para criar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="49bd9-267">Now that you have registered your app in Azure AD and configured it with the necessary permissions, you're ready to build your app.</span></span> <span data-ttu-id="49bd9-268">A seguir, alguns dos principais aspectos a serem considerados ao projetar e criar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="49bd9-268">The following are some of the key aspects to consider when designing and building your app:</span></span>

- <span data-ttu-id="49bd9-269">**A experiência de consentimento**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-269">**The consent experience**.</span></span> <span data-ttu-id="49bd9-270">Para obter o consentimento dos clientes, você deve direcioná-los em um navegador para o site do Azure AD, usando a URL especialmente criada descrita anteriormente, e você deve ter um site para o qual o Azure AD redirecionará o administrador assim que der o consentimento.</span><span class="sxs-lookup"><span data-stu-id="49bd9-270">To obtain consent from your customers, you must direct them in a browser to the Azure AD website, using the specially constructed URL described previously, and you must have a website to which Azure AD will redirect the admin once they grant consent.</span></span> <span data-ttu-id="49bd9-271">Este site deve extrair o código de autorização da URL e usá-lo para solicitar um token de acesso do qual possa obter a ID do locatário.</span><span class="sxs-lookup"><span data-stu-id="49bd9-271">This website must extract the authorization code from the URL and use it to request an access token from which it can obtain the tenant ID.</span></span>
    
- <span data-ttu-id="49bd9-272">**Armazenamento da ID do locatário em seu sistema**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-272">**Store the tenant ID in your system**.</span></span> <span data-ttu-id="49bd9-273">Isso será necessário ao solicitar tokens de acesso do Azure AD e ao chamar as APIs de Gerenciamento do Office.</span><span class="sxs-lookup"><span data-stu-id="49bd9-273">This will be needed when requesting access tokens from Azure AD and when calling the Office Management APIs.</span></span>
    
- <span data-ttu-id="49bd9-274">**Gerenciamento dos tokens de acesso**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-274">**Managing access tokens**.</span></span> <span data-ttu-id="49bd9-275">Você precisará de um componente que solicite e gerencie os tokens de acesso conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="49bd9-275">You will need a component that requests and manages access tokens as needed.</span></span> <span data-ttu-id="49bd9-276">Se seu aplicativo chamar as APIs periodicamente, ele poderá solicitar tokens sob demanda ou, se chamar as APIs continuamente para recuperar dados, poderá solicitar tokens em intervalos regulares (por exemplo, a cada 45 minutos).</span><span class="sxs-lookup"><span data-stu-id="49bd9-276">If your app calls the APIs periodically, it can request tokens on demand, or if it calls the APIs continuously to retrieve data, it can request tokens at regular intervals (for example, every 45 minutes).</span></span>
    
- <span data-ttu-id="49bd9-277">**Implementar um ouvinte de webhook** conforme necessário pela API específica que você está usando.</span><span class="sxs-lookup"><span data-stu-id="49bd9-277">**Implement a webhook listener** as needed by the particular API you are using.</span></span>
    
- <span data-ttu-id="49bd9-278">**Recuperação e armazenamento de dados**.</span><span class="sxs-lookup"><span data-stu-id="49bd9-278">**Data retrieval and storage**.</span></span> <span data-ttu-id="49bd9-279">Você precisará de um componente que recupere dados para cada locatário, usando a pesquisa contínua ou em resposta às notificações do webhook, dependendo da API específica que estiver usando.</span><span class="sxs-lookup"><span data-stu-id="49bd9-279">You'll need a component that retrieves data for each tenant, either by using continuous polling or in response to webhook notifications, depending on the particular API you are using.</span></span>
    