---
title: Execute os fluxos com base nas propriedades de email. | Microsoft Docs
description: "Inicie um fluxo com base em propriedades como o assunto, do endereço, ou o destinatário de um email."
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
ms.date: 06/08/2017
ms.author: deonhe
ms.openlocfilehash: 395cb9bc1d58e50e5ac8ebac9afaed544f3261ec
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="trigger-a-flow-based-on-email-properties"></a>Dispare um fluxo com base nas propriedades de email
Use o gatilho **Quando um novo email chega** para criar um fluxo que é executado quando uma ou mais dessas propriedades d email correspondem aos critérios fornecidos:

| Propriedade | Quando usar |
| --- | --- |
| Pasta |Disparar um fluxo sempre que emails chegam em uma pasta específica. Essa propriedade pode ser útil se você tiver regras para rotear emails em pastas diferentes. |
| Para |Disparar um fluxo com base no endereço para o qual um email foi enviado. Essa propriedade pode ser útil se você receber o email enviado aos endereços de email diferentes na mesma caixa de entrada. |
| De |Disparar um fluxo com base no endereço de email do remetente. |
| Importância |Disparar um fluxo com base na importância com a qual os emails foram enviados. O email pode ser enviado com importância alta, normal ou baixa. |
| Tem anexo |Disparar um fluxo com base na presença de anexos de emails de entrada. |
| Filtro de assunto |Procurar a presença de palavras específicas no assunto de um email. Em seguida, seu fluxo executa *ações* com base nos resultados da pesquisa. |

