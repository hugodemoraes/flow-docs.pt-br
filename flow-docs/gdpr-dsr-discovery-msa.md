---
title: Solicitações de descoberta de titular dos dados do RGPD do Microsoft Flow para contas da Microsoft (MSA) | Microsoft Docs
description: Saiba como usar o Microsoft Flow para responder às solicitações de descoberta de titular dos dados do RGPD para contas da Microsoft.
services: ''
suite: flow
documentationcenter: na
author: KentWeareMSFT
manager: KFile
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 5/16/2018
ms.author: keweare
search.app:
- Flow
- Powerplatform
search.audienceType:
- admin
ms.openlocfilehash: 9a7031780ed6582d9f881571c3d07ce8aece074d
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44690711"
---
# <a name="respond-to-gdpr-data-subject-discovery-requests"></a>Responder às solicitações de descoberta de titular dos dados do RGPD 

A primeira etapa para responder a uma solicitação de DSR é localizar os dados pessoais que são assunto da solicitação.
Aqui está um resumo dos recursos do Microsoft Flow que contêm dados pessoais de um usuário que se autentica com sua conta da Microsoft (MSA).

|Recurso|Finalidade|
|-----|-----|
|Histórico de execuções|Fornece o histórico de execução de cada fluxo nos últimos 28 dias. Esses dados incluem a hora de início, a hora de término, o status e todas as informações de entrada/saída de cada execução de fluxo. Saiba mais sobre o [histórico de execução de fluxo](https://flow.microsoft.com/blog/download-history-recurrence/).|
|Feed de atividades| Fornece uma recapitulação das atividades de cada fluxo, incluindo as notificações, as falhas e os status de execução.|
|Fluxos|A lógica de fluxo de trabalho de um [fluxo](https://docs.microsoft.com/flow/get-started-logic-flow).|
|Conexões|Usadas pelos conectores e permitem a conectividade com APIs, sistemas, bancos de dados e muito mais. Saiba mais sobre [conexões](add-manage-connections.md).|

