---
ms.technology: o365-service-communications
ms.TocTitle: Get started with Office 365 Management APIs
title: Introdução às APIs de Gerenciamento do Office 365
description: As APIs usam o Azure AD para fornecer serviços de autenticação que você pode usar para conceder direitos de acesso a esses serviços para o seu aplicativo.
ms.ContentId: 74137c9a-29e0-b588-6122-26f4d2c5e3fc
ms.topic: reference (API)
ms.date: ''
ms.localizationpriority: high
ms.openlocfilehash: ef4ea62f03eb9d536bf42234d9a9f5b28de005e8
ms.sourcegitcommit: 6c9efd49e6406ee72edc7450afa811d6c660992c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2021
ms.locfileid: "60235842"
---
# <a name="get-started-with-office-365-management-apis"></a>Introdução às APIs de Gerenciamento do Office 365

Quando você cria um aplicativo que precisa de acesso a serviços protegidos, como as APIs de Gerenciamento do Office 365, é necessário criar uma maneira de informar ao serviço se o aplicativo tem direito de acesso. As APIs de Gerenciamento do Office 365 usam o Azure AD para fornecer serviços de autenticação que você pode usar para conceder direitos de acesso a esses serviços para o aplicativo. 

Há quatro etapas principais:

1. **Registrar seu aplicativo no Azure AD**. Para permitir que seu aplicativo acesse as APIs de Gerenciamento do Office 365, é necessário registrá-lo no Azure AD. Isso permite que você estabeleça uma identidade para o aplicativo e especifique os níveis de permissão necessários para acessar as APIs.
    
2. **Obter o consentimento do administrador do locatário do Office 365**. Um administrador do locatário do Office 365 deve conceder explicitamente o consentimento para permitir que seu aplicativo acesse os dados de locatário por meio das APIs de Gerenciamento do Office 365. O processo de consentimento é uma experiência no navegador que exige que o administrador do locatário entre na **IU de consentimento do Azure AD** e analise as permissões de acesso que seu aplicativo está solicitando e conceda ou negue a solicitação. Após o consentimento, a IU redireciona o usuário de volta ao aplicativo com um código de autorização na URL. O aplicativo faz uma chamada de serviço a serviço ao Azure AD para trocar esse código de autorização por um token de acesso, que contém informações sobre o administrador do locatário e seu aplicativo. A ID do locatário deve ser extraída do token de acesso e armazenada para uso futuro.
    
3. **Solicitar tokens de acesso do Azure AD**. Usando as credenciais do aplicativo, conforme definidas no Azure AD, seu aplicativo solicita tokens de acesso adicionais para um locatário autorizado continuamente, sem a necessidade de mais interação do administrador do locatário. Esses tokens de acesso são chamados de tokens somente aplicativo porque não incluem informações sobre o administrador do locatário.
    
4. **Chamar as APIs de Gerenciamento do Office 365**. Os tokens de acesso somente do aplicativo são passados para as APIs de Gerenciamento do Office 365 para autenticar e autorizar seu aplicativo.
    
O diagrama a seguir mostra a sequência de solicitações de consentimento e token de acesso.

![Fluxo de autorizações de introdução às APIs de Gerenciamento](images/authorization-flow.png)

> [!IMPORTANT]
> Para poder acessar dados por meio da API de Atividade de Gerenciamento do Office 365, habilite o log de auditoria unificado para a sua organização do Office 365. Para fazer isso, ative o log de auditoria do Office 365. Para obter instruções, confira [Ativar ou desativar a pesquisa de log de auditoria do Office 365](/office365/securitycompliance/turn-audit-log-search-on-or-off). <br/><br/>A habilitação do log de auditoria unificado não é necessária se você usa apenas a API de Comunicações de Serviço do Office 365.

## <a name="register-your-application-in-azure-ad"></a>Registrar seu aplicativo no Azure AD

As APIs de Gerenciamento do Office 365 usam o Azure AD para fornecer autenticação segura aos dados de locatário do Office 365. Para acessar as APIs de Gerenciamento do Office 365, é preciso registrar seu aplicativo no Azure AD e, como parte da configuração, especificar os níveis de permissão necessários para o aplicativo acessar as APIs.

