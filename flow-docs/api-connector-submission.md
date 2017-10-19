---
title: "Enviar para certificação como um Conector de API | Microsoft Docs"
description: "Ao certificar um conector, ele fica disponível para todos os usuários do Microsoft Flow, PowerApps e Aplicativos Lógicos."
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
ms.openlocfilehash: 7eb357458161ba398864604bfe8912636ddc4d39
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="submit-your-connectors-for-microsoft-certification"></a>Envie seus conectores para certificação da Microsoft
Para disponibilizar publicamente os conectores personalizados para todos os usuários no Microsoft Flow, os Aplicativos Lógicos do Azure e os Microsoft PowerApps, envie seu conector à Microsoft para revisão, validação e aprovação para publicação. 

## <a name="certification-criteria"></a>Critérios de certificação
| Recurso | Detalhes | Necessários ou recomendados |
| --- | --- | --- |
| Aplicativo de Software-como um Serviço (SaaS) |Conheça um cenário de usuário que se ajuste bem a Aplicativos Lógicos, Fluxo e PowerApps. |Necessário |
| Tipo de Autenticação |Sua API deve oferecer suporte ao OAuth2, Chave de API ou Autenticação Básica. |Necessário |
| Suporte |Você deve fornecer um contato de suporte para que os clientes possam obter ajuda. |Necessário |
| Disponibilidade e tempo de atividade |Seu aplicativo tem pelo menos 99,9% de tempo de atividade. |Recomendado |
|  | | |

Além disso, se você não for um parceiro da Microsoft ou um ISV (fornecedor de software independente) e se quiser certificar e lançar publicamente um conector, deverá ser proprietário do serviço subjacente ou dos direitos explícitos presentes para usar a API.

Para obter a certificação, o conector será revisado em duas fases: 

1. Validação de Funcionalidade
   
    O conector personalizado está avaliado para:
   
   * Os erros de swagger ou JSON inválidos na seção Definição do assistente de conector personalizado
   * Erros de validação de esquema e de tempo de execução na seção Testes do assistente
     
     Consequentemente, cada operação é totalmente testada no Flow, nos Aplicativos Lógicos e no PowerApps para todos os erros no lado do cliente.
2. Validação de Conteúdo
   
    Um conector bem escrito usa nomes e descrições amigáveis para cada entidade. Avaliamos o swagger para garantir que cada operação, parâmetro de entrada e atributo de resposta contenha:
   
   * [Resumo](../logic-apps/custom-connector-openapi-extensions.md#summary)
   * [Descrição](../logic-apps/custom-connector-openapi-extensions.md#description)
   * [Informações de visibilidade](../logic-apps/custom-connector-openapi-extensions.md#visibility)

## <a name="nominate-and-submit-your-connector-to-microsoft-for-certification"></a>Nomear e enviar seu conector à Microsoft para certificação
Para se candidatar à certificação, siga estas etapas:

1. **Indicar**
   
   1. [Enviar sua nomeação](https://go.microsoft.com/fwlink/?linkid=848754).
   2. Assine o Contrato de Parceiro e o Contrato de Confidencialidade mútuo recebido. 
      A Microsoft exige esses contratos assinados antes de continuar. 
      Então, podemos verificar se o seu conector atende aos critérios de certificação. 
   3. Se o conector for aprovado, a Microsoft notificará você com instruções para integração.
2. **Revisão**
   
   1. Envie as informações a seguir ao seu contato de indicação para revisão:
      
      * O arquivo OpenAPI que descreve sua API
      * O arquivo de ícone (.png ou .jpg) que representa seu conector. (O ícone deve ter um logotipo de aproximadamente 160 pixels em um quadrado de 230 pixels. Um logotipo branco em um plano de fundo colorido é preferencial).
      * Cor da marca do seu ícone no formato hexadecimal, que deve corresponder ao plano de fundo colorido no arquivo de ícone
      * Uma conta de teste para validação
      * Um contato de suporte
   2. Se for necessário obter mais informações, nós entraremos em contato.
3. **Publicar**
   
    Depois de validar o conteúdo e a funcionalidade e o conteúdo do conector, preparamos o conector para implantação entre todos os produtos e regiões. Normalmente, o processo de certificação e de implantação demora cerca de três semanas.
   
    Por padrão, todos os conectores são publicados como "premium". 
    Se você tiver criado seu aplicativo com o Azure, poderá se candidatar à listagem do seu conector como um conector "padrão" disponível para todos os usuários com planos do Office 365 Enterprise. 
    Para obter mais detalhes, pergunte ao seu contato de indicação.

