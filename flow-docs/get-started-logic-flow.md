---
title: Automatizar as tarefas criando um fluxo | Microsoft Docs
description: "Crie um fluxo para executar automaticamente uma ou mais ações, como enviar email, quando ocorrem eventos, como alguém que adiciona uma linha a uma lista do SharePoint."
services: 
suite: flow
documentationcenter: na
author: aftowen
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/28/2017
ms.author: deonhe
ms.openlocfilehash: fd6ed3973ed09442108bf780f76b750deea20eeb
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="create-a-flow-in-microsoft-flow"></a>Criar um fluxo no Microsoft Flow
<iframe width="560" height="315" src="https://www.youtube.com/embed/Gt3CMhLAQqE?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF" frameborder="0" allowfullscreen></iframe>

Crie um fluxo que executa uma ou mais tarefas automaticamente depois dela ser disparada por um evento. Por exemplo, crie um fluxo que o notifique por email quando alguém envia um tweet contendo uma palavra-chave especificada. Neste exemplo, o envio do tweet é o evento e o envio do email é a ação.

## <a name="prerequisites"></a>Pré-requisitos
* Uma conta em [flow.microsoft.com](https://flow.microsoft.com)
* Uma conta do Twitter
* Credenciais do Office 365

## <a name="specify-an-event-to-start-the-flow"></a>Especificar um evento para iniciar o fluxo
Primeiro, você precisará selecionar qual evento, ou *gatilho*, inicia o fluxo.

1. Em [flow.microsoft.com](https://flow.microsoft.com), selecione **Meus fluxos** na barra de navegação superior e, em seguida, selecione **Criar do zero**.
   
    ![Opção Fluxos na barra de navegação à esquerda](./media/get-started-logic-flow/create-logic-flow.png)
2. Na caixa que informa **Pesquisar todos os conectores e gatilhos**, digite ou cole **Twitter**, em seguida, selecione **Twitter – Quando um novo tweet é postado**.
   
    ![Evento do Twitter](./media/get-started-logic-flow/twitter-search.png)
3. Se você ainda não conectou sua conta do Twitter ao Microsoft Flow, selecione **Entrar no Twitter** e, em seguida, forneça suas credenciais.
   
    ![Entrada do Twitter](./media/get-started-logic-flow/twitter-signin.png)
4. Na caixa **Texto de consulta** digite a palavra-chave que você deseja encontrar.
   
    ![Palavra-chave do Twitter](./media/get-started-logic-flow/twitter-keyword.png)

## <a name="specify-an-action"></a>Especificar uma ação
1. Selecione **Nova Etapa** e depois selecione **Adicionar uma ação**.
   
    ![Adicionar ação](./media/get-started-logic-flow/add-action-icon.png)
2. Na caixa que mostra **Pesquisar todos os conectores e ações**, digite ou cole **enviar email**, em seguida, selecione **Outlook do Office 365 - Enviar um email**.
   
    ![Lista de ações](./media/get-started-logic-flow/send-email.png)
3. Se solicitado, selecione o botão de entrada e, em seguida, forneça suas credenciais.
4. No formulário que aparece, digite ou cole o endereço de email na caixa **Para** e selecione seu nome na lista de contatos que é exibida.
   
    ![Mensagem de email em branco](./media/get-started-logic-flow/blank-email.png)
5. Na caixa **Assunto** , digite ou cole **Novo tweet de:** e, em seguida, digite um espaço.
   
    ![Linha do assunto com espaço reservado](./media/get-started-logic-flow/message-token.png)
6. Na lista de tokens, selecione o token **Publicado por** para adicionar um espaço reservado.
   
    ![Adicionar parâmetro](./media/get-started-logic-flow/add-parameter.png)
7. Clique ou toque na caixa **Corpo**, depois, clique ou toque no token **Texto do tweet** para adicionar um espaço reservado.
8. (opcional) Adicione mais tokens, outro conteúdo, ou ambos, ao corpo do email.
9. Próximo à parte superior da tela, especifique um nome para o fluxo e, em seguida, selecione **Criar fluxo**.
   
    ![Selecione o botão de Criar fluxo](./media/get-started-logic-flow/create-button.png)
10. Selecione **Concluído** para atualizar a lista de seus fluxos.
    
     ![Selecionar o botão Concluído](./media/get-started-logic-flow/done-button.png)
11. Envie uma tweet com a palavra-chave que você indicou.
    
     Dentro de um minuto, uma mensagem de email notifica sobre o novo tweet.

## <a name="manage-a-flow"></a>Gerenciar um fluxo
1. Em [flow.microsoft.com](https://flow.microsoft.com), selecione **Meus fluxos** na barra de navegação superior.
2. Na lista de fluxos, siga um destes procedimentos:
   
   * Para pausar um fluxo, defina sua alternância como **Desligada**.
     
       ![Pausar fluxo](./media/get-started-logic-flow/pause-flow.png)
   * Para retomar um fluxo, defina sua alternância como **Ligada**.
     
       ![Retomar fluxo](./media/get-started-logic-flow/resume-flow.png)
   * Para editar um fluxo, selecione o ícone de lápis que corresponde ao fluxo que você deseja editar.
     
       ![Selecionar fluxo](./media/get-started-logic-flow/select-flow.png)
   * Para excluir um fluxo, selecione o ícone **...**, selecione **Excluir**, em seguida, selecione **Excluir** na caixa de mensagem que aparece.
     
       ![Ícone Excluir](./media/get-started-logic-flow/delete-icon.png)
   * Para exibir o histórico de execuções de um fluxo, selecione o fluxo na página **Meus fluxos** e exiba o histórico na seção **HISTÓRICO DE EXECUÇÕES** da página aberta.
     
       ![histórico de fluxos](./media/get-started-logic-flow/run-history.png)
     
     Selecione uma execução de fluxo na lista de execuções para acessar as entradas e saídas de cada etapa.

**Observação**: você pode ter até 50 fluxos na conta. Se você já tiver 50, exclua um antes de criar outro.

## <a name="next-steps"></a>Próximas etapas
* [Adicionar etapas](multi-step-logic-flow.md), como diferentes maneiras de ser notificado, ao seu fluxo.
* [Execute tarefas em uma agenda](run-tasks-on-a-schedule.md) quando você quiser que uma ação ocorra diariamente, em determinada data, ou após determinado número de minutos.
* [Adicionar um fluxo a um aplicativo](https://powerapps.microsoft.com/tutorials/using-logic-flows/) para permitir que seu aplicativo inicie lógica na nuvem.
* [Comece a usar os fluxos de equipe](create-team-flows.md) e convide outras pessoas para colaborar com a criação de fluxos.

