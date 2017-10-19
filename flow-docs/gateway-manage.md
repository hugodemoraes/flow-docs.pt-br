---
title: Saiba como gerenciar os gateways de dados locais | Microsoft Docs
description: Exibir e instalar um gateway de dados local no Microsoft Flow
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
ms.date: 02/15/2017
ms.author: deonhe
ms.openlocfilehash: 41f5d40ca2ad5fcce3a7967beef7104dd532b1d8
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="manage-an-on-premises-data-gateway-in-microsoft-flow"></a>Gerenciar um gateway de dados locais no Microsoft Flow
Instale e gerencie um gateway de dados local para integrar com segurança uma variedade de aplicativos baseados em nuvem com dados e aplicativos locais por meio do Microsoft Flow.

Com um gateway, você pode conectar aos dados locais através dessas conexões:

* SharePoint
* SQL Server
* Oracle
* Informix
* Filesystem
* DB2

> [!IMPORTANT]
> Os gateways de dados do Microsoft SharePoint oferecem suporte a tráfego HTTP, mas não ao tráfego HTTPS.
> 
> 

## <a name="prerequisites"></a>Pré-requisitos
* O nome de usuário e senha usados para se [inscrever](sign-up-sign-in.md) no Microsoft Flow.
* Permissões administrativas em um gateway.
  
  Você tem essas permissões por padrão para cada gateway que instala e um administrador de outro gateway pode lhe conceder essas permissões para esse gateway.
* Uma licença que oferece suporte a gateways. Para obter mais informações, confira a seção “Conectividade” da [página de preços](https://flow.microsoft.com/pricing/).
* Crie um gateway e uma conexão local em seu [ambiente padrão](environments-overview-maker.md).

## <a name="view-your-gateways"></a>Exibir seus gateways
No canto superior direito do [site do Microsoft Flow](https://flow.microsoft.com), clique ou toque no ícone de engrenagem e clique ou toque em **Gateways**.

![Gateway em gerenciamento][1]

**Observação**: se você criou ou recebeu acesso a um gateway no PowerApps, esse gateway aparecerá na lista **Meus gateways** no Microsoft Flow.

## <a name="install-a-gateway"></a>Instalar um gateway
1. Faça download do [assistente de instalação do gateway](http://go.microsoft.com/fwlink/?LinkID=820580&clcid=0x409).
   
    Também é possível baixar esse assistente clicando ou tocando no ícone de engrenagem no canto superior direito do [site do Microsoft Flow](https://flow.microsoft.com), clicando ou tocando em **Gateways** e clicando ou tocando em **Criar gateway**.
   
    ![Instalação do gateway][2]
2. Execute o assistente, fornecendo as mesmas credenciais com as quais você entrou no Microsoft Flow.
   
    Depois de registrar e configurar o gateway com êxito, ele aparecerá na lista **Meus gateways** no Microsoft Flow.

Para saber mais, consulte [Entender os gateways](gateway-reference.md).

<!-- Image references -->
[1]: ./media/manage-gateway/view-gateways.png
[2]: ./media/manage-gateway/list-gateways.png
