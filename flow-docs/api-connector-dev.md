---
title: Desenvolver um conector da API | Microsoft Docs
description: "Descreva sua API, especifique o tipo de autenticação, crie gatilhos e ações, e teste."
services: 
suite: flow
documentationcenter: na
author: asavaritayal
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/06/2017
ms.author: astay
ms.openlocfilehash: 8731e8a90a62bac4a05068386d23d2449952860b
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="develop-an-api-connector-microsoft-flow"></a>Desenvolver um conector da API (Microsoft Flow)
Criar um conector envolve várias etapas. Para começar - no [Microsoft Flow](https://flow.microsoft.com/), clique ou toque no botão **Configurações** (o ícone de engrenagem) no canto superior direito da página. Em seguida, clique ou toque em **Conectores Personalizados**.

![Localizando os conectores da API](./media/api-connectors-dev/finding-custom-apis.png)

## <a name="describe-your-api"></a>Descrever sua API
Os conectores da API são descritos usando o [OpenAPI padrão](https://swagger.io/) para definir a interface de uma API HTTP. Você pode começar criando um arquivo do OpenAPI existente ou pode importar uma [Coleção Postman](https://www.getpostman.com/docs/collections), que gera automaticamente o arquivo do OpenAPI para você. 

![Definir o diagrama da API](./media/api-connectors-dev/build-your-api-updated.png)

Se você iniciar a partir destas descrições da API, os campos de metadados no assistente serão preenchidos automaticamente. Você pode editá-los a qualquer momento.  

## <a name="build-security"></a>Promover a segurança
Escolha o tipo de autenticação com suporte de seu serviço e forneça detalhes adicionais para habilitar a identidade para fluir adequadamente entre o serviço e todos os clientes. 

![Diagrama da Segurança](./media/api-connectors-dev/security.png)

[Saiba mais](register-custom-api.md) sobre a segurança do conector.

## <a name="build-triggers-and-actions"></a>Criar gatilhos e ações
1. Para criar gatilhos e ações para o conector, troque para a guia **Definição**. 
   
    ![Diagrama da Definição](./media/api-connectors-dev/definition.png)
2. Usando o assistente, você pode adicionar novas operações ou editar o esquema e a resposta para as existentes. As propriedades **Geral** para cada operação permitem controlar a experiência do usuário final para o conector. Saiba mais sobre os diferentes tipos de operações usando os links abaixo:
   
   * [Gatilhos](customapi-webhooks.md) (não visíveis no PowerApps)
   * [Ações](register-custom-api.md)
     
     Para implementar a funcionalidade avançada do Microsoft Flow, consulte [Extensões do OpenAPI para os conectores da API](https://flow.microsoft.com/documentation/customapi-how-to-swagger/). 
3. Por fim, clique ou toque em **Criar conector** para registrar o conector da API.

Para obter os recursos adicionais indisponíveis no assistente, entre em contato com [ condevhelp@microsoft.com ](mailto:condevhelp@microsoft.com).

## <a name="test-the-connector"></a>Testar o conector
Antes do envio, teste seu conector da API de uma ou mais maneiras: 

* Usando o [Assistente de teste](https://flow.microsoft.com/blog/new-updates-custom-api/) do conector da API, você pode chamar cada operação para verificar sua funcionalidade e o esquema de resposta.
* No designer do Microsoft Flow, você pode criar visualmente fluxos usando o conector da API. Esse método de teste fornece visibilidade da funcionalidade de interface do usuário e recursos do seu conector.
* No PowerApps Studio, você pode chamar cada operação usando a barra de fórmulas e associar a resposta aos controles na tela.

Este tópico fornece uma visão geral. Para obter mais informações, consulte [Registrar e usar um conector personalizado](register-custom-api.md).

