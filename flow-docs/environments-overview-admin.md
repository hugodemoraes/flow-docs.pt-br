---
title: "Visão geral do ambiente para Administradores | Microsoft Docs"
description: Usar, criar e gerenciar ambientes no Microsoft Flow
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
ms.openlocfilehash: f1c50e5d16d5b9fbbd3e6db3128947b0554e9a85
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="using-environments-within-microsoft-flow"></a>Uso de ambientes no Microsoft Flow
## <a name="benefits"></a>Benefícios
Os ambientes são um novo recurso no Microsoft Flow e têm os seguintes benefícios: 

* **Localidade dos dados**: ambientes podem ser criados em diferentes regiões e são associados a esse local geográfico. Quando você cria um fluxo em um ambiente, esse fluxo é roteado para todos os datacenters no local geográfico. Isso também fornece um benefício de desempenho. 
  
    Se os usuários estiverem na Europa, crie e use o ambiente na região da Europa. Se os usuários estiverem nos Estados Unidos, crie e use o ambiente na região dos EUA. 
  
    Se você excluir o ambiente, todos os fluxos dentro desse ambiente também são excluídos. Isso se aplica a qualquer item que você criar no ambiente, incluindo conexões, gateways, PowerApps e muito mais.
* **Prevenção de perda de dados**: como um administrador, você não quer fluxos que recebem dados de um local interno (como *OneDrive for Business*) e, em seguida, postem dados publicamente (como *Twitter*). Com a prevenção de perda de dados, você controla quais serviços podem ser usados em uma política de somente dados de negócios. 
  
    Por exemplo, você pode adicionar serviços do *SharePoint* e do *OneDrive for Business* a uma política de somente dados de negócios. Qualquer fluxo criado nesse ambiente pode usar esses serviços do *SharePoint* e do *OneDrive for Business*. Apenas os serviços que você adicionar estarão disponíveis. 
  
  > [!NOTE]
  > A prevenção de perda de dados está disponível com alguns SKUs de licença, incluindo a licença P2. 
  > 
  > 
* **Limite de isolamento para todos os recursos**: quaisquer fluxos, gateways, conexões, conectores personalizados, entre outros, residem neste ambiente específico. Eles não existem em qualquer outro ambiente. 
* **Common Data Service**: digamos que você queira criar um fluxo que insere dados em algum lugar. As opções são:
  
  * Inserir dados em um arquivo do Excel e armazenar o arquivo do Excel em uma conta de armazenamento de nuvem, como o OneDrive.
  * Criar seu próprio Banco de Dados SQL e armazenar seus dados nele.
  * Use o Common Data Service para armazenar seus dados.
    
    Cada ambiente pode ter zero ou um armazenamento de banco de dados para seus fluxos no Common Data Service. O acesso ao Common Data Service depende da licença que você compra. Não está incluído na Licença gratuita.

## <a name="limitations"></a>Limitações
Embora ambientes ofereçam muitos benefícios, eles também apresentam novas limitações. O fato de os ambientes serem um limite de isolamento significa que você nunca pode ter recursos que fazem referência a outros recursos *entre* ambientes. Por exemplo, é impossível criar um conector personalizado em um ambiente e criar um fluxo que usa o conector personalizado e um gateway em um ambiente diferente.

Portanto, é importante que os ambientes sejam criados apenas quando necessário. A criação de muitos ambientes dificultará o compartilhamento de recursos entre os usuários da sua organização.

## <a name="use-the-default-environment"></a>Use o ambiente padrão
O ambiente **Padrão** está disponível para cada usuário e é compartilhado por todos os usuários. Cada usuário pode criar fluxos neste ambiente.

> [!TIP]
> Se você for um Usuário de visualização, todos os fluxos existentes residirão no ambiente padrão. Um *Usuário de visualização* é alguém que utilizou o Microsoft Flow antes da liberação para Disponibilidade Geral (GA). 
> 
> 

## <a name="use-the-administrator-center"></a>Como utilizar o centro de administrador
Os administradores usam o centro de administrador para criar ambientes, adicione usuários a esses ambientes e outras tarefas semelhantes. Há duas maneiras de abrir o centro de administrador:

