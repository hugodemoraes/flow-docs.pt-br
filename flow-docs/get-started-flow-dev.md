---
title: "Começar a criar | Microsoft Docs"
description: "Crie um conector personalizado, compartilhe-o, insira um fluxo e faça muito mais."
services: 
suite: flow
documentationcenter: na
author: bbarath
manager: erikre
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/22/2016
ms.author: barathb
ms.openlocfilehash: d22193ac40b6eb8f90abf2ae5ced91b39c2faad9
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="start-to-build-with-microsoft-flow"></a>Começar a criar com o Microsoft Flow
Estenda seu aplicativo com o Microsoft Flow das seguintes maneiras, entre outras:

* criar e conectar a um conector personalizado
* compartilhar essa API com todos os usuários do Microsoft Flow
* inserir a experiência de fluxo de dentro de um aplicativo
* aproveitar todas os APIs do desenvolvedor para que os usuários podem interagir com o Microsoft Flow da melhor maneira para eles

## <a name="prerequisites"></a>Pré-requisitos
* Uma conta em [flow.microsoft.com](https://flow.microsoft.com)

## <a name="create-a-custom-connector"></a>Criar um conector personalizado
Quando você tem um serviço Web que quer que seja capaz de automatizar com o Microsoft Flow, terá de criar primeiro um conector personalizado. Ao registrar um conector personalizado, você informa ao Microsoft Flow sobre as características de sua API Web, incluindo a autenticação necessária, os gatilhos e as ações que ela dá suporte e os parâmetros e as saídas para cada uma dessas ações.

Siga [este tutorial](https://powerapps.microsoft.com/tutorials/register-custom-api/) para registrar um conector personalizado. Depois de registrá-la, você pode compartilhar a API dentro de sua organização para que outras pessoas possam ajudá-lo a testá-la.

## <a name="share-a-custom-connector-with-all-microsoft-flow-users"></a>Compartilhar um conector personalizado com todos os usuários do Microsoft Flow
Depois de testar completamente seu conector personalizado, inicie o processo de análise conforme estabelecido na [postagem deste blog](https://flow.microsoft.com/blog/calling-all-saas-apps-now-you-can-build-your-own-connector-for-flow-and-logic-apps/):

* Um arquivo OpenAPI que representa sua API e informações de autenticação
* Um ícone para o conector
* Uma descrição de sua API
* Cerca de 10 ideias de como a API pode beneficiar outros usuários por meio de modelos

Depois de enviar essas informações, a Microsoft começará avaliar a função da API no Microsoft Flow e Microsoft PowerApps.

## <a name="embed-the-flow-experience-in-your-website-or-app"></a>Inserir a experiência de fluxo no site ou aplicativo
Por fim, você pode inserir o Microsoft Flow de dentro do aplicativo para habilitar integração profunda, em contexto, entre o aplicativo e todos os outros serviços aos quais o Microsoft Flow dá suporte. Por exemplo, você pode:

* Procurar todos os modelos relacionados ao serviço e permitir que usuários selecionem um modelo
* Gerenciar os fluxos que os usuários relacionaram ao aplicativo

Execute [Este tutorial](embed-flow-dev.md) para obter mais informações sobre como inserir o Microsoft Flow dentro de um aplicativo.

