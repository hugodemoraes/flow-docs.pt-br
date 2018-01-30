---
title: "Visão geral do conector da API | Microsoft Docs"
description: "Os proprietários de serviços de ISVs e SaaS podem criar conectores e tê-los certificados pela Microsoft."
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
ms.openlocfilehash: 62f8f8d0af72292a61324d75bd46f53d559b46a3
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="api-connector-overview-microsoft-flow"></a>Visão geral do conector da API (Microsoft Flow)
Um **conector da API** é um componente, baseado no OpenAPI (Swagger), de uma API REST que permite ao serviço subjacente comunicar-se com o [Microsoft Flow](https://flow.microsoft.com), [PowerApps](https://powerapps.microsoft.com), e [Aplicativos Lógicos](https://docs.microsoft.com/azure/logic-apps/). Ele fornece uma maneira dos usuários se conectarem às suas contas e utilizarem um conjunto de **gatilhos** e **ações** predefinidos para criar seus aplicativos e fluxos de trabalho.

Como um **fornecedor de software independente (ISV)** ou **proprietário do serviço SaaS**, você pode criar conectores para habilitar uma ampla variedade de cenários comerciais e de produtividade para seus usuários. Um conector ajuda a ir além de um conjunto definido de integrações e aumentar o alcance, a detectabilidade e uso do serviço.

## <a name="requirements"></a>Requisitos
Para criar e enviar um conector, o serviço deve atender aos seguintes requisitos:

* Cenário de usuário comercial que se ajusta bem com o Microsoft Flow, PowerApps e Aplicativos Lógicos
* Serviço publicamente disponível com APIs REST estáveis

## <a name="build-your-connector"></a>Criar seu conector
A primeira etapa para criar um Conector da API é criar um conector personalizado totalmente funcional. Um conector personalizado opera exatamente como um conector da API, mas é limitado em disponibilidade para o autor e usuários específicos dentro do locatário do autor.

O processo para criar um conector envolve várias etapas:

![Etapas de criação do conector da API](./media/api-connectors-overview/authoring-steps.png)

[Saiba mais](api-connector-dev.md) sobre como desenvolver um conector da API.

## <a name="submit-for-certification"></a>Enviar para certificação
Depois que você ter criado um conector, poderá enviá-lo para a certificação. Como parte de nosso processo de certificação de terceiros, a Microsoft examina o conector antes da publicação.

Esse processo valida a funcionalidade de seu conector no Microsoft Flow e no PowerApps, e verifica a conformidade técnica e do conteúdo.

[Saiba mais](api-connector-submission.md) sobre o processo para enviar seu conector para a certificação e publicação.

## <a name="get-support"></a>Obter suporte
Para obter suporte de integração e desenvolvimento, envie um email para [condevhelp@microsoft.com ](mailto:condevhelp@microsoft.com). Essa conta é ativamente monitorada e gerenciada. As consultas do desenvolvedor e incidentes rapidamente serão encaminhados para a equipe apropriada.

