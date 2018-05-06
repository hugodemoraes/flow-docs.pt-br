---
title: Solicitações de exclusão de entidade de dados de GDPR do Microsoft Flow | Microsoft Docs
description: Saiba como usar o Microsoft Flow para responder às Solicitações de exclusão de entidade de dados de GPDR.
services: ''
suite: flow
documentationcenter: na
author: KentWeareMSFT
manager: anneta
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 4/17/2018
ms.author: keweare
ms.openlocfilehash: d750ee2bc672d08bff940341349663b4721f9a57
ms.sourcegitcommit: 12fbfe22fedd780d42ef1d2febfd7a0769b4902e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="responding-to-gdpr-data-subject-delete-requests-for-microsoft-flow"></a>Responder às Solicitações de exclusão de entidade de dados de GDPR do Microsoft Flow

O "direito de eliminação" pela remoção de dados pessoais dos Dados do Cliente de uma organização é uma proteção importante no GDPR. A remoção de dados pessoais inclui a remoção de todos os dados pessoais e de logs gerados pelo sistema, com exceção das informações de log de auditoria.

O Microsoft Flow permite que os usuários criem fluxos de trabalho de automação fundamentais para as operações diárias da sua organização. Quando um usuário deixa a sua organização, um administrador precisa revisar e determinar manualmente se quer ou não excluir determinados recursos e dados criados pelo usuário. Há outros dados pessoais que são excluídos automaticamente sempre que a conta de um usuário é excluída do Azure Active Directory.

A tabela a seguir mostra quais dados pessoais são excluídos automaticamente e quais dados exigem a revisão e exclusão manual de um administrador:

|Exige revisão e exclusão manual|Excluído automaticamente quando o usuário é excluído do Azure Active Directory|
|------|------|
|Ambiente*|Logs gerados pelo sistema|
|Permissões de ambiente**|Histórico de execuções|
|Fluxos|Trabalhos de usuário|
|Permissões do Flow|Gateway |
|Detalhes do usuário|Permissões de gateway |
|Conexões*||
|Permissões de conexão||
|Conector personalizado*||
|Permissões do conector personalizado||

* Cada um desses recursos contém registros "Criado por" e "Modificado por" que incluem dados pessoais. Por motivos de segurança, esses registros ficam retidos até que o recurso seja excluído.