#### <a name="option-1-select-settings"></a>Opção 1: selecionar configurações
1. Entre em [flow.microsoft.com](https://flow.microsoft.com).
2. Selecione a engrenagem Configurações e escolha **Centro do Administrador** na lista:  
   ![Configurações e Portal do Administrador](./media/environments-overview-admin/settings.png)
3. O centro de administrador é exibido.

#### <a name="option-2-open-adminflowmicrosoftcom"></a>Opção 2: abra admin.flow.microsoft.com
Vá até [admin.flow.microsoft.com](https://admin.flow.microsoft.com) e entre com sua conta de trabalho. O centro de administrador é exibido.

## <a name="create-an-environment"></a>Criar um ambiente
1. No [Centro de administração do Microsoft Flow](https://admin.flow.microsoft.com), selecione **Ambientes**. Os ambientes existentes são exibidos:  
   ![](./media/environments-overview-admin/environments-list.png)
2. Selecione **Novo ambiente**. Insira as seguintes informações:
   
   | Propriedade | Descrição |
   | --- | --- |
   | Nome do Ambiente |Insira o nome do seu ambiente, como `Human Resources`, ou `Europe flows`. |
   | Região |Escolha o local para hospedar seu ambiente. Para obter o melhor desempenho, use uma região mais próxima de seus usuários. Por exemplo, se os usuários do Flow são de Londres, escolha a região da Europa. Se os usuários do Flow estão em Nova Iorque, escolha a região dos Estados Unidos. |
3. Selecione **Criar um ambiente**. Seu novo ambiente está listado. 

Em seguida, adicione os usuários no ambiente.

## <a name="manage-your-existing-environments"></a>Gerencie os ambientes existentes
1. No [Centro de administração do Microsoft Flow](https://admin.flow.microsoft.com), selecione **Ambientes**:  
   ![](./media/environments-overview-admin/select-environments.png)  
2. Selecione um ambiente para abrir suas propriedades. 
3. Os **Detalhes** mostram informações adicionais sobre o ambiente, incluindo quem criou o ambiente, sua localização geográfica e outras propriedades:  
   ![](./media/environments-overview-admin/open-environment.png)
4. Selecione **Segurança**. Em **Funções de ambiente**, há duas opções: **Administrador** e **Criador**:  
   
    ![](./media/environments-overview-admin/environment-roles.png)
   
    Um **Criador** pode criar novos recursos em um ambiente, como fluxos, conexões de dados e gateways. 
   
   > [!NOTE]
   > Um usuário não precisa ser um **Criador** para *editar* recursos em um ambiente, apenas para criar *novos* recursos. Cada criador de recurso pode determinar quem pode editar esse recurso e pode conceder permissões de edição para usuários que não são Criadores do ambiente.
   > 
   > 
   
    Um **Administrador** pode criar políticas de prevenção de perda e também concluir tarefas administrativas, como criar ambientes, adicionar usuários a um ambiente e atribuir privilégios de administrador/criador.  
   
   1. Selecione a função **Criador do ambiente** e selecione **Usuários**:  
      ![](./media/environments-overview-admin/add-environment-maker.png)
   2. Insira um nome, endereço de email ou grupo de usuários que você deseja fornecer à função do Criador. Conforme você começa a digitar, o intellisense começa a listar os usuários/grupos que correspondam ao texto. 
   3. Selecione **Salvar** para concluir a adição de usuários. 
5. Em **segurança**, selecione **Funções de Usuário**:  
    ![](./media/environments-overview-admin/security-user-roles.png)
   
    Todas as funções existentes são listadas, inclusive as opções para editar ou excluir a função. 
   
    Selecione **Nova função** para criar uma nova função. 
6. Em **Segurança**, selecione **Conjuntos de Permissões**:  
    ![](./media/environments-overview-admin/security-permission-set.png)
   
    Todas as permissões existentes são listadas, inclusive as opções para editar ou excluir a função. 
   
    Selecione **Novo conjunto de permissões** para criar um novo. 
7. Em **Banco de Dados**, você pode escolher criar um banco de dados para armazenar seus dados. Esse banco de dados faz parte do Common Data Service.

## <a name="commonly-asked-questions"></a>Perguntas frequentes
##### <a name="can-i-migrate-a-microsoft-flow-in-my-us-environment-to-a-europe-environment"></a>Posso migrar um Microsoft Flow em meu ambiente dos EUA para um ambiente da Europa?
Não, os fluxos não podem ser movidos entre ambientes. Recrie o fluxo no ambiente diferente.

##### <a name="which-license-includes-the-common-data-service"></a>Qual licença inclui o Common Data Service?
Somente o Plano 2 do Microsoft PowerApps inclui direitos para criar bancos de dados com o Common Data Service. No entanto, todos os planos pagos (planos 1 e 2 do Microsoft Flow e planos 1 e 2 do Microsoft PowerApps) tem os direitos para usar o Common Data Service.

O [Preço do fluxo](https://flow.microsoft.com/pricing/) pode ajudá-lo a escolher o plano certo para você.  

As [perguntas sobre cobrança](billing-questions.md) também ajudam a percorrer algumas perguntas comuns recebidas. 

##### <a name="can-the-common-data-service-be-used-outside-of-an-environment"></a>O Common Data Service pode ser usado fora de um ambiente?
Não. O Common Data Service requer um ambiente. [Leia mais](common-data-model-intro.md) sobre ele.

##### <a name="what-regions-include-microsoft-flow"></a>Quais regiões estão incluídas no Microsoft Flow?
Microsoft Flow oferece suporte à maioria das regiões que compatíveis com o Office 365, consulte [a visão geral das regiões](regions-overview.md) para obter mais detalhes.

##### <a name="what-is-needed-to-create-my-own-custom-environment"></a>O que é necessário para meu próprio ambiente personalizado?
Todos os usuários com a licença do Microsoft Flow Plan 2 podem criar seus próprios ambientes, além do ambiente padrão. Todos os usuários do Microsoft Flow, incluindo o Office 365 e Gratuito, podem usar os ambientes criados pelos administradores do Plano 2, mas não podem criar seus próprios ambientes. 

