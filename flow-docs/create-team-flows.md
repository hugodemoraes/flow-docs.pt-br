---
title: Saiba como adicionar outros proprietários a um fluxo e criar fluxos de equipe | Microsoft Docs
description: O Microsoft Flow facilita a automatização de tarefas repetitivas. Você pode adicionar usuários ou grupos como proprietários e colaborar com eles para criar e gerenciar fluxos.
services: ''
suite: flow
documentationcenter: na
author: msftman
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/21/2017
ms.author: deonhe
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 238ef8eac80d3259981cb11cc21e3b05eb83e0ec
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44689722"
---
# <a name="create-team-flows"></a>Criar fluxos de equipe
Crie um fluxo de equipe ao adicionar outras pessoas na sua organização como proprietários. Todos os proprietários de um fluxo de equipe podem executar essas ações:

* Exiba o histórico do fluxo (ou seja, cada execução).
* Gerencie as propriedades do fluxo (por exemplo, inicie ou interrompa o fluxo, adicione proprietários ou atualize as credenciais para uma conexão).
* Edite a definição do fluxo (por exemplo, adicione ou remova uma ação ou condição).
* Adicione e remova outros proprietários (mas não o criador do fluxo).
* Exclua o fluxo.

Se você for o criador ou proprietário de um fluxo, encontra listado na guia **Fluxos da equipe** no [Microsoft Flow](https://flow.microsoft.com).

![guia de fluxos de equipe](./media/create-team-flows/addowner5.png)

> [!NOTE]
> As conexões compartilhadas podem ser usadas **somente** no fluxo no qual elas foram criadas.
> 
> 

Os proprietários podem usar os serviços em um fluxo, mas não podem modificar as credenciais para uma conexão que outro proprietário criou.

## <a name="prerequisites"></a>Pré-requisitos
Você deve ter um [plano pago do Microsoft Flow](https://flow.microsoft.com/pricing/) para criar um fluxo de equipe. Além disso, você deve ser o criador ou o proprietário para adicionar ou remover os proprietários de um fluxo de equipe.

## <a name="create-a-team-flow"></a>Criar um fluxo de equipe
Siga estas etapas para criar um fluxo de equipe ou adicionar mais proprietários a um fluxo de equipe.

1. Entre no [Microsoft Flow](https://flow.microsoft.com) e, em seguida, selecione **Meus fluxos**.
2. Selecione o ícone de pessoas para o fluxo que você deseja modificar:
   
    ![ícone de equipe](./media/create-team-flows/addowner1.png)
3. Insira o nome, endereço de email ou o nome do grupo da pessoa ou grupo que você deseja adicionar como proprietário:
   
    ![pesquise o usuário](./media/create-team-flows/addowner2.png)
4. Na lista exibida, selecione o usuário que você deseja tornar proprietário:
   
    ![selecione o usuário](./media/create-team-flows/addowner3.png)
   
     O usuário ou grupo que selecionou se torna proprietário do fluxo:
   
    ![novo proprietário](./media/create-team-flows/addowner4.png)
   
     Parabéns &mdash; seu fluxo de equipe foi criado!

##<a name="add-a-list-as-a-co-owner"></a>Adicionar uma lista como um coproprietário

Você pode adicionar listas do SharePoint como coproprietários a um fluxo para que todos com acesso de edição à lista obtenham automaticamente acesso de edição ao fluxo. Depois que o fluxo for compartilhado, você poderá distribuir um link para ele.

## <a name="remove-an-owner"></a>Remover um proprietário
> [!IMPORTANT]
> Quando remove um proprietário cujas credenciais são usadas nos serviços do Microsoft Flow, deve atualizar as credenciais para essas conexões para que o fluxo continue a executar adequamente.
> 
> 

1. Selecione o ícone de pessoas para o fluxo que você deseja modificar:
   
    ![ícone de selecionar pessoas](./media/create-team-flows/removeowner1.png)
2. Selecione o ícone **Excluir** do proprietário que você deseja remover:
   
    ![selecionar exclusão](./media/create-team-flows/removeowner2.png)
3. Na caixa de diálogo de confirmação, selecione **Remover esse proprietário**:
   
    ![confirmar remoção](./media/create-team-flows/removeowner3.png)
4. Parabéns &mdash;, o usuário ou grupo que você removeu não está mais listado como proprietário do fluxo:
   
    ![usuário removido](./media/create-team-flows/removeowner4.png)

## <a name="embedded-and-other-connections"></a>Conexões inseridas e outras
Conexões usadas em um fluxo se enquadram em duas categorias:

* **Incorporada** &mdash; Essas conexões são usadas no fluxo.
* **Outras** &mdash; Essas conexões foram definidas para um fluxo, mas não são usadas nele.

Se parar de usar uma conexão em um fluxo, essa conexão aparece na lista de **Outras** conexões, onde permanecem até que um proprietário a inclua no fluxo novamente.

A lista de conexões aparece na lista de proprietários nas propriedades de um fluxo:

![conexões inseridas](./media/create-team-flows/embeddedconnections.png)

