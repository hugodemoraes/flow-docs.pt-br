---
title: Melhores práticas para processos de fluxo de trabalho no PowerApps | Microsoft Docs
description: Entender as maneiras recomendadas para usar fluxos de trabalho
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 34e34c33-003a-494f-858c-3d34aacb308c
caps.latest.revision: 10
ms.author: matp
manager: kvivek
search.app:
- Flow
search.audienceType:
- flowmaker
- enduser
ms.openlocfilehash: 94c38a54fec91e6a480cd90d0a72f19ca56ae51c
ms.sourcegitcommit: a20fbed9941f0cd8b69dc579277a30da9c8bb31b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44689515"
---
# <a name="best-practices-for-workflow-processes"></a>Melhores práticas para processos de fluxo de trabalho

Este tópico contém as melhores práticas para criar e gerenciar processos de fluxo de trabalho.  
  
<a name="BKMK_AvoidInfiniteLoops"></a>   
## <a name="avoid-infinite-loops"></a>Evitar loops infinitos  
 É possível criar a lógica em um fluxo de trabalho que inicia um loop infinito, o que consome recursos do servidor e afeta o desempenho. A situação comum em que um loop infinito poderá ocorrer é se você tiver um fluxo de trabalho configurado para ser iniciado quando um atributo for atualizado e, em seguida, atualizar o atributo na lógica do fluxo de trabalho. A ação de atualização dispara o mesmo fluxo de trabalho que atualiza o registro e dispara o fluxo de trabalho novamente.  
  
 Os fluxos de trabalho que você cria incluem lógica para detectar e parar loops infinitos. Se um processo de fluxo de trabalho é executado mais de um determinado número de vezes em um registro específico em um curto período de tempo, o processo falha com o seguinte erro: **Esse trabalho do fluxo de trabalho foi cancelado porque o fluxo de trabalho que o iniciou incluía um loop infinito. Corrija a lógica de fluxo de trabalho e tente novamente**. O limite de vezes é 16.  
  
<a name="BKMK_UseWorkflowTemplates"></a>   
## <a name="use-workflow-templates"></a>Usar modelos de fluxo de trabalho  
 Se você tiver fluxos de trabalho que são semelhantes e prever a criação de mais fluxos de trabalho que seguem o mesmo padrão, salve seu fluxo de trabalho como um modelo de fluxo de trabalho. Dessa forma, na próxima vez que você precisar criar um fluxo de trabalho semelhante, crie o fluxo de trabalho usando o modelo e evite a inserção de todas as condições e ações do zero.  
  
 Na caixa de diálogo **Criar processo**, escolha **Novo processo de um modelo existente (selecionar na lista)**.  
  
<a name="BKMK_UseChildWorkflows"></a>   
## <a name="use-child-workflows"></a>Usar fluxos de trabalho filho  
 Se você aplicar a mesma lógica em diferentes fluxos de trabalho ou em ramificações condicionais, defina essa lógica como um fluxo de trabalho filho para que você não precise replicar essa lógica manualmente em cada fluxo de trabalho ou ramificação condicional. Isso ajuda a facilitar a manutenção de seus fluxos de trabalho. Em vez de examinar vários fluxos de trabalho que podem aplicar a mesma lógica, você pode apenas atualizar um fluxo de trabalho.  
  
## <a name="automatically-delete-completed-workflow-jobs"></a>Exclusão automática de trabalhos de fluxo de trabalho concluído
Para fluxos de trabalho em segundo plano (assíncronos), é recomendável selecionar a opção **Excluir automaticamente trabalhos de fluxo de trabalho concluídos (para economizar espaço em disco)** na definição de fluxo de trabalho. Marcar essa caixa permite que o sistema exclua os logs de fluxo de trabalho para execuções com êxito para economizar espaço. Observe que os logs de execuções de fluxo de trabalho com falha serão sempre salvos para solução de problemas.  

![Retenção de trabalho de fluxo de trabalho](media/workflow-job-retention.png)

<a name="BKMK_AutoDeleteCompletedWorkflowJobs"></a>   
## <a name="keep-logs-for-workflow-jobs-that-encountered-errors"></a>Mantenha os logs para trabalhos de fluxo de trabalho que encontraram erros  
Para fluxos de trabalho que não são executados em segundo plano (síncronos), é recomendável selecionar a opção **Manter os logs para trabalhos de fluxo de trabalho que encontraram erros** na definição de fluxo de trabalho. Selecionar essa opção permite que os logs de execuções de fluxo de trabalho com falha sejam salvos para solução de problemas. Logs de execuções bem-sucedidas de fluxo de trabalho síncrono sempre serão excluídos para economizar espaço.   

![Mantenha os logs para a opção de fluxos de trabalho com falha](media/keep-logs-for-workflows.png)

## <a name="limit-the-number-of-workflows-that-update-the-same-entity"></a>Limite o número de fluxos de trabalho que atualizam a mesma entidade
Executar mais de um fluxo de trabalho que atualiza a mesma entidade pode causar problemas de bloqueio dos recursos. Imagine vários fluxos de trabalho em execução em que cada atualização de oportunidade dispara uma atualização para a conta associada. Várias instâncias desses fluxos de trabalho executando e tentando atualizar o mesmo registro de conta ao mesmo tempo podem resultar em problemas de bloqueio do recurso. Ocorrem falhas de fluxo de trabalho e uma mensagem de erro, como **Tempo limite do SQL: não é possível obter o bloqueio no recurso *nome do recurso***, é registrada. 

  
<a name="BKMK_DocumentChangesUsingNotes"></a>   
## <a name="use-notes-to-keep-track-of-changes"></a>Use as observações para manter controle das alterações  
 Ao editar os fluxos de trabalho, você deve usar a guia Observações e digitar o que fez e por que fez. Isso permite que outra pessoa possa entender as alterações feitas por você.  
  
## <a name="next-steps"></a>Próximas etapas  
 [Visão geral dos processos de fluxo de trabalho](workflow-processes.md)   
 [Configurar os processos de fluxo de trabalho](configure-workflow-steps.md)   
 [Monitorar e gerenciar processos de fluxo de trabalho](monitor-manage-processes.md)
   
