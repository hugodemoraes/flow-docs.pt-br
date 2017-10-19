---
title: Usar o Azure Active Directory com um conector personalizado | Microsoft Docs
description: "Saiba como criar um conector personalizado para o Azure Resource Manager com a autenticação do Azure Active Directory."
services: 
suite: flow
documentationcenter: 
author: msftman
manager: anneta
editor: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/03/2016
ms.author: deonhe
ms.openlocfilehash: d98a3505ab7d667f5a64eed9a23041efec95b1d7
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="use-azure-active-directory-with-a-custom-connector-in-microsoft-flow"></a>Usar o Azure Active Directory com um conector na Microsoft | Microsoft Flow
O Azure Resource Manager (ARM) permite gerenciar os componentes de uma solução no Azure - componentes como bancos de dados, máquinas virtuais e aplicativos Web. Este tutorial demonstra como habilitar a autenticação no Azure Active Directory, registrar uma das APIs do ARM como um conector personalizado, em seguida, conectar no Microsoft Flow. Isso poderá ser útil se você quiser gerenciar os recursos do Azure como parte de um fluxo. Para obter mais informações sobre o ARM, consulte a [Visão Geral do Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).

## <a name="prerequisites"></a>Pré-requisitos
* Uma [assinatura do Azure](https://azure.microsoft.com/free/).
* Uma [conta do Microsoft Flow](https://flow.microsoft.com).
* O [arquivo de exemplo do OpenAPI](http://pwrappssamples.blob.core.windows.net/samples/AzureResourceManager.json) usado neste tutorial.

## <a name="enable-authentication-in-azure-active-directory"></a>Habilitar a autenticação no Azure Active Directory
Primeiro, precisamos criar um aplicativo do AAD (Azure Active Directory) que executará a autenticação ao chamar o ponto de extremidade de API ARM.

1. Entre no [portal do Azure](https://portal.azure.com).  Se você tiver mais de um locatário do Azure Active Directory, verifique se está conectado ao diretório correto examinando seu nome de usuário no canto superior direito.
   
    ![Nome de Usuário](./media/customapi-azure-resource-manager-tutorial/current-user.png)
2. No menu à esquerda, clique em **Mais serviços**.  Na caixa de texto **Filtrar**, digite **Azure Active Directory** e clique em **Azure Active Directory**.
   
    ![Azure Active Directory](./media/customapi-azure-resource-manager-tutorial/azureaad.png)
   
    A folha Azure Active Directory é aberta.   
3. No menu na folha do Azure Active Directory, clique em **Registros de aplicativo**.
   
    ![Registros de aplicativo](./media/customapi-azure-resource-manager-tutorial/azureapplication.png)
4. Na lista de aplicativos registrados, clique em **Adicionar**.
   
    ![Botão Adicionar](./media/customapi-azure-resource-manager-tutorial/add-app-btn.png)   
5. Digite um nome para o aplicativo, deixe **Aplicativo Web/API** selecionado e, para **URL de logon**, digite `https://login.windows.net`.  Clique em **Criar**.  
   
    ![Novo formulário de aplicativo](./media/customapi-azure-resource-manager-tutorial/newapplication.png)
6. Clique no novo aplicativo na lista.
   
    ![Novo aplicativo na lista](./media/customapi-azure-resource-manager-tutorial/newapplication2.png)
   
    A folha Aplicativo registrado é aberta.  Anote a **ID do aplicativo**.  Precisaremos dela posteriormente.
7. A folha Configurações também deve ter sido aberta.  Caso contrário, clique no botão **Configurações**.
   
    ![Botão Configurações](./media/customapi-azure-resource-manager-tutorial/settings-btn.png)
8. Na folha Configurações, clique em **URLs de resposta**. Na lista de URLs, adicione `https://msmanaged-na.consent.azure-apim.net/redirect` e clique em **Salvar**.
   
    ![URLs de resposta](./media/customapi-azure-resource-manager-tutorial/reply-urls.png)
9. De volta à folha Configurações, clique em **Permissões necessárias**.  Na folha Permissões necessárias, clique em **Adicionar**.
   
    ![Permissões necessárias](./media/customapi-azure-resource-manager-tutorial/permissions.png)
   
    A folha adicionar acesso de API é aberta.
10. Clique em **Selecionar uma API**. Na folha que é aberta, clique na opção para a API de Gerenciamento de Serviços do Azure e clique em **Selecionar**.
    
    ![Selecionar uma API](./media/customapi-azure-resource-manager-tutorial/permissions2.png)
11. Clique em **Selecionar permissões**.  Em *permissões delegadas*, clique em **Acessar o Gerenciamento de Serviço do Azure como usuários da organização** e clique em **Selecionar**.
    
    ![Permissões delegadas](./media/customapi-azure-resource-manager-tutorial/permissions3.png)
12. Na folha Adicionar acesso de API, clique em **Concluído**.
13. De volta à folha Configurações, clique em **Chaves**.  Na folha Chaves, digite uma descrição para a chave, selecione um período de expiração e clique em **Salvar**.  Sua nova chave será exibida.  Anote o valor da chave, pois ele também será necessário mais tarde.  Agora você pode fechar o portal do Azure.
    
    ![Criar uma chave](./media/customapi-azure-resource-manager-tutorial/configurekeys.png)

## <a name="add-the-connection-in-microsoft-flow"></a>Adicionar a conexão no Microsoft Flow
Agora que o aplicativo do AAD está configurado, adicionaremos o conector personalizado.

1. No [aplicativo Web do Microsoft Flow](https://flow.microsoft.com/), clique no botão **Configurações** no canto superior direito da página (ele se parece com uma engrenagem).  Em seguida, clique em **conectores personalizados**.
   
    ![Localizar conectores personalizados](./media/customapi-azure-resource-manager-tutorial/finding-custom-apis.png)  
2. Clique em **Criar conector personalizado**.  
   
    Você será solicitado a fornecer as propriedades da API.  
   
   | Propriedade | Descrição |
   | --- | --- |
   | Nome |Na parte superior da página, clique em **Sem título** e dê um nome ao fluxo. |
   | Arquivo do OpenAPI |Navegue até o [arquivo ARM do OpenAPI de exemplo](http://pwrappssamples.blob.core.windows.net/samples/AzureResourceManager.json). |
   | Carregar ícone de API |Clique em **Carregar ícone** para selecionar um arquivo de imagem para o ícone. Nenhuma imagem PNG ou JPG com tamanho inferior a 1 MB funcionará. |
   | Descrição |Digite uma descrição para o conector personalizado (opcional). |
   
    ![Criar um conector personalizado](./media/customapi-azure-resource-manager-tutorial/create-custom-api.png)  
   
    Selecione **Continuar**.
3. Na próxima tela, como o arquivo do OpenAPI usa o aplicativo do AAD para a autenticação, precisamos fornecer ao Flow algumas informações sobre o aplicativo.  Em **id do cliente**, digite a **ID do aplicativo** do AAD que você anotou anteriormente.  Para o segredo do cliente, use a **chave**.  E, finalmente, para **URL de recurso**, digite `https://management.core.windows.net/`.
   
   > [!IMPORTANT]
   > Inclua a URL de Recurso exatamente conforme descrito acima, incluindo a barra à direita.
   > 
   > 
   
    ![Configurações de OAuth](./media/customapi-azure-resource-manager-tutorial/oauth-settings.png)
   
    Depois de inserir as informações de segurança, clique na marca de seleção (**&#x2713;**) ao lado do nome do fluxo na parte superior da página para criar o conector personalizado.
4. Agora, o conector personalizado é exibido em **conectores personalizados**.
   
    ![APIs disponíveis](./media/customapi-azure-resource-manager-tutorial/list-custom-apis.png)  
5. Agora que o conector personalizado foi registrado, você deve criar uma conexão com o ele para que possa ser usado nos aplicativos e fluxos.  Clique em **+** à direita do nome do conector personalizado e conclua a tela de logon.

> [!NOTE]
> O OpenAPI de exemplo não define o conjunto completo de operações ARM e, atualmente, contém apenas a operação [Listar todas as assinaturas](https://msdn.microsoft.com/library/azure/dn790531.aspx).  Você pode editar esse OpenAPI ou criar outro arquivo do OpenAPI usando o [editor OpenAPI online](http://editor.swagger.io/).
> 
> Esse processo pode ser usado para acessar qualquer API RESTful autenticada usando o AAD.
> 
> 

## <a name="next-steps"></a>Próximas etapas
Para obter informações mais detalhadas sobre como criar um fluxo, confira [Começar a criar com o Microsoft Flow](get-started-logic-flow.md).

Para fazer perguntas ou comentários sobre os conectores personalizados, [participe de nossa comunidade](https://aka.ms/flow-community).

