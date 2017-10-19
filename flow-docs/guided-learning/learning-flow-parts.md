---
title: "Blocos de construção do Microsoft Flow | Microsoft Docs"
description: Confira as diferentes partes do Microsoft Flow e como elas se relacionam. Crie novos fluxos de modelos e a partir do zero.
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: 9U8jMRO-Jv0
courseduration: 9m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/22/2016
ms.author: deonhe
ms.openlocfilehash: 6a7fe2d56c7bc3b2253b675ce26f3f29042a7a71
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="building-blocks-of-microsoft-flow"></a>Blocos de construção do Microsoft Flow
Agora que você conhece o básico do Microsoft Flow, faremos **um tour do Microsoft Flow**. Veremos rapidamente como criar os fluxos a partir de modelos e criar fluxos a partir do zero.

## <a name="check-out-the-templates"></a>Conferir alguns modelos
Em flow.microsoft.com, se você clicar no link **Modelos** no topo da página, será saudado com vários modelos que você pode utilizar imediatamente com os serviços da Web. Explore esses aplicativos para **ter uma ideia do que é possível** e como o Microsoft Flow pode ajudar sua empresa.

![Modelos de fluxo](./media/learning-flow-parts/template-list.png)

Cada fluxo de modelo foi projetado para uma finalidade específica, como receber notificações quando algo acontece, copiar um novo arquivo de um serviço para outro ou controlar as aprovações do SharePoint. Esses modelos estão **pronto para o uso**.  Você só precisa **configurar os modelos** para adicionar os fluxos à sua conta. Faça isso clicando em **Usar este modelo**, entrando nos serviços necessários e preenchendo os formulário que se seguem.  Por exemplo, isso é um fluxo criado a partir de um modelo para enviar notificações por email quando uma lista do SharePoint é modificada. 

![Modelo do fluxo de exemplo](./media/learning-flow-parts/example-template.png)

Há centenas de modelos disponíveis e você pode encontrá-los no **Microsoft Flow para Web** ou no **Microsoft Flow para dispositivos móveis**.

![Web e dispositivos móveis do Flow](./media/learning-flow-parts/flow-web-mobile.png)

## <a name="create-a-flow-from-scratch"></a>Crie um fluxo a partir do zero
Você já viu como criar um fluxo usando um modelo, mas e se houver uma tarefa que você deseja automatizar, mas não é possível encontrar um modelo apropriado? Você pode **criar um fluxo a partir do zero**.  Quando você cria um fluxo do zero, inicia em uma tela em branco e adiciona **serviços, gatilhos e ações** para compilar seu fluxo.  

![Fluxo em branco](./media/learning-flow-parts/flow-from-blank.png)

## <a name="building-blocks-of-a-flow"></a>Blocos de construção de um fluxo
Se você estiver criando um fluxo de um modelo ou a partir do zero, ele conterá os **blocos de construção** que funcionam juntos de determinadas maneiras, semelhante a um fluxograma.

* Os **Serviços** são as fontes e os destinos dos dados em um fluxo.
* Os **gatilhos** são os eventos que iniciam um fluxo.
* As **ações** são tarefas executadas pelo fluxo.
* As **condições** permitem a ramificação if/then lógica em um fluxo.
* Os **loops** são para iterar as ações mais de uma vez.

### <a name="services"></a>Serviços
O Microsoft Flow pode conectar muitos **aplicativos e serviços** diferentes.  Alguns serviços de exemplo são o **Twitter**, **Github**, **Wunderlist** e **Office 365** e **Google Docs**.  Essas são as **fontes** que fornecem dados ao Microsoft Flow, além de fornecer os **destinos** para o trabalho realizado pelo Microsoft Flow.  Você pode exibir toda a lista de serviços clicando no link **Serviços** na parte superior de **flow.microsoft.com**.

![Conectores do fluxo](./media/learning-flow-parts/flow-connectors.png)

### <a name="triggers"></a>Gatilhos
Todo fluxo começa com um **gatilho**.  Há muitos tipos diferentes de gatilho.  Alguns são eventos em seus serviços Web conectados, como **quando um determinado usuário envia um tweet** ou **um arquivo é salvo em sua conta do Dropbox**.  Outros gatilhos são recursos internos, como **executar um fluxo em um agendamento recorrente** ou **executar um fluxo em resposta a uma solicitação da Web**.  Finalmente, há gatilhos manuais, como iniciar um fluxo clicando em um **botão no Microsoft Flow ou no Microsoft PowerApps**.  Os gatilhos geralmente **passam as informações sobre o evento que ocorreu** para as ações em seu fluxo.

![Gatilhos do fluxo](./media/learning-flow-parts/flow-triggers.png)  

### <a name="actions"></a>Ações
Uma **ação** representa o que você deseja realmente que **aconteça** depois do fluxo ser disparado.  Pode ser uma **notificação**, **copiar os dados ou arquivos** de uma origem para um destino ou alguma outra ação, como **postar na mídia social** ou **atrasar por um período de tempo**.  Você também pode usar as ações para **recuperar os dados de um serviço** para usar com outras ações.

![Ações do fluxo](./media/learning-flow-parts/flow-actions.png) 

### <a name="conditions"></a>Condições
As **condições** permitem que você adicione a tomada de decisão ao seu fluxo.  Quando uma condição é avaliada, o fluxo se ramifica em um caminho **Sim** e um caminho **não**.   Por exemplo, se você quiser copiar as fotos de suas férias postadas no **Dropbox** para o **OneDrive**, poderá criar uma condição após um gatilho de **novo arquivo do Dropbox** que verifica se o nome do arquivo contém a palavra *férias* e se tiver, copiará o arquivo para o **OneDrive**, mas caso contrário, escolherá não fazer nada.

![Condição do fluxo](./media/learning-flow-parts/flow-condition.png) 

### <a name="loops"></a>Loops
Os **loops** permitem que você execute uma ação mais de uma vez, por exemplo, se uma ação precisa ocorrer repetidamente ou uma vez por item em uma coleção de itens.

## <a name="next-lesson"></a>Próxima lição
Neste tópico, vimos o Microsoft Flow.  Navegamos os **modelos** e falamos sobre como **criar um fluxo a partir do zero**.  Criamos os fluxos conectando os aplicativos e serviços, **gatilhos** para iniciar o fluxo, **ações** fazer algo acontecer no fluxo, **condições** para tomar decisões e **loops** para iterar um fluxo.  **A maneira mais fácil de aprender sobre o Microsoft Flow é começar com um modelo** e conectá-lo aos aplicativos e serviços que você já usa. 

Em seguida, analisaremos o que aprendemos até aqui neste curso de Aprendizado Guiado.

