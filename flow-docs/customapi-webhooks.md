---
title: Usar webhooks com o Microsoft Flow| Microsoft Docs
description: Aprenda a criar fluxos que interagem com webhooks no Microsoft Flow
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
ms.date: 05/08/2017
ms.author: deonhe
ms.openlocfilehash: d36b8671f737ebd1685c260beaa5ebab4e123e9f
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="use-webhooks-with-microsoft-flow"></a>Usar webhooks com o Microsoft Flow
[Webhooks](http://www.webhooks.org/) são simples retornos de chamada de HTTP usados para fornecer notificações de eventos.  O Microsoft Flow permite usar webhooks para disparar fluxos.  Este tutorial mostra como criar um fluxo disparado por um webhook.

> [!NOTE]
> Usaremos o GitHub como exemplo de um serviço que pode enviar notificações via webhooks. No entanto, as técnicas demonstradas aqui podem ser estendidas para qualquer serviço que utilizar webhooks.
> 
> 

## <a name="prerequisites"></a>Pré-requisitos
Para concluir o tutorial, você precisará de:

* Noções básicas sobre [webhooks](http://www.webhooks.org/).
* Noções básicas sobre a [Especificação OpenAPI](http://swagger.io/specification/) (Swagger).
* Uma conta do [GitHub](https://www.github.com).
* O [arquivo de exemplo JSON do OpenAPI](http://pwrappssamples.blob.core.windows.net/samples/githubWebhookSample.json) deste tutorial.
* Como alternativa, você também pode usar a [IU dos gatilhos](customapi-webhooks.md#creating-webhook-triggers-from-the-ui) para definir os gatilhos do webhook, caso não queira gravar manualmente o arquivo do OpenAPI.

## <a name="the-openapi-file"></a>Arquivo do OpenAPI
Os webhooks são implementados no Microsoft Flow como um tipo de [conector personalizado](register-custom-api.md), portanto, precisaremos fornecer um arquivo JSON do OpenAPI para definir a forma de nosso webhook.  O OpenAPI contém três definições essenciais para fazer webhook funcionar:

1. Criar o webhook
2. Definir a solicitação de entrada do webhook a partir da API (nesse caso, o GitHub)
3. Excluir o webhook

### <a name="creating-the-webhook"></a>Criar o webhook
O webhook é criado no lado do GitHub por um HTTP POST para `/repos/{owner}/{repo}/hooks`.  O Microsoft Flow precisará postar nessa URL quando um novo fluxo for criado usando o gatilho definido no OpenAPI ou sempre que o gatilho for modificado.  No exemplo abaixo, a propriedade `post` contém o esquema da solicitação que será postado no GitHub.

```json
"/repos/{owner}/{repo}/hooks": {
    "x-ms-notification-content": {
    "description": "Details for Webhook",
    "schema": {
        "$ref": "#/definitions/WebhookPushResponse"
    }
    },
    "post": {
    "description": "Creates a Github webhook",
    "summary": "Triggers when a PUSH event occurs",
    "operationId": "webhook-trigger",
    "x-ms-trigger": "single",
    "parameters": [
        {
        "name": "owner",
        "in": "path",
        "description": "Name of the owner of targetted repository",
        "required": true,
        "type": "string"
        },
        {
        "name": "repo",
        "in": "path",
        "description": "Name of the repository",
        "required": true,
        "type": "string"
        },
        {
        "name": "Request body of webhook",
        "in": "body",
        "description": "This is the request body of the Webhook",
        "schema": {
            "$ref": "#/definitions/WebhookRequestBody"
        }
        }
    ],
    "responses": {
        "201": {
        "description": "Created",
        "schema": {
            "$ref": "#/definitions/WebhookCreationResponse"
        }
        }
    }
    }
},
```

> [!IMPORTANT]
> A propriedade `"x-ms-trigger": "single"` é uma extensão do esquema que informa ao Microsoft Flow para exibir esse webhook na lista de gatilhos disponíveis no designer do fluxo, portanto, inclua-a.
> 
> 

### <a name="defining-the-incoming-hook-request-from-the-api"></a>Definir a solicitação de entrada do webhook a partir da API
A forma da solicitação de entrada do webhook (a notificação do GitHub para o Microsoft Flow) é definida na propriedade `x-ms-notification-content` personalizada, conforme mostrado no exemplo acima.  Ela não precisa conter todo o conteúdo da solicitação, apenas as partes que você deseja usar em seus fluxos.

### <a name="deleting-the-webhook"></a>Excluir o webhook
É muito importante incluir uma definição no OpenAPI que informa ao Microsoft Flow como excluir o webhook.  O Microsoft Flow tentará excluir o webhook sempre que você atualizar o gatilho no fluxo ou quando excluir seu fluxo.

```json
"/repos/{owner}/{repo}/hooks/{hook_Id}": {
    "delete": {
    "description": "Deletes a Github webhook",
    "operationId": "DeleteTrigger",
    "parameters": [
        {
        "name": "owner",
        "in": "path",
        "description": "Name of the owner of targetted repository",
        "required": true,
        "type": "string"
        },
        {
        "name": "repo",
        "in": "path",
        "description": "Name of the repository",
        "required": true,
        "type": "string"
        },
        {
        "name": "hook_Id",
        "in": "path",
        "description": "ID of the Hook being deleted",
        "required": true,
        "type": "string"
        }
    ]
    }
},
```

> [!IMPORTANT]
> Para que o Microsoft Flow consiga excluir um webhook, a API **deve** incluir um cabeçalho HTTP `Location` na resposta 201 no momento em que o webhook é criado.  O cabeçalho `Location` deve conter o caminho para o webhook que será usado com o HTTP DELETE.  Por exemplo, o `Location` incluído com a resposta do GitHub segue este formato: `https://api.github.com/repos/<user name>/<repo name>/hooks/<hook ID>`.
> 
> 

## <a name="authentication"></a>Autenticação
A API que envia a solicitação do webhook para o Microsoft Flow geralmente terá alguma forma de autenticação e o GitHub não é uma exceção.  Há suporte para vários tipos de autenticação.  Neste tutorial, vamos usar tokens de acesso pessoal do GitHub.

1. Navegue até [GitHub](https://www.github.com) e entre, se ainda não o tiver feito.
2. No canto superior direito, clique em sua **imagem do perfil** e, em seguida, no menu, clique em **Configurações**.
   
    ![Configurações](./media/customapi-webhooks/github-settings.png)
3. No menu à esquerda, em **Configurações do desenvolvedor**, clique em **Tokens de acesso pessoal**.
   
    ![Tokens de acesso pessoal](./media/customapi-webhooks/personal-access-tokens.png)
4. Clique no botão **Gerar novo token**.
   
    ![Gerar novo token](./media/customapi-webhooks/generate-new-token.png)
5. Na caixa **Descrição do token**, digite uma descrição.
6. Marque a caixa de seleção **admin:repo_hook**.
   
    ![admin:repo_hook](./media/customapi-webhooks/repo-hook.png)
7. Clique no botão **Gerar token**.
8. Anote o novo token.
   
    ![Novo token](./media/customapi-webhooks/new-token.png)
   
   > [!IMPORTANT]
   > Você não conseguirá acessar esse token novamente. Você deve copiá-lo e colá-lo em algum lugar, como o Bloco de Notas, para usar posteriormente no tutorial.
   > 
   > 

## <a name="adding-the-webhook-to-microsoft-flow"></a>Adicionando o webhook ao Microsoft Flow
Agora, temos tudo o que precisamos para adicionar o webhook ao Microsoft Flow como um conector personalizado.

1. Navegue até o [Portal da Web do Microsoft Flow](https://flow.microsoft.com) e entre, se ainda não o tiver feito.
2. Clique no ícone de **configurações** e depois em **Conectores Personalizados**.
   
    ![conectores personalizados](./media/customapi-webhooks/custom-apis.png)
3. Clique no botão **Criar conector personalizado**.
4. Clique no ícone da pasta de arquivo na caixa **Importar OpenAPI**, em seguida, selecione o arquivo de exemplo do OpenAPI.
5. Clique em **Carregar ícone** na seção **Informações gerais** e, em seguida, escolha um arquivo de imagem para usar como ícone.
6. Clique em **Continuar**.
   
    ![Importar OpenAPI](./media/customapi-webhooks/import-swagger.png)
7. Na tela seguinte, definiremos as configurações de segurança.  Em **Tipo de autenticação**, escolha **Autenticação básica**.
8. Na seção **Autenticação básica**, nos campos de rótulo, insira o texto **Nome de usuário** e **Senha**.  Observe que esses são apenas os rótulos que serão exibidos quando o gatilho for usado em um fluxo.
   
    ![Autenticação básica](./media/customapi-webhooks/basic-auth.png)
9. Na parte superior da página, dê um nome ao fluxo e clique em **Criar conector**.
   
    ![Criar API](./media/customapi-webhooks/create-api.png)

O novo conector personalizado agora deverá aparecer na lista na página dos conectores personalizados.

## <a name="creating-webhook-triggers-from-the-ui"></a>Criando gatilhos de webhook a partir da IU
1. Depois de carregar/criar o arquivo do OpenAPI da linha de base, navegue até a guia **Definição** do assistente de conector personalizado.
2. No painel esquerdo, clique em **+ Novo gatilho**e preencha a descrição do seu gatilho. Neste exemplo, estamos criando um gatilho que é acionado quando uma solicitação por pull é feita em um repositório.
   
    ![Criar Gatilho-1](./media/customapi-webhooks/create-new-trigger-1.png)
3. Em seguida, defina a solicitação para criar o gatilho do webhook. Você pode fazer isso importando uma solicitação de amostra para *criar um gatilho do webhook*. Consulte a [referência da API do Github](https://developer.github.com/v3/repos/hooks/#create-a-hook) para criar um webhook. 
4. O Microsoft Flow adiciona automaticamente o ```content-type``` padrão e os cabeçalhos de segurança para que não seja necessário definir isso durante a importação de uma amostra. 
   
    ![Criar Gatilho-2](./media/customapi-webhooks/create-new-trigger-2.png)
5. Depois de importar a solicitação para criar o webhook, em seguida, definiremos a resposta do webhook importando a partir de uma resposta de exemplo. Consulte a [referência da API do Github](https://developer.github.com/v3/activity/events/types/#pullrequestevent) para obter um evento de solicitação por pull. 
   
    **Observação**: não é necessário colar a resposta completa. Somente os campos necessários devem ser definidos.
   Para este exemplo, estamos extraindo apenas a url da PR e as informações do usuário que fez a PR.
   
    ![Criar Gatilho-3](./media/customapi-webhooks/create-new-trigger-3.png)
6. A etapa final é selecionar um parâmetro na solicitação para criar o webhook, no valor de qual Microsoft Flow deve preencher uma URL de retorno de chamada para o Github preencher. Para nós, essa é a propriedade da url no objeto ```config```.
   
    ![Criar Gatilho-4](./media/customapi-webhooks/create-new-trigger-4.png)

## <a name="using-the-webhook-as-a-trigger"></a>Usar o webhook como um gatilho
Agora que temos tudo configurado, podemos usar o webhook em um fluxo.  Criaremos um fluxo que enviará uma notificação por push para o aplicativo móvel do Microsoft Flow sempre que nosso repositório do GitHub receber um git push.

1. No [Portal da Web do Microsoft Flow](https://flow.microsoft.com), na parte superior da página, clique em **Meus fluxos**.
2. Clique em **Criar do zero**.
3. No designer do Microsoft Flow, pesquise o conector personalizado que registramos anteriormente.
   
    ![Novo gatilho](./media/customapi-webhooks/new-trigger.png)
   
    Clique no item na lista para usá-lo como um gatilho.
4. Por ser a primeira vez que usamos esse conector personalizado, precisamos conectá-lo.  Em **Nome da conexão**, insira um nome descritivo.  Em **Nome de usuário**, use seu nome de usuário do GitHub.  Em **Senha**, use o **token de acesso pessoal** criado anteriormente.
   
    ![Nova conexão](./media/customapi-webhooks/new-connection.png)
   
    Clique em **Criar**.
5. Agora, precisamos fornecer informações ao Microsoft Flow sobre o repositório que desejamos monitorar.  Você pode reconhecer os campos do objeto **WebhookRequestBody** no arquivo do OpenAPI.  Em **proprietário** e **repositório**, digite o nome do proprietário e o nome do repositório de um repositório do GitHub que você deseja monitorar.
   
    ![Informações sobre o repositório](./media/customapi-webhooks/repo-info.png)
   
   > [!IMPORTANT]
   > Neste exemplo, estou usando o repositório do [Visual Studio Code](https://code.visualstudio.com). Você deve usar um repositório para o qual sua conta tenha direitos.  A maneira mais fácil de fazer isso seria usar seu próprio repositório.
   > 
   > 
6. Clique em **+ Nova etapa** e em **Adicionar uma ação**.
7. Procure e selecione a ação **Notificação por push**.
   
    ![Notificação por push](./media/customapi-webhooks/push-notification.png)
8. Insira texto no campo **Texto**.  Observe que o objeto **WebhookPushResponse** no arquivo do OpenAPI define a lista de parâmetros que você pode usar.
   
    ![Detalhes da notificação por push](./media/customapi-webhooks/push-details.png)
9. Na parte superior da página, dê um nome ao fluxo e clique em **Criar fluxo**.
   
    ![Nome do fluxo](./media/customapi-webhooks/flow-name.png)

## <a name="verification-and-troubleshooting"></a>Verificação e solução de problemas
Para verificar se tudo está configurado corretamente, clique em **Meus fluxos** e, em seguida, clique no **ícone de informações** ao lado do novo fluxo para exibir o histórico de execução.  Você já deve ver, pelo menos, uma execução "Bem-sucedida" na criação do webhook.  Isso indica que o webhook foi criado com sucesso no lado do GitHub.  Se a execução falhar, analise os detalhes de execução para ver o motivo da falha.  Se a falha tiver ocorrido devido a uma resposta "404 Não Encontrado", é provável que sua conta do GitHub não tenha as permissões corretas para criar um webhook no repositório usado.

## <a name="summary"></a>Resumo
Se tudo estiver configurado corretamente, você agora receberá notificações por push no aplicativo móvel do Microsoft Flow sempre que ocorrer um git push no repositório do GitHub selecionado.  Usando o processo acima, você pode usar qualquer serviço compatível com webhooks como um gatilho nos fluxos.

## <a name="next-steps"></a>Próximas etapas
* [Registrar um conector personalizado](register-custom-api.md).
* [Usar uma API Web do ASP.NET](customapi-web-api-tutorial.md).
* [Registrar uma API do Azure Resource Manager](customapi-azure-resource-manager-tutorial.md).

