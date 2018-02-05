---
title: Perguntas Frequentes do conector da API | Microsoft Docs
description: "Encontre respostas para perguntas sobre requisitos, gatilhos e outras áreas."
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
ms.date: 09/19/2017
ms.author: astay
ms.openlocfilehash: 1715700fa6a94bb35733865556a2c9be0ba3ce9f
ms.sourcegitcommit: f3236f9f1ec050cda0d9c3e2b9c356132b2a2594
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2018
---
# <a name="api-connector-faq-microsoft-flow"></a>Perguntas Frequentes do conector da API (Microsoft Flow)
## <a name="requirements"></a>Requisitos
**P:** posso criar um conector sem APIs REST? </br>
**R:** Não, para criar um conector, você deve dar suporte a APIs REST de HTTP estáveis para o serviço. 

**P:** Quais ferramentas posso usar para criar um conector? </br>
**R:** O Azure tem recursos e serviços que você pode usar para expor qualquer serviço como uma API, como o Serviço de Aplicativo do Azure para hospedagem, Gerenciamento de API e muito mais.

**P:** Há suporte para quais tipos de autenticação? </br>
**R:** Você pode usar estes padrões de autenticação com suporte:

* [OAuth 2.0](https://oauth.net/2/), incluindo o [Azure Active Directory](https://azure.microsoft.com/develop/identity/) ou serviços específicos, como o Dropbox, o SalesForce e o GitHub
* OAuth 2.0. Genérico
* [Autenticação básica](https://swagger.io/docs/specification/authentication/basic-authentication/)
* [Chave de API](https://swagger.io/docs/specification/authentication/api-keys/)

## <a name="triggers"></a>Gatilhos
**P:** posso criar gatilhos sem webhooks? </br>
**R:** Não, os conectores personalizados para os Aplicativos Lógicos do Azure e o Microsoft Flow dão suporte somente com base em gatilhos baseados em webhook. Se você deseja solicitar outros padrões para implementação, entre em contato com [condevhelp@microsoft.com](mailto:condevhelp@microsoft.com) com mais detalhes sobre a sua API.

## <a name="certification"></a>Certificação
**P**: Não sou um parceiro da Microsoft ou ISV (Fornecedor de Software Independente). Ainda posso criar conectores? </br>
**R**: Sim, você pode registrar esses conectores para uso interno em sua organização, mas se quiser verificar e lançar publicamente um conector, deverá ser proprietário do serviço subjacente ou dos direitos explícitos presentes para usar a API.

## <a name="other"></a>Outros
**P:** minhas APIs usam um host dinâmico. Como fazer para implementá-los com o OpenAPI? </br>
**R:** Os conectores personalizados não oferecem suporte a hosts dinâmicos. Em vez disso, use um host estático para fins de testes e desenvolvimento. Se você deseja certificar seu conector, pergunte ao seu contato da Microsoft sobre a implementação dinâmica.

**P:** você oferece suporte à Coleção Postman V2? </br>
**R:** Não, somente o Postman Collection V1 tem suporte no momento.

**P:** você oferece suporte ao OpenAPI 3.0? </br>
**R:** Não, somente a OpenAPI 2.0 tem suporte no momento.

