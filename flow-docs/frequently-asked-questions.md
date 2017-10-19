---
title: Perguntas frequentes | Microsoft Docs
description: "Respostas a várias perguntas comuns sobre o Microsoft Flow"
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
ms.date: 03/15/2017
ms.author: stepsic
ms.openlocfilehash: 5b8deda5f22bcc1fa7cfa37a0d4244f26c2004a4
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="frequently-asked-questions"></a>Perguntas frequentes
## <a name="audience-and-strategy"></a>Público e estratégia
### <a name="what-is-microsoft-flow"></a>O que é Microsoft Flow?
O Microsoft Flow é um serviço baseado em nuvem que torna mais prático e simples para os usuários da linha de negócios criar fluxos de trabalho que automatizam os processos e tarefas de negócios demorados entre os aplicativos e serviços.

### <a name="who-is-the-intended-audience-for-microsoft-flow"></a>Quem é o público-alvo do Microsoft Flow?
O Microsoft Flow tem dois tipos de público distintos:

* Linha de negócios "Cidadãos integradores" em empresas que são parceiras da TI para aproximar a responsabilidade das soluções de negócios para o negócio em si.
* Tomadores de decisão da TI que desejam capacitar os parceiros da linha de negócios para criar suas próprias soluções para que os profissionais de TI e especialistas de integração possam focar seus conhecimentos nas ferramentas de integração mais avançadas, como os Aplicativos Lógicos do Azure.

