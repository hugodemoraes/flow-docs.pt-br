---
title: "Introdução às políticas de prevenção contra a perda de dados (DLP). | Microsoft Docs"
description: "Introdução a políticas de prevenção de perda de dados para o Microsoft Flow."
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
ms.date: 01/24/2016
ms.author: deonhe
ms.openlocfilehash: 29eaa9299e09c641538ab8f9dfbc9954bca66a3b
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="data-loss-prevention-dlp-policies"></a>Políticas de DLP (prevenção de perda de dados)
## <a name="what-is-a-data-loss-prevention-policy"></a>O que é a política de prevenção de perda de dados?
Os dados de uma organização são fundamentais para o sucesso. Os dados precisam estar prontamente disponíveis para a tomada de decisões, mas precisam ser protegidos para que não sejam compartilhados com audiências que não devem ter acesso a eles. Para proteger esses dados, o Microsoft Flow (Flow) fornece a capacidade de criar e aplicar políticas que definem com quais serviços de consumidor/conectores é possível compartilhar dados de negócios específicos. As políticas que definem como os dados podem ser compartilhados são chamadas de políticas de DLP (prevenção de perda de dados).

## <a name="why-create-a-dlp-policy"></a>Por que criar uma política de DLP?
Você deve criar a política de DLP para definir claramente com quais serviços de consumidor os dados de negócios podem ser compartilhados. Por exemplo, uma organização que usa o Flow pode não querer que seus dados de negócios sejam armazenados no SharePoint para serem publicados automaticamente em seu feed do Twitter. Para evitar isso, você pode criar uma política de DLP que impeça que os dados do SharePoint sejam usados como a origem para tweets.

## <a name="benefits-of-a-dlp-policy"></a>Benefícios de uma política de DLP
* Garante que os dados sejam gerenciados de maneira uniforme em toda a organização  
* Impede que dados de negócios importantes sejam acidentalmente publicados em serviços como sites de mídia social.   

## <a name="managing-dlp-policies"></a>Gerenciar políticas de DLP
**Pré-requisitos**  
Para criar, editar ou excluir políticas de DLP, os seguintes itens são necessários: 

* Permissões de administrador de ambiente ou administrador de locatário. Você pode saber mais sobre permissões no [tópico de ambientes](environments-overview-admin.md).  
* Um [licença do Flow P2](billing-questions.md).  

## <a name="create-a-dlp-policy"></a>Criar uma política de DLP
**Pré-requisitos**  
Para criar uma política de DLP, você deve ter permissões para pelo menos um ambiente.  

Siga estas etapas para criar uma política de DLP que impede que os dados armazenados no SharePoint de sua empresa sejam publicados no Twitter:  

1. Na guia Políticas de Dados, selecione o link **Nova política**:  
   ![Entrar](./media/prevent-data-loss/create-policy-1.png)    
2. Insira o nome da política de DLP como *Acesso Seguro aos Dados da Contoso* no rótulo **Nome da Política de Dados** na parte superior da página que é aberta:   
   ![Entrar](./media/prevent-data-loss/create-policy-2.png)  
3. Selecione o [ambiente](environments-overview-admin.md) na guia **Aplica-se a**.  
   **Observação:** como administrador de ambiente, você pode criar políticas que se aplicam apenas a um único ambiente. Como administrador de locatário, você pode criar uma política que se aplique a todos os ambientes, a um ou mais ambientes selecionados ou a todos os ambientes, exceto um conjunto selecionado:  
   ![Entrar](./media/prevent-data-loss/create-policy-3.png)  
4. Selecione a guia **Grupos de dados**:  
   ![Entrar](./media/prevent-data-loss/create-policy-4.png)  
5. Selecione o link **+Adicionar** localizado na caixa de grupo **Somente dados de negócios**:    
   ![Entrar](./media/prevent-data-loss/create-policy-5.png)  
6. Selecione os serviços **SharePoint** e **Salesforce** na página **Adicionar serviços**:  
   ![Entrar](./media/prevent-data-loss/create-policy-6.png)  
7. Selecione o botão **Adicionar serviços** para adicionar os serviços que têm permissão para compartilhar dados de negócios:    
   ![Entrar](./media/prevent-data-loss/create-policy-7.png)  
8. Selecione **Salvar Política**:  
   ![Entrar](./media/prevent-data-loss/create-policy-8.png)  
9. Após alguns instantes, a nova política de DLP será exibida na lista de políticas de prevenção de perda de dados:  
   ![Entrar](./media/prevent-data-loss/create-policy-9.png)  
10. **Opcional** envie um email ou outras comunicações à sua equipe, avisando que uma nova política de DLP está disponível agora.

Parabéns, você criou uma política de DLP que permite que o aplicativo compartilhe dados entre o SharePoint e o SalesForce e bloqueia o compartilhamento de dados com outros serviços.  

