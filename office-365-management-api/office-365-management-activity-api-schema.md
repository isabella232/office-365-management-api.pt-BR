---
ms.TocTitle: Office 365 Management Activity API schema
title: Esquema da API da Atividade de Gerenciamento do Office 365
description: 'O esquema da API da Atividade de Gerenciamento do Office 365 é fornecido como um serviço de dados em duas camadas: esquema Comum e esquema específico do produto.'
ms.ContentId: 1c2bf08c-4f3b-26c0-e1b2-90b190f641f5
ms.topic: reference (API)
ms.date: ''
localization_priority: Priority
ms.openlocfilehash: 012d2951c12b5da0b5767ff3edd2dd7fb64fd695
ms.sourcegitcommit: 1345cb6bd688ee7ca4320b073eacdf614dae9b08
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "35601527"
---
# <a name="office-365-management-activity-api-schema"></a>Esquema da API da Atividade de Gerenciamento do Office 365
 
O esquema da API da Atividade de Gerenciamento do Office 365 é fornecido como um serviço de dados em duas camadas:

- **Esquema comum**. A interface para acessar os principais conceitos de auditoria do Office 365, como Tipo de Registro, Hora de Criação, Tipo de Usuário e Ação, além de fornecer dimensões principais (como ID de Usuário), detalhes de local (como endereço IP do Cliente) e propriedades específicas do produto (como Identificação do Objeto). Ele estabelece exibições uniformes e consistentes para os usuários extraírem todos os dados de auditoria do Office 365 em algumas exibições de nível superior com os parâmetros apropriados e fornece um esquema fixo para todas as fontes de dados, o que reduz significativamente o custo do aprendizado. O esquema Comum é originado de dados de produto que pertencem a cada equipe de produto, como o Exchange, o SharePoint, o Azure Active Directory, o Yammer e o OneDrive for Business. O campo Identificação do Objeto pode ser estendido por equipes de produto para adicionar propriedades específicas do produto.
    
- **Esquema específico do produto**. Desenvolvido com base no esquema Comum para fornecer um conjunto de atributos específicos do produto; por exemplo, esquema do Sway, esquema do SharePoint, esquema do OneDrive for Business e esquema de administração do Exchange.
    
**Qual camada você deve usar para o seu cenário?**
Em geral, se os dados estiverem disponíveis em uma camada superior, não retorne a uma camada inferior. Em outras palavras, se os requisitos de dados puderem ser ajustados a um esquema específico do produto, não é preciso retornar ao esquema Comum. 

## <a name="office-365-management-api-schemas"></a>Esquemas da API de Gerenciamento do Office 365

Este artigo fornece detalhes sobre o esquema Comum, bem como cada um dos esquemas específicos de produto. A tabela a seguir descreve os esquemas disponíveis. 

