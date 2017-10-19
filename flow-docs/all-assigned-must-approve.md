---
title: "Criar um fluxo de aprovação que exige a aprovação de todos | Microsoft Docs"
description: "Crie um fluxo de aprovação que exige a aprovação de todos, ou a rejeição da solicitação por uma pessoa."
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/22/2017
ms.author: deonhe
ms.openlocfilehash: 0e0309793cfcb45ca7ee72910803a4abc27d2f26
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="create-an-approval-flow-that-requires-everyone-to-approve"></a>Criar um fluxo de aprovação que exige a aprovação de todos
Este passo a passo mostra como criar um fluxo de trabalho de aprovação que exige a aprovação de todos (todos os aprovadores atribuídos) para um pedido de férias ser aprovado, mas qualquer aprovador pode rejeitar toda a solicitação.

Esse tipo de fluxo de trabalho de aprovação é útil em uma organização que exige a aprovação do gerente de uma pessoa, e do gerente do gerente, para que um pedido de férias seja aprovado. No entanto, qualquer um dos gerentes pode recusar o pedido sem a aceitação ou recusa da outra pessoa.

## <a name="prerequisites"></a>Pré-requisitos
* Acesso ao [Microsoft Flow](https://flow.microsoft.com), Office 365 Outlook e usuários do Office 365.
* Uma [lista](https://support.office.com/en-us/article/SharePoint-lists-I-An-introduction-f11cd5fe-bc87-4f9e-9bfe-bbd87a22a194) do SharePoint Online.
  
    Este passo a passo pressupõe que você já criou uma lista do SharePoint Online usada para pedir férias. Consulte o passo a passo de [aprovações paralelas](parallel-modern-approvals.md) para obter um exemplo avançado que detalha a aparência das suas listas do SharePoint.
* Familiaridade com os conceitos básicos de criação de fluxos.
  
    Você pode examinar como adicionar [ações, disparadores](multi-step-logic-flow.md#add-another-action) e [condições](add-a-condition.md). As etapas a seguir pressupõem que você sabe como executar essas ações.

> [!NOTE]
> Enquanto usamos o SharePoint Online e o Outlook do Office 365 neste passo a passo, você pode usar outros serviços, como Zendesk, Salesforce, Gmail ou qualquer um dos mais de [150 serviços](https://flow.microsoft.com/connectors/) com suporte do Microsoft Flow.
> 
> 

## <a name="create-the-flow"></a>Criar o fluxo
> [!NOTE]
> Se você não tiver criado uma conexão com o SharePoint ou Office 365, siga as instruções quando receber a solicitação para entrar.
> 
> 

Este passo a passo usa tokens. Para exibir a lista de tokens, toque ou clique em qualquer controle de entrada e, em seguida, procure o token na lista **Conteúdo dinâmico** que é aberta.

Entre no [Microsoft Flow](https://flow.microsoft.com) e, em seguida, execute as seguintes etapas para criar seu fluxo.

1. Selecione **Meus fluxos** > **Criar de um modelo em branco**.
2. Adicione o gatilho **SharePoint - Quando um item for criado ou modificado**.
3. Insira o **Endereço do Site** para o site do SharePoint que hospeda sua lista de pedidos de férias e, em seguida, selecione a lista na caixa **Nome da Lista**.
4. Adicione a ação **Usuários do Office 365 - Obter gerente** e, em seguida, adicione o token **Criado por Email** à caixa **Usuário (UPN)**.
   
    O token **Criado por Email** está localizado na categoria **Quando um item for criado ou modificado** da lista **Conteúdo dinâmico**.
5. Adicione outra ação **Usuários do Office 365 - Obter gerente** e, em seguida, adicione o token **Email** à caixa **Usuário (UPN)**.
   
    O token **Email** está localizado sob a categoria **Obter gerente** da lista **Conteúdo dinâmico**.
   
    Você também pode renomear o cartão **Obter gerente 2** para algo significativo como "Ignorar gerente de nível".
6. Adicione a ação **Iniciar uma aprovação** e selecione **Todos da lista atribuída** na lista **Tipo aprovação**.
   
   > [!IMPORTANT]
   > Se qualquer aprovador rejeitar, o pedido de aprovação será considerada rejeitada por todos os aprovadores.
   > 
   > 
7. Use a tabela a seguir como guia para concluir o cartão **Iniciar uma aprovação**.
   
   | Campo | Descrição |
   | --- | --- |
   |  Tipo de aprovação |Use **Qualquer pessoa da lista atribuída** para indicar que qualquer um dos aprovadores pode aprovar ou rejeitar o pedido. </p>Use **Todos da lista atribuída** para indicar que um pedido só será aprovado se todos concordarem, e o pedido será negado se uma única pessoa o rejeitar. |
   |  Título |O título do pedido de aprovação. |
   |  Atribuído a |Os endereços de email dos aprovadores. |
   |  Detalhes |Quaisquer informações adicionais que você deseja enviar aos aprovadores listados no campo **Atribuído a**. |
   |  Link do item |Uma URL para o item de aprovação. Neste exemplo, é um link para o item no SharePoint. |
   |  Descrição do link do item |Uma descrição de texto para o **Link do item**. |
   
   > [!TIP]
   > A ação **Iniciar uma aprovação** fornece vários tokens, incluindo **Resposta** e **Resumo da resposta**. Use esses tokens em seu fluxo para fornecer relatórios avançados dos resultados de uma execução de um fluxo de pedido de aprovação.
   > 
   > 
   
    O cartão **Iniciar uma aprovação** é um modelo para o pedido de aprovação enviado aos aprovadores. Configure-o de um jeito útil para a sua organização. Veja um exemplo.
   
    ![iniciar uma aprovação](media/all-assigned-must-approve/start-an-approval-card.png)
8. Adicione a ação **Outlook do Office 365 - Enviar um email** e, em seguida, configure-a para enviar um email com os resultados do pedido.
   
    Veja um exemplo da provável aparência do cartão **Enviar um email**.
   
    ![enviar um email](media/all-assigned-must-approve/send-an-email-card.png)

> [!NOTE]
> Qualquer ação que segue a ação **Iniciar uma aprovação** é executada com base na seleção feita na lista **Tipo aprovação** no cartão **Iniciar uma aprovação**. A tabela a seguir lista o comportamento com base em sua seleção.
> 
> 

| Tipo de aprovação | Comportamento |
| --- | --- |
| Qualquer pessoa da lista atribuída |Ações que seguem a ação **Iniciar uma aprovação** são executadas após a decisão de qualquer um dos aprovadores. |
| Todos da lista atribuída |Ações que seguem a ação **Iniciar uma aprovação** são executadas após um aprovador recusar, ou todos aprovarem o pedido. |

Na parte superior da tela, insira um nome para o fluxo na caixa **Nome do fluxo** e, em seguida, selecione **Criar fluxo** para salvá-lo.

Parabéns, o fluxo está concluído! Se você tiver acompanhado o processo, seu fluxo será semelhante a esta imagem.

![imagem do fluxo geral](media/all-assigned-must-approve/overall-flow.png)

Agora, sempre que um item em sua lista do SharePoint mudar, seu fluxo será disparado e enviará pedidos de aprovação para todos os aprovadores listados na caixa **Atribuído a** do cartão **Iniciar uma aprovação**. Seu fluxo envia pedidos de aprovação por meio do aplicativo móvel do Microsoft Flow e por email. A pessoa que cria o item no SharePoint recebe um email que resume os resultados, indicando claramente se o pedido foi aprovado ou rejeitado.

Veja um exemplo de pedido de aprovação enviado a cada aprovador.

![solicitação de aprovação](media/all-assigned-must-approve/approval-request.png)

Aqui está um exemplo de como uma resposta, e uma resposta resumida, após a execução de seu fluxo.

![tokens de resposta](media/all-assigned-must-approve/response-output.png)

## <a name="learn-more-about-approvals"></a>Saiba mais sobre as aprovações
* [Aprovações modernas do aprovador único](modern-approvals.md)
* [Aprovações modernas sequenciais](sequential-modern-approvals.md)
* [Aprovações modernas paralelas](sequential-modern-approvals.md)

