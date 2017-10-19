---
title: Solucionando problemas de um fluxo | Microsoft Docs
description: Resolver alguns dos motivos mais comuns para os fluxos falharem
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
ms.date: 01/17/2017
ms.author: stepsic
ms.openlocfilehash: 7f4e41437fa19f58c08e2ecd1fb65a3a30092ef8
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="troubleshooting-a-flow"></a>Solução de problemas de um fluxo
## <a name="identify-the-error"></a>Identificar o erro
Antes de você poder corrigir um fluxo, deverá identificar o motivo da falha. Clique ou toque no ícone de notificações na parte superior do portal da Web (ou abra a guia **Atividade** no aplicativo móvel) e clique ou toque em seu fluxo na lista que aparece.

![Notificações](./media/fix-flow-failures/notifications-toolbar.png)

Os detalhes sobre o fluxo aparecem e pelo menos uma etapa mostra um ícone com exclamação vermelho. Abra essa etapa e examine a mensagem de erro.

![Mensagem de erro](./media/fix-flow-failures/flow-run-failure.png)

## <a name="authentication-failures"></a>Falhas de autenticação
Em muitos casos, os fluxos falham devido a um erro de autenticação. Se você tiver esse tipo de erro, a mensagem de erro conterá **Não autorizado** ou um código de erro **401** ou **403** aparecerá. Geralmente, você pode corrigir um erro de autenticação atualizando a conexão:

1. Na parte superior do portal da Web, clique ou toque no ícone de engrenagem para abrir o menu **Configurações**, em seguida, clique ou toque em **Conexões**.
2. Role até a conexão para a qual você viu a mensagem de erro **Não autorizado**.
3. Ao lado da conexão, clique ou toque no link **Verificar senha** na mensagem sobre a conexão que não está sendo autenticada.
4. Verifique suas credenciais seguindo as instruções que aparecem, retorne para a execução do fluxo com falha e clique ou toque em **Reenviar**.
   
    Agora, ela deve ser executada conforme o esperado.

## <a name="action-configuration"></a>Configuração de ação
Os fluxos também falharão se uma configuração em uma ação do fluxo não funcionar conforme o esperado. Neste caso, a mensagem de erro conterá **Solicitação ruim** ou **Não encontrada**, ou um código de erro **400** ou **404** aparecerá.

A mensagem de erro deve especificar como corrigir a falha. Você precisará clicar ou tocar no botão **Editar**, em seguida, corrigir o problema na definição do fluxo. Salve o fluxo atualizado e clique ou toque em **Reenviar** para tentar executar novamente com a configuração atualizada.

## <a name="other-failures"></a>Outras falhas
Se o código de erro **500** ou **502** aparecer, a falha será temporária ou transitória. Clique ou toque em **Reenviar** para tentar novamente o fluxo.

Se você encontrar algum problema, [pergunte à nossa comunidade](https://go.microsoft.com/fwlink/?LinkID=787467) porque outras pessoas podem ter encontrado um problema semelhante.

