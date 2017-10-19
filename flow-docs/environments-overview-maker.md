---
title: Alternar ambientes ao criar um Microsoft Flow | Microsoft Docs
description: "Como um criador utiliza ambientes diferentes durante a criação de um Microsoft Flow"
services: 
suite: flow
documentationcenter: na
author: sunaysv
manager: anneta
editor: 
tags: 
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/27/2016
ms.author: sunayv
ms.openlocfilehash: bcbb566c20291da14881d771c538dd89689b6b1d
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="choosing-an-environment"></a>Escolhendo um ambiente
Com o Microsoft Flow, é possível trabalhar em ambientes diferentes e trocar facilmente entre eles. O escopo deste artigo abordará os seguintes tópicos no ambiente:

* Histórico do que os ambientes fornecem
* Alternância de ambientes
* Como criar um fluxo no ambiente certo

## <a name="environments-overview"></a>Visão geral de ambientes
Os ambientes fornecem um limite de isolamento para seus fluxos, conexões, gateways e outros recursos. Ao criar um fluxo, é possível escolher em qual ambiente hospedá-lo e os recursos usados por este fluxo. Você pode usar diferentes ambientes em cenários diferentes.

Alguns exemplos:

* Você está criando um fluxo que usa uma conexão com o Serviço de Dados Comuns da Microsoft. Nesse cenário, o fluxo e o Serviço de Dados Comuns residem no mesmo ambiente. Isso garante que todos os dados estejam isolados dentro desse ambiente (limite de isolamento).
* Você está criando um fluxo para seu departamento de Recursos Humanos. Você deseja garantir que somente usuários no departamento de Recursos Humanos tenham acesso ao fluxo. Por exemplo, você não quer que seu Grupo de vendas utilize o fluxo. Nesse cenário, é possível usar um ambiente separado, no qual somente os usuários de RH têm permissão para hospedar o fluxo e qualquer recurso que utilize o fluxo, incluindo gateways ou conexões.
* Na Europa, há usuários que utilizam um fluxo para mostrar dados do SharePoint. Nesse cenário, crie um ambiente na Europa que hospeda o fluxo e a conexão do SharePoint. Esse ambiente da Europa oferece o melhor desempenho aos usuários europeus, já que todos os recursos são locais para Europa (localidade dos dados).

Os ambientes são criados pelos administradores do Microsoft Flow. Esses administradores também controlam quem tem acesso a ambientes diferentes.

Este tópico mostra como navegar entre ambientes diferentes. Para obter detalhes sobre como criá-los e gerenciá-los, consulte [administrar ambientes](environments-overview-admin.md).

## <a name="switching-environments"></a>Alternância de ambientes
O Microsoft Flow facilita a alternância entre ambientes. Ao alternar, você está vendo todos os itens nesse ambiente específico. Você não está vendo os itens em qualquer outro ambiente.

Veja um exemplo.

Criar um fluxo chamado *NewEmployee* no ambiente *Recursos Humanos*. Em [flow.microsoft.com](http://flow.microsoft.com), abra o ambiente de *Vendas*. O fluxo *NewEmployee* não está listado. Para ver o fluxo *NewEmployee* fluxo, abra o ambiente *Recursos Humanos*. Lembre-se de que isso se aplica a qualquer item que você criar no ambiente, incluindo conexões, gateways, PowerApps e muito mais.

1. Abra [flow.microsoft.com](http://flow.microsoft.com).
2. No canto superior direito, você verá seu nome e o ambiente em que está:  
   ![](./media/environments-overview-maker/default-environment.png)
   
    Na imagem, observe as notificações. Essas notificações são específicas ao fluxo nesse ambiente padrão.
3. Selecione seu nome. Na lista suspensa, todos os ambientes disponíveis são listados. Seu ambiente atual é verificado:  
   ![](./media/environments-overview-maker/all-environments.png)
4. Para alternar para outro ambiente, selecione o ambiente na lista:  
   ![](./media/environments-overview-maker/select-europe.png)
5. O Microsoft Flow alterna automaticamente para o novo ambiente:  
   ![](./media/environments-overview-maker/europe-environment.png)
   
    Na imagem, observe que não há notificações. O novo ambiente Europa não tem notificações.

## <a name="create-flows-in-the-right-environment"></a>Criar fluxos no ambiente certo
Antes de criar um fluxo, verifique se selecionou o ambiente desejado para o fluxo. Caso contrário, será necessário excluir e recriar o fluxo no ambiente correto.

Considere os seguintes fatores ao escolher o ambiente para criar os fluxos:

* Os gateways são criados no ambiente Padrão. Os gateways não podem ser criados em outros ambientes, então se quiser conectar-se a dados locais, você precisará usar o ambiente Padrão.
* Os fluxos podem usar somente conexões e outros recursos no mesmo ambiente. Não podem usar recursos em outro ambiente. Por exemplo, você está criando um fluxo que usa um conector personalizado. Esse conector personalizado deve estar no mesmo ambiente que o fluxo.
* O banco de dados do Serviço de Dados Comuns da Microsoft está sempre ligado a exatamente um ambiente. Isso significa que, caso queira trabalhar com os dados do Serviço de Dados Comuns, você deverá selecionar o mesmo ambiente que o banco de dados está.
* Você verá todos os ambientes nos quais é possível editar recursos. Porém, isso não significa que você pode criar novos recursos em todos os ambientes. Deste modo, pode ser que você não consiga criar novos fluxos em alguns ambientes. Você precisa solicitar ao administrador para adicioná-lo como um **Criador** a esse ambiente, ou escolha um ambiente diferente para criar o fluxo (sempre será possível criar fluxos no ambiente padrão).

## <a name="what-you-did"></a>O que você fez
Usando essas etapas, você troca entre ambientes que têm permissões de uso. Agora, vamos começar a criar seus fluxos.

## <a name="next-steps"></a>Próximas etapas
[Criar um fluxo a partir de um modelo](get-started-logic-template.md)  
[Criar um fluxo](get-started-logic-flow.md)  
[Visão geral do ambiente para Administradores](environments-overview-admin.md)

