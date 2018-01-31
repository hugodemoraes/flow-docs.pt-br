---
title: Criar um conector personalizado para uma API Web | Microsoft Docs
description: "Saiba como criar uma API Web do ASP.NET com a autenticação do Azure Active Directory no Microsoft Flow."
services: 
suite: flow
documentationcenter: 
author: sunaysv
manager: anneta
editor: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/06/2016
ms.author: sunayv
ms.openlocfilehash: fef904b02d4b0f028edba236b73e19155b6f4919
ms.sourcegitcommit: f3236f9f1ec050cda0d9c3e2b9c356132b2a2594
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
---
# <a name="build-a-custom-connector-for-a-web-api-in-microsoft-flow"></a>Criar um conector personalizado para uma API Web no Microsoft Flow
Este tutorial mostra como começar a criar uma API Web do ASP.NET, hospedá-la nos Aplicativos Web do Azure, habilitar a autenticação do Azure Active Directory e registrar a API Web do ASP.NET no Microsoft Flow. Depois da API ser registrada, você pode conectá-la e chamá-la a partir de seu fluxo. 

## <a name="prerequisites"></a>Pré-requisitos
* Uma [assinatura do Azure](https://azure.microsoft.com/free/).
* Uma [conta do PowerApps](https://powerapps.microsoft.com).
* [Visual Studio](https://www.visualstudio.com/vs/) 2013 ou superior.

## <a name="create-an-aspnet-web-api-and-deploy-it-to-azure"></a>Criar uma API Web do ASP.NET e implantá-lo no Azure
1. No Visual Studio, clique em **Arquivo** > **Novo Projeto** para criar um novo aplicativo Web C# ASP.NET.
   
    ![Novo aplicativo Web](./media/customapi-web-api-tutorial/newwebapp.png)
2. Selecione o modelo **API Web**.  Deixe a opção **Host na nuvem** marcada.  Clique em **Alterar Autenticação**.
   
    ![Novo modelo de projeto da Web](./media/customapi-web-api-tutorial/new-web-api.png)
3. Selecione **Sem Autenticação** e clique em **OK**.
   
    ![Sem Autenticação](./media/customapi-web-api-tutorial/noauth.png)
4. Clique em **OK** na caixa de diálogo **Novo projeto do ASP.NET**.  A caixa de diálogo Configurar Aplicativo Web do Microsoft Azure é mostrada.
   
    ![Configurar aplicativo Web do Microsoft Azure](./media/customapi-web-api-tutorial/azure-publishing.png)]
   
    Selecione sua conta do Azure, digite um **Nome de aplicativo Web** (ou mantenha o padrão) e selecione a **assinatura** do Azure.  Selecione ou crie um **Plano do Serviço de Aplicativo** (uma coleção de aplicativos Web em sua assinatura).  Selecione ou crie um **Grupo de recursos** (um agrupamento de recursos do Azure em sua assinatura).  Selecione a região em que o aplicativo Web deve ser implantado.  Se for necessário para a API Web, selecione ou crie um **servidor de banco de dados** do Azure.  Por fim, clique em **OK**.
5. Crie a API Web.
   
   > [!NOTE]
   > Se você ainda não tiver o código pronto para uma API Web, experimente o tutorial [Introdução à API Web 2 do ASP.NET (C#)](https://www.asp.net/web-api/overview/getting-started-with-aspnet-web-api/tutorial-your-first-web-api).
   > 
   > 
6. Para conectar a API Web ao PowerApps, é necessário um arquivo do [Swagger](http://swagger.io/) que descreve suas operações.  Você poderia escrever seu próprio OpenAPI usando o [editor online](http://editor.swagger.io/), mas, para este tutorial, usará uma ferramenta de fonte aberta denominada [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle/blob/master/README.md).  Instale o pacote do Swashbuckle Nuget em seu projeto do Visual Studio clicando em **Ferramentas** > **NuGet Package Manager** > **Package Manager Console** e, em seguida, no Package Manager Console. Depois, digite o comando `Install-Package Swashbuckle`.
   
    ![Install-Package Swashbuckle](./media/customapi-web-api-tutorial/swashbuckle-console.png)
   
   > [!TIP]
   > Quando você executar seu aplicativo API Web depois de instalar o Swashbuckle, um arquivo do OpenAPI será gerado na URL `http://<your root URL>/swagger/docs/v1`.  Uma interface do usuário gerada também está disponível em `http://<your root URL>/swagger`.
   > 
   > 
7. Quando a API Web estiver pronta, publique-a no Azure. Para publicar no Visual Studio, clique com o botão direito do mouse no projeto Web no Gerenciador de Soluções, clique em **Publicar...** e siga as instruções na caixa de diálogo Publicar.
8. Recupere o JSON do OpenAPI navegando para `https://<azure-webapp-url>/swagger/docs/v1`.  Salve o conteúdo como um arquivo JSON.  Dependendo do navegador, você precisará copiar e colar o texto em um arquivo de texto vazio.   
   
   > [!IMPORTANT]
   > Um documento do OpenAPI com IDs de operação duplicadas é inválido. Se você está usando o modelo de exemplo de C#, a ID da operação `Values_Get` é repetida duas vezes. Você pode corrigir isso alterando uma instância para `Value_Get` e publicando novamente.
   > 
   > Você também pode baixar um [OpenAPI de exemplo](https://pwrappssamples.blob.core.windows.net/samples/webAPI.json) neste tutorial. Remova os comentários (começando com `//`) antes de usá-lo.
   > 
   > 

## <a name="set-up-azure-active-directory-authentication"></a>Configurar a autenticação do Azure Active Directory
Agora, você criará dois aplicativos do Azure Active Directory (AAD) no Azure.  Para obter um exemplo de como fazer isso, consulte o [tutorial do Azure Resource Manager](customapi-azure-resource-manager-tutorial.md#enable-authentication-in-azure-active-directory).

> [!IMPORTANT]
> Ambos os aplicativos devem estar no mesmo diretório.
> 
> 

### <a name="first-aad-application-securing-the-web-api"></a>Primeiro aplicativo do AAD: proteger a API Web
O primeiro aplicativo do AAD é usado para proteger a API Web. Nomeie-o como **webAPI**.  Siga as etapas do tutorial vinculadas acima (apenas a seção intitulada “Habilitar a autenticação no Azure Active Directory”) com os seguintes valores:

* URL de entrada: `https://login.windows.net`
* URL de resposta: `https://<your-root-url>/.auth/login/aad/callback`
* Não é necessária uma chave de cliente.
* Não é necessário delegar permissões.
* **Importante!** Anote a ID do aplicativo.  Você precisará dele mais tarde.

### <a name="second-aad-application-securing-the-custom-connector-and-delegated-access"></a>Segundo aplicativo do AAD: protegendo o conector personalizado e o acesso delegado
O segundo aplicativo do AAD é usado para proteger o registro do conector personalizado e adquirir o acesso delegado à API Web protegida pelo primeiro aplicativo. Nomeie-o como **webAPI customAPI** .

* URL de entrada: `https://login.windows.net`
* URL de resposta: `https://msmanaged-na.consent.azure-apim.net/redirect`
* Adicione permissões para ter acesso delegado à API Web.
* Você precisará da ID do aplicativo mais tarde, por isso, anote-a.
* Gere uma chave de cliente e armazene-a em local seguro. Precisaremos dessa chave mais tarde.

## <a name="add-authentication-to-your-azure-web-app"></a>Adicionar autenticação ao aplicativo Web do Azure
1. Entre no [portal do Azure](https://portal.azure.com) e localize seu aplicativo Web implantado na primeira seção.
2. Clique em **Configurações** e selecione **Autenticação/Autorização**.
3. Ative a **Autenticação do Serviço de Aplicativo** e selecione **Azure Active Directory**.  Na próxima folha, selecione **Express**.  
4. Clique em **Selecionar Aplicativo Existente do AD** e selecione o aplicativo **webAPI** do AAD que você criou anteriormente.

Agora, você poderá usar o AAD para autenticar seu aplicativo Web.

## <a name="add-the-custom-connector-to-microsoft-flow"></a>Adicionar o conector personalizado ao Microsoft Flow
1. Modifique o OpenAPI para adicionar o objeto `securityDefintions` e a autenticação do AAD usada para o Aplicativo Web. A seção de seu OpenAPI com a propriedade **host** deve ter esta aparência:

```javascript
// File header should be above here...

"host": "<your-root-url>",
"schemes": [
    "https"         //Make sure this is https!
],
"securityDefinitions": {
    "AAD": {
        "type": "oauth2",
        "flow": "accessCode",
        "authorizationUrl": "https://login.windows.net/common/oauth2/authorize",
        "tokenUrl" : "https://login.windows.net/common/oauth2/token",
        "scopes": {}
    }
},

// The rest of the OpenAPI follows...
```

1. Navegue até o [Microsoft Flow](https://flow.powerapps.com) e adicione um conector personalizado, conforme descrito em [Registrar e usar conectores personalizados no Microsoft Flow](register-custom-api.md).
2. Depois que você carregar o OpenAPI, o assistente detectará automaticamente que você está usando a autenticação do AAD para a API Web.
3. Configure a autenticação do AAD para o conector personalizado.  
   
   * **ID do cliente**: *ID do cliente de webAPI-CustomAPI*
   * **Segredo**: *chave do cliente de webAPI-CustomAPI*
   * **URL de logon**: `https://login.windows.net`
   * **ResourceUri**: *ID de cliente da API Web*
4. Clique em **Criar** e crie uma conexão com o conector personalizado.

## <a name="next-steps"></a>Próximas etapas
Percorra o [tutorial do conector personalizado do Azure Resource Manager](customapi-azure-resource-manager-tutorial.md).