* Para ambientes que incluem um banco de dados do Common Data Service for Apps, as permissões de ambiente (por exemplo, quais usuários recebem as funções de Administrador e Criador de Ambiente) são armazenadas como registros no banco de dados do Common Data Service. Veja [Executar DSRs em dados de cliente de Common Data Service](https://go.microsoft.com/fwlink/?linkid=872251), para obter diretrizes sobre como responder a DSRs para usuários que usam o Common Data Service.

Para os dados e recursos que exigem revisão manual, o Microsoft Flow oferece as seguintes experiências para localizar ou alterar os dados pessoais de um usuário específico:

* **Acesso ao site:** entre no [Centro de Administração do PowerApps](https://admin.powerapps.com/) ou no [Centro de Administração do Microsoft Flow](https://admin.flow.microsoft.com/)

* **Acesso do PowerShell:** [cmdlets do PowerShell de Administração do PowerApps](https://go.microsoft.com/fwlink/?linkid=871804) 

Confira a divisão das experiências que estão disponíveis para um administrador excluir cada tipo de dados pessoais em cada tipo de recurso:

|Recursos que contêm dados pessoais|Acesso ao site|Acesso ao PowerShell|Exclusão automatizada|
|-----|----|----|----|
|Logs gerados pelo sistema|[Portal de Confiança do Serviço Office 365](https://servicetrust.microsoft.com/)|||
|Ambiente|Centro de Administração do Microsoft Flow|Cmdlets de PowerApps||
|Permissões de ambiente*|Centro de Administração do Microsoft Flow|Cmdlets de PowerApps||
|Histórico de execuções||| Excluído pela política de retenção de 28 dias|
|Feed de atividades ||Cmdlets de PowerApps||
|Trabalhos de usuário|| ||
|Fluxos|Microsoft Flow Maker Portal**|||
|Permissões do Flow|Microsoft Flow Maker Portal|||
|Detalhes do usuário|| ||
|Conexões|Microsoft Flow Maker Portal| ||
|Permissões de conexão|Microsoft Flow Maker Portal| ||
|Conector personalizado|Microsoft Flow Maker Portal| ||
|Permissões do conector personalizado|Microsoft Flow Maker Portal| ||
|Histórico de aprovações|Microsoft PowerApps Maker Portal*|||

*Com a introdução do Common Data Service for Apps, se um banco de dados é criado dentro do ambiente, as permissões de ambiente e permissões de aplicativos controladas por modelos são armazenadas como registros dentro da instância de banco de dados do Common Data Service for Apps. Veja [Executar DSRs em dados de cliente de Common Data Service](https://go.microsoft.com/fwlink/?linkid=872251), para obter diretrizes sobre como responder a DSRs para usuários que usam o Common Data Service.

**O administrador só poderá acessar esses recursos no Portal do Criador do Microsoft Flow se tiver recebido acesso do Centro de Administração do Microsoft Flow.

## <a name="manage-delete-requests"></a>Gerenciar solicitações de exclusão

As etapas a seguir descrevem como as funções administrativas existe para atender às solicitações de exclusão de GDPR.

> [!IMPORTANT]
> Para evitar a corrupção de dados, execute estas etapas na ordem.
>
>

## <a name="list-and-re-assign-flows"></a>Listar e reatribuir fluxos

Estas etapas copiam os fluxos existentes de um usuário que está saindo. Se você atribuir uma nova propriedade às cópias, esses fluxos poderão continuar a oferecer suporte a processos comerciais existentes. Copiar esses fluxos é importante para excluir vínculos de identificação pessoal do usuário que está saindo, e é necessário estabelecer novas conexões para que o fluxo se conecte com outros aplicativos SaaS e APIs.

1. Entre no [Centro de Administração do Microsoft Flow](https://admin.flow.microsoft.com/) e, em seguida, selecione o ambiente que contém fluxos pertencentes ao usuário excluído.

    ![Exibir ambientes](./media/gdpr-dsr-delete/view-environments.png)

1. Selecione **Recursos** > **Fluxos** e, em seguida, selecione o título do fluxo que você quer reatribuir.

    ![Exibir fluxos](./media/gdpr-dsr-delete/admin-view-flows.png)

1. Selecione **Gerenciar compartilhamento**.

    ![Gerenciar compartilhamento](./media/gdpr-dsr-delete/admin-manage-sharing.png)

1. No painel **Compartilhamento** que aparece perto da borda direita, adicione a si mesmo como proprietário e, depois, selecione **Salvar**.

    ![Compartilhar o fluxo](./media/gdpr-dsr-delete/flow-sharing-save.png)

1. Entre no [Microsoft Flow](https://flow.microsoft.com/), selecione **Meus fluxos** e selecione **Fluxos de equipe**:

1. Selecione as reticências **(...)** para o fluxo que você quer copiar e, em seguida, selecione **Salvar como**.

    ![Salvar fluxo como](./media/gdpr-dsr-delete/flow-save-as.png)

1. Configure as conexões conforme o necessário e, depois, selecione **Continuar**.

1. Forneça um novo nome e, depois, selecione **Salvar**.

    ![Criar cópia de fluxo](./media/gdpr-dsr-delete/create-copy-flow.png)

1. Essa nova versão do fluxo de aparece em **Meu fluxos**, onde você pode compartilhá-la com outros usuários, se quiser.

    ![Fluxos de equipe](./media/gdpr-dsr-delete/team-flows.png)

1. Exclua o fluxo original selecionando as reticências **(...)** dele, selecionando **Excluir** e, depois, selecionando **Excluir** novamente quando receber a solicitação. Esta etapa também removerá identificadores pessoais subjacentes que estão incluídos nas dependências do sistema entre o usuário e o Microsoft Flow.

    ![Excluir confirmação do fluxo](./media/gdpr-dsr-delete/delete-flow-confirmation.png)

1. Habilite a cópia do fluxo abrindo **Meus fluxos** e, depois, alterando o controle para **Ativado**.
    ![Habilitar o fluxo](./media/gdpr-dsr-delete/toggle-on.png)

1. Agora, a cópia executa a mesma lógica de fluxo de trabalho que a versão original.

## <a name="delete-approval-history-from-microsoft-flow"></a>Excluir histórico de aprovação do Microsoft Flow

 Os dados de aprovação do Microsoft Flow são armazenados na versão atual ou anterior do Common Data Service for Apps. Dentro de uma aprovação, há informações pessoais na forma de atribuições de aprovação e comentários incluídos na resposta de uma aprovação. Os administradores podem acessar esses dados executando estas etapas:

1. Entre no [PowerApps](https://web.powerapps.com/).

1. Selecione **Sados** e **Entidades**.

1. Selecione as reticências **(...)** da entidade **Aprovação do Fluxo** e, em seguida, abra os dados no Microsoft Excel.

1. No Microsoft Excel, pesquise, filtre e exclua os dados de aprovação, conforme o necessário.

Veja [Executar DSRs em dados de cliente de Common Data Service](https://go.microsoft.com/fwlink/?linkid=872251), para obter diretrizes adicionais sobre como responder a DSRs para usuários que usam o Common Data Service.

## <a name="delete-connections-created-by-a-user"></a>Excluir conexões criadas por um usuário

As conexões são usadas em conjunto com os conectores para estabelecer a conectividade com outros sistemas APIs e SaaS.  Conexões incluem referências ao usuário que criou e, como resultado, podem ser excluídas para remover quaisquer referências ao usuário.

Cmdlets do PowerShell do PowerApps Maker

Um usuário pode excluir todas as suas conexões usando a função Remover-Conexão dos [cmdlets do PowerShell do PowerApps Maker](https://go.microsoft.com/fwlink/?linkid=871448):

```PowerShell
Add-PowerAppsAccount

#Retrieves all connections for the calling user and deletes them
Get-Connection | Remove-Connection
```

Cmdlets do PowerShell de Administração do PowerApps

Não disponível.

## <a name="delete-the-users-permissions-to-shared-connections"></a>Excluir as permissões do usuário para conexões compartilhadas

Cmdlets do PowerShell do PowerApps Maker

Um usuário pode excluir todas as atribuições de função de conexão para a função Remove-ConnectionRoleAssignment de conexões compartilhadas nos [cmdlets do PowerShell do PowerApps Maker](https://go.microsoft.com/fwlink/?linkid=871448):

```PowerShell
Add-PowerAppsAccount

#Retrieves all connection role assignments for the calling users and deletes them
Get-ConnectionRoleAssignment | Remove-ConnectionRoleAssignment
```

> [!NOTE]
> As atribuições de função de proprietário não podem ser excluídas sem excluir o recurso de conexão.
>
>

Cmdlets do PowerShell de Administração do PowerApps

Não disponível.

## <a name="delete-custom-connectors-created-by-the-user"></a>Excluir conectores personalizados criados pelo usuário

Conectores personalizados complementam os conectores originais existentes e permitem a conectividade com outras APIs, SaaS e sistemas personalizados. Conectores personalizados incluem referências ao usuário que os criou e, como resultado, podem ser excluídos para remover referências ao usuário.

Cmdlets do PowerShell do PowerApps Maker

Um usuário pode excluir todos os conectores personalizados usando a função Remover-Conexão nos [cmdlets do PowerShell do PowerApps Maker](https://go.microsoft.com/fwlink/?linkid=871448):

```PowerShell
Add-PowerAppsAccount

#Retrieves all custom connectors for the calling user and deletes them
Get-Connector -FilterNonCustomConnectors | Remove-Connector
```

Cmdlets do PowerShell de Administração do PowerApps

Não disponível.

## <a name="delete-the-users-permissions-to-shared-custom-connectors"></a>Excluir as permissões do usuário aos conectores personalizados compartilhados

Cmdlets do PowerShell do PowerApps Maker

Um usuário pode excluir todas as atribuições de função de conector do conector personalizado compartilhado com a função Remove-ConnectorRoleAssignment nos [cmdlets do PowerShell do PowerApps Maker](https://go.microsoft.com/fwlink/?linkid=871448):

```PowerShell
Add-PowerAppsAccount

#Retrieves all connector role assignments for the calling users and deletes them
Get-ConnectorRoleAssignment | Remove-ConnectorRoleAssignment
```

> [!NOTE]
> As atribuições de função de proprietário não podem ser excluídas sem excluir o recurso de conexão.
>
>

Cmdlets do PowerShell de Administração do PowerApps

Não disponível.

## <a name="delete-or-reassign-all-environments-created-by-the-user"></a>Excluir ou reatribuir todos os ambientes criados pelo usuário

Como administrador, você tem duas decisões a serem tomadas ao processar uma solicitação de exclusão de DSR de um usuário para cada um dos ambientes criados pelo usuário:

1. Se você determinar que o ambiente não está sendo usado por outras pessoas em sua organização, opte por excluir o ambiente
1. Se você determinar que o ambiente ainda é necessário, opte por não excluir o ambiente e adicione você mesmo (ou outro usuário em sua organização) como Administrador do Ambiente.
    > [!IMPORTANT]
    > A exclusão de um ambiente excluirá permanentemente todos os recursos dentro do ambiente, incluindo todos os aplicativos, fluxos, conexões etc., portanto, examine o conteúdo de um ambiente antes da exclusão.
    >
    >

## <a name="give-access-to-a-users-environments-from-the-microsoft-flow-admin-center"></a>Dê acesso aos ambientes de um usuário pelo Centro de Administração do Microsoft Flow

Um administrador pode conceder acesso de Administrador a um ambiente criado por um usuário específico no [Centro de Administração do Microsoft Flow](https://admin.flow.microsoft.com/). Para saber mais sobre como administrar ambientes, navegue até [Usar ambientes no Microsoft Flow](https://docs.microsoft.com/flow/environments-overview-admin).

## <a name="delete-the-users-permissions-to-all-other-environments"></a>Excluir permissões do usuário a todos os outros ambientes

Os usuários podem receber permissões (como Administrador de Ambiente, Criador de Ambiente etc.) em um ambiente, as quais são armazenadas no serviço Microsoft Flow como uma "atribuição de função".

Com a introdução do Common Data Service for Apps, se um banco de dados é criado dentro do ambiente, essas "atribuições de função" são armazenadas como registros dentro da instância de banco de dados do Common Data Service for Apps.

Para saber mais sobre como remover a permissão de um usuário em um ambiente, navegue até [Usar ambientes no Microsoft Flow](https://docs.microsoft.com/flow/environments-overview-admin).
