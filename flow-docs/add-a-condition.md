---
title: "Adicionar uma condição a um fluxo | Microsoft Docs"
description: "Especifique se um fluxo executa uma ou mais tarefas apenas se determinada condição for verdadeira."
services: 
suite: flow
documentationcenter: na
author: stepsic-microsoft-com
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/22/2016
ms.author: stepsic
ms.openlocfilehash: 1291b32f001be211acddbf1c83f3b1bdf03f2ac3
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="add-a-condition-to-a-flow"></a>Adicionar uma condição a um fluxo
Especifique se um fluxo executa uma ou mais tarefas apenas se determinada condição for verdadeira. Por exemplo, especifique que você receberá um email somente se um tweet que contém uma palavra-chave for retweetado pelo menos 10 vezes.

**Pré-requisitos**

* [Criar um fluxo](get-started-logic-template.md) de um modelo: este tutorial [usará este modelo](https://flow.microsoft.com/galleries/public/templates/e78571e5c70e4806a18eeacba5a897c8/) como exemplo

## <a name="add-a-condition"></a>Adicionar uma condição
1. Em [flow.microsoft.com](https://flow.microsoft.com), selecione **Meus Fluxos** na barra de navegação superior.
2. Na lista de fluxos, selecione um fluxo que você criou. Este tutorial usa um exemplo com um gatilho do Twitter e uma ação do SharePoint.
3. Na última ação, selecione o botão **Nova etapa**.
4. Selecione **Adicionar uma condição**.
   
    ![Botão de condição](./media/add-a-condition/add-condition.png)
5. Selecione uma área vazia no **Nome do objeto** e selecione **Adicionar conteúdo dinâmico** para abrir o menu de conteúdo dinâmico.
6. Selecione o parâmetro **Retweetar contagem** para adicioná-lo à caixa.
7. Na caixa **Relação**, selecione **é maior que ou igual a**.
8. Na caixa **Valor**, digite **10**.
   
    ![A caixa NOME DO OBJETO contendo um parâmetro](./media/add-a-condition/specify-condition.png)
9. Clique no cabeçalho da ação desejada dentro de condição (como **Criar item**) e arraste-o abaixo do texto que lê **SE SIM**. Quando você soltar o cursor, a ação deverá se mover para a caixa.
   
    ![Arrastar ação](./media/add-a-condition/drag-action.png)
10. Salvar o fluxo.

## <a name="edit-in-advanced-mode"></a>Editar no modo avançado
Você também pode selecionar o link **Editar no modo avançado** para gravar condições mais avançadas. Você pode usar qualquer expressão da *Linguagem de definição de fluxo de trabalho* aqui. [Saiba mais sobre](https://msdn.microsoft.com/library/azure/mt643789.aspx) quais funções estão disponíveis.

