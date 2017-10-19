---
title: "Aguardar a aprovação em um fluxo | Microsoft Docs"
description: "Os fluxos podem esperar que um evento externo ocorra, como um usuário aprovar ou rejeitar uma alteração, antes de executar uma ação, como o envio da notificação da decisão."
services: 
suite: flow
documentationcenter: na
author: merwanhade
manager: erikre
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/24/2016
ms.author: merwanhade
ms.openlocfilehash: a26566486cf6310dc1c33ef226bfc37b30a5ad16
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="wait-for-approval-in-microsoft-flow"></a>Aguardar a aprovação no Microsoft Flow
<iframe width="560" height="315" src="https://www.youtube.com/embed/W6oxcYRtW-8?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF" frameborder="0" allowfullscreen></iframe>

Crie um fluxo que, se você criar um item no SharePoint, envia um email de aprovação e notifica se o item foi aprovado ou rejeitado. Para acompanhar este tutorial de maneira exata, crie uma lista simples do SharePoint como uma ação de gatilho, mas você pode usar outra fonte de dados, como o Dropbox ou o OneDrive.

**Pré-requisitos**

* Crie uma lista simples do SharePoint Online chamada de **Rastreador de projetos** com uma coluna chamada **Título** e adicione uma coluna de Pessoa ou Grupo, denominada **Atribuído a**.
  
   ![Imagem da lista de Rastreador de projetos do SPO](./media/wait-for-approvals/project-tracker.png)

## <a name="add-an-event-to-trigger-the-flow"></a>Adicione um evento para disparar o fluxo
1. Em [flow.microsoft.com](https://flow.microsoft.com), selecione **Meus fluxos** na barra de navegação superior e, em seguida, selecione **Criar novo fluxo**.
   
    ![Imagem de criar o novo fluxo](./media/wait-for-approvals/create-a-new-flow.png)
2. Na caixa **Como você deseja iniciar?** digite ou cole **novo item** e, em seguida, selecione **SharePoint Online – quando um novo item é criado**.
   
    ![Imagem do gatilho do SPO](./media/wait-for-approvals/send-approval-email-select-2.png)
3. Se for solicitado, entre no SharePoint Online.
4. Em **Site url**, digite ou cole a URL do site que contém a lista.
   
    ![Imagem do siteurl do SPO](./media/wait-for-approvals/SPO-site-url.png)
5. Em **Nome da lista**, selecione uma lista, como a **Rastreador de projetos**.
   
    ![Imagem de listname do SPO](./media/wait-for-approvals/SPO-list-name.png)

## <a name="add-the-resulting-action"></a>Adicione a ação resultante
1. Selecione o botão **+** e, em seguida, selecione **Adicionar uma ação.**
   
    ![Imagem de adicionar uma ação](./media/wait-for-approvals/add-an-action.png)
2. Na caixa **O que você deseja fazer em seguida?** digite ou cole **Enviar email** e, em seguida, selecione **Outlook do Office 365 – enviar email de aprovação**.
   
    ![Imagem de enviar email de aprovação](./media/wait-for-approvals/send-approval-mail.png)
3. Se for solicitado, entre no Outlook do Office 365.
4. Selecione o campo **Para** e, em seguida, selecione **Atribuídos a Email**.
   
    O usuário na coluna **Atribuído a** receberá o email para aprovar ou rejeitar o item. Quando você criar um item para testar o fluxo, você especificará você mesmo nesse campo. Dessa forma, você não irá apenas aprovar ou rejeitar o item mas também receber o email de notificação.
   
    **Observação**: você pode personalizar os campos de **Assunto** e **Opções do usuário** para se adequar às suas necessidades.
   
    ![Imagem do campo enviar o email de aprovação para](./media/wait-for-approvals/send-approval-email-to.png)

## <a name="add-a-condition"></a>Adicionar uma condição
1. Selecione o botão **+** e, em seguida, selecione **Adicionar uma condição**.
   
    ![Imagem de adicionar uma condição](./media/wait-for-approvals/add-a-condition.png)
2. No campo **Nome do Objeto**, selecione **SelectedOption**.
3. No **Campo de valor**, digite ou cole **Aprovar**.
   
    ![Imagem da placa de condição](./media/wait-for-approvals/condition-card-2.png)
4. Na área **Se sim**, selecione **Adicionar uma ação**.
   
    ![Imagem de sim-adicionar uma ação](./media/wait-for-approvals/yes-add-an-action.png)
5. Na caixa **O que você deseja fazer em seguida?** digite ou cole **Enviar email** e, em seguida, selecione **Outlook do Office 365 – Enviar Email**.
   
    ![Imagem de sim-enviar-email](./media/wait-for-approvals/yes-send-email.png)
6. Na caixa **Assunto**, especifique um assunto.
   
    Por exemplo, selecione **Atribuído a DisplayName**, digite **Aprovou** com um espaço em cada lado e, em seguida, selecione **Título**.
7. Na caixa **Corpo**, especifique o corpo de email com algo como **Pronto para prosseguir com a próxima fase do projeto.**
8. No campo **Para** insira um destinatário como **Criado por Email**.
   
    A pessoa que criou o item na lista do SharePoint será notificada se o projeto foi aprovado ou rejeitado.
   
    ![Imagem de sim-enviar-email](./media/wait-for-approvals/if-yes-send-email-card-3.png)
9. Na área **Se não**, repita as cinco últimas etapas alterando o **Assunto** e **Corpo** para demonstrar que o projeto foi rejeitado.
   
     ![Imagem de não-enviar-email](./media/wait-for-approvals/no-send-email-2.png)

## <a name="finish-and-test-your-flow"></a>Concluir e testar seu fluxo
1. Nomeie seu fluxo e, em seguida, selecione **Criar fluxo**.
   
     ![Imagem de criar-fluxo](./media/wait-for-approvals/create-flow.png)
2. Crie um item na sua lista do SharePoint.
   
    Um email de aprovação é enviado para o destinatário que você havia especificado. Quando o destinatário seleciona **Aprovar** ou **Rejeitar** naquela mensagem, você recebe email que indica a resposta. 