### <a name="prerequisites"></a>Pré-requisitos

Para registrar seu aplicativo no Azure AD, você precisa de uma assinatura do Office 365 e de uma assinatura do Azure que tenha sido associada à assinatura do Office 365. Você pode usar assinaturas de avaliação do Office 365 e do Azure para começar. Confira mais detalhes em [Bem-vindo ao Programa para Desenvolvedores do Office 365](/office/developer-program/office-365-developer-program).

### <a name="use-the-azure-portal-to-register-your-application-in-azure-ad"></a>Use o Portal Azure para registrar seu aplicativo no Microsoft Azure AD

Depois de ter um locatário da Microsoft com as assinaturas adequadas, você poderá registrar seu aplicativo no Azure AD.

1. Entre no[portal do Azure](https://portal.azure.com), usando as credenciais do seu locatário da Microsoft que tem a assinatura do Office 365 que você deseja usar. Você também pode acessar o Portal do Azure através de um link que aparece no painel de navegação esquerdo no [Centro de administração do Microsoft 365](https://admin.microsoft.com/).

2. No painel de navegação esquerdo, selecione **Azure Active Directory** (1).

   ![Página principal do Portal Azure](images/AzurePortal1.png)

3. Na página **Azure Active Directory**, selecione **Registros de aplicativos** (2) e, em seguida, selecione **Novo registro** (3).

   ![Página de registro de aplicativos no Azure Active Directory](images/AzureAppRegistration2.png)

4. Na página de **Registros de Aplicativo**, selecione **Novo registro**.

   Uma nova página aparecerá para você iniciar o registro do aplicativo.

5. Na página **Registrar um aplicativo**, faça o seguinte:

   ![Processo de registro do aplicativo](images/AzureAppRegistration3.png)

   1. Nomeie seu aplicativo.

   2. Escolha quem pode usar o aplicativo e acessar a API.

   3. Forneça um URL de redirecionamento para o redirecionamento do usuário após a autenticação, se necessário.

6. Clique em **Registrar** para registrar o novo aplicativo.

### <a name="configure-your-application-properties-in-azure-ad"></a>Configurar as propriedades do aplicativo no Azure AD

Agora que seu aplicativo está registrado, há várias propriedades importantes que você deve especificar para determinar como ele funciona no Azure AD e como os administradores de locatário darão o consentimento para permitir que o aplicativo acesse seus dados usando as APIs de Gerenciamento do Office 365.

Confira mais informações sobre a configuração do aplicativo do Azure AD em geral em [Propriedades do Objeto do Aplicativo](/azure/active-directory/develop/active-directory-application-objects).

1. **ID do cliente**. Esse valor é gerado automaticamente pelo Azure AD. Seu aplicativo usará esse valor ao solicitar o consentimento dos administradores do locatário e ao solicitar tokens somente aplicativo do Azure AD.

2. **O aplicativo é multilocatário**. Essa propriedade deve ser definida como **SIM** para permitir que os administradores de locatários deem consentimento para que o aplicativo acesse seus dados usando as APIs de Gerenciamento do Office 365. Se essa propriedade for definida como **NÃO**, seu aplicativo só poderá acessar os dados do seu próprio locatário.

3. **URL de resposta**. Esta é a URL para a qual um administrador de locatários será redirecionado após dar o consentimento para que o aplicativo acesse seus dados usando as APIs de Gerenciamento do Office 365. Você pode configurar várias URLs de resposta, conforme necessário. O Azure define automaticamente a primeira para corresponder à URL de logon especificada quando você criou o aplicativo, mas é possível alterar esse valor conforme necessário.

Escolha **Salvar** depois de fazer uma alteração nessas propriedades.

### <a name="generate-a-new-key-for-your-application"></a>Gerar uma nova chave para o aplicativo

As chaves, também conhecidas como *segredos do cliente*, são usadas ao trocar um código de autorização por um token de acesso.

1. Na página **Azure Active Directory** no portal do Azure, selecione **Registros de aplicativos**, e então selecione seu aplicativo.

    ![Selecione o aplicativo que você acabou de registrar](images/AzureAppRegistration4.png)

2. Depois que a página do aplicativo for exibida, selecione **Certificados e segredos** (1) no painel esquerdo. Nesta página, você pode fazer o upload de certificados e criar novos segredos do cliente (2).

    ![A página de Certificados e segredos do aplicativo](images\AzureAppRegistrationCertificatesSecrets.png)

3. Na página **Certificados e segredos** (1), selecione **Novo segredo do cliente** (2), digite uma descrição e selecione a duração da sua chave (3) e, em seguida, selecione **Adicionar** (4).

   ![Criar um segredo do cliente](images\AzureAppRegistration5.png)

4. Depois de criar o segredo do cliente, o valor será exibido em **Segredos do cliente** (2). Clique no ícone da área de transferência (3) para copiar o valor do segredo do cliente para a área de transferência.

   ![Copie o valor do segredo do cliente para a área de transferência e salve-o para uso posterior](images\AzureAppRegistration6.png)

   > [!IMPORTANT]
   > O Azure só exibe o valor do segredo do cliente no momento em que você o gera inicialmente. Você não pode voltar a esta página e recuperar o valor do segredo do cliente mais tarde. Certifique-se de copiá-lo e salvá-lo em um local seguro para que você possa utilizá-lo mais tarde.

### <a name="configure-an-x509-certificate-to-enable-service-to-service-calls"></a>Configurar um certificado X.509 para habilitar as chamadas de serviço a serviço

Um aplicativo que está sendo executado em segundo plano, como um daemon ou serviço, pode usar credenciais de cliente para solicitar tokens de acesso somente aplicativo sem solicitar repetidamente o consentimento do administrador do locatário após o consentimento inicial.

Confira mais informações em [Chamadas de serviço a serviço usando credenciais do cliente](https://msdn.microsoft.com/library/azure/dn645543.aspx).

Você deve configurar um certificado X.509 com seu aplicativo para ser usado como credenciais de cliente ao solicitar tokens de acesso somente de aplicativo do Microsoft Azure Active Directory. Há duas etapas para o processo:

- Obtenha um certificado X.509. Você pode usar um certificado autoassinado ou um certificado emitido por uma autoridade de certificação publicamente confiável.

- Modificar o manifesto do seu aplicativo para incluir a impressão digital e a chave pública do seu certificado.

As instruções a seguir mostram como usar a ferramenta _makecert_ do Visual Studio ou do Windows SDK para gerar um certificado autoassinado e exportar a chave pública para um arquivo codificado em base64.

1. Na linha de comando, execute o seguinte:

   ```powershell
    makecert -r -pe -n "CN=MyCompanyName MyAppName Cert" -b 03/15/2015 -e 03/15/2017 -ss my -len 2048
   ```

   > [!NOTE]
   > Quando você estiver gerando o certificado X.509, verifique se o tamanho da chave é pelo menos 2048. Comprimentos de chave mais curtos não são aceitos como chaves válidas.

2. Abra o snap-in do MMC dos Certificados e conecte-se à sua conta de usuário.

3. Localize o novo certificado na pasta Pessoal e exporte a chave pública para um arquivo codificado em base64 (por exemplo, `mycompanyname.cer`). O aplicativo usará esse certificado para se comunicar com o Azure AD, portanto, mantenha o acesso à chave privada também.

   > [!NOTE]
   > Você pode usar o Windows PowerShell para extrair a chave pública codificada por impressão digital e base64. Outras plataformas fornecem ferramentas semelhantes para recuperar propriedades de certificados.

4. A partir de um prompt do Windows PowerShell, digite e execute o seguinte:

   ```powershell
    $cer = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2
    $cer.Import("mycer.cer")
    $bin = $cer.GetRawCertData()
    $base64Value = [System.Convert]::ToBase64String($bin)
    $bin = $cer.GetCertHash()
    $base64Thumbprint = [System.Convert]::ToBase64String($bin)
    $keyid = [System.Guid]::NewGuid().ToString()
   ```

5. Armazene os valores para `$base64Thumbprint`, `$base64Value` e `$keyid` a serem usados ​​quando você atualizar o manifesto do aplicativo no próximo conjunto de etapas.

   Usando os valores extraídos do certificado e da ID de chave gerada, você deve atualizar o manifesto do seu aplicativo no Azure AD.

6. No Portal do Azure, acesse **Registros de aplicativos** > **Todos os aplicativos**, selecione seu aplicativo e, em seguida, selecione **Manifesto** no painel esquerdo.

7. Na barra de navegação superior da página **Manifesto** (1), selecione **Baixar** (2).

   ![Baixe o manifesto para que você possa editá-lo](images/AzureAppRegistration7.png)

8. Abra o manifesto baixado em um editor e substitua a propriedade *keyCredentials* vazia pelo seguinte JSON:
    
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
   > A propriedade [KeyCredentials](https://msdn.microsoft.com/library/azure/ad/graph/api/entity-and-complex-type-reference#KeyCredentialType) é uma coleção, possibilitando o upload de vários certificados X.509 para cenários de sobreposição ou a exclusão de certificados para cenários de comprometimento.

9. Salve suas alterações e faça o upload do manifesto atualizado escolhendo **Gerenciar Manifesto** na barra de comandos, escolhendo **Carregar Manifesto**, navegando até o arquivo de manifesto atualizado e selecionando-o.

### <a name="specify-the-permissions-your-app-requires-to-access-the-office-365-management-apis"></a>Especificar as permissões que o aplicativo requer para acessar as APIs de Gerenciamento do Office 365

Por fim, você precisa especificar exatamente quais permissões seu aplicativo requer das APIs de Gerenciamento do Office 365. Para isso, adicione acesso às APIs de Gerenciamento do Office 365 ao seu aplicativo e especifique as permissões necessárias.

1. No Portal do Azure, acesse **Registros de aplicativos** > **Todos os aplicativos**, selecione seu aplicativo e, em seguida, selecione **Permissões de API** (1) no painel esquerdo. Clique em **Adicionar uma permissão** (2) para exibir a página do submenu **Solicitação de permissão de API** (3).

   ![Adicionar permissões de API](images/AzureAppRegistration8.png)

2. Na guia **APIs da Microsoft**, selecione **APIs de Gerenciamento do Office 365** (4).

   ![Selecione as APIs de Gerenciamento do Office 365 na guia de APIs da Microsoft](images/AzureAppRegistration9.png)

3. Na página de submenu, selecione os seguintes tipos de permissões (3) exigidos pelo aplicativo e clique em **Adicionar permissões**

   ![Selecione os tipos de permissões para seu aplicativo](images/AzureAppRegistration10.png)

   1. **Permissões delegadas**. Permite que seu aplicativo cliente execute operações em nome do usuário conectado, como a leitura de email ou a modificação do perfil do usuário.

   2. **Permissões de Aplicativos**. Permissões que possibilitam que o aplicativo cliente se autentique como ele mesmo sem interação ou consentimento do usuário, como um aplicativo usado por serviços em segundo plano ou aplicativos daemon.

4. As APIs de Gerenciamento do Office agora aparecem na lista de aplicativos para os quais seu aplicativo exige permissões. Em **Permissões do aplicativo** e **Permissões delegadas**, se necessário, selecione as permissões exigidas pelo aplicativo. Confira mais detalhes sobre cada permissão na referência da API específica.  

   ![Permissões de API para seu aplicativo](images/AzureAppRegistration11.png)

5. Selecione **Conceder consentimento de administrador para “nome do locatário"** para consentir com as permissões concedidas ao seu aplicativo.

## <a name="get-office-365-tenant-admin-consent"></a>Obter o consentimento do administrador do locatário do Office 365

Agora que o aplicativo está configurado com as permissões necessárias para usar as APIs de Gerenciamento do Office 365, um administrador de locatário deve conceder explicitamente ao seu aplicativo essas permissões para acessar os dados de seus locatários usando as APIs. Para dar o consentimento, o administrador do locatário deve entrar no Azure AD usando a seguinte URL especialmente criada, em que eles podem revisar as permissões solicitadas do aplicativo. Esta etapa não é necessária ao usar as APIs para acessar dados de seu próprio locatário.

```http
https://login.windows.net/common/oauth2/authorize?response_type=code&resource=https%3A%2F%2Fmanage.office.com&client_id={your_client_id}&redirect_uri={your_redirect_url }
```

A URL de redirecionamento deve corresponder ou ser um subcaminho em uma das URLs de resposta configuradas para seu aplicativo no Azure AD.

Por exemplo:

```http
https://login.windows.net/common/oauth2/authorize?response_type=code&resource=https%3A%2F%2Fmanage.office.com&client_id=2d4d11a2-f814-46a7-890a-274a72a7309e&redirect_uri=http%3A%2F%2Fwww.mycompany.com%2Fmyapp%2F
```

Você pode testar a URL de consentimento colando-a em um navegador e entrando usando as credenciais de um administrador do Office 365 para um locatário diferente do locatário que você usou para registrar o aplicativo. Você verá a solicitação para conceder permissão ao aplicativo para usar as APIs de Gerenciamento do Office.

![Página de consentimento de permissões](images/AzureAppRegistration12.png)

Depois de escolher **Aceitar**, você será redirecionado para a página especificada, e haverá um código na cadeia de caracteres de consulta.

Por exemplo:

```http
http://www.mycompany.com/myapp/?code=AAABAAAAvPM1KaPlrEqdFSB...
```

Seu aplicativo usa esse código de autorização para obter um token de acesso do Azure AD, do qual a ID do locatário pode ser extraída. Depois de extrair e armazenar a ID do locatário, você poderá obter os tokens de acesso subsequentes sem exigir que o administrador do locatário se conecte.

## <a name="request-access-tokens-from-azure-ad"></a>Solicitar tokens de acesso do Azure AD

Há dois métodos para solicitar tokens de acesso do Azure AD:

- O [Fluxo de Concessão do Código de Autorização](https://msdn.microsoft.com/library/azure/dn645542.aspx) envolve um administrador do locatário que dá o consentimento explícito, que retorna um código de autorização para o aplicativo. Seu aplicativo então troca o código de autorização por um token de acesso. Este método é necessário para obter o consentimento inicial de que seu aplicativo precisa para acessar os dados do locatário usando a API, e esse primeiro token de acesso é necessário para obter e armazenar o ID do locatário.
    
- O [Fluxo de Concessão de Credenciais do Cliente](https://msdn.microsoft.com/library/azure/dn645543.aspx) permite que seu aplicativo solicite tokens de acesso subsequentes à medida que os antigos expirem, sem exigir que o administrador do locatário faça login e dê explicitamente o consentimento. Esse método deve ser usado para aplicativos que são executados continuamente em segundo plano chamando as APIs depois que o consentimento inicial do administrador do locatário é dado.
    

### <a name="request-an-access-token-using-the-authorization-code"></a>Solicitar um token de acesso usando o código de autorização

Depois que um administrador de locatário der o consentimento, seu aplicativo receberá um código de autorização como um parâmetro de string de consulta quando o Azure AD redirecionar o administrador do locatário para a URL designada.

```http
http://www.mycompany.com/myapp/?code=AAABAAAAvPM1KaPlrEqdFSB...
```

Seu aplicativo faz um HTTP REST POST para o Azure AD para trocar o código de autorização de um token de acesso. Como a ID do locatário ainda não é conhecida, o POST será para o ponto de extremidade "comum", que não possui a ID do locatário incorporada à URL:

```http
https://login.windows.net/common/oauth2/token
```

O corpo do POST contém o seguinte:

```json
resource=https%3A%2F%2Fmanage.office.com&amp;client_id=a6099727-6b7b-482c-b509-1df309acc563 &amp;redirect_uri= http%3A%2F%2Fwww.mycompany.com%2Fmyapp%2F &amp;client_secret={your_client_key}&amp;grant_type=authorization_code&amp;code= AAABAAAAvPM1KaPlrEqdFSB...
```

#### <a name="sample-request"></a>Solicitação de amostra

```json
POST https://login.windows.net/common/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.windows.net
Content-Length: 944

resource=https%3A%2F%2Fmanage.office.com&amp;client_id=a6099727-6b7b-482c-b509-1df309acc563 &amp;redirect_uri= http%3A%2F%2Fwww.mycompany.com%2Fmyapp%2F &amp;client_secret={your_client_key}&amp;grant_type=authorization_code&amp;code=AAABAAAAvPM1KaPlrEqdFSB...
```

<br/>

O corpo da resposta incluirá várias propriedades, inclusive o token de acesso.

#### <a name="sample-response"></a>Resposta de amostra

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Content-Length: 3265

{"expires_in":"3599","token_type":"Bearer","scope":"ActivityFeed.Read ActivityReports.Read ServiceHealth.Read","expires_on":"1438290275","not_before":"1438286375","resource":"https://manage.office.com","access_token":"eyJ0eX...","refresh_token":"AAABAAA...","id_token":"eyJ0eXAi..."}
```

O token de acesso retornado é um token JWT que inclui informações sobre o administrador que deu o consentimento e o aplicativo que está solicitando acesso. A seguir temos um exemplo de um token não codificado. O aplicativo deve extrair a ID de locatário "tid" desse token e armazená-la para que ela possa ser usada para solicitar tokens de acesso adicionais à medida que eles expiram, sem interação administrativa posterior.

#### <a name="sample-token"></a>Token de amostra

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

### <a name="request-an-access-token-by-using-client-credentials"></a>Solicitar um token de acesso usando credenciais de cliente

Depois que a ID do locatário é conhecida, seu aplicativo pode fazer chamadas de serviço a serviço ao Azure AD para solicitar tokens de acesso adicionais à medida que eles expiram. Esses tokens incluem informações apenas sobre o aplicativo solicitante e não sobre o administrador que originalmente deu o consentimento. Chamadas de serviço a serviço requerem que seu aplicativo use um certificado X.509 para criar uma declaração de cliente na forma de um token de portador JWT assinado em SHA256 codificado em base64.

Quando você estiver desenvolvendo su aplicativo em.NET, você poderá usar a [Biblioteca de Autenticação do Microsoft Azure AD (ADAL)](/azure/active-directory/develop/active-directory-authentication-libraries) para criar declarações de cliente. Outras plataformas de desenvolvimento devem ter bibliotecas semelhantes.

Um token JWT não codificado consiste em um cabeçalho e o conteúdo com as seguintes propriedades.

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

#### <a name="sample-jwt-token"></a>Token JWT de amostra


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

A asserção do cliente é então passada para o Azure AD como parte de uma chamada de serviço a serviço para solicitar um token de acesso. Ao usar as credenciais do cliente para solicitar um token de acesso, use um HTTP POST para um ponto de extremidade específico do locatário, onde a ID do locatário previamente extraída e armazenada é incorporada na URL.


```http
https://login.windows.net/{tenantid}/oauth2/token
```

O corpo do POST contém o seguinte:


```json
resource=https%3A%2F%2Fmanage.office.com&amp;client_id={your_app_client_id}&amp;grant_type=client_credentials&amp;client_assertion_type=urn%3Aietf%3Aparams%3Aoauth%3Aclient-assertion-type%3Ajwt-bearer&amp;client_assertion={encoded_signed_JWT_token}
```

#### <a name="sample-request"></a>Solicitação de amostra

```json
POST https://login.windows.net/41463f53-8812-40f4-890f-865bf6e35190/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.windows.net
Content-Length: 994

resource=https%3A%2F%2Fmanage.office.com&amp;client_id= a6099727-6b7b-482c-b509-1df309acc563&amp;grant_type=client_credentials &amp;client_assertion_type=urn%3Aietf%3Aparams%3Aoauth%3Aclient-assertion-type%3Ajwt-bearer&amp;client_assertion=eyJhbGciOiJSUzI1NiIsIng1dCI6Ill5ZnNoSkMzclBRLWtwR281ZFVhaVk1dDNpVSJ9.eyJhdWQiOiJodHRwczpcL1wvbG9naW4ud2luZG93cy5uZXRcLzQxNDYzZjUzLTg4MTItNDBmNC04OTBmLTg2NWJmNmUzNTE5MFwvb2F1dGgyXC90b2tlbiIsImV4cCI6MTQyNzI0ODY0OCwiaXNzIjoiYTYwOTk3MjctNmI3Yi00ODJjLWI1MDktMWRmMzA5YWNjNTYzIiwianRpIjoiMGNlMjU0YzQtODFiMS00YTJlLTg0MzYtOWE4YzNiNDlkZmI5IiwibmJmIjoxNDI3MjQ4MDQ4LCJzdWIiOiJhNjA5OTcyNy02YjdiLTQ4MmMtYjUwOS0xZGYzMDlhY2M1NjMifQ.vfDrmCjiXgoj2JrTkwyOpr-NOeQTzlXQcGlKGNpLLe0oh4Zvjdcim5C7E0UbI3Z2yb9uKQdx9G7GeqS-gVc9kNV_XSSNP4wEQj3iYNKpf_JD2ikUVIWBkOg41BiTuknRJAYOMjiuBE2a6Wyk-vPCs_JMd7Sr-N3LiNZ-TjluuVzWHfok_HWz_wH8AzdoMF3S0HtrjNd9Ld5eI7MVMt4OTpRfh-Syofi7Ow0HN07nKT5FYeC_ThBpGiIoODnMQQtDA2tM7D3D6OlLQRgLfI8ir73PVXWL7V7Zj2RcOiooIeXx38dvuSwYreJYtdphmrDBZ2ehqtduzUZhaHL1iDvLlw
```

A resposta será a mesma de antes, mas o token não terá as mesmas propriedades porque não contém propriedades do administrador que deu o consentimento. 

#### <a name="sample-response"></a>Resposta de amostra

```json
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Content-Length: 1276

{"token_type":"Bearer","expires_in":"3599","expires_on":"1431659094","not_before":"1431655194","resource":"https://manage.office.com","access_token":"eyJ0eXAiOiJKV1QiL..."}
```

#### <a name="sample-access-token"></a>Token de acesso de amostra

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


## <a name="build-your-app"></a>Criar seu aplicativo

Agora que você registrou o aplicativo no Azure AD e o configurou com as permissões necessárias, está pronto para criar seu aplicativo. A seguir, alguns dos principais aspectos a serem considerados ao projetar e criar seu aplicativo:

- **A experiência de consentimento**. Para obter o consentimento dos clientes, você deve direcioná-los em um navegador para o site do Azure AD, usando a URL especialmente criada descrita anteriormente, e você deve ter um site para o qual o Azure AD redirecionará o administrador assim que der o consentimento. Este site deve extrair o código de autorização da URL e usá-lo para solicitar um token de acesso do qual possa obter a ID do locatário.
    
- **Armazenamento da ID do locatário no seu sistema**. Isso será necessário ao solicitar tokens de acesso do Microsoft Azure AD e ao chamar as APIs de Gerenciamento do Office.
    
- **Gerenciamento de tokens de acesso**. Você precisará de um componente que solicite e gerencie os tokens de acesso conforme necessário. Se o aplicativo chamar as APIs periodicamente, ele poderá solicitar tokens sob demanda ou, se chamar as APIs continuamente para recuperar dados, poderá solicitar tokens em intervalos regulares (por exemplo, a cada 45 minutos).
    
- **Implementar um ouvinte de webhook** conforme necessário pela API específica que você está usando.
    
- **Recuperação e armazenamento de dados**. Você precisará de um componente que recupere os dados de cada locatário, usando sondagem contínua ou em resposta a notificações do webhook, dependendo da API específica que você está usando.
    
