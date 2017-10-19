---
title: Registrar e usar conectores personalizados | Microsoft Docs
description: Registre e use os conectores personalizados no Microsoft Flow, usando o OpenAPI e Postman.
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
ms.date: 05/09/2017
ms.author: sunayv
ms.openlocfilehash: 94d46b2948f03316162e1c1d45860ae94feb897c
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="register-and-use-custom-connectors-in-microsoft-flow"></a>Registrar e usar conectores personalizados no Microsoft Flow
O Microsoft Flow permite que você crie fluxos de trabalho sem código. Mas, em alguns casos, você precisa estender os recursos do Microsoft Flow e os serviços da Web são naturalmente adequados para isso. Seu fluxo pode conectar um serviço, executar operações e obter dados. Quando você tiver um serviço Web que deseja conectar com o Microsoft Flow, registre o serviço como um conector personalizado. Esse processo permite que o Microsoft Flow entenda as características de sua API Web, incluindo a autenticação necessária, as operações suportadas e os parâmetros e saídas para cada uma dessas operações.

Neste tópico, veremos as etapas necessárias para registrar e usar um conector personalizado, e usaremos a [API de Análise de Texto](https://www.microsoft.com/cognitive-services/text-analytics-api) dos Serviços Cognitivos do Azure. Essa API identifica a linguagem, sentimento e frases-chave no texto que você passa para ela.

## <a name="prerequisites"></a>Pré-requisitos
* Uma [conta do Microsoft Flow](https://flow.microsoft.com).
* Um arquivo do OpenAPI 2.0 (antes conhecido como Swagger) no formato JSON, uma URL para uma definição do OpenAPI ou uma Coleção Postman para sua API. Se você não tiver nenhum, forneceremos orientações.
* Uma imagem para usar como um ícone para o conector personalizado (opcional).

## <a name="steps-in-the-custom-connector-process"></a>Etapas do processo do conector personalizado
O processo do conector personalizado tem várias etapas, que descrevemos resumidamente abaixo. Este artigo pressupõe que você já tem uma API RESTful com algum tipo de acesso autenticado, portanto, focaremos nas etapas 3 a 6 no restante do artigo. Para obter um exemplo das etapas 1 e 2, consulte [Criar uma API Web personalizada para o Microsoft Flow](customapi-web-api-tutorial.md).

1. **Criar uma API RESTful** na linguagem e plataforma de sua escolha. Para as tecnologias da Microsoft, recomendamos um dos seguintes (mas você pode usar qualquer plataforma):
   
   * Azure Functions
   * Aplicativos Web do Azure
   * Aplicativos de API do Azure
2. **Proteja sua API** usando um dos seguintes mecanismos de autenticação. Você pode permitir o acesso não autenticado a seus conectores, mas não é recomendável.
   
   * Azure Active Directory. Para obter mais informações, consulte [Usar o Azure Active Directory com um conector personalizado no Microsoft Flow](customapi-azure-resource-manager-tutorial.md).
   * OAuth 2.0 para serviços específicos, como o Dropbox, Facebook e SalesForce
   * OAuth 2.0. Genérico
   * Chave de API
   * Autenticação Básica
3. **Descreva sua API** em uma das duas maneiras padrão da indústria para que o Microsoft Flow possa conectá-la.
   
   * Um arquivo do OpenAPI
   * Uma Coleção Postman
     
     Você também pode criar um arquivo do OpenAPI na etapa 4 como parte do processo de registro.
4. **Registre seu conector personalizado** usando um assistente no Microsoft Flow, no qual você especifica uma descrição da API, os detalhes de segurança e outras informações.
5. **Use o conector personalizado** em um aplicativo. Crie uma conexão com o conector em seu aplicativo e chame todas as operações que a API fornece, assim como você chama as conexões padrão no Microsoft Flow.
6. **Compartilhe seu conector personalizado** como faz com os outros recursos no Microsoft Flow. Esta etapa é opcional, mas geralmente faz sentido compartilhar os conectores personalizados entre vários criadores de aplicativo.

## <a name="describe-your-api"></a>Descrever sua API
Supondo que você tenha uma API com algum tipo de acesso autenticado, precisará de uma maneira de descrever a API para que o Microsoft Flow possa conectá-la. Para fazer isso, você cria um arquivo do OpenAPI ou uma Coleção Postman – o que pode ser feito de *qualquer* ponto de extremidade de API REST, incluindo:

* Conectores disponíveis publicamente. Alguns exemplos incluem [Spotify](https://developer.spotify.com/), [Uber](https://developer.uber.com/), [Slack](https://api.slack.com/), [Rackspace](http://docs.rackspace.com/) e muito mais.
* Uma API que você cria e implanta em qualquer provedor de hospedagem de nuvem, incluindo o AWS (Amazon Web Services), Heroku, Google Cloud e muito mais.
* Uma API de linha de negócios personalizada implantada em sua rede, contanto que a API seja exposta na Internet pública.

O OpenAPI 2.0 (anteriormente conhecido como Swagger) e as Coleções Postman usam formatos diferentes, mas ambos são documentos legíveis por máquina independentes da linguagem que descrevem as operações e os parâmetros da API:

* Você pode gerar esses documentos usando várias ferramentas, dependendo da linguagem e da plataforma que baseiam sua API. Consulte a [documentação da API de Análise de Texto](https://westus.dev.cognitive.microsoft.com/docs/services/TextAnalytics.V2.0/export?DocumentFormat=Swagger&ApiName=Azure) para obter um exemplo de um arquivo do OpenAPI.
* Se você ainda não tiver um arquivo do OpenAPI para sua API e não quiser criar um, poderá criar facilmente um conector personalizado usando uma Coleção Postman. Consulte [Criar uma Coleção Postman](postman-collection.md) para obter mais informações.
* O Microsoft Flow usa o OpenAPI internamente, portanto, uma Coleção Postman é analisada e convertida em um arquivo de definição do OpenAPI.

**Observação**: o tamanho do arquivo deve ser menor que 1 MB.

### <a name="getting-started-with-openapi-and-postman"></a>Introdução ao OpenAPI e Postman
* Se você for novo no OpenAPI, consulte [Introdução ao OpenAPI](http://swagger.io/getting-started/) no site swagger.io.
* Se for novo no Postman, instale o [aplicativo Postman](https://www.getpostman.com/apps) a partir de seu site.
* Se a API for criada com os Aplicativos de API do Azure ou as Azure Functions, consulte [Exportando uma API hospedada pelo Azure para o Microsoft Flow e Microsoft Flow](https://docs.microsoft.com/azure/app-service/app-service-export-api-to-powerapps-and-flow) para obter mais informações.

## <a name="register-your-custom-connector"></a>Registrar um conector personalizado
Agora, você usará o arquivo do OpenAPI ou a Coleção Postman para registrar seu conector personalizado no Microsoft Flow.

1. Em [flow.microsoft.com](https://flow.microsoft.com), na barra superior, selecione a engrenagem para abrir o menu de configurações. Selecione a opção **Conectores Personalizados**.
   
    ![Criar um conector personalizado](./media/register-custom-api/managecustomapi.png)  
2. Selecione **Criar conector personalizado**.
   
    ![Propriedades do conector personalizado](./media/register-custom-api/newcustomapi.png)
3. Na guia **Geral**, escolha como você deseja criar o conector personalizado.
   
   * Carregar OpenAPI
   * Colar URL do OpenAPI
   * Carregar uma Coleção Postman V1
     
     ![Como criar um conector personalizado](./media/register-custom-api/choosehowtocreate.png)
     
     Carregue um ícone para o conector personalizado. Os campos Descrição, Host e URL de Base, em geral, são preenchidos automaticamente com as informações do arquivo do OpenAPI. Se eles não forem preenchidos automaticamente, você poderá adicionar informações a esses campos. Selecione **Continuar**.
4. Na guia **Segurança**, insira as propriedades de autenticação.
   
    ![Tipos de autenticação](./media/register-custom-api/authenticationtypes.png)
   
   * O tipo de autenticação é preenchido automaticamente com base no que está definido no seu objeto `securityDefinitions` do OpenAPI. Abaixo está um exemplo de OAuth 2.0.
     
       ```
       "securityDefinitions": {
           "AAD": {
           "type": "oauth2",
           "flow": "accessCode",
           "authorizationUrl": "https://login.windows.net/common/oauth2/authorize",
           "tokenUrl": "https://login.windows.net/common/oauth2/token"
           "scopes": {}
           }
       },
       ```
   * Se o arquivo do OpenAPI não usar o objeto `securityDefintions`, talvez os valores adicionais não sejam necessários.
   * Ao usar uma Coleção Postman, o tipo de autenticação é preenchido automaticamente somente ao usar os tipos de autenticação com suporte, como OAuth 2.0 ou Basic.
   * Para obter um exemplo de configuração da autenticação do Azure Active Directory (AAD), consulte [Criar uma API da Web personalizada para o Microsoft Flow](customapi-web-api-tutorial.md#set-up-azure-active-directory-authentication).
5. Na guia **Definições**, todas as operações definidas em seu arquivo do OpenAPI ou Coleção Postman, juntamente com os valores de solicitação e resposta, são preenchidas automaticamente. Se todas as operações necessárias forem definidas, você poderá ir para a etapa 6 do processo de registro sem fazer alterações nessa tela.
   
    ![Guia Definição](./media/register-custom-api/definitiontab.png)
   
    Se você quiser editar as ações existentes ou adicionar novas ações ao conector personalizado, continue lendo abaixo.
   
   1. Se quiser adicionar uma nova ação que ainda não estava em seu arquivo do OpenAPI ou Coleção Postman, selecione **Nova ação** no painel esquerdo e preencha a seção **Geral** com o nome, descrição e visibilidade de sua operação.
   2. Na seção **Solicitação**, selecione **Importar do exemplo** à direita superior. No formulário à direita, cole uma solicitação de exemplo. As solicitações de exemplo estão geralmente disponíveis na documentação da API, onde você pode obter informações para preencher os campos **Verbo**, **URL de Solicitação**, **Cabeçalhos** e **Corpo**. Consulte a [documentação da API de Análise de Texto](https://westus.dev.cognitive.microsoft.com/docs/services/TextAnalytics.V2.0/operations/56f30ceeeda5650db055a3c6) para obter um exemplo.
      
      > [!IMPORTANT]
      > Não se esqueça de remover o cabeçalho `Content-type` das ações, pois ele será adicionado automaticamente pelo Microsoft Flow. Os cabeçalhos de autenticação que foram definidos na seção **Segurança** também devem ser removidos das ações e gatilhos. 
      > 
      > 
      
      ![Importar do exemplo](./media/register-custom-api/importfromsample.png)
   3. Selecione **Importar** para concluir a definição da solicitação. Defina uma resposta de maneira semelhante.
6. Assim que você tiver todas as operações definidas, selecione **Criar** para criar o conector personalizado.
7. Depois de criar o conector personalizado, vá para a guia **Testar** para testar as operações definidas na API. Escolha uma conexão e forneça os parâmetros de entrada para testar uma operação.
   
    ![Testar um conector personalizado](./media/register-custom-api/testcustomapi.png)
   
    Se a chamada for bem-sucedida, você obterá uma resposta válida.
   
    ![Testar Resposta do conector](./media/register-custom-api/testapiresponse.png)

### <a name="quota-and-throttling"></a>Cota e limitação
* Consulte a página [Preços do Microsoft Flow](https://flow.microsoft.com/pricing/) para obter detalhes sobre as cotas de criação do conector personalizado. Os conectores personalizados compartilhados com você não contam em relação a essa cota.
* Para cada conexão criada em um conector personalizado, os usuários podem fazer até 500 solicitações por minuto.

## <a name="share-your-custom-connector"></a>Compartilhar um conector personalizado
Agora que você tem um conector personalizado, poderá compartilhá-lo com outros usuários em sua organização. Lembre-se que quando você compartilha um conector personalizado, outras pessoas podem começar a depender dele e a exclusão de um conector personalizado exclui todas as conexões com o conector. Se você quiser fornecer um conector para usuários fora de sua organização, consulte [Visão geral da certificação dos conectores personalizados no Microsoft Flow](api-connector-overview.md).

1. Em [flow.microsoft.com](https://flow.microsoft.com), na barra superior, selecione a engrenagem para abrir o menu de configurações. Selecione a opção **Conectores personalizados**.
   
    ![Nova conexão](./media/register-custom-api/managecustomapi.png)
2. Selecione o botão de reticências (**...** ) para o conector, em seguida, selecione **Exibir propriedades**.  
   
    ![Exibir propriedades do conector](./media/register-custom-api/view-properties.png)
3. Selecione **Compartilhar**, em seguida, insira os usuários ou grupos aos quais você deseja conceder acesso a seu conector.  
   
    ![Compartilhar conector personalizado](./media/register-custom-api/sharecustomapi.png)
4. Selecione **Salvar**.

## <a name="next-steps"></a>Próximas etapas
[Saiba como criar uma Coleção Postman](postman-collection.md)

[Saiba mais sobre as extensões personalizadas do OpenAPI](customapi-how-to-swagger.md).

[Usar uma API Web do ASP.NET](customapi-web-api-tutorial.md).

[Registrar uma API do Azure Resource Manager](customapi-azure-resource-manager-tutorial.md).