|Nome do esquema|Descrição|
|:-----|:-----|
|[Esquema Comum](#common-schema)|O modo de exibição para extrair o Tipo de Registro, ID de Usuário, IP do Cliente, Tipo de Usuário e Ação junto com as dimensões principais, como propriedades do usuário (como UserID), propriedades de localização (como IP do Cliente) e propriedades específicas do produto (como Identificação do Objeto).|
|[Esquema Base do SharePoint](#sharepoint-base-schema)|Estende o esquema Comum com as propriedades específicas de todos os dados de auditoria do SharePoint.|
|[Operações de Arquivos do SharePoint](#sharepoint-file-operations)|Estende o esquema Base do SharePoint com as propriedades específicas do acesso e manipulação de arquivos no SharePoint.|
|[Esquema de compartilhamento do SharePoint](#sharepoint-sharing-schema)|Estende o esquema Base do SharePoint com as propriedades específicas do compartilhamento de arquivos.|
|[Esquema do SharePoint](#sharepoint-schema)|Estende o esquema Base do SharePoint com as propriedades específicas do SharePoint, mas não está relacionado ao acesso e manipulação de arquivos.|
|[Esquema do Project](#project-schema)|Estende o esquema Base do SharePoint com as propriedades específicas do Project.|
|[Esquema de administração do Exchange](#exchange-admin-schema)|Estende o esquema Comum com as propriedades específicas de todos os dados de auditoria do Exchange.|
|[Esquema de caixa de correio do Exchange](#exchange-mailbox-schema)|Estende o esquema Comum com as propriedades específicas de todos os dados de auditoria da caixa de correio do Exchange.|
|[Esquema Base do Azure Active Directory](#azure-active-directory-base-schema)|Estende o esquema Comum com as propriedades específicas de todos os dados de auditoria do Azure Active Directory.|
|[Esquema de Logon da Conta do Azure Active Directory](#azure-active-directory-account-logon-schema)|Estende o esquema Base do Azure Active Directory com as propriedades específicas de todos os eventos de logon do Azure Active Directory.|
|[Esquema de logon seguro do STS do Active Directory do Azure](#azure-active-directory-secure-token-service-sts-logon-schema)|Estende o esquema de base do Azure Active Directory às propriedades específicas de todos os eventos de logon do Serviço de Token Seguro (STS) do Active Directory do Azure.|
|[Esquema do Azure Active Directory](#azure-active-directory-schema)|Estende o esquema Comum com as propriedades específicas de todos os dados de auditoria do Azure Active Directory.|
|[Esquema DLP](#dlp-schema)|Estende o esquema Comum com as propriedades específicas de Eventos de Prevenção Contra Perda de Dados.|
|[Esquema do Centro de Conformidade e Segurança](#security-and-compliance-center-schema)|Estende o esquema Comum com as propriedades específicas de todos os Eventos do Centro de Conformidade e Segurança.|
|[Esquema de Alertas de Conformidade e Segurança](#security-and-compliance-alerts-schema)|Estende o esquema Comum com as propriedades específicas de todos os alertas de conformidade e segurança do Office 365.|
|[Esquema do Yammer](#yammer-schema)|Estende o esquema Comum com as propriedades específicas de todos os eventos do Yammer.|
|[Esquema do Sway](#sway-schema)|Estende o esquema Comum com as propriedades específicas de todos os eventos do Sway.|
|[Esquema Base de Segurança do Data Center](#data-center-security-base-schema)|Estende o esquema Comum com as propriedades específicas de todos os dados de auditoria de segurança do data center.|
|[Esquema Cmdlet de Segurança do Data Center](#data-center-security-cmdlet-schema)|Estende o esquema Base de Segurança do Data Center com as propriedades específicas de todos os dados de auditoria do cmdlet de segurança do datacenter.|
|[Esquema do Microsoft Teams](#microsoft-teams-schema)|Estende o esquema Comum com as propriedades específicas de todos os eventos do Microsoft Teams.|
|[Esquema de complementos do Microsoft Teams](#microsoft-teams-add-ons-schema)|Estende o esquema do Microsoft Teams com as propriedades específicas dos complementos do Microsoft Teams.|
|[Esquema de Configurações do Microsoft Teams](#microsoft-teams-settings-schema)|Estende o esquema do Microsoft Teams com as propriedades específicas dos eventos de alteração de configurações do Microsoft Teams.|
|[Esquema de Proteção Avançada contra Ameaças e Investigação e Resposta contra Ameaças do Office 365](#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema)|Estende o esquema Comum com as propriedades específicas dos dados da Proteção Avançada contra Ameaças e Investigação e Resposta contra Ameaças do Office 365.|
|[Esquema do Power BI](#power-bi-schema)|Estende o esquema Comum com as propriedades específicas de todos os eventos do Power BI.|
|[Workplace Analytics](#workplace-analytics-schema)|Estende o esquema Comum com as propriedades específicas de todos os eventos do Microsoft Workplace Analytics.|
|||

## <a name="common-schema"></a>Esquema Comum

**EntityType Name**: AuditRecord

|Parâmetro|Tipo|Obrigatório?|Descrição|
|:-----|:-----|:-----|:-----|
|Id|Combination GUIDEdm.Guid|Sim|Identificador exclusivo de um registro de auditoria.|
|RecordType|Self.[AuditLogRecordType](#auditlogrecordtype)|Sim|O tipo de operação indicado pelo registro. Confira a tabela [AuditLogRecordType](#auditlogrecordtype) para obter detalhes sobre os tipos de registros de log de auditoria.|
|CreationTime|Edm.Date|Sim|A data e hora no Tempo Universal Coordenado (UTC) de quando o usuário realizou a atividade.|
|Operation|Edm.String|Sim|O nome do usuário ou atividade administrativa. Para obter uma descrição das operações/atividades mais comuns, veja [Pesquisar o log de auditoria no Centro de Proteção do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=708432). Para a atividade de administração do Exchange, essa propriedade identifica o nome do cmdlet que foi executado. Para eventos Dlp, as opções podem ser "DlpRuleMatch", "DlpRuleUndo" ou "DlpInfo", que são descritas em "Esquema DLP" abaixo.|
|OrganizationId|Edm.Guid|Sim|O GUID do locatário do Office 365 da sua organização. Este valor será sempre o mesmo para a sua organização, independentemente do serviço do Office 365 em que ocorre.|
|UserType|Self.[UserType](#user-type)|Sim|O tipo de usuário que executou a operação. Confira a tabela [UserType](#user-type) para detalhes sobre os tipos de usuários.|
|UserKey|Edm.String|Sim|Uma ID alternativa para o usuário identificado na propriedade UserId. Por exemplo, essa propriedade é preenchida com a ID exclusiva do passaporte (PUID) para eventos executados por usuários no SharePoint, no OneDrive for Business e no Exchange. Essa propriedade também pode especificar o mesmo valor da propriedade UserID para eventos que ocorrem em outros serviços e eventos executados por contas do sistema.|
|Workload|Edm.String|Não|O serviço do Office 365 em que a atividade ocorreu. 
|ResultStatus|Edm.String|Não|Indica se a ação (especificada na propriedade Operation) foi bem-sucedida ou não. Os valores possíveis são **Succeeded**, **PartiallySucceeded** ou **Failed**. Para a atividade de administração do Exchange, o valor é **Verdadeiro** ou **Falso**.<br/><br/>**Importante**: Cargas de trabalho diferentes podem substituir o valor da propriedade ResultStatus. Por exemplo, para eventos de logon do STS do Active Directory do Azure, um valor de **Sucesso** para ResultStatus indica apenas que a operação HTTP foi bem-sucedida; isso não significa que o logon foi bem-sucedido. Para determinar se o logon real foi bem-sucedido ou não, consulte a propriedade LogonError no [esquema de logon do STS do Azure Active Directory](#azure-active-directory-secure-token-service-sts-logon-schema). Se o logon falhar, o valor dessa propriedade conterá o motivo da falha na tentativa de logon. |
|ObjectId|Edm.string|Não|Para atividades do SharePoint e do OneDrive for Business, o nome do caminho completo do arquivo ou pasta acessado pelo usuário. Para o log de auditoria do administrador do Exchange, o nome do objeto que foi modificado pelo cmdlet.|
|UserId|Edm.string|Sim|O UPN (User Principal Name) do usuário que executou a ação (especificado na propriedade Operation) que resultou no registro sendo registrado; por exemplo, `my_name@my_domain_name`. Observe que os registros da atividade executada pelas contas do sistema (como SHAREPOINT\system ou NT AUTHORITY\SYSTEM) também são incluídos.|
|ClientIP|Edm.String|Sim|O endereço IP do dispositivo que foi usado quando a atividade foi registrada. O endereço IP é exibido em um formato de endereço IPv4 ou IPv6.|
|Scope|Self.[AuditLogScope](#auditlogscope)|Não|Esse evento foi criado por um serviço hospedado do O365 ou por um servidor local? Os valores possíveis são **online** e **onprem**. Observe que o SharePoint é a única carga de trabalho enviando eventos do local para o O365 atualmente.|

### <a name="enum-auditlogrecordtype---type-edmint32"></a>Enumeração: AuditLogRecordType - Tipo: Edm.Int32

#### <a name="auditlogrecordtype"></a>AuditLogRecordType

|Valor|Nome do membro|Descrição|
|:-----|:-----|:-----|
|1|ExchangeAdmin|Eventos do log de auditoria do administrador do Exchange.|
|2|ExchangeItem|Eventos de um log de auditoria de caixa de correio do Exchange para ações executadas em um único item, como criar ou receber uma mensagem de email.|
|3|ExchangeItemGroup|Eventos de um log de auditoria de caixa de correio do Exchange para ações que podem ser executadas em vários itens, como mover ou excluir uma ou mais mensagens de email.|
|4|SharePoint|Eventos do SharePoint.|
|6|SharePointFileOperation|Eventos de operação de arquivos do SharePoint.|
|8|AzureActiveDirectory|Eventos do Azure Active Directory.|
|9|AzureActiveDirectoryAccountLogon|Eventos de logon do Azure Active Directory OrgId (descontinuando).|
|10|DataCenterSecurityCmdlet|Eventos de cmdlet de segurança do Data Center.|
|11|ComplianceDLPSharePoint|Eventos de proteção contra perda de dados (DLP) no SharePoint e no OneDrive for Business.|
|12|Sway|Eventos dos clientes e serviço do Sway.|
|13|ComplianceDLPExchange|Eventos de Proteção contra a Perda de Dados (DLP), quando configurados via Política DLP Unificada. Não há suporte para eventos de DLP com base em Regras de Transporte do Exchange.|
|14|SharePointSharingOperation|Eventos de compartilhamento do SharePoint.|
|15|AzureActiveDirectoryStsLogon|Eventos de logon do Serviço de Token Seguro (STS) no Azure Active Directory.|
|18|SecurityComplianceCenterEOPCmdlet|Ações de administração do Centro de Conformidade e Segurança.|
|20|PowerBIAudit|Eventos do Power BI.|
|21|CRM|Eventos Microsoft CRM.|
|22|Yammer|Eventos do Yammer.|
|23|SkypeForBusinessCmdlets|Eventos do Skype for Business.|
|24|Descoberta|Eventos para atividades de Descoberta Eletrônica realizados executando pesquisas de conteúdo e gerenciando casos de Descoberta Eletrônica no Centro de Conformidade e Segurança.|
|25|MicrosoftTeams|Eventos do Microsoft Teams.|
|28|ThreatIntelligence|Eventos de phishing e malware da Proteção do Exchange Online e da Proteção Avançada contra Ameaças do Office 365.|
|30|MicrosoftFlow|Eventos do Microsoft Flow.|
|31|AeD|Eventos de Descoberta Eletrônica Avançada.|
|32|MicrosoftStream|Eventos do Microsoft Stream.|
|35|Project|Eventos do Microsoft Project.|
|36|SharepointListOperation|Eventos de lista do SharePoint.|
|38|DataGovernance|Eventos relacionados às políticas de retenção e rótulos de retenção no Centro de Conformidade e Segurança|
|40|SecurityComplianceAlerts|Sinais de alerta de conformidade e segurança.|
|41|ThreatIntelligenceUrl|Eventos de bloqueio de tempo e bloqueio de links seguros da Proteção Avançada contra Ameaças do Office 365.|
|44|WorkplaceAnalytics|Eventos do Workplace Analytics.|
|45|PowerAppsApp|Eventos do aplicativo PowerApps.|
|47|ThreatIntelligenceAtpContent|Eventos de phishing e malware para arquivos no SharePoint, OneDrive for Business e o Microsoft Teams da Proteção Avançada contra Ameaças do Office 365.|
|54|SharePointListItemOperation|Eventos de lista do SharePoint.|
|55|SharePointContentTypeOperation|Eventos do tipo de conteúdo de lista do SharePoint.|
||||

### <a name="enum-user-type---type-edmint32"></a>Enumeração: User Type - Tipo: Edm.Int32

#### <a name="user-type"></a>User Type

|Valor|Nome do membro|Descrição|
|:-----|:-----|:-----|
|0|Regular|Um usuário regular.|
|1|Reserved|Um usuário reservado.|
|2|Admin|Um administrador.|
|3|DcAdmin|Um operador de datacenter da Microsoft.|
|4|System|Uma conta do sistema.|
|5|Application|Um aplicativo.|
|6|ServicePrincipal|Uma entidade de serviço.|

> [!NOTE] 
> Somente as operações do Exchange incluem um tipo de usuário. As operações do SharePoint não especificam um tipo de usuário. 

### <a name="enum-auditlogscope---type-edmint32"></a>Enumeração: AuditLogScope - Tipo: Edm.Int32

#### <a name="auditlogscope"></a>AuditLogScope

|Valor|Nome do membro|Descrição|
|:-----|:-----|:-----|
|0|Online|Este evento foi criado por um serviço hospedado no O365.|
|1|Onprem|Este evento foi criado por um servidor local.|


## <a name="sharepoint-base-schema"></a>Esquema base do SharePoint

|**Parâmetro**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|Site|Edm.Guid|Não|O GUID do site onde o arquivo ou pasta acessado pelo usuário está localizado.|
|ItemType|Edm.String String="Microsoft.Office.Audit.Schema.SharePoint.[ItemType](#itemtype)"|Não|O tipo de objeto que foi acessado ou modificado. Confira a tabela [ItemType](#itemtype) para obter detalhes sobre os tipos de objetos.|
|EventSource|Edm.String String="Microsoft.Office.Audit.Schema.SharePoint.[EventSource](#eventsource)"|Não|Identifica que um evento ocorreu no SharePoint. Valores possíveis são **SharePoint** ou **ObjectModel**.|
|SourceName|Edm.String|Não|A entidade que acionou a operação auditada. Valores possíveis são SharePoint ou **ObjectModel**.|
|UserAgent|Edm.String|Não|Informações sobre o cliente ou navegador do usuário. Esta informação é fornecida pelo cliente ou navegador.|
|MachineDomainInfo|Edm.String Term="Microsoft.Office.Audit.Schema.PIIFlag" Bool="true"|Não|Informações sobre as operações de sincronização do dispositivo. Essas informações são relatadas somente se estiverem presentes na solicitação.|
|MachineId|Edm.String Term="Microsoft.Office.Audit.Schema.PIIFlag" Bool="true"|Não|Informações sobre as operações de sincronização do dispositivo. Essas informações são relatadas somente se estiverem presentes na solicitação.|


### <a name="enum-itemtype---type-edmint32"></a>Enumeração: ItemType - Tipo: Edm.Int32

#### <a name="itemtype"></a>ItemType

|**Valor**|**Nome do membro**|**Descrição**|
|:-----|:-----|:-----|
|0|Invalid|O item não consiste em nenhum dos outros tipos de itens (listados nesta tabela).|
|1|File|O item é um arquivo.|
|5|Folder|O item é uma pasta.|
|6|Web|O item é uma Web.|
|7|Site|O item é um site.|
|8|Tenant|O item é um locatário.|
|9|DocumentLibrary|O item é uma biblioteca de documentos.|
|11|Page|O item é uma página.|

### <a name="enum-eventsource---type-edmint32"></a>Enumeração: EventSource - Tipo: Edm.Int32

#### <a name="eventsource"></a>EventSource

|**Valor**|**Nome do membro**|**Descrição**|
|:-----|:-----|:-----|
|0|SharePoint|A origem do evento é o SharePoint.|
|1|ObjectModel|A origem do evento é o ObjectModel.|


### <a name="enum-sharepointauditoperation---type-edmint32"></a>Enumeração: SharePointAuditOperation - Tipo: Edm.Int32

|**Nome do membro**|**Descrição**|
|:-----|:-----|
|AccessInvitationAccepted*|O destinatário de um convite para exibir ou editar um arquivo compartilhado (ou pasta) acessou o arquivo compartilhado clicando no link do convite.|
|AccessInvitationCreated*|O usuário envia um convite a outra pessoa (dentro ou fora da organização) para exibir ou editar um arquivo ou pasta compartilhada em um site do SharePoint ou do OneDrive for Business. Os detalhes da entrada do evento identificam o nome do arquivo que foi compartilhado, o usuário ao qual o convite foi enviado e o tipo de permissão de compartilhamento selecionado pela pessoa que enviou o convite.|
|AccessInvitationExpired*|Um convite enviado a um usuário externo expirou. Por padrão, um convite enviado a um usuário fora de sua organização expira após sete dias se não for aceito.|
|AccessInvitationRevoked*|O administrador do site ou proprietário de um site ou documento no SharePoint ou OneDrive for Business retira um convite que foi enviado para um usuário fora da organização. Um convite pode ser retirado somente antes de ser aceito.|
|AccessInvitationUpdated*|O usuário que criou e enviou um convite a outra pessoa para exibir ou editar um arquivo (ou pasta) compartilhado em um site do SharePoint ou do OneDrive for Business reenvia o convite.|
|AccessRequestApproved|O administrador do site ou proprietário de um site ou documento no SharePoint ou no OneDrive for Business aprova uma solicitação do usuário para acessar o site ou documento.|
|AccessRequestCreated|O usuário solicita acesso a um site ou documento no SharePoint ou no OneDrive for Business que ele não tem permissão para acessar. |
|AccessRequestRejected*|O administrador do site ou proprietário de um site ou documento no SharePoint recusa uma solicitação do usuário para acessar o site ou documento.|
|ActivationEnabled*|Os usuários podem habilitar modelos de formulário para navegador que não contenham código de formulário, exijam confiança total, permitam a renderização em um dispositivo móvel ou usem uma conexão de dados gerenciada por um administrador de servidor.|
|AdministratorAddedToTermStore*|Administrador do repositório de termos adicionado.|
|AdministratorDeletedFromTermStore*|Administrador do repositório de termos adicionado excluído.|
|AllowGroupCreationSet*|O administrador ou proprietário do site adiciona um nível de permissão a um site do SharePoint ou do OneDrive for Business que permite ao usuário designado criar um grupo para esse site.|
|AppCatalogCreated*|Catálogo de aplicativos criado para disponibilizar aplicativos de negócios personalizados para o seu ambiente do SharePoint.|
|AuditPolicyRemoved*|Política de Ciclo de Vida do Documento removida para um conjunto de sites.|
|AuditPolicyUpdate*|Política de Ciclo de Vida do Documento atualizada para um conjunto de sites.|
|AzureStreamingEnabledSet*|Um proprietário de portal de vídeo permitiu o streaming de vídeo do Azure.|
|CollaborationTypeModified*|O tipo de colaboração permitido em sites (por exemplo, intranet, extranet ou público) foi modificado.|
|ConnectedSiteSettingModified|O usuário criou, modificou ou excluiu o link entre um projeto e um site de projeto ou o usuário modificou a configuração de sincronização no link do Project Web App.|
|CreateSSOApplication*|Aplicativo de destino criado no Serviço de Repositório Seguro.|
|CustomFieldOrLookupTableCreated|O usuário criou um campo personalizado ou uma tabela/item de consulta no Project Web App.|
|CustomFieldOrLookupTableDeleted|O usuário excluiu um campo personalizado ou uma tabela/item de consulta no Project Web App.|
|CustomFieldOrLookupTableModified|O usuário modificou um campo personalizado ou uma tabela/item de consulta no Project Web App.|
|CustomizeExemptUsers*|O administrador global personalizou a lista de agentes do usuário isentos no Centro de administração do SharePoint. Você pode especificar quais agentes do usuário ficarão isentos do recebimento de uma página da Web completa para indexar. Isso significa que quando um agente do usuário que você especificou como isento encontrar um formulário do InfoPath, o formulário será retornado como um arquivo XML em vez de uma página da Web completa. Isso torna a indexação de formulários do InfoPath mais rápida.|
|DefaultLanguageChangedInTermStore*|Configuração de idioma alterada no repositório de terminologia.|
|DelegateModified|O usuário criou ou modificou um representante de segurança no Project Web App.|
|DelegateRemoved|O usuário excluiu um representante de segurança no Project Web App.|
|DeleteSSOApplication*|Um aplicativo SSO foi excluído.|
|eDiscoveryHoldApplied*|Um Bloqueio In-loco foi colocado em uma fonte de conteúdo. Os Bloqueios In-loco são gerenciados usando um conjunto de sites de Descoberta Eletrônica (como o Centro de Descoberta Eletrônica) no SharePoint.|
|eDiscoveryHoldRemoved*|Um Bloqueio In-loco foi removido de uma fonte de conteúdo. Os Bloqueios In-loco são gerenciados usando um conjunto de sites de Descoberta Eletrônica (como o Centro de Descoberta Eletrônica) no SharePoint.|
|eDiscoverySearchPerformed*|Uma pesquisa de Descoberta Eletrônica foi realizada usando um conjunto de sites de Descoberta Eletrônica no SharePoint.|
|EngagementAccepted|O usuário aceita um compromisso de recurso no Project Web App.|
|EngagementModified|O usuário modifica um compromisso de recurso no Project Web App.|
|EngagementRejected|O usuário rejeita um compromisso de recurso no Project Web App.|
|EnterpriseCalendarModified|O usuário copia, modifica ou exclui um calendário da empresa no Project Web App.|
|EntityDeleted|O usuário exclui um quadro de horários no Project Web App.|
|EntityForceCheckedIn|O usuário força um check-in em um calendário, campo personalizado ou tabela de pesquisa no Project Web App.|
|ExemptUserAgentSet*|O administrador global adiciona um agente do usuário à lista de agentes do usuário isentos no Centro de administração do SharePoint.|
|FileAccessed|O usuário ou a conta do sistema acessa um arquivo em um site do SharePoint ou OneDrive for Business. Contas do sistema também podem gerar eventos FileAccessed.|
|FileCheckOutDiscarded*|O usuário descarta (ou desfaz) um arquivo em check-out. Isso significa que todas as alterações que ele tiver feito nesse arquivo durante o estado de check-out serão descartados, e não salvas na versão do documento localizada na biblioteca de documentos.|
|FileCheckedIn*|O usuário faz check-in em um documento em que fez check-out de uma Biblioteca de documentos do SharePoint ou do OneDrive for Business.|
|FileCheckedOut*|O usuário faz check-out de um documento localizado em uma biblioteca de documentos do SharePoint ou do OneDrive for Business. Os usuários podem fazer check-out e alterações nos documentos que foram compartilhados com eles.|
|FileCopied|O usuário copia um documento de um site do SharePoint ou do OneDrive for Business. O arquivo copiado pode ser salvo em outra pasta no site.|
|FileDeleted|O usuário exclui um documento de um site do SharePoint ou do OneDrive for Business.|
|FileDeletedFirstStageRecycleBin|O usuário exclui um arquivo da lixeira em um site do SharePoint ou do OneDrive for Business.|
|FileDeletedSecondStageRecycleBin|O usuário exclui um arquivo da lixeira de segundo estágio em um site do SharePoint ou do OneDrive for Business.|
|FileDownloaded|O usuário faz download de um documento de um site do SharePoint ou do OneDrive for Business.|
|FileFetched|Este evento foi substituído pelo evento FileAccessed e foi descontinuado.|
|FileModified|O usuário ou a conta do sistema modifica o conteúdo ou as propriedades de um documento localizado em um site do SharePoint ou do OneDrive for Business.|
|FileMoved|O usuário move um documento de seu local atual em um site do SharePoint ou do OneDrive for Business para um novo local.|
|FilePreviewed|O usuário visualiza um documento em um site do SharePoint ou OneDrive for Business.|
|FileRenamed|O usuário renomeia um documento em um site do SharePoint ou OneDrive for Business.|
|FileRestored|O usuário restaura um documento da lixeira de um site do SharePoint ou OneDrive for Business. |
|FileSyncDownloadedFull|O usuário estabelece um relacionamento de sincronização e faz download dos arquivos com êxito pela primeira vez em seu computador a partir de uma biblioteca de documentos do SharePoint ou do OneDrive for Business.|
|FileSyncDownloadedPartial|O usuário faz o download com êxito de qualquer alteração nos arquivos da biblioteca de documentos do SharePoint ou do OneDrive for Business. Esse evento indica que as alterações feitas nos arquivos da biblioteca de documentos foram baixados para o computador do usuário. Apenas as alterações foram baixadas, pois a biblioteca de documentos foi baixada anteriormente pelo usuário (conforme indicado pelo evento FileSyncDownloadedFull).|
|FileSyncUploadedFull*|O usuário estabelece um relacionamento de sincronização e faz upload dos arquivos com êxito pela primeira vez do seu computador para uma biblioteca de documentos do SharePoint ou do OneDrive for Business.|
|FileSyncUploadedPartial*|O usuário faz o upload com êxito das alterações nos arquivos da biblioteca de documentos do SharePoint ou do OneDrive for Business. Esse evento indica que quaisquer alterações feitas na versão local de um arquivo de uma biblioteca de documentos foram carregadas com êxito para a biblioteca de documentos. Somente as alterações são carregadas, pois esses arquivos foram carregados anteriormente pelo usuário (conforme indicado pelo evento FileSyncUploadedFull).|
|FileUploaded|O usuário faz upload de um documento para uma pasta em um site do SharePoint ou do OneDrive for Business. |
|FileViewed|Este evento foi substituído pelo evento FileAccessed e foi descontinuado.|
|FolderCopied|O usuário copia uma pasta de um site do SharePoint ou do OneDrive for Business para outro local no SharePoint ou no OneDrive for Business.|
|FolderCreated|O usuário cria uma pasta em um site do SharePoint ou do OneDrive for Business.|
|FolderDeleted|O usuário exclui uma pasta de um site do SharePoint ou do OneDrive for Business.|
|FolderDeletedFirstStageRecycleBin|O usuário exclui uma pasta da lixeira em um site do SharePoint ou do OneDrive for Business.|
|FolderDeletedSecondStageRecycleBin|O usuário exclui uma pasta da lixeira de segundo estágio em um site do SharePoint ou do OneDrive for Business.|
|FolderModified|O usuário modifica uma pasta em um site do SharePoint ou do OneDrive for Business. Este evento inclui alterações de metadados da pasta, como tags e propriedades.|
|FolderMoved|O usuário move uma pasta de um site do SharePoint ou do OneDrive for Business.|
|FolderRenamed|O usuário renomeia uma pasta de um site do SharePoint ou do OneDrive for Business.|
|FolderRestored|O usuário restaura uma pasta da lixeira em um site do SharePoint ou do OneDrive for Business.|
|GroupAdded*|O administrador ou proprietário do site cria um grupo para um site do SharePoint ou OneDrive for Business ou executa uma tarefa que resulta na criação de um grupo. Por exemplo, na primeira vez que um usuário cria um link para compartilhar um arquivo, um grupo de sistemas é adicionado ao site do OneDrive for Business do usuário. Esse evento também pode ser o resultado de um usuário ter criado um link com permissões de edição para um arquivo compartilhado.|
|GroupRemoved*|O usuário exclui um grupo de um site do SharePoint ou do OneDrive for Business. |
|GroupUpdated*|O administrador ou proprietário do site altera as configurações de um grupo para um site do SharePoint ou do OneDrive for Business. Isso pode incluir a alteração do nome do grupo, quem pode visualizar ou editar a associação ao grupo e como as solicitações de associação são tratadas.|
|LanguageAddedToTermStore*|Idioma adicionado ao repositório de terminologia.|
|LanguageRemovedFromTermStore*|Idioma removido do repositório de terminologia.|
|LegacyWorkflowEnabledSet*|O administrador ou proprietário do site adiciona o tipo de conteúdo Tarefa do Fluxo de Trabalho do SharePoint ao site. Os administradores globais também podem ativar fluxos de trabalho para toda a organização no Centro de administração do SharePoint.|
|LookAndFeelModified|O usuário modifica um início rápido, formatos de gráfico de gantt ou formatos de grupo. Ou o usuário cria, modifica ou exclui uma exibição no Project Web App.|
|ManagedSyncClientAllowed|O usuário estabelece com êxito uma relação de sincronização com um site do SharePoint ou do OneDrive for Business. A relação de sincronização é bem-sucedida porque o computador do usuário é membro de um domínio que foi adicionado à lista de domínios (chamada de Lista de Destinatários Confiáveis) que pode acessar bibliotecas de documentos em sua organização. Para obter mais informações sobre esse recurso, confira [Usar os cmdlets do Windows PowerShell para habilitar a sincronização do OneDrive para domínios que estão na Lista de Destinatários Confiáveis](http://go.microsoft.com/fwlink/p/?LinkID=534609).|
|MaxQuotaModified*|A cota máxima de um site foi modificada.|
|MaxResourceUsageModified*|O uso máximo permitido de recursos para um site foi modificado.|
|MySitePublicEnabledSet*|O sinalizador que permite aos usuários ter MySites públicos foi definido pelo administrador do SharePoint.|
|NewsFeedEnabledSet*|O administrador ou proprietário do site habilita feeds RSS para um site do SharePoint ou do OneDrive for Business. Os administradores globais podem ativar feeds RSS para toda a organização no Centro de administração do SharePoint.|
|ODBNextUXSettings*|Uma nova interface do usuário do OneDrive for Business foi ativada.|
|OfficeOnDemandSet*|O administrador do site habilita o Office on Demand, que permite aos usuários acessar a versão mais recente dos aplicativos da área de trabalho do Office. O Office on Demand está habilitado no Centro de administração do SharePoint e exige uma assinatura do Office 365 que inclua aplicativos completos do Office instalados.|
|PageViewed|O usuário visualiza uma página em um site do SharePoint ou no site do OneDrive for Business. Isso não inclui a exibição de arquivos da biblioteca de documentos de um site do SharePoint ou do site One Drive for Business em um navegador.|
|PeopleResultsScopeSet*|O administrador do site cria ou altera a fonte de resultados para Pesquisas de Pessoas em um site do SharePoint.|
|PermissionSyncSettingModified|O usuário modifica as configurações de sincronização de permissão do projeto no Project Web App.|
|PermissionTemplateModified|O usuário cria, modifica ou exclui um modelo de permissões no Project Web App.|
|PortfolioDataAccessed|O usuário acessa o conteúdo do portfólio (biblioteca de driver, priorização de driver, análises de portfólio) no Project Web App.|
|PortfolioDataModified|O usuário cria, modifica ou exclui dados do portfólio (biblioteca de driver, priorização de driver, análises de portfólio) no Project Web App.|
|PreviewModeEnabledSet*|O administrador do site habilita a visualização do documento para um site do SharePoint.|
|ProjectAccessed|O usuário acessa o conteúdo do projeto no Project Web App.|
|ProjectCheckedIn|O usuário faz check-in em um projeto que ele fez check-out de um Project Web App.|
|ProjectCheckedOut|O usuário faz check-out de um projeto localizado em um Project Web App. Os usuários podem fazer check-out e fazer alterações em projetos para os quais têm permissão para abrir.|
|ProjectCreated|O usuário cria um projeto no Project Web App.|
|ProjectDeleted|O usuário exclui um projeto no Project Web App.|
|ProjectForceCheckedIn|O usuário força um check-in em um projeto no Project Web App.|
|ProjectModified|O usuário modifica um projeto no Project Web App.|
|ProjectPublished|O usuário publica um projeto no Project Web App.|
|ProjectWorkflowRestarted|O usuário reinicia um fluxo de trabalho no Project Web App.|
|PWASettingsAccessed|O usuário acessa as configurações do Project Web App via CSOM.|
|PWASettingsModified|O usuário modifica a configuração do Project Web App.|
|QueueJobStateModified|O usuário cancela ou reinicia um trabalho de fila no Project Web App.|
|QuotaWarningEnabledModified*|Aviso de cota de armazenamento modificada.|
|RenderingEnabled*|Modelos de formulário habilitados para navegador serão processados ​​pelos serviços de formulários do InfoPath.|
|ReportingAccessed|O usuário acessou o ponto de extremidade de relatório no Project Web App.|
|ReportingSettingModified|O usuário modifica a configuração de relatório no Project Web App.|
|ResourceAccessed|O usuário acessa um conteúdo de recursos da empresa no Project Web App.|
|ResourceCheckedIn|O usuário faz check-in em um recurso da empresa que ele fez check-out de um Project Web App.|
|ResourceCheckedOut|O usuário faz check-out de um recurso da empresa localizado no Project Web App.|
|ResourceCreated|O usuário cria um recurso da empresa no Project Web App.|
|ResourceDeleted|O usuário exclui um recurso da empresa no Project Web App.|
|ResourceForceCheckedIn|O usuário força um check-in de um recurso da empresa no Project Web App.|
|ResourceModified|O usuário modifica um recurso da empresa no Project Web App.|
|ResourcePlanCheckedInOrOut|O usuário faz check-in ou check-out de um plano de recursos no Project Web App.|
|ResourcePlanModified|O usuário modifica um plano de recursos no Project Web App.|
|ResourcePlanPublished|O usuário publica um plano de recursos no Project Web App.|
|ResourceRedacted|O usuário cria um recurso corporativo que remove todas as informações pessoais no Project Web App.|
|ResourceWarningEnabledModified*|Aviso de cota de recursos modificada.|
|SSOGroupCredentialsSet*|Credenciais de grupo definidas no Serviço de Repositório Seguro.|
|SSOUserCredentialsSet*|Credenciais de usuário definidas no Serviço de Repositório Seguro.|
|SearchCenterUrlSet*|Conjunto de URLs do Centro de Pesquisa.|
|SecondaryMySiteOwnerSet*|Um usuário adicionou um proprietário secundário ao seu MySite.|
|SecurityCategoryModified|O usuário cria, modifica ou exclui uma categoria de segurança no Project Web App.|
|SecurityGroupModified|O usuário cria, modifica ou exclui um grupo de segurança no Project Web App.|
|SendToConnectionAdded*|O administrador global cria uma nova conexão Enviar para na página Gerenciamento de registros no Centro de administração do SharePoint. Uma conexão Enviar para especifica configurações para um repositório de documentos ou um centro de registros. Quando você cria uma conexão Enviar para, um Organizador de Conteúdo pode enviar documentos para o local especificado.|
|SendToConnectionRemoved*|O administrador global exclui uma conexão Enviar para na página Gerenciamento de registros no Centro de administração do SharePoint.|
|SharedLinkCreated|O usuário cria um link para um arquivo compartilhado no SharePoint ou no OneDrive for Business. Este link pode ser enviado para outras pessoas para dar acesso ao arquivo. Um usuário pode criar dois tipos de links: um link que permite ao usuário visualizar e editar o arquivo compartilhado, ou um link que permite ao usuário apenas visualizar o arquivo.|
|SharedLinkDisabled*|O usuário desabilita (permanentemente) um link que foi criado para compartilhar um arquivo.|
|SharingInvitationAccepted *|O usuário aceita um convite para compartilhar um arquivo ou uma pasta. Esse evento é registrado quando um usuário compartilha um arquivo com outros usuários.|
|SharingRevoked*|O usuário descompartilha um arquivo ou pasta anteriormente compartilhada com outros usuários. Esse evento é registrado quando um usuário deixa de compartilhar um arquivo com outros usuários.|
|SharingSet|O usuário compartilha um arquivo ou pasta localizado no SharePoint ou no OneDrive for Business com outro usuário dentro de sua organização.|
|SiteAdminChangeRequest*|O usuário solicita ser adicionado como um administrador do conjunto de sites de um conjunto de sites do SharePoint. Os administradores do conjunto de sites têm permissões de controle total para o conjunto de sites e todos os subsites.|
|SiteCollectionAdminAdded*|O administrador ou proprietário do conjunto de sites adiciona uma pessoa como administrador do conjunto de sites para um site do SharePoint ou do OneDrive for Business. Os administradores do conjunto de sites têm permissões de controle total para o conjunto de sites e todos os subsites.|
|SiteCollectionCreated*| O administrador global cria um novo conjunto de sites em sua organização do SharePoint.|
|SiteRenamed*|O administrador ou proprietário do site renomeia um site do SharePoint ou do OneDrive for Business.|
|StatusReportModified|O usuário cria, modifica ou exclui um relatório de status no Project Web App.|
|SyncGetChanges*|O usuário clica em **Sincronizar** na bandeja de ação no SharePoint ou no OneDrive for Business para sincronizar as alterações feitas no arquivo em uma biblioteca de documentos ao computador.|
|TaskStatusAccessed|O usuário acessa o status de uma ou mais tarefas no Project Web App.|
|TaskStatusApproved|O usuário aprova uma atualização de status de uma ou mais tarefas no Project Web App.|
|TaskStatusRejected|O usuário rejeita uma atualização de status de uma ou mais tarefas no Project Web App.|
|TaskStatusSaved|O usuário salva uma atualização de status de uma ou mais tarefas no Project Web App.|
|TaskStatusSubmitted|O usuário envia uma atualização de status de uma ou mais tarefas no Project Web App.|
|TimesheetAccessed|O usuário acessa um quadro de horários no Project Web App.|
|TimesheetApproved|O usuário aprova um quadro de horários no Project Web App.|
|TimesheetRejected|O usuário rejeita um quadro de horários no Project Web App.|
|TimesheetSaved|O usuário salva um quadro de horários no Project Web App.|
|TimesheetSubmitted|O usuário envia um quadro de horários de status no Project Web App.|
|UnmanagedSyncClientBlocked|O usuário tenta estabelecer uma relação de sincronização com um site do SharePoint ou do OneDrive for Business em um computador que não é membro do domínio de sua organização ou que é membro de um domínio que não foi adicionado à lista de domínios (chamada de Lista de Destinatários Confiáveis) que podem acessar bibliotecas de documentos em sua organização. A relação de sincronização não é permitida e o computador do usuário é impedido de sincronizar, fazer download ou fazer upload de arquivos em uma biblioteca de documentos. Para obter informações sobre esse recurso, confira [Usar os cmdlets do Windows PowerShell para habilitar a sincronização do OneDrive para domínios que estão na Lista de Destinatários Confiáveis](https://docs.microsoft.com/pt-BR/powershell/module/sharepoint-online/index?view=sharepoint-ps).|
|UpdateSSOApplication*|Aplicativo de destino atualizado no Serviço de Repositório Seguro.|
|UserAddedToGroup*|O administrador ou proprietário do site adiciona uma pessoa a um grupo em um site do SharePoint ou OneDrive for Business. Adicionar uma pessoa a um grupo concede ao usuário as permissões que foram atribuídas ao grupo. |
|UserRemovedFromGroup*|O administrador ou proprietário do site remove uma pessoa de um grupo em um site do SharePoint ou OneDrive for Business. Depois que a pessoa é removida, ela não recebe mais as permissões que foram atribuídas ao grupo. |
|WorkflowModified|O usuário cria, modifica ou exclui fases ou estágios do tipo de projeto ou fluxo de trabalho corporativo no Project Web App.|


> [!NOTE] 
> * Esta operação está em visualização.



## <a name="sharepoint-file-operations"></a>Operações de arquivos do SharePoint

Os eventos do SharePoint relacionados a arquivos listados na seção "Atividades de arquivos e pastas" em [Pesquisar o log de auditoria do Centro de Proteção do Office 365](https://support.office.com/pt-BR/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c?ui=en-US&amp;rs=en-US&amp;ad=US) usam este esquema.



|**Parâmetro**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|SiteUrl|Edm.String|Sim|A URL do site onde o arquivo ou pasta acessado pelo usuário está localizado.|
|SourceRelativeUrl|Edm.String|Não|O URL da pasta que contém o arquivo acessado pelo usuário. A combinação dos valores para os parâmetros _SiteURL_, _SourceRelativeURL_ e _SourceFileName_ é igual ao valor da propriedade **ObjectID**, que é o nome do caminho completo para o arquivo acessado pelo usuário.|
|SourceFileName|Edm.String|Sim|O nome do arquivo ou pasta acessado pelo usuário.|
|SourceFileExtension|Edm.String|Não|A extensão do arquivo que foi acessado pelo usuário. Esta propriedade fica em branco se o objeto que foi acessado for uma pasta.|
|DestinationRelativeUrl|Edm.String|Não|A URL da pasta de destino em que um arquivo é copiado ou movido. A combinação dos valores para os parâmetros _SiteURL_, _DestinationRelativeURL_ e _DestinationFileName_ é igual ao valor da propriedade **ObjectID**, que é o nome do caminho completo para o arquivo que foi copiado. Essa propriedade é exibida apenas para eventos FileCopied e FileMoved.|
|DestinationFileName|Edm.String|Não|O nome do arquivo que foi copiado ou movido. Essa propriedade é exibida apenas para eventos FileCopied e FileMoved.|
|DestinationFileExtension|Edm.String|Não|A extensão de um arquivo que foi copiado ou movido. Essa propriedade é exibida apenas para eventos FileCopied e FileMoved.|
|UserSharedWith|Edm.String|Não|O usuário com o qual um recurso foi compartilhado.|
|SharingType|Edm.String|Não|O tipo de permissões de compartilhamento que foram designadas ao usuário com o qual o recurso foi compartilhado. Este usuário é identificado pelo parâmetro _UserSharedWith_.|



## <a name="sharepoint-sharing-schema"></a>Esquema de compartilhamento do SharePoint

 Os eventos do SharePoint relacionados ao compartilhamento de arquivos. Eles são diferentes dos eventos relacionados a arquivos e pastas em que um usuário está realizando uma ação que afeta outro usuário. Para obter informações sobre o esquema de compartilhamento do SharePoint, confira [Usar a auditoria de compartilhamento no log de auditoria do Office 365g](https://support.office.com/pt-BR/article/Use-sharing-auditing-in-the-Office-365-audit-log-50bbf89f-7870-4c2a-ae14-42635e0cfc01?ui=en-US&amp;rs=en-US&amp;ad=US).



|**Parâmetro**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|TargetUserOrGroupName |Edm.String|Não|Armazena o UPN ou o nome do usuário ou grupo de destino com o qual um recurso foi compartilhado.|
|TargetUserOrGroupType|Edm.String|Não|Identifica se o usuário ou grupo de destino é um Membro, Convidado, Grupo ou Parceiro. |
|EventData|Código XML|Não|Transmite informações de acompanhamento sobre a ação de compartilhamento que ocorreu, como adicionar um usuário a um grupo ou conceder permissões de edição.|


## <a name="sharepoint-schema"></a>Esquema do SharePoint

Os eventos do SharePoint listados em [Pesquisar o log de auditoria do Centro de Proteção do Office 365](https://support.office.com/pt-BR/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c?ui=en-US&amp;rs=en-US&amp;ad=US) (excluindo os eventos de arquivo e pasta) usam este esquema.



|**Parâmetro**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|CustomEvent|Edm.String|Não|Cadeia de caracteres opcional para eventos personalizados.|
|EventData|Edm.String|Não|Carga opcional para eventos personalizados.|
|ModifiedProperties|Collection(ModifiedProperty)|Não|A propriedade está incluída para eventos de administrador, como adicionar um usuário como membro de um site ou grupo de administradores de um conjunto de sites. A propriedade inclui o nome da propriedade que foi modificada (por exemplo, o grupo Administrador do Site), o novo valor da propriedade modificada (como o usuário que foi adicionado como administrador do site) e o valor anterior do objeto modificado.|


## <a name="project-schema"></a>Esquema do Project

|**Parâmetro**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|Entity|Edm.String|Sim| [ProjectEntity](#project-entity) da auditoria.|
|Action|Edm.String|Sim|[ProjectAction](#project-action) tomada.|
|OnBehalfOfResId|Edm.Guid|Não|A ID do recurso em nome da qual a ação foi tomada.|

<a name="project-action"></a>

### <a name="enum-project-action---type-edmint32"></a>Enumeração: Project Action - Tipo: Edm.Int32


|**Nome do membro**|**Descrição**|
|:-----|:-----|
|Accepted|O usuário aceitou um evento ou fluxo de trabalho.|
|Accessed|O usuário acessou uma entidade.|
|Activated|O usuário ativou uma entidade, evento ou fluxo de trabalho.|
|Cancelled|O usuário cancelou um evento ou fluxo de trabalho.|
|CheckedIn|O usuário fez check-in em uma entidade.|
|CheckedOut|O usuário fez check-out em uma entidade.|
|Copied|O usuário copiou uma entidade.|
|Created|O usuário criou uma entidade.|
|Deactivated|O usuário desativou uma entidade.|
|Deleted|O usuário excluiu uma entidade.|
|Exported|O usuário exportou uma entidade.|
|ForceCheckedIn|O usuário fez com que uma entidade fosse obrigada a fazer check-in.|
|Modified|O usuário modificou uma entidade.|
|Published|O usuário publicou uma entidade.|
|Redacted|O usuário redigiu uma entidade.|
|Rejected|O usuário rejeitou uma entidade.|
|Restarted|O usuário reiniciou um evento ou fluxo de trabalho.|
|Saved|O usuário salvou uma entidade.|
|Sent|O usuário enviou uma entidade.|
|Submitted|O usuário enviou uma entidade para revisão ou fluxo de trabalho.|

<a name="project-entity"></a>
### <a name="enum-project-entity---type-edmint32"></a>Enumeração: Project Entity - Tipo: Edm.Int32

|**Nome do membro**|**Descrição**|
|:-----|:-----|
|CustomField|Representa um campo personalizado da empresa.|
|Driver|Representa um indicador de portfólio.|
|DriverPrioritization|Representa uma priorização de portfólio.|
|Engagement|Representa um compromisso de recurso.|
|EnterpriseCalendar|Representa um calendário de recursos da empresa.|
|EnterpriseProjectType|Representa um tipo de projeto corporativo.|
|FiscalPeriod|Representa um período fiscal.|
|GanttChartFormat|Representa um formato de gráfico de Gantt.|
|GroupingFormat|Representa um formato de agrupamento de visualizações.|
|LineClassification|Representa uma classificação de linha de quadro de horários.|
|LookupTable|Representa uma tabela de pesquisa corporativa.|
|PermissionTemplate|Representa um modelo de permissão de segurança.|
|PortfolioAnalysis|Representa uma análise de portfólio.|
|Project|Representa um projeto.|
|QueueJob|Representa um trabalho em fila.|
|QuickLaunch|Representa um item de inicialização rápida.|
|Reporting|Representa o ponto de extremidade de relatório.|
|Resource|Representa um recurso da empresa.|
|ResourcePlan|Representa um plano de recursos associado a um projeto.|
|SecurityCategory|Representa uma categoria de segurança.|
|SecurityGroup|Representa um grupo de segurança.|
|Setting|Representa uma configuração do Project Web App.|
|Statusing|Representa uma atualização de status da tarefa.|
|StatusReport|Representa um relatório de status.|
|TimeReportingPeriod|Representa um período de tempo para um quadro de horários.|
|Timesheet|Representa uma entidade de quadro de horários.|
|TimesheetAuditLog|Representa um log de auditoria do quadro de horários.|
|TimesheetManager|Representa o gerente de um quadro de horários.|
|UserDelegate|Representa uma delegação de usuário para outro usuário.|
|View|Representa uma definição de exibição.|
|WorkflowPhase|Representa uma fase em um fluxo de trabalho.|
|WorkflowStage|Representa um estágio em um fluxo de trabalho.|

## <a name="exchange-admin-schema"></a>Esquema de administração do Exchange



|**Parâmetros**|**Tipo**|**Obrigatório**|**Descrição**|
|:-----|:-----|:-----|:-----|
|ModifiedObjectResolvedName|Edm.String|Não|Esse é o nome amigável do objeto que foi modificado pelo cmdlet. Ele é registrado somente se o cmdlet modificar o objeto.|
|Parâmetros|Collection(Common.NameValuePair)|Não|O nome e o valor de todos os parâmetros que foram usados ​​com o cmdlet identificado na propriedade Operations.|
|ModifiedProperties|Collection(Common.ModifiedProperty)|Não|A propriedade está incluída para eventos de administrador. A propriedade inclui o nome da propriedade que foi modificada, o novo valor da propriedade modificada e o valor anterior do objeto modificado.|
|ExternalAccess|Edm.Boolean|Sim|Especifica se o cmdlet foi executado por um usuário em sua organização, pela equipe de datacenters da Microsoft ou por uma conta de serviço do datacenter ou por um administrador delegado. O valor **Falso** indica que o cmdlet foi executado por alguém em sua organização. O valor **Verdadeiro** indica que o cmdlet foi executado pela equipe do datacenter, por uma conta de serviço do datacenter ou por um administrador delegado.|
|OriginatingServer|Edm.String|Não|O nome do servidor do qual o cmdlet foi executado.|
|OrganizationName|Edm.String|Não|O nome do locatário.|


## <a name="exchange-mailbox-schema"></a>Esquema de caixa de correio do Exchange



|**Parâmetros**|**Tipo**|**Obrigatório**|**Descrição**|
|:-----|:-----|:-----|:-----|
|LogonType|Self.[LogonType](#logontype)|Não| Indica o tipo de usuário que acessou a caixa de correio e executou a operação que foi registrada.|
|InternalLogonType|Self.[LogonType](#logontype)|Não|Reservado para uso interno.|
|MailboxGuid|Edm.String|Não|O GUID do Exchange da caixa de correio que foi acessada.|
|MailboxOwnerUPN|Edm.String|Não|O endereço de email da pessoa que possui a caixa de correio que foi acessada.|
|MailboxOwnerSid|Edm.String|Não|O SID do proprietário da caixa de correio.|
|MailboxOwnerMasterAccountSid|Edm.String|Não|SID da conta principal da conta do proprietário da caixa de correio.|
|LogonUserSid|Edm.String|Não|O SID do usuário que executou a operação.|
|LogonUserDisplayName|Edm.String|Não|O nome amigável do usuário que executou a operação.|
|ExternalAccess|Edm.Boolean|Sim|Isso se aplica se o domínio do usuário de logon for diferente do domínio do proprietário da caixa de correio.|
|OriginatingServer |Edm.String|Não|De onde a operação se originou.|
|OrganizationName|Edm.String|Não|O nome do locatário.|
|ClientInfoString|Edm.String|Não|Informações sobre o cliente de email que foi usado para executar a operação, como uma versão do navegador, versão do Outlook e informações do dispositivo móvel.|
|ClientIPAddress|Edm.String|Não|O endereço IP do dispositivo que foi usado quando a operação foi registrada. O endereço IP é exibido em um formato de endereço IPv4 ou IPv6.|
|ClientMachineName|Edm.String|Não|O nome da computador que hospeda o cliente do Outlook.|
|ClientProcessName|Edm.String|Não|O cliente de email que foi usado para acessar a caixa de correio. |
|ClientVersion|Edm.String|Não|A versão do cliente de email.|


### <a name="enum-logontype---type-edmint32"></a>Enumeração: LogonType - Tipo: Edm.Int32

#### <a name="logontype"></a>LogonType


|**Valor**|**Nome do membro**|**Descrição**|
|:-----|:-----|:-----|
|0|Owner|O proprietário da caixa de correio.|
|1|Admin|Uma pessoa com privilégios administrativos para a caixa de correio de uma pessoa.|
|2|Delegated|Uma pessoa com privilégios de delegado para a caixa de correio de uma pessoa.|
|3|Transport|Um serviço de transporte no datacenter da Microsoft.|
|4|SystemService|Uma conta de serviço no datacenter da Microsoft.|
|5|BestAccess|Reservado para uso interno.|
|6|DelegatedAdmin|Um administrador delegado.|


### <a name="exchangemailboxauditgrouprecord-schema"></a>Esquema ExchangeMailboxAuditGroupRecord



|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|Folder|Self.[ExchangeFolder](#exchangefolder-complex-type)|Não|A pasta onde um grupo de itens está localizado.|
|CrossMailboxOperations|Edm.Boolean|Não|Indica se a operação envolveu mais de uma caixa de correio.|
|DestMailboxId|Edm.Guid|Não|Definido somente se o parâmetro CrossMailboxOperations for **True**. Especifica o GUID da caixa de correio de destino.|
|DestMailboxOwnerUPN|Edm.String|Não|Definido somente se o parâmetro CrossMailboxOperations for **True**. Especifica o UPN do proprietário da caixa de correio de destino.|
|DestMailboxOwnerSid|Edm.String|Não|Definido somente se o parâmetro CrossMailboxOperations for **True**. Especifica o SID da caixa de correio de destino.|
|DestMailboxOwnerMasterAccountSid|Edm.String|Não|Definido somente se o parâmetro CrossMailboxOperations for **True**. Especifica o SID do SID da conta principal do proprietário da caixa de correio de destino.|
|DestFolder|Self.[ExchangeFolder](#exchangefolder-complex-type)|Não|A pasta de destino, para operações como Mover.|
|Folders|Collection(Self.[ExchangeFolder](#exchangefolder-complex-type))|Não|Informações sobre as pastas de origem envolvidas em uma operação; por exemplo, se as pastas forem selecionadas e excluídas.|
|AffectedItems|Collection(Self.[ExchangeItem](#exchangeitem-complex-type))|Não|Informações sobre cada item no grupo.|



### <a name="exchangemailboxauditrecord-schema"></a>Esquema ExchangeMailboxAuditRecord



|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|Item|Self.[ExchangeItem](#exchangeitem-complex-type)|Não|Representa o item no qual a operação foi executada|
|ModifiedProperties|Collection(Edm.String)|Não|A definir|
|SendAsUserSmtp|Edm.String|Não|Endereço SMTP do usuário que está sendo representado.|
|SendAsUserMailboxGuid|Edm.Guid|Não|O GUID do Exchange da caixa de correio que foi acessada para enviar email.|
|SendOnBehalfOfUserSmtp|Edm.String|Não|O endereço SMTP do usuário em nome de quem o email é enviado.|
|SendOnBehalfOfUserMailboxGuid|Edm.Guid|Não|O GUID do Exchange da caixa de correio que foi acessada para enviar emails.|


### <a name="exchangeitem-complex-type"></a>Tipo complexo ExchangeItem


|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|Id|Edm.String|Sim|A ID do repositório.|
|Subject|Edm.String|Não|A linha de assunto da mensagem que foi acessada.|
|ParentFolder|Edm.ExchangeFolder|Não|O nome da pasta onde o item está localizado.|
|Attachments|Edm.String|Não|Uma lista dos nomes e tamanho de arquivo de todos os itens anexados à mensagem.|

### <a name="exchangefolder-complex-type"></a>Tipo complexo ExchangeFolder



|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|Id|Edm.String|Sim|A ID do repositório do objeto da pasta.|
|Path|Edm.String|Não|O nome da pasta da caixa de correio em que a mensagem que foi acessada está localizada.|



## <a name="azure-active-directory-base-schema"></a>Esquema Base do Azure Active Directory



|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|AzureActiveDirectoryEventType|Self.[AzureActiveDirectoryEventType](#azureactivedirectoryeventtype)|Sim|O tipo de evento do Azure AD. |
|ExtendedProperties|Collection(Common.NameValuePair)|Não|As propriedades estendidas do evento do Azure AD.|
|ModifiedProperties|Collection(Common.ModifiedProperty)|Não|Esta propriedade está incluída para eventos de administrador. A propriedade inclui o nome da propriedade que foi modificada, o novo valor da propriedade modificada e o valor anterior da propriedade modificada.|

### <a name="enum-azureactivedirectoryeventtype---type--edmint32"></a>Enumeração: AzureActiveDirectoryEventType - Tipo: Edm.Int32

#### <a name="azureactivedirectoryeventtype"></a>AzureActiveDirectoryEventType

|**Nome do membro**|**Descrição**|
|:-----|:-----|
|AccountLogon|O evento de logon da conta.|
|AzureApplicationAuditEvent|O evento de segurança do aplicativo do Azure.|

## <a name="azure-active-directory-account-logon-schema"></a>Esquema de Logon da Conta do Azure Active Directory



|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|Application|Edm.String|Não|O aplicativo que dispara o evento de login da conta, como o Office 15.|
|Client|Edm.String|Não|Detalhes sobre o dispositivo cliente, o SO do dispositivo e o navegador do dispositivo que foi usado para o evento de logon da conta.|
|LoginStatus|Edm.Int32|Sim|Esta propriedade é diretamente do OrgIdLogon.LoginStatus. O mapeamento de várias falhas interessantes de logon pode ser feito por meio do alerta de algoritmos.|
|UserDomain|Edm.String|Sim|Informações de Identidade do Locatário (TII, Tenant Identity Information).|



### <a name="enum-credentialtype---type-edmint32"></a>Enumeração: CredentialType - Tipo: Edm.Int32



|**Valor**|**Nome do membro**|**Descrição**|
|:-----|:-----|:-----|
|-1|Other|Outra autenticação.|
|0|Password|A credencial do usuário é o nome de usuário e a senha.|
|1|MobilePhone|A credencial do usuários é o telefone celular.|
|2|SecretQuestion|A credencial do usuário é a pergunta secreta.|
|3|SecurePin|A credencial do usuário é um PIN seguro.|
|4|SecurePinReset|A credencial do usuário é a redefinição do PIN seguro.|
|11|EasyID|A credencial do usuário é EasyID.|
|14|PasswordIndexCredentialType|A credencial do usuário é PasswordIndexCredentialType.|
|16|Device|A credencial do usuário é um dispositivo.|
|17|ForeignRealmIndex|A credencial do usuário é ForeignRealmIndex.|

### <a name="enum-logintype---type-edmint32"></a>Enumeração: LoginType - Tipo: Edm.Int32



|**Valor**|**Nome do membro**|**Descrição**|
|:-----|:-----|:-----|
|-1|Other|Outro tipo de i.|
|1|InitialAuth|Login com autenticação inicial.|
|2|CookieCopy|Login com cookies.|
|3|SilentReAuth|Logon com reautenticação silenciosa.|


### <a name="enum-authenticationmethod---type-edmint32"></a>Enumeração: AuthenticationMethod - Tipo: Edm.Int32



|**Valor**|**Nome do membro**|**Descrição**|
|:-----|:-----|:-----|
|0|Min|O método de autenticação é um Min.|
|1|Password|O método de autenticação é uma senha.|
|2|Digest|O método de autenticação é um resumo.|
|3|ProxyAuth|O método de autenticação é um ProxyAuth.|
|4|InfoCard|O método de autenticação é um InfoCard.|
|5|DAToken|O método de autenticação é um DAToken.|
|6|Sha1RememberMyPassword|O método de autenticação é um Sha1RememberMyPassword.|
|7|LMPasswordHash|O método de autenticação é um LMPasswordHash.|
|8|ADFSFederatedToken|O método de autenticação é um ADFSFederatedToken.|
|9|EID|O método de autenticação é um EID.|
|10|DeviceID|O método de autenticação é um DeviceID. |
|11|MD5|O método de autenticação é MD5.|
|12|EncProxyPasswordHash|O método de autenticação é um EncProxyPasswordHash.|
|13|LWAFederation|O método de autenticação é um LWAFederation.|
|14|Sha1HashedPassword|O método de autenticação é um Sha1HashedPassword.|
|15|SecurePin|O método de autenticação é um Pin seguro.|
|16|SecurePinReset|O método de autenticação é uma redefinição de um Pin seguro.|
|17|SAML20PostSimpleSign|O método de autenticação é um SAML20PostSimpleSign.|
|18|SAML20Post|O método de autenticação é um SAML20Post.|
|19|OneTimeCode|O método de autenticação é um código único.|



## <a name="azure-active-directory-schema"></a>Esquema do Azure Active Directory



|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|Actor|Collection(Self.[IdentityTypeValuePair](#complex-type-identitytypevaluepair))|Não|O usuário ou a entidade de serviço que executou a ação.|
|ActorContextId|Edm.String|Não|O GUID da organização à qual o ator pertence.|
|ActorIpAddress|Edm.String|Não|O endereço IP do ator no formato de endereço IPV4 ou IPV6.|
|InterSystemsId|Edm.String|Não|O GUID que controla as ações entre componentes dentro do serviço do Office 365.|
|IntraSystemsId|Edm.String|Não|O GUID gerado pelo Azure Active Directory para acompanhar a ação.|
|SupportTicketId|Edm.String|Não|O ID do ticket de suporte ao cliente para a ação em situações de "agir em nome de".|
|Target|Collection(Self.[IdentityTypeValuePair](#complex-type-identitytypevaluepair))|Não|O usuário em que a ação (identificada pela propriedade Operation) foi executada.|
|TargetContextId|Edm.String|Não|O GUID da organização à qual o usuário de destino pertence.|



### <a name="complex-type-identitytypevaluepair"></a>Tipo complexo IdentityTypeValuePair



|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|ID|Edm.String|Sim|O valor da identidade de acordo com o tipo.|
|Type|Self.IdentityType|Sim|O tipo da identidade.|

### <a name="enum-identitytype---type-edmint32"></a>Enumeração: IdentityType - Tipo: Edm.Int32

#### <a name="identitytype"></a>IdentityType

|**Nome do membro**|**Descrição**|
|:-----|:-----|
|Claim|A identidade é uma declaração para fins de autorização.|
|Name|O ator de ação de auditoria ou o nome de exibição da identidade de destino.|
|Other|A identidade do ator é outro tipo, como o ObjectId no GUID gerado pelo serviço do Office 365.|
|PUID|O ator da ação de auditoria ou a ID exclusiva do passaporte de destino (PUID).|
|SPN|A identidade de uma entidade de segurança de serviço, se a ação for executada pelo serviço do Office 365.|
|UPN|O nome da entidade de segurança do usuário.|


## <a name="azure-active-directory-secure-token-service-sts-logon-schema"></a>Esquema de logon do Serviço de Token Seguro (STS) do Active Directory do Azure

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|ApplicationId|Edm.String|Não|O GUID que representa o aplicativo que está solicitando o logon. O nome de exibição pode ser pesquisado por meio da API de gráfico do Azure Active Directory.|
|Client|Edm.String|Não|Informações do dispositivo cliente, fornecidas pelo navegador que executa o logon.|
|LogonError|Edm.String|Não|Para logons com falha, contém o motivo pelo qual o logon falhou.|

## <a name="dlp-schema"></a>Esquema DLP

Os eventos de DLP estão disponíveis para o Exchange Online, o SharePoint Online e o OneDrive For Business. Observe que os eventos de DLP no Exchange só estão disponíveis para eventos com base na política DLP unificada (por exemplo, configurados por meio do Centro de Conformidade e Segurança). Não há suporte para eventos de DLP com base em Regras de Transporte do Exchange.

Os eventos de DLP (Prevenção contra Perda de Dados) sempre terão UserKey = "DlpAgent" no esquema Comum. Existem três tipos DlpEvents que estão armazenados como o valor da propriedade Operation do esquema comum:

- DlpRuleMatch – indica que uma regra foi correspondida. Esses eventos existem no Exchange, no SharePoint Online e no OneDrive for Business. Para o Exchange, inclui informações de falsos positivos e de substituição. Para o SharePoint Online e o OneDrive for Business, falsos positivos e as substituições geram eventos separados.

- DlpRuleUndo – existem apenas no SharePoint Online e no OneDrive for Business e indicam que uma ação de política aplicada anteriormente foi "desfeita" – seja por causa de designação de falso positivo/substituição pelo usuário, ou porque o documento não está mais sujeito à política (seja devido a mudança de política ou alteração de conteúdo no documento).

- DlpInfo – existem apenas no SharePoint Online e no OneDrive for Business e indicam uma designação de falso positivo, mas nenhuma ação foi "desfeita".

|**Parâmetros**|**Tipo**|**Obrigatório**|**Descrição**|
|:-----|:-----|:-----|:-----|
|SharePointMetaData|Self.[SharePointMetadata](#sharepointmetadata-complex-type)|Não|Descreve os metadados sobre o documento no SharePoint ou o OneDrive for Business que continham as informações confidenciais.|
|ExchangeMetaData|Self.[ExchangeMetadata](#exchangemetadata-complex-type)|Não|Descreve os metadados sobre a mensagem de email que continha as informações confidenciais.|
|ExceptionInfo|Edm.String|Não|Identifica os motivos pelos quais uma política não se aplica mais e/ou qualquer informação sobre falso positivos e/ou substituição observada pelo usuário final.|
|PolicyDetails|Collection(Self.[PolicyDetails](#policydetails-complex-type))|Sim|Informações sobre uma ou mais políticas que dispararam o evento de DLP.|
|SensitiveInfoDetectionIsIncluded|Boolean|Sim|Indica se o evento contém o valor do tipo de dados confidenciais e o contexto adjacente do conteúdo de origem. O acesso a dados confidenciais exige a permissão "Ler eventos de política DLP, incluindo detalhes confidenciais" no Azure Active Directory.|

### <a name="sharepointmetadata-complex-type"></a>Tipo complexo SharePointMetadata

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|From|Edm.String|Sim|O usuário que disparou o evento. Será FileOwner, LastModifier ou LastSharer.|
|itemCreationTime|Edm.Date|Sim|Datetimestamp em UTC de quando o evento foi registrado.|
|SiteCollectionGuid|Edm.Guid|Sim|O GUID do conjunto de sites.|
|SiteCollectionUrl|Edm.String|Sim|Nome do site do SharePoint.|
|FileName|Edm.String|Sim|Nome do caminho.|
|FileOwner|Edm.String|Sim|O proprietário do documento.|
|FilePathUrl|Edm.String|Sim|A URL do documento.|
|DocumentLastModifier|Edm.String|Sim|O usuário que modificou o documento pela última vez.|
|DocumentSharer|Edm.String|Sim|O usuário que modificou pela última vez o compartilhamento do documento.|
|UniqueId|Edm.String|Sim|Uma GUID que identifica o arquivo.|
|LastModifiedTime|Edm.DateTime|Sim|Carimbo de data/hora em UTC de quando o documento foi modificado pela última vez.|


### <a name="exchangemetadata-complex-type"></a>Tipo complexo ExchangeMetadata

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|MessageID|Edm.String|Sim|A ID da mensagem do email que disparou o evento.|
|From|Edm.String|Sim|O usuário que enviou o email.|
|To|Collection(Edm.String)|Não|Uma coleção de endereços de email que estavam na linha Para da mensagem.|
|CC|Collection(Edm.String)|Não|Uma coleção de endereços de email que estavam na linha CC da mensagem.|
|BCC|Collection(Edm.String)|Não|Uma coleção de endereços de email que estavam na linha BCC da mensagem.|
|Subject|Edm.String|Sim|Assunto da mensagem de email.|
|Sent|Edm.DateTime|Sim|O horário em UTC de quando o email foi enviado.|
|RecipientCount|Edm.Int32|Sim|O número total de todos os destinatários nas linhas TO, CC e BCC da mensagem.|


### <a name="policydetails-complex-type"></a>Tipo complexo PolicyDetails

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|PolicyId|Edm.Guid|Sim|O GUID da política DLP para este evento.|
|PolicyName|Edm.String|Sim|O nome amigável da política DLP para este evento.|
|Rules|Collection(Self.[Rules](#rules-complex-type))|Sim|As informações sobre as regras da política que foram atendidas para este evento.|

### <a name="rules-complex-type"></a>Tipo complexo Rules

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|RuleId|Edm.Guid|Sim|O GUID da regra DLP para este evento.|
|RuleName|Edm.String|Sim|O nome amigável da regra DLP para este evento.|
|Actions|Collection(Edm.String)|Não|Uma lista de ações tomadas como resultado de um evento DLP RuleMatch.|
|OverriddenActions|Collection(Edm.String)|Não|Uma lista de ações realizadas anteriormente que foram desfeitas como resultado de um evento DLPRuleUndo. |
|Severity|Edm.String|Não|A gravidade (Baixa, Média e Alta) da conformidade com a regra.|
|RuleMode|Edm.String|Sim|Indique se a regra DLP foi definida como Enforce, Audit with Notify ou somente Audit.|
|ConditionsMatched|Self.[ConditionsMatched](#conditionsmatched-complex-type)|Não|Os detalhes sobre quais condições da regra foram atendidas para este evento.|

### <a name="conditionsmatched-complex-type"></a>Tipo complexo ConditionsMatched

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|SensitiveInformation|Collection(Self.[SensitiveInformation](#sensitiveinformation-complex-type))|Não|As informações sobre o tipo de informações confidenciais detectadas.|
|DocumentProperties|Collection(NameValuePair)|Não|As informações sobre as propriedades do documento que dispararam uma correspondência de regra.|
|OtherConditions|Collection(NameValuePair)|Não|Uma lista de pares de valores chave que descrevem quaisquer outras condições que foram correspondidas.|

### <a name="sensitiveinformation-complex-type"></a>Tipo complexo SensitiveInformation

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|Confidence|Edm.Int|Sim|A confiança do padrão que correspondeu à detecção.|
|Count|Edm.Int|Sim|O número de instâncias confidenciais detectadas.|
|SensitiveType|Edm.Guid|Sim|Um guid que identifica o tipo de dados confidenciais detectados.|
|SensitiveInformationDetections|Self.SensitiveInformationDetections|Não|Uma matriz de objetos que contêm dados de informações confidenciais com os seguintes detalhes – valor correspondente e contexto do valor correspondente.|

### <a name="sensitiveinformationdetections-complex-type"></a>Tipo complexo SensitiveInformationDetections 
Os dados confidenciais de DLP só estão disponíveis na API de feed de atividades para usuários que receberam permissões para "Ler dados confidenciais de DLP". 

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|Detections|Collection(Self.Detections)|Sim|Uma matriz de informações confidenciais que foram detectadas. As informações contêm pares de valores chave com Valor = valor correspondente (por exemplo, o valor de cartão de crédito de seguro social dos EUA) e o Contexto = um trecho do conteúdo de origem que contém o valor correspondente. |
|ResultsTruncated|Edm.Boolean|Sim|Indica se os logs foram truncados devido ao grande número de resultados. |

### <a name="exceptioninfo-complex-type"></a>Tipo complexo ExceptionInfo

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|Reason|Edm.String|Não|Para um evento DLPRuleUndo, isso indica por que a regra não se aplica mais, o que pode ocorrer devido a um dos três motivos: substituição, alteração de documento ou alteração de política|
|FalsePositive|Edm.Boolean|Não|Indica se o usuário designou esse evento como falso positivo.|
|Justification|Edm.String|Não|Se o usuário tiver optado por substituir a política, qualquer justificativa especificada pelo usuário será capturada aqui.|
|Rules|Collection(Edm.Guid)|Não|Uma coleção de guids para cada regra designada como falso positivo ou substituta, ou para a qual uma ação foi desfeita.|

## <a name="security-and-compliance-center-schema"></a>Esquema do Centro de Conformidade e Segurança

|**Parâmetros**|**Tipo**|**Obrigatório**|**Descrição**|
|:-----|:-----|:-----|:-----|
|StartTime|Edm.Date|Não|A data e hora em que o cmdlet foi executado.|
|ClientRequestId|Edm.String|Não|Um GUID que pode ser usado para correlacionar esse cmdlet com as operações de UX do Centro de Conformidade e Segurança. Essas informações são usadas apenas pelo suporte da Microsoft.|
|CmdletVersion|Edm.String|Não|A versão de build do cmdlet quando foi executado.|
|EffectiveOrganization|Edm.String|Não|O GUID da organização afetada pelo cmdlet. (Descontinuado: este parâmetro será retirado no futuro.)|
|UserServicePlan|Edm.String|Não|O plano de serviço Proteção do Exchange Online atribuído ao usuário que executou o cmdlet.|
|ClientApplication|Edm.String|Não|Se o cmdlet tiver sido executado por um aplicativo, ao contrário do powershell remoto, esse campo conterá o nome desse aplicativo.|
|Parâmetros|Edm.String|Não|O nome e o valor dos parâmetros que foram usados ​​com o cmdlet que não incluem Informações de Identificação Pessoal.|
|NonPiiParameters|Edm.String|Não|O nome e o valor dos parâmetros que foram usados ​​com o cmdlet que incluem Informações de Identificação Pessoal. (Preterido: esse campo será retirado no futuro e seu conteúdo mesclado com o campo de parâmetros.)|

## <a name="security-and-compliance-alerts-schema"></a>Esquema de Alertas de Conformidade e Segurança

Os sinais de alerta incluem:

- Todos os alertas gerados baseados nas [Políticas de alerta no Centro de Conformidade e Segurança](https://docs.microsoft.com/office365/securitycompliance/alert-policies#default-alert-policies).
- Alertas relacionados ao Office 365 gerados no [Office 365 Cloud App Security](https://docs.microsoft.com/office365/securitycompliance/office-365-cas-overview) e no [Microsoft Cloud App Security](https://docs.microsoft.com/pt-BR/cloud-app-security/what-is-cloud-app-security).

O UserId e o UserKey desses eventos são sempre SecurityComplianceAlerts. Existem dois tipos de sinais de alerta armazenados como o valor da propriedade Operation do esquema comum:

- AlertTriggered – um novo alerta é gerado devido a uma correspondência com a política.

- AlertEntityGenerated – uma nova entidade é adicionada a um alerta. Este evento somente é aplicável aos alertas gerados com base nas Políticas de alerta no Centro de Conformidade e Segurança do Office 365. Cada alerta gerado pode ser associado a um ou vários desses eventos. Por exemplo, uma política de alerta é definida para disparar um alerta se um usuário exclui mais de 100 arquivos em cinco minutos. Se dois usuários ultrapassarem o limite ao mesmo tempo, haverá dois eventos AlertEntityGenerated, mas apenas um evento AlertTriggered.

|**Parâmetros**|**Tipo**|**Obrigatório**|**Descrição**|
|:-----|:-----|:-----|:-----|
|AlertId|Edm.Guid|Sim|O GUID do alerta.|
|AlertType|Self.String|Sim|Tipo do alerta. Os tipos de alertas incluem: <ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p>Sistema</p></li><li><p>Personalizado</p></li>|
|Name|Edm.String|Sim|Nome do alerta.|
|PolicyId|Edm.Guid|Não|O GUID da política que disparou o alerta.|
|Status|Edm.String|Não|Status do alerta. Os status incluem: <ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p>Ativo</p></li><li><p>Investigando</p></li><li><p>Resolvido</p></li><li><p>Descartado</p></li></ul>|
|Severity|Edm.String|Não|Gravidade do alerta. Os níveis de gravidade incluem: <ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p>Baixo</p></li><li><p>Médio</p></li><li><p>Alto</p></li></ul>|
|Categoria|Edm.String|Não|Categoria do alerta. As categorias incluem: <ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p>DataLossPrevention</p></li><li><p>ThreatManagement</p></li><li><p>DataGovernance</p></li><li><p>AccessGovernance</p></li><li><p>MailFlow</p></li><li><p>Other</p></li></ul>|
|Source|Edm.String|Não|Fonte do alerta. As fontes incluem: <ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p>Conformidade e Segurança do Office 365</p></li><li><p>Segurança no Aplicativo na Nuvem</p></li></ul>|
|Comments|Edm.String|Não|Comentários realizados pelos usuários que visualizaram o alerta. Por padrão, é "Novo alerta".|
|Data|Edm.String|Não|O BLOB de dados de detalhes do alerta ou da entidade de alerta.|
|AlertEntityId|Edm.String|Não|O identificador da entidade de alerta. Esse parâmetro só é aplicável em eventos AlertEntityGenerated.|
|EntityType|Edm.String|Não|Tipo de entidade ou entidade de alerta. Os tipos de entidades incluem: <ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p>User</p></li><li><p>Recipients</p></li><li><p>Sender</p></li><li><p>MalwareFamily</p></li></ul>Esse parâmetro só é aplicável em eventos AlertEntityGenerated.|

## <a name="yammer-schema"></a>Esquema do Yammer

Os eventos do Yammer listados em [Pesquisar o log de auditoria no Centro de Proteção do Office 365](https://support.office.com/pt-BR/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c?ui=en-US&amp;rs=en-US&amp;ad=US) usarão este esquema.

|**Parâmetros**|**Tipo**|**Obrigatório**|**Descrição**|
|:-----|:-----|:-----|:-----|
|ActorUserId|Edm.String|Não|Email do usuário que executou a operação.|
|ActorYammerUserId|Edm.Int64|Não|ID do usuário que executou a operação.|
|DataExportType|Edm.String|Não|Retorna "dados" se a exportação de dados incluir mensagens, notas, arquivos, tópicos, usuários e grupos; retorna "usuário" se a exportação de dados incluir apenas usuários.|
|FileId|Edm.Int64|Não|ID do arquivo na operação. |
|FileName|Edm.String|Não|Nome do arquivo na operação. Será exibido em branco se não for relevante para a operação.|
|GroupName|Edm.String|Não|Nome do grupo na operação. Será exibido em branco se não for relevante para a operação.|
|IsSoftDelete|Edm.Boolean|Não|Retorna "true" se a política de retenção de dados da rede estiver definida como exclusão reversível; retorna "false" se a política de retenção de dados da rede estiver definida como Exclusão Irreversível.|
|MessageId|Edm.Int64|Não|ID da mensagem na operação.|
|YammerNetworkId|Edm.Int64|Não|ID da rede do usuário que executou a operação.|
|TargetUserId|Edm.String|Não|Email do usuário de destino na operação. Será exibido em branco se não for relevante para a operação.|
|TargetYammerUserId|Edm.Int64|Não|ID do usuário de destino na operação.|
|VersionId|Edm.Int64|Não|ID da versão do arquivo na operação.|

## <a name="sway-schema"></a>Esquema do Sway

Os eventos do Sway listados em [Pesquisar o log de auditoria do Centro de Proteção do Office 365](https://support.office.com/pt-BR/article/Search-the-audit-log-in-the-Office-365-Security-Compliance-Center-0d4d0f35-390b-4518-800e-0c7ec95e946c?ui=en-US&amp;rs=en-US&amp;ad=US) (excluindo os eventos de arquivo e pasta) usarão este esquema.

|**Parâmetro**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|ObjectType|Self.[ObjectType](#objecttype)|Não|O ponto de acesso para o evento disparado. Os pontos de acesso incluem: <ul xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mtps="http://msdn2.microsoft.com/mtps" xmlns:mshelp="http://msdn.microsoft.com/mshelp" xmlns:ddue="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:msxsl="urn:schemas-microsoft-com:xslt"><li><p>Sway</p></li><li><p>Sway inserido em um host</p></li><li><p>Configurações do Sway no portal de administração do Office 365</p></li></ul>|
|Endpoint|Self.[Endpoint](#endpoint)|Não|O ponto de extremidade do cliente Sway para o evento disparado. O ponto de extremidade do cliente Sway pode ser Web, iOS, Windows ou Android. |
|BrowserName|Edm.String|Não|O navegador usado para acessar o Sway para o evento disparado. |
|DeviceType|Self.[DeviceType](#devicetype)|Não|O tipo de dispositivo usado para acessar o Sway para o evento disparado. O tipo de dispositivo pode ser desktop, celular ou tablet.|
|SwayLookupId|Edm.String|Não|A ID do Sway. |
|SiteUrl|Edm.String|Não|A URL para o Sway.|
|OperationResult|Self.[OperationResult](#operationresult)|Não|Sucesso ou falha.|


### <a name="enum-objecttype---type-edmint32"></a>Enumeração: ObjectType - Tipo: Edm.Int32

#### <a name="objecttype"></a>ObjectType

|**Valor**|**Nome do membro**|**Descrição**|
|:-----|:-----|:-----|
|0|Sway|O evento foi disparado de um Sway.|
|1|SwayEmbedded|O evento foi disparado de um Sway, que é inserido em um host.|
|2|SwayAdminPortal|O evento foi disparado a partir das configurações do serviço Sway no portal de administração do Office 365.|


### <a name="enum-operationresult---type-edmint32"></a>Enumeração: OperationResult - Tipo: Edm.Int32

#### <a name="operationresult"></a>OperationResult

|**Valor**|**Nome do membro**|**Descrição**|
|:-----|:-----|:-----|
|0|Succeeded|O evento foi bem-sucedido.|
|1|Failed|O evento falhou.|


### <a name="enum-endpoint---type-edmint32"></a>Enumeração: Endpoint - Tipo: Edm.Int32

#### <a name="endpoint"></a>Endpoint

|**Valor**|**Nome do membro**|**Descrição**|
|:-----|:-----|:-----|
|0|SwayWeb|O evento foi acionado usando o cliente Web do Sway.|
|1|SwayIOS|O evento foi acionado usando o cliente iOS do Sway.|
|2|SwayWindows|O evento foi acionado usando o cliente Windows do Sway.|
|3|SwayAndroid|O evento foi acionado usando o cliente Android do Sway.|



### <a name="enum-devicetype---type-edmint32"></a>Enumeração: DeviceType - Tipo: Edm.Int32

#### <a name="devicetype"></a>DeviceType

|**Valor**|**Nome do membro**|**Descrição**|
|:-----|:-----|:-----|
|0|Desktop|O evento foi acionado usando o desktop.|
|1|Mobile|O evento foi acionado usando um dispositivo móvel.|
|2|Tablet|O evento foi acionado usando um dispositivo tablet.|



### <a name="enum-swayauditoperation---type-edmint32"></a>Enumeração: SwayAuditOperation - Tipo: Edm.Int32

#### <a name="swayauditoperation"></a>SwayAuditOperation

|**Valor**|**Nome do membro**|**Descrição**|
|:-----|:-----|:-----|
|1|Create|O usuário cria um Sway.|
|2|Delete|O usuário exclui um Sway.|
|3|View|O usuário exibe um Sway.|
|4|Edit|O usuário edita um Sway.|
|5|Duplicate|O usuário duplica um Sway.|
|7|Compartilhar|O usuário inicia o compartilhamento de um Sway. Esse evento captura a ação do usuário de clicar em um destino de compartilhamento específico no menu de compartilhamento do Sway. O evento não indica se o usuário realmente segue e conclui a ação de compartilhamento.|
|8|ChangeShareLevel|O usuário altera o nível da compartilhamento de um Sway. Esse evento captura o usuário alterando o escopo de compartilhamento associado a um Sway. Por exemplo, público em comparação a interno da organização.|
|9|RevokeShare|O usuário para de compartilhar um Sway revogando o acesso. Revogar o acesso altera os links associados a um Sway.|
|10|EnableDuplication|O usuário habilita a duplicação de um Sway (ativado por padrão).|
|11|DisableDuplication|O usuário desabilita a duplicação de um Sway (desativado por padrão).|
|12|ServiceOn|O usuário habilita o Sway para toda a organização através do Centro de administração do Office 365 (ativado por padrão).|
|13|ServiceOff|O usuário desabilita o Sway para toda a organização através do Centro de administração do Office 365 (desativado por padrão).|
|14|ExternalSharingOn|O usuário habilita o compartilhamento externo para toda a organização através do Centro de administração do Office 365.|
|15|ExternalSharingOff|O usuário desabilita o compartilhamento externo para toda a organização através do Centro de administração do Office 365.|

## <a name="data-center-security-base-schema"></a>Esquema Base de Segurança do Data Center

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|DataCenterSecurityEventType|Self.[DataCenterSecurityEventType](#datacentersecurityeventtype)|Sim|O tipo de evento cmdlet na caixa de bloqueio.|

### <a name="enum-datacentersecurityeventtype---type-edmint32"></a>Enumeração: DataCenterSecurityEventType: - Tipo: Edm.Int32

#### <a name="datacentersecurityeventtype"></a>DataCenterSecurityEventType


|**Nome do membro**|**Descrição**|
|:-----|:-----|
|DataCenterSecurityCmdletAuditEvent|Esse é o valor de enumeração para o evento de tipo de auditoria de cmdlet.|



## <a name="data-center-security-cmdlet-schema"></a>Esquema Cmdlet de Segurança do Data Center



|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|StartTime|Edm.Date|Sim|O horário de início da execução do cmdlet.|
|EffectiveOrganization|Edm.String|Sim|O nome do locatário para o qual a elevação/cmdlet foi direcionado.|
|ElevationTime|Edm.Date|Sim|O horário de início da elevação.|
|ElevationApprover|Edm.String|Sim|O nome de um gerente da Microsoft.|
|ElevationApprovedTime|Edm.Date|Não|O carimbo de data/hora para quando a elevação foi aprovada.|
|ElevationRequestId|Edm.Guid|Sim|Um identificador exclusivo para a solicitação de elevação.|
|ElevationRole|Edm.String|Não|A função da elevação.|
|ElevationDuration|Edm.Int32|Sim|A duração para a qual a elevação estava ativa.|
|GenericInfo|Edm.String|Não|Usada para comentários e outras informações genéricas.|


## <a name="microsoft-teams-schema"></a>Esquema do Microsoft Teams

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|MessageId|Edm.String|Não|Um identificador para uma mensagem de bate-papo ou canal.|
|MeetupId|Edm.String|Não|Identificador para uma reunião agendada ou ad hoc.|
|Members|Collection(Self.[MicrosoftTeamsMember](#microsoftteamsmember-complex-type))|Não|Uma lista de usuários dentro de uma equipe.|
|TeamName|Edm.String|Não|O nome da equipe que está sendo auditada.|
|TeamGuid|Edm.Guid|Não|Um identificador exclusivo para a equipe que está sendo auditada.|
|ChannelName|Edm.String|Não|O nome do canal que está sendo auditado.|
|ChannelGuid|Edm.Guid|Não|Um identificador exclusivo para o canal que está sendo auditado.|

### <a name="microsoftteamsmember-complex-type"></a>Tipo complexo MicrosoftTeamsMember

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|UPN|Edm.String|Não|O nome da entidade de segurança do usuário.|
|Role|Self.[MemberRoleType](#memberroletype)|Não|A função de usuário dentro da equipe.|
|DisplayName|Edm.String|Não|O nome de exibição do usuário.|

### <a name="enum-memberroletype---type-edmint32"></a>Enumeração: MemberRoleType - Tipo: Edm.Int32

#### <a name="memberroletype"></a>MemberRoleType

|**Valor**|**Nome do membro**|**Descrição**|
|:-----|:-----|:-----|
|0|Member|Um usuário que é um membro da equipe.|
|1|Owner|Um usuário que é o proprietário da equipe.|
|2|Guest|Um usuário que não é um membro da equipe.|


## <a name="microsoft-teams-add-ons-schema"></a>Esquema de Complementos do Microsoft Teams

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|AddOnType|Self.[AddOnType](#addontype)|Não|O tipo de complemento que gerou esse evento.|
|AddonName|Edm.String|Não|O nome do complemento que gerou esse evento.|
|AddOnGuid|Edm.Guid|Não|O identificador exclusivo do complemento que gerou esse evento.|
|TabType|Edm.String|Não|O tipo de guia que gerou esse evento.|

### <a name="enum-addontype---type-edmint32"></a>Enumeração: AddOnType - Tipo: Edm.Int32

#### <a name="addontype"></a>AddOnType

|**Valor**|**Nome do membro**|**Descrição**|
|:-----|:-----|:-----|
|1|Bot|Um bot do Microsoft Teams.|
|2|Connector|Um conector do Microsoft Teams.|
|3|Tab|Uma guia do Microsoft Teams.|


## <a name="microsoft-teams-settings-schema"></a>Esquema de Configurações do Microsoft Teams

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|ModifiedProperty|Common.ModifiedProperty|Não|A propriedade que foi modificada. Ela conterá **Name**, **OldValue** e **NewValue** da propriedade.|
|ExtendedProperties|Collection(Common.NameValuePair)|Não|Uma lista de propriedades estendidas para a configuração que está sendo alterada. Cada propriedade terá um **Nome** e **Valor**.|

## <a name="office-365-advanced-threat-protection-and-threat-investigation-and-response-schema"></a>Esquema de Proteção Avançada contra Ameaças e Investigação e Resposta contra Ameaças do Office 365

Os eventos da Proteção Avançada contra Ameaças e Investigação e Resposta contra Ameaças do Office 365 estão disponíveis para clientes do Office 365 que têm uma assinatura do plano Proteção Avançada contra Ameaças Plano 1 do Office 365, Proteção Avançada contra Ameaças Plano 2 do Office 365ou uma assinatura do E5. Cada evento no feed de ATP do Office 365 corresponde aos seguintes itens que foram designados para conter uma ameaça:

- Detecção em mensagens de email enviadas ou recebidas por um usuário na organização no momento da entrega e na [Limpeza automática zero hora](https://support.office.com/pt-BR/article/Zero-hour-auto-purge-protection-against-spam-and-malware-96deb75f-64e8-4c10-b570-84c99c674e15). 

- Detecção de URLs mal-intencionadas clicadas por um usuário na organização no momento do clique com base na proteção [Links seguros de ATP do Office 365](https://docs.microsoft.com/office365/securitycompliance/atp-safe-links).  

- Um arquivo armazenado nos serviços SharePoint Online, OneDrive for Business ou Microsoft Teams, detectado como mal intencionado pela proteção da [ATP do Office 365](https://docs.microsoft.com/pt-BR/office365/securitycompliance/atp-for-spo-odb-and-teams).

> [!NOTE]
> Os recursos de Proteção Avançada contra Ameaças do Office 365 e Investigação e Resposta contra Ameaças do Office 365 (anteriormente conhecidos como Office 365 Threat Intelligence) agora fazem parte do Proteção Avançada contra Ameaças Plano 2 do Office 365, com recursos extras de proteção contra ameaças. Para saber mais, confira [Planos e preços da ATP do Office 365](https://products.office.com/exchange/advance-threat-protection) e a [Descrição do serviço da ATP do Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

### <a name="email-message-events"></a>Eventos de mensagens de email

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|AttachmentData|Collection(Self.[AttachmentData](#attachmentdata))|Não|Os dados sobre anexos na mensagem de email que acionaram o evento.|
|Tipo de detecção|Edm.String|Sim|O tipo de detecção (por exemplo, **Embutido** – detectada na hora da entrega; **Atrasado** – detectada após a entrega; **ZAP** – mensagens removidas pela [Limpeza Automática Zero Hora](https://support.office.com/pt-BR/article/Zero-hour-auto-purge-protection-against-spam-and-malware-96deb75f-64e8-4c10-b570-84c99c674e15)). Os eventos com o tipo de detecção ZAP normalmente são precedidos por uma mensagem com um tipo de detecção **Atrasado**.|
|DetectionMethod|Edm.String|Sim|A tecnologia ou método usado pelo Office 365 ATP para a detecção.|
|InternetMessageId|Edm.String|Sim|A ID da mensagem da Internet.|
|NetworkMessageId|Edm.String|Sim|A ID da mensagem de rede do Exchange Online.|
|P1Sender|Edm.String|Sim|O caminho de retorno do remetente da mensagem de email.|
|P2Sender|Edm.String|Sim|O remetente da mensagem de email.|
|Recipients|Collection(Edm.String)|Sim|Uma matriz de destinatários da mensagem de email.|
|SenderIp|Edm.String|Sim|O endereço IP que enviou o email do Office 365. O endereço IP é exibido em um formato de endereço IPv4 ou IPv6.|
|Subject|Edm.String|Sim|A linha de assunto da mensagem.|
|Verdict|Edm.String|Sim|A conclusão da mensagem.|
|MessageTime|Edm.Date|Sim|Data e hora em UTC (Tempo Universal Coordenado), na qual a mensagem de email foi recebida ou enviada.|
|EventDeepLink|Edm.String|Sim|Link profundo para o evento de email no Explorador ou para relatórios em tempo real no Centro de Conformidade e Segurança do Office 365.|

### <a name="attachmentdata-complex-type"></a>Tipo complexo AttachmentData

#### <a name="attachmentdata"></a>AttachmentData

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|FileName|Edm.String|Sim|O nome do arquivo do anexo.|
|FileType|Edm.String|Sim|O tipo de arquivo do anexo.|
|FileVerdict|Self.[FileVerdict](#fileverdict)|Sim|O veredicto de malware do arquivo.|
|MalwareFamily|Edm.String|Não|A família de malware do arquivo.|
|SHA256|Edm.String|Sim|O hash SHA256 do arquivo.|

### <a name="enum-fileverdict---type-edmint32"></a>Enumeração: FileVerdict - Tipo: Edm.Int32

#### <a name="fileverdict"></a>FileVerdict

|**Valor**|**Nome do membro**|**Descrição**|
|:-----|:-----|:-----|
|0|Good|Nenhuma ameaça detectada.|
|1|Bad|Malware encontrado no anexo.|
|-1|Error|Erro de varredura/análise.|
|-2|Timeout|Tempo limite de varredura/análise.|
|-3|Pending|Varredura/análise não concluída.|

### <a name="url-time-of-click-events"></a>Eventos de momento do clique da URL

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|UserId|Edm.String|Sim|O identificador (por exemplo, endereço de email) do usuário que clicou na URL.|
|AppName|Edm.String|Sim|O serviço do Office 365 em que a URL foi clicada (por exemplo, o Email).|
|URLClickAction|Automaticamente. [URLClickAction](#urlclickaction)|Sim|Clique em ação da URL com base nas políticas da organização for [Links seguros do Office 365 ATP](https://docs.microsoft.com/office365/securitycompliance/atp-safe-links).|
|SourceId|Edm.String|Sim|O identificador do serviço do Office 365 em que a URL foi clicada (por exemplo, para o Email, essa é a ID de Mensagens da Rede do Exchange Online).|
|TimeOfClick|Edm.Date|Sim|A data e hora no Tempo Universal Coordenado (UTC) de quando o usuário clicou na URL.|
|URL|Edm.String|Sim|URL clicada pelo usuário.|
|UserIp|Edm.String|Sim|O endereço IP do usuário que clicou na URL. O endereço IP é exibido em um formato de endereço IPv4 ou IPv6.|

### <a name="enum-urlclickaction---type-edmint32"></a>Enumeração: URLClickAction – Tipo: Edm.Int32

#### <a name="urlclickaction"></a>URLClickAction

|**Valor**|**Nome do membro**|**Descrição**|
|:-----|:-----|:-----|
|2|Blockpage|O usuário é impedido de navegar para a URL pelo serviço [Links seguros da ATP do Office 365](https://docs.microsoft.com/office365/securitycompliance/atp-safe-links).|
|3|PendingDetonationPage|O usuário recebe a página de detonação pendente do serviço [Links seguros da ATP do Office 365](https://docs.microsoft.com/office365/securitycompliance/atp-safe-links).|
|4|BlockPageOverride|O usuário é impedido de navegar para a URL pelo serviço [Links seguros da ATP do Office 365](https://docs.microsoft.com/office365/securitycompliance/atp-safe-links), no entanto, ele substitui o bloqueio para navegar até a URL.|
|5|PendingDetonationPageOverride|O usuário recebe a página de detonação do serviço [Links seguros da ATP do Office 365](https://docs.microsoft.com/office365/securitycompliance/atp-safe-links), no entanto, ele a substitui para navegar até a URL.|


### <a name="file-events"></a>Eventos de arquivo

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|FileData|Self.[FileData](#filedata)|Sim|Dados sobre o arquivo que disparou o evento.|
|SourceWorkload|Self.[SourceWorkload](#sourceworkload)|Sim|Carga de trabalho ou serviço em que o arquivo foi encontrado (por exemplo, SharePoint Online, OneDrive for Business ou Microsoft Teams)
|DetectionMethod|Edm.String|Sim|A tecnologia ou o método usado pela ATP do Office 365 para a detecção.|
|LastModifiedDate|Edm.Date|Sim|Data e hora em UTC (Tempo Universal Coordenado), na qual o arquivo foi criado ou modificado pela última vez.|
|LastModifiedBy|Edm.String|Sim|O identificador (por exemplo, um endereço de email) do usuário que criou ou modificou pela última vez o arquivo.|
|EventDeepLink|Edm.String|Sim|Link profundo para o evento de arquivo no Explorador ou para relatórios em tempo real no Centro de Conformidade e Segurança.|

### <a name="filedata-complex-type"></a>Tipo complexo FileData

#### <a name="filedata"></a>FileData

|**Parâmetros**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
|DocumentId|Edm.String|Sim|O identificador exclusivo do arquivo nas plataformas SharePoint, OneDrive ou Microsoft Teams.|
|FileName|Edm.String|Sim|Nome do arquivo que disparou o evento.|
|FilePath|Edm.String|Sim|Caminho (local) do arquivo no SharePoint, OneDrive ou Microsoft Teams.|
|FileVerdict|Self.[FileVerdict](#fileverdict)|Sim|O veredicto de malware do arquivo.|
|MalwareFamily|Edm.String|Não|A família de malware do arquivo.|
|SHA256|Edm.String|Sim|O hash SHA256 do arquivo.|
|FileSize|Edm.String|Sim|Tamanho do arquivo em bytes.|

### <a name="enum-sourceworkload---type-edmint32"></a>Enumeração: SourceWorkload – Tipo: Edm.Int32

#### <a name="sourceworkload"></a>SourceWorkload

|**Valor**|**Nome do membro**|
|:-----|:-----|
|0|SharePoint Online|
|1|OneDrive for Business|
|2|Microsoft Teams|

## <a name="power-bi-schema"></a>Esquema do Power BI

Os eventos do Power BI listados em [Pesquisar o log de auditoria no Centro de Proteção do Office 365](/power-bi/service-admin-auditing#activities-audited-by-power-bi) usarão este esquema.

|**Parameters**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
| AppName               | Edm.String Term="Microsoft.Office.Audit.Schema.PIIFlag" Bool="true"                            |  Não  | O nome do aplicativo em que o evento ocorreu. |
| DashboardName         | Edm.String Term="Microsoft.Office.Audit.Schema.PIIFlag" Bool="true"                            |  Não  | O nome do painel onde o evento ocorreu. |
| DataClassification    | Edm.String Term="Microsoft.Office.Audit.Schema.PIIFlag" Bool="true"                            |  Não  | As [classificação dos dados](/power-bi/service-data-classification), se houver, do painel onde o evento ocorreu. |
| DatasetName           | Edm.String Term="Microsoft.Office.Audit.Schema.PIIFlag" Bool="true"                            |  Não  | O nome do conjunto de dados onde o evento ocorreu. |
| MembershipInformation | Conjunto ([MembershipInformationType](#membershipinformationtype-complex-type)) Term="Microsoft.Office.Audit.Schema.PIIFlag" booleano = "true" |  Não  | Informações de associação sobre o grupo. |
| OrgAppPermission      | Edm.String Term="Microsoft.Office.Audit.Schema.PIIFlag" Bool="true"                            |  Não  | Lista de permissões de um aplicativo organizacional (toda a organização, usuários específicos ou grupos específicos). |
| NomeDoRelatório            | Edm.String Term="Microsoft.Office.Audit.Schema.PIIFlag" Bool="true"                            |  Não  | O nome do relatório em que o evento ocorreu. |
| SharingInformation    | Conjunto ([SharingInformationType](#sharinginformationtype-complex-type)) Term="Microsoft.Office.Audit.Schema.PIIFlag" booleano = "true"    |  Não  | Informações sobre a pessoa para quem é enviado um convite de compartilhamento. |
| SwitchState           | Edm.String Term="Microsoft.Office.Audit.Schema.PIIFlag" Bool="true"                            |  Não  | Informações sobre o estado das várias opções de nível do locatário. |
| WorkSpaceName         | Edm.String Term="Microsoft.Office.Audit.Schema.PIIFlag" Bool="true"                            |  Não  | O nome do espaço de trabalho em que o evento ocorreu. |

### <a name="membershipinformationtype-complex-type"></a>Tipo de complexo MembershipInformationType

|**Parameters**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
| MemberEmail | Edm.String Term="Microsoft.Office.Audit.Schema.PIIFlag" Bool="true" |  Não  | O endereço de email do grupo. |
| Status      | Edm.String Term="Microsoft.Office.Audit.Schema.PIIFlag" Bool="true" |  Não  | Não está preenchido no momento. |

### <a name="sharinginformationtype-complex-type"></a>SharingInformationType tipo complexo

|**Parameters**|**Tipo**|**Obrigatório?**|**Descrição**|
|:-----|:-----|:-----|:-----|
| RecipientEmail    | Edm.String Term="Microsoft.Office.Audit.Schema.PIIFlag" Bool="true" |  Não  | O endereço de email do destinatário de um convite de compartilhamento. |
| RecipientName    | Edm.String Term="Microsoft.Office.Audit.Schema.PIIFlag" Bool="true" |  Não  | O nome do destinatário de um convite de compartilhamento. |
| ResharePermission | Edm.String Term="Microsoft.Office.Audit.Schema.PIIFlag" Bool="true" |  Não  | A permissão sendo concedida ao destinatário. |

## <a name="workplace-analytics-schema"></a>Esquema do Workplace Analytics

Os eventos do WorkPlace Analytics listados em [Pesquisar o log de auditoria no Centro de Conformidade e Segurança do Office 365](https://docs.microsoft.com/office365/securitycompliance/search-the-audit-log-in-security-and-compliance#microsoft-workplace-analytics-activities) usarão este esquema.

| **Parâmetros**     | **Tipo**            | **Obrigatório?** | **Descrição**|
|:------------------ | :------------------ | :--------------|:--------------|
| WpaUserRole        | Edm.String | Não     | A função do Workplace Analytics do usuário que executou a ação.                                                                                            |
| ModifiedProperties | Coleção (Common.ModifiedProperty) | Não | Essa propriedade inclui o nome da propriedade que foi modificada, o novo valor da propriedade modificada e o valor anterior da propriedade modificada.|
| OperationDetails   | Coleção (Common.NameValuePair)    | Não | Uma lista de propriedades estendidas para a configuração que foi alterada. Cada propriedade terá um **Nome** e **Valor**.|
||||
