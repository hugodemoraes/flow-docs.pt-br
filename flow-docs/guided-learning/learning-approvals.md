---
title: "Solicitações de Aprovação com o Microsoft Flow | Microsoft Docs"
description: "Saiba como usar o Microsoft Flow para gerenciar um fluxo de trabalho de aprovação."
services: 
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: 
tags: 
featuredvideoid: o-pgEBW3fOI
courseduration: 14m
ms.service: flow
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/22/2016
ms.author: deonhe
ms.openlocfilehash: 049b713ed653ab5555e5f48f63e46cce7f3207ee
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="approval-requests"></a>Solicitações de aprovação
Além de ajudá-lo a **receber notificações**, **copiar arquivos** e **coletar dados**, o Microsoft Flow também pode ajudá-lo **simplificar os processos de aprovação**.

## <a name="vacation-scenario"></a>Cenário de férias
Vamos imaginar que você seja o **gerente** de uma equipe e peça a seus funcionários para criarem **solicitações de férias** em uma **lista do SharePoint**. Agora, você deseja compilar um **processo de aprovação** nesses itens da lista para que as novas solicitações de férias sejam **processadas rapidamente** e o solicitante seja **notificado automaticamente**.  

## <a name="sharepoint-and-microsoft-flow"></a>SharePoint e Microsoft Flow
O **SharePoint** tem um Microsoft Flow **interno**.  Na **lista do SharePoint**, clique na lista suspensa **Fluxo**, em seguida, em **Criar um fluxo**.

![Criar fluxo](./media/learning-approvals/new-flow.png)   

No **menu à direita**, procure um **modelo** como este.

![Modelo de Aprovação](./media/learning-approvals/approval-template.png)

## <a name="using-the-template"></a>Usando o modelo
O gatilho do **SharePoint** no modelo vem **preenchido previamente** com as informações da lista.  Tudo o que você precisa fazer é adicionar um **endereço de email** para o **aprovador**.  Observe que ele **não altera o item original do SharePoint**.  Para tanto, precisaremos adicionar a ação **SharePoint - Atualizar item**.

![Atualizar item](./media/learning-approvals/update-item.png)

E se **não houver nenhuma** ramificação de *Enviar emailScope*?  Por padrão, ela não faz nada.  Talvez você queira adicionar uma ação para enviar ao autor da solicitação uma mensagem informando que a solicitação foi rejeitada. 

![Se nenhuma](./media/learning-approvals/if-no.png)

## <a name="next-lesson"></a>Próxima lição
Agora, iremos examinar o que aprendemos nesta seção.