> [!IMPORTANT]
> Cada [plano do Microsoft Flow](https://flow.microsoft.com/pricing/) inclui uma cota de execução. Quando possível, verifique sempre as propriedades no gatilho do fluxo. Isso evita o uso de sua cota de execução desnecessariamente. Se você verificar uma propriedade em uma condição, cada execução conta em relação à cota de execução do plano, mesmo se a condição de filtro que você definiu não for atendida. Por exemplo, se você verificar o endereço *de* de um email em uma condição, cada execução conta em relação à cota de execução do plano, mesmo que não seja o endereço *de* do seu interesse.
> 
> 

Na passo a passo abaixo, verificamos todas as propriedades no gatilho **Quando um novo email chega**. Você pode aprender mais visitando as [perguntas frequentes sobre a cobrança](billing-questions.md#what-counts-as-a-run) e a página [preços](https://ms.flow.microsoft.com/pricing/).

## <a name="prerequisites"></a>Pré-requisitos
* Uma conta com acesso ao [Microsoft Flow](https://flow.microsoft.com).
* uma conta do Outlook do Office 365.
* O aplicativo móvel Microsoft Flow para [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios), ou [Windows Phone](https://aka.ms/flowmobilewindows).
* conexões com o Outlook do Office 365 e o serviço de notificação por push.

## <a name="trigger-a-flow-based-on-an-emails-subject"></a>Dispare um fluxo com base no assunto do email
Neste passo a passo, criamos um fluxo que envia uma notificação por push para seu celular caso o assunto de qualquer novo email tenha a palavra "loteria" nele. Seu fluxo marca esses emails como *lido*.

Observação: embora este passo a passo envie uma notificação por push, você pode usar qualquer outra ação que atenda às suas necessidades de fluxo de trabalho. Por exemplo, você poderia armazenar o conteúdo de email em outro repositório, como as Planilhas Google ou um arquivo do Microsoft Excel armazenado no Dropbox.

Ok. Vamos começar:

[!INCLUDE [sign-in-use-blank-select-email-trigger-and-inbox-folder](includes/sign-in-use-blank-select-email-trigger-and-inbox-folder.md)]

1. Na caixa **Filtro de assunto**, digite o texto que seu fluxo usa para filtrar os emails de entrada.
   
     Neste exemplo, tenho interesse em qualquer email que tenha a palavra "loteria" no assunto.
   
    ![opções avançadas](./media/email-triggers/email-triggers-subject-text.png)

[!INCLUDE [add-mobile-notification-action](includes/add-mobile-notification-action.md)]

1. Insira os detalhes para a notificação móvel que você gostaria de receber quando um email que corresponda ao **Filtro de assunto** especificado anteriormente chega.
   
    ![detalhes da notificação](./media/email-triggers/email-triggers-4.png)

[!INCLUDE [add-mark-as-read-action](includes/add-mark-as-read-action.md)]

1. Nomeie o fluxo e, em seguida, salve-o selecionando **Criar fluxo** na parte superior da página.
   
    ![salvar fluxo](./media/email-triggers/email-triggers-subject-notification.png)

Parabéns, você receberá uma notificação por push sempre que receber um email que contenha a palavra "loteria" no assunto.

## <a name="trigger-a-flow-based-on-an-emails-sender"></a>Dispare um fluxo com base no remetente do email
Neste passo a passo, criamos um fluxo que envia uma notificação por push para seu celular quando novos emails forem recebidos de um remetente específico (endereço de email). O fluxo também marca esses emails como *lido*.

[!INCLUDE [sign-in-use-blank-select-email-trigger-and-inbox-folder](includes/sign-in-use-blank-select-email-trigger-and-inbox-folder.md)]

1. Insira o endereço de email do remetente em **De**.
   
     Seu fluxo age em qualquer email enviado deste endereço.
   
    ![propriedade do email](./media/email-triggers/email-triggers-from.png)

[!INCLUDE [add-mobile-notification-action](includes/add-mobile-notification-action.md)]

1. Insira os detalhes para a notificação móvel que você gostaria de receber sempre que uma mensagem chega do endereço de email inserido anteriormente.
   
    ![detalhes da notificação](./media/email-triggers/email-triggers-sender-notification.png)

[!INCLUDE [add-mark-as-read-action](includes/add-mark-as-read-action.md)]

1. Nomeie o fluxo e, em seguida, salve-o selecionando **Criar fluxo** na parte superior da página.
   
    ![salvar fluxo](./media/email-triggers/email-triggers-sender-5.png)

## <a name="trigger-a-flow-when-emails-arrive-in-a-specific-folder"></a>Disparar um fluxo ao receber emails em uma pasta específica
Se você tiver regras que encaminham email para pastas diferentes com base em determinadas propriedades, como o endereço, utilize este tipo de fluxo.

Vamos começar:

> [!NOTE]
> Se você ainda não tiver uma regra que encaminha email para uma pasta diferente de sua caixa de entrada, crie essa regra e confirme se ela funciona enviando um email de teste.
> 
> 

[!INCLUDE [sign-in-use-blank-select-email-trigger-and-specific-folder](includes/sign-in-use-blank-select-email-trigger-and-specific-folder.md)]

1. Selecione a pasta para a qual você criou a regra para encaminhar emails específicos. Para exibir todas as pastas de email, primeiro selecione o ícone **Mostrar seletor**, que está localizado do lado direito da caixa **Pasta** no cartão **Quando um novo email chega**.
   
    ![selecionar pasta](./media/email-triggers/email-triggers-2.png)

[!INCLUDE [add-mobile-notification-action](includes/add-mobile-notification-action.md)]

1. Insira os detalhes para a notificação móvel que você gostaria de receber quando chega um email na pasta selecionada anteriormente. Se você ainda não fez isso, insira as credenciais para o serviço de notificações.
   
    ![detalhes da notificação](./media/email-triggers/email-triggers-folder-notification.png)

[!INCLUDE [add-mark-as-read-action](includes/add-mark-as-read-action.md)]

1. Nomeie o fluxo e, em seguida, salve-o selecionando **Criar fluxo** na parte superior da página.
   
    ![salvar fluxo](./media/email-triggers/email-triggers-7.png)

Teste o fluxo enviando um email encaminhado para a pasta que você selecionou anteriormente neste passo a passo.

