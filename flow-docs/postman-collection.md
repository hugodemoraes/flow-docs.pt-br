---
title: Descrever um conector personalizado com o Postman | Microsoft Docs
description: "Criar uma Coleção Postman para registrar os conectores personalizados"
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
ms.date: 04/28/2017
ms.author: sunayv
ms.openlocfilehash: fe98999ea307367c7f3b032974fef9be6ca3f388
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="describe-a-custom-connector-with-postman"></a>Descrever um conector personalizado com o Postman
[Postman](https://www.getpostman.com/) é uma ferramenta para tornar o desenvolvimento do API mais rápido e fácil. Este tutorial mostra como criar uma coleção Postman, que você pode usar para criar facilmente [conectores personalizados](register-custom-api.md) no Microsoft Flow.

## <a name="prerequisites"></a>Pré-requisitos
* Instale o [aplicativo Postman](https://www.getpostman.com/apps).

## <a name="create-a-postman-collection"></a>Criar uma Coleção Postman
Iremos criar uma Coleção Postman para a [API de Análise de Texto](https://www.microsoft.com/cognitive-services/text-analytics-api) dos Serviços Cognitivos do Azure. Essa API identifica a linguagem, sentimento e frases-chave no texto que você passa para ela.

1. A primeira etapa na criação de uma Coleção Postman é criar uma solicitação. Ao criar a solicitação, você pode definir o verbo HTTP, URL da solicitação, parâmetros da consulta ou do caminho, cabeçalhos e corpo. Para obter mais informações, consulte [Enviando Solicitações](https://www.getpostman.com/docs/requests) na documentação do Postman. Para o ponto de extremidade de API de Detecção de Idioma, defina os valores como a seguir:
   
    ![Solicitação do Postman](./media/postman-collection/request.png)
   
    Detalhes dos parâmetros e valores usados:
   
   | Parâmetro | Valor |
   | --- | --- |
   | Verbo |POSTAR |
   | URL da Solicitação |https://westus.api.cognitive.microsoft.com/text/analytics/v2.0/languages |
   | Params |numberOfLanguagesToDetect |
   | Autorização |"Nenhuma Autenticação" |
   | Cabeçalhos |Ocp-Apim-Subscription-Key = <your subscription key> <br/>Content-Type = application/json |
   | Corpo |<code>{<br/>&nbsp;&nbsp;&nbsp;"documents": [<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"id": "1",<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"text": "Hello World"<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br/>&nbsp;&nbsp;]<br/>}<code> |
2. Clique em **Enviar** para fazer a solicitação e ter uma resposta de volta.
3. Clique em **Salvar** para salvar a solicitação em uma Coleção Postman.
   
    ![Resposta do Postman](./media/postman-collection/request-response-save.png)
4. Forneça um **Nome da solicitação** e uma **Descrição da solicitação** na caixa de diálogo **Salvar Solicitação**. Você usará esses valores em seu conector personalizado.
   
    ![Salvar Coleção do Postman](./media/postman-collection/save-request-note.png)
   
    Você também pode salvar a resposta para a solicitação. Os conectores personalizados atualmente suportam apenas uma resposta por solicitação. Se você salvar várias respostas por solicitação, somente a primeira será usada.
   
    ![Salvar Resposta do Postman](./media/postman-collection/save-response.png)
5. Continue criando sua Coleção Postman criando e salvando outras solicitações e respostas.
6. Depois de ter concluído a criação da Coleção Postman para todas as suas solicitações e respostas, exporte a coleção.
   
    ![Exportar Postman](./media/postman-collection/export.png)
7. Escolha **Coleção v1** como o formato de exportação.
   
    ![Exportar Postman](./media/postman-collection/export2.png)

Agora, você pode usar essa coleção Postman para criar um conector personalizado no Microsoft Flow.

> [!IMPORTANT]
> Ao criar um conector personalizado a partir de uma coleção do Postman, não se esqueça de remover o cabeçalho `Content-type` das ações e gatilhos, pois ele será adicionado automaticamente pelo Microsoft Flow. Os cabeçalhos de autenticação (por exemplo, `Ocp-Apim-Subscription-Key`) devem ser definidos na seção **Segurança** e devem ser removidos das ações e gatilhos. 
> 
> 

Para obter mais informações, consulte [Registrar e usar conectores personalizados no Microsoft Flow](register-custom-api.md).