### <a name="how-do-microsoft-flow-and-logic-apps-relate-to-each-other"></a>Como o Microsoft Flow e os Aplicativos Lógicos se relacionam entre si?
O Microsoft Flow fornece recursos que ajudam os usuários da linha de negócios a criar fluxos de trabalho automatizados. Os Aplicativos Lógicos são um serviço do Azure que fornece todos os ótimos recursos do Microsoft Flow, além de recursos adicionais, como a integração com o Azure Resource Manager e o Portal do Azure, PowerShell, CLI xPlat, Visual Studio e conectores extras. [Saiba mais sobre os Aplicativos Lógicos](https://azure.microsoft.com/services/app-service/logic/).

### <a name="how-does-microsoft-flow-fit-in-microsofts-overall-business-application-platform-strategy"></a>Como o Microsoft Flow se encaixa na estratégia de plataforma do aplicativo de negócios geral da Microsoft?
O Microsoft Flow faz parte de uma plataforma de aplicativos de negócios poderosa e adaptável que inclui o PowerApps, Common Data Service, Dynamics 365 e Office 365. Essa plataforma permite que nossos clientes, parceiros e parceiros ISV criem soluções desenvolvidas especificamente para suas próprias empresas, setor, funções ou até mesmo regiões específicas. Os usuários da linha de negócios, que entendem melhor suas necessidades negócios, podem agora analisar, compor e simplificar facilmente os processos e dados. Os desenvolvedores profissionais podem estender facilmente a automação, análise e linha de negócios dos aplicativos para aproveitar os serviços do Azure, como as Funções, Serviço de Aplicativo e Aplicativos Lógicos. Os conectores da API, gateways e Common Data Service da Microsoft tornam possível obter mais valor dos dados ou serviços já em uso, na nuvem ou no local.

## <a name="functionality"></a>Funcionalidade
### <a name="what-do-i-need-to-use-microsoft-flow"></a>O que é necessário para usar o Microsoft Flow?
Para usar o Microsoft Flow, tudo o que você precisa é de um navegador da Web e um endereço de email.

### <a name="what-browsers-does-microsoft-flow-support"></a>O Microsoft Flow dá suporte a quais navegadores?
O Microsoft Flow dá suporte ao Microsoft Edge e às versões atuais do Chrome e Safari.

### <a name="which-email-addresses-are-supported"></a>Quais endereços de email têm suporte?
O Microsoft Flow oferece suporte aos endereços de email terminando com qualquer coisa, exceto .gov e .mil.  

### <a name="is-microsoft-flow-available-on-premises"></a>O Microsoft Flow está disponível localmente?
O Microsoft Flow é apenas um serviço de nuvem público. No entanto, você pode conectar seguramente seus próprios serviços locais por meio do gateway de dados local.

### <a name="what-services-can-microsoft-flow-connect-to"></a>A quais serviços o Microsoft Flow pode se conectar?
O Microsoft Flow conecta a mais de 100 fontes de dados prontas para uso e estamos adicionando mais o tempo todo. Alguns exemplos de fontes de dados e serviços incluem o seguinte:

* SharePoint
* Dynamics 365
* OneDrive
* OneDrive for Business
* Google Drive
* Planilhas Google
* Trello
* Twitter
* Box
* Facebook
* SalesForce.com
* Mailchimp
* APIs de cliente

Você pode encontrar uma lista completa dos conectores disponíveis [aqui](https://go.microsoft.com/fwlink/?LinkId=832211).

Você pode acessar as fontes de dados em sua própria infraestrutura de TI por meio do [gateway de dados local](gateway-manage.md).

### <a name="what-are-templates"></a>O que são modelos?
Modelos são fluxos previamente criados para cenários comuns e populares. O uso de um modelo exige apenas que você tenha acesso aos serviços do modelo e preencha as configurações necessárias.

### <a name="what-data-sources-will-i-be-able-to-connect-to"></a>Com quais fontes de dados poderei me conectar?
Você pode se conectar a mais de 100 serviços padrão da Microsoft e de terceiros, como o Office 365, Twitter, SharePoint, OneDrive, Dropbox, SQL e muito mais. Você também pode se conectar aos serviços premium, como Salesforce e o Serviço de Dados Comum para PowerApps.

### <a name="how-do-i-connect-to-a-rest-api-in-my-flow"></a>Como me conectar a uma API REST em meu fluxo?
Você pode se conectar a qualquer API REST que use JSON e ofereça suporte a pelo menos um dos mais de 10 métodos de autenticação ao criar [um conector personalizado](register-custom-api.md).

### <a name="how-do-i-connect-to-sql-server-and-other-on-premises-data-sources"></a>Como me conectar ao SQL Server e outras fontes de dados locais?
Você pode se conectar aos serviços na rede local usando o [gateway de dados locais](gateway-manage.md).

### <a name="can-i-share-the-flows-i-create"></a>Posso compartilhar os fluxos que eu criar?
Você pode compartilhar fluxos em qualquer uma das seguintes maneiras:

* Você pode adicionar colegas de trabalho ou grupos em sua organização como proprietários em seus fluxos, de forma que eles também possam editar e gerenciar o fluxo.
* Para fluxos que podem ser executados manualmente, você também pode conceder a outras pessoas ou grupos em sua organização a permissão para executar o fluxo.

### <a name="how-many-flows-can-i-have"></a>Quantos fluxos posso ter?
O Microsoft Flow vem com até 50 fluxos. Se precisar de mais, você pode solicitar.

### <a name="where-do-i-get-started-with-microsoft-flow"></a>Onde começo com o Microsoft Flow?
Comece com os seguintes recursos:

* [Blog](https://flow.microsoft.com)
* [Canal do YouTube](https://youtube.com/playlist?list=PL8nfc9haGeb55I9wL9QnWyHp3ctU2_ThF)
* [Tópico](getting-started.md)
* [Comunidade](http://powerusers.microsoft.com)

### <a name="what-operating-systems-does-the-mobile-app-for-microsoft-flow-support"></a>A quais sistemas operacionais o aplicativo móvel do Microsoft Flow oferece suporte?
O aplicativo móvel Microsoft Flow está disponível para [Android](https://aka.ms/flowmobiledocsandroid), [iOS](https://aka.ms/flowmobiledocsios), ou [Windows Phone](https://aka.ms/flowmobilewindows).

### <a name="what-regions-and-languages-does-microsoft-flow-support"></a>Para quais regiões e idiomas o Microsoft Flow oferece suporte?
O Microsoft Flow está disponível em 42 idiomas e [seis regiões](regions-overview.md).

### <a name="how-does-microsoft-flow-compare-to-sharepoint-designer-2013"></a>Como o Microsoft Flow se compara ao SharePoint Designer 2013?
O Microsoft Flow é o sucessor do SharePoint Designer para muitos cenários comerciais comuns, como aprovações, análise de documentos e integração/remoção. Será a ferramenta padrão para criar a automação de negócios no SharePoint no futuro.

### <a name="how-does-microsoft-flow-ensure-that-corporate-data-isnt-accidentally-released-to-social-media-services"></a>Como o Microsoft Flow garante que os dados corporativos não foram acidentalmente liberados para serviços de mídia social?
Os administradores podem criar [políticas de prevenção contra perda de dados](prevent-data-loss.md) para garantir que somente os serviços sancionados são usados no Microsoft Flow.

## <a name="licensing"></a>Licenciamento
### <a name="will-microsoft-flow-still-have-a-free-or-trial-option"></a>O Microsoft Flow ainda tem uma opção gratuita ou de avaliação?
Sim. Você pode usar nossa oferta gratuita, que tem direitos do usuário limitados, ou pode inscrever-se para ter uma avaliação gratuita de 90 dias do Microsoft Flow. É possível ativar sua assinatura a qualquer momento durante a avaliação.

### <a name="what-pricing-plans-do-you-offer"></a>Quais planos de preços você oferece?
O Microsoft Flow oferece níveis de serviços pagos e gratuitos. [Saiba mais sobre preços](billing-questions.md).