**Observação**: adicionar um serviço a um dos grupos de dados automaticamente removerá este serviço do outro grupo de dados. Por exemplo, se atualmente o Twitter estiver localizado no grupo de dados **somente dados de negócios** e você não quiser permitir que os dados de negócios sejam compartilhados com o Twitter, basta adicionar o serviço do Twitter ao grupo de **dados de negócios não permitidos**. Isso removerá o Twitter do grupo de dados somente dados de negócios.  

## <a name="data-sharing-violations"></a>Violações de compartilhamento de dados
Supondo que você criou a política DLP descrita acima, se um usuário cria um fluxo que compartilha dados entre o Salesforce (que está no grupo de dados **somente dados de negócios**) e Twitter (que está no grupo de dados **dados de negócios não permitidos**), o usuário será informado de que o fluxo está **suspenso** devido a um conflito com a política de prevenção de perda de dados criada por você.  
![criar fluxo](./media/prevent-data-loss/10.png)  

Se os usuários entrarem em contato com você sobre fluxos suspensos, veja alguns itens a considerar:  

1. Neste exemplo, se houver um motivo comercial válido para compartilhar dados de negócios entre o SharePoint e o Twitter, você pode editar a política DLP.  
2. Peça ao usuário para editar o fluxo de acordo com a política DLP.  
3. Peça ao usuário para deixar o fluxo no estado suspenso até que seja feita uma decisão sobre o compartilhamento de dados entre essas duas entidades.  

## <a name="find-a-dlp-policy"></a>Localizar uma política de DLP
### <a name="admins"></a>Administradores.
Os administradores podem usar o recurso de pesquisa do Centro de administração para localizar políticas de DLP específicas.  

**OBSERVAÇÃO** os administradores devem publicar todas as políticas de DLP para que os usuários da organização estejam cientes das políticas antes da criação de fluxos.

### <a name="makers"></a>Criadores
Se você não tem permissões de administrador e deseja saber mais sobre as políticas de DLP em sua organização, contate o administrador. Você também pode saber mais no [tópico de ambientes de fabricante](environments-overview-maker.md)  

**OBSERVAÇÃO** somente administradores podem editar ou excluir políticas de DLP.  

## <a name="edit-a-dlp-policy"></a>Editar uma política de DLP
1. Inicie o Centro de administração navegando para https://admin.flow.microsoft.com.  
2. No Centro de administração iniciado, selecione o link **Políticas de dados** no lado esquerdo.  
   ![Entrar](./media/prevent-data-loss/2.png)  
3. Pesquise a lista de políticas de DLP existentes e selecione o botão Editar junto à política que você pretende editar:  
   ![Entrar](./media/prevent-data-loss/3.png)  
4. Faça as alterações desejadas. Você pode modificar o ambiente ou os serviços nos grupos de dados, por exemplo.  
5. Selecione **Salvar Política** para salvar as alterações:  
   ![Entrar](./media/prevent-data-loss/create-policy-8.png)  

A política foi atualizada. Você pode confirmar que as alterações foram feitas na política localizando-a na lista de políticas de prevenção de perda dados e examinando suas propriedades.   

**Observação** políticas de DLP criadas por administradores de locatários podem ser exibidas por administradores de ambiente, mas não podem ser editadas por administradores de ambiente.  

## <a name="delete-a-dlp-policy"></a>Excluir uma política de DLP
1. Inicie o Centro de administração navegando para https://admin.flow.microsoft.com.  
2. No Centro de administração iniciado, selecione o link **Políticas de dados** no lado esquerdo.  
   ![Entrar](./media/prevent-data-loss/2.png)  
3. Pesquise a lista de políticas de DLP existentes e selecione o botão Excluir ao lado de política que você pretende excluir:  
   ![Entrar](./media/prevent-data-loss/3-delete.png)  
4. Confirme que você realmente deseja excluir a política selecionando o botão **Excluir**:  
   ![Entrar](./media/prevent-data-loss/4.png)  

A política foi excluída. Você pode confirmar que a política não está mais na lista de políticas de prevenção de perda de dados selecionando o link **Políticas de Dados** à esquerda e examinando a lista de políticas.   

## <a name="dlp-policy-permissions"></a>Permissões de política de DLP
Apenas os administradores de locatários e de ambiente podem criar e modificar políticas de DLP. Saiba mais sobre permissões no tópico [ambientes](environments-overview-admin.md).  

## <a name="next-steps"></a>Próximas etapas
* [Saiba mais sobre os ambientes](environments-overview-admin.md)  
* [Saiba mais sobre o Microsoft Flow](getting-started.md)  
* [Saiba mais sobre o centro de administração](introduction-to-the-admin-center.md)  

