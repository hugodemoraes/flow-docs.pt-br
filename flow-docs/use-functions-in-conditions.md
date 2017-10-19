---
title: "Use funções com condições. | Microsoft Docs"
description: "Usar funções avançadas, como "
"\"and\"\",": 
"\"\"or\"\",": 
"\"\"empty\"\",": 
"\"\"less\"\"": 
and: 
"\"\"greater\"\"": 
with: 
microsoft: 
flow: 
conditions.": 
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
ms.date: 08/01/2017
ms.author: deonhe
ms.openlocfilehash: 26f8dd2f8f9c027584bba197d301e4c8a32b0857
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="use-functions-in-conditions-to-check-multiple-values"></a>Usar funções nas condições para verificar diversos valores
Neste passo a passo, você aprenderá a usar as funções e **Condições** para comparar diversos valores no **modo Avançado**.

Ao criar um fluxo, use o cartão [ **Condição**](add-a-condition.md#add-a-condition) no modo básico para comparar rapidamente um único valor com outro. No entanto, há vezes em que você precisará comparar diversos valores. Por exemplo, talvez você queira verificar o valor de algumas colunas em uma planilha ou tabela do banco de dados.

É possível usar qualquer combinação das seguintes funções lógicas em suas condições.

| Função | Descrição | Exemplo |
| --- | --- | --- |
| <a href="#use-the-and-function">and</a> |Obtém dois argumentos e retorna true se ambos os valores são verdadeiros.<br><b>Observação</b>: ambos os argumentos devem ser boolianos. |Essa função retorna false: <br>and(greater(1,10),equals(0,0)) |
| <a href="#use-the-or-function">or</a> |Obtém dois argumentos e retorna true se qualquer um dos valores é verdadeiro. <br><b>Observação</b>: ambos os argumentos devem ser boolianos. |Essa função retorna true:<br>or(greater(1,10),equals(0,0)) |
| equals |Retorna true se os dois valores são iguais. |Por exemplo, se o parameter1 é someValue, essa função retorna true:<br>equals(parameters('parameter1'), 'someValue') |
| <a href="#use-the-less-function">less</a> |Obtém dois argumentos e retorna true se o primeiro argumento é menor que o segundo argumento. <br><b>Observação</b>: os tipos suportados são: inteiro, flutuante e cadeia de caracteres. |Essa função retorna true:<br>less(10,100) |
| lessOrEquals |Obtém dois argumentos e retorna true se o primeiro argumento é menor que ou igual ao segundo argumento. <br><b>Observação</b>: os tipos suportados são: inteiro, flutuante e cadeia de caracteres. |Essa função retorna true:<br>lessOrEquals(10,10) |
| <a href="#use-the-greater-function">greater</a> |Obtém dois argumentos e retorna true se o primeiro argumento é maior que o segundo argumento. <br><b>Observação</b>: os tipos suportados são: inteiro, flutuante e cadeia de caracteres. |Essa função retorna false:<br>greater(10,10) |
| greaterOrEquals |Obtém dois argumentos e retorna true se o primeiro argumento é maior que ou igual ao segundo argumento. <br><b>Observação</b>: os tipos suportados são: inteiro, flutuante e cadeia de caracteres. |Essa função retorna false:<br>greaterOrEquals(10,100) |
| <a href="#use-the-empty-function">empty</a> |Retorna true se a matriz, cadeia de caracteres ou objeto estiver vazio. |Essa função retorna true:<br>empty('') |
| not |Obtém dois argumentos e retorna true se os argumentos são falsos. <br><b>Observação</b>: ambos os argumentos devem ser boolianos. |Essa função retorna true:<br>not(contains('200 Success','Fail')) |
| if |Retorna um valor específico se a expressão resulta em true ou false. |Essa função retorna "yes":<br>if(equals(1, 1), 'yes', 'no') |

## <a name="prerequisites"></a>Pré-requisitos
* Acesso ao Microsoft Flow.
* Mais adiante neste passo a passo, apresentaremos uma planilha com as tabelas descritas. Salve a planilha em um local como o Dropbox ou o Microsoft OneDrive para que o Microsoft Flow possa acessá-la.
* Outlook do Microsoft Office 365 (enquanto usamos o Outlook do Office 365, você pode usar qualquer serviço de email com suporte em seus fluxos.)

## <a name="use-the-or-function"></a>Usar a função or
Às vezes, o fluxo de trabalho precisa executar uma ação se o valor de um item for o valorA **ou** o valorB. Por exemplo, você pode acompanhar o status das tarefas em uma tabela da planilha. Suponha que a tabela possua uma coluna denominada *Status* e os possíveis valores na coluna *Status* sejam:

* **concluído**
* **bloqueado**
* **desnecessário**
* **não iniciado**

Veja um exemplo da provável aparência da planilha:

![planilha de exemplo](./media/use-functions-in-conditions/spreadsheet-table.png)

Dada a planilha anterior, você deseja usar o Microsoft Flow para remover todas as linhas com uma coluna *Status* definida como *concluído* ou *desnecessário*.

Vamos criar o fluxo.

### <a name="start-with-a-blank-flow"></a>Iniciar com um fluxo em branco
1. Entre no [Microsoft Flow](https://flow.microsoft.com).
   
    ![entrar](includes/media/modern-approvals/sign-in.png)
2. Selecione a guia **Meus fluxos**.
   
    ![selecione meus fluxos](includes/media/modern-approvals/select-my-flows.png)
3. Selecione **Criar do zero**.
   
    ![criar do zero](includes/media/modern-approvals/blank-template.png)

### <a name="add-a-trigger-to-your-flow"></a>Adicionar um gatilho ao fluxo
1. Procure **Agendamento** e, em seguida, escolha o gatilho **Agendamento - Recorrência**
   
    ![agendar o gatilho](includes/media/schedule-trigger/schedule-trigger.png)
2. Defina o agendamento para ser executado uma vez por dia.
   
    ![definir o agendamento](includes/media/schedule-trigger/set-schedule.png)

### <a name="select-the-spreadsheet-and-get-all-rows"></a>Selecionar a planilha e obter todas as linhas
1. Selecione **Nova etapa** > **Adicionar uma ação**.
   
    ![nova etapa](includes/media/new-step/action.png)
2. Procure as **linhas** e, em seguida, selecione **Excel - Obter linhas**.
   
    Observação: selecione a ação "obter linhas" que corresponde à planilha que você está usando. Por exemplo, se você estiver usando as Planilhas do Google, selecione **Planilhas do Google - Obter linhas**.
   
    ![obter Linhas](includes/media/new-step/get-excel-rows.png)
3. Selecione o ícone de pasta na caixa **Nome do arquivo**, navegue e escolha a planilha que contém seus dados.
   
    ![selecionar planilha](includes/media/new-step/select-spreadsheet.png)
4. Escolha a tabela que contém seus dados na lista **Nome da tabela**.
   
    ![selecionar tabela](includes/media/new-step/select-table.png)

### <a name="check-the-status-column-of-each-row"></a>Verificar a coluna de status de cada linha
1. Selecione **Nova etapa** > **Mais** > **Adicionar um aplicar a cada**.
   
    ![selecionar tabela](includes/media/new-step/apply-to-each.png)
2. Adicione o token **Valor** à caixa **Selecionar uma saída nas etapas anteriores**.
   
    ![selecionar tabela](includes/media/apply-to-each/add-value-token.png)
3. Selecione **Adicionar uma condição** > **Editar no modo avançado**.
4. Adicione a função **or** a seguir. A função **or** verifica o valor de cada linha na tabela (uma linha é conhecida como um item quando é acessada em uma função). Se o valor da coluna **status** for *concluído* **ou** *desnecessário*, a função **or** será avaliada como "true".
   
    A função **or** aparece como mostrado aqui:
   
    ````@or(equals(item()?['status'], 'unnecessary'), equals(item()?['status'], 'completed'))````
   
    O cartão **Condição** é semelhante a esta imagem:
   
    ![imagem da função or](./media/use-functions-in-conditions/or-function.png)

### <a name="delete-matching-rows-from-the-spreadsheet"></a>Excluir linhas correspondentes da planilha
1. Selecione **Adicionar uma ação** na ramificação da condição **SE SIM, NÃO FAÇA NADA**.
2. Pesquise **Excluir linha** e, em seguida, selecione **Excel - Excluir linha**.
   
    ![excluir a imagem da linha](includes/media/new-step/select-delete-excel-row.png)
3. Na caixa **Nome do arquivo**, pesquise e escolha o arquivo da planilha que contém os dados que você deseja excluir.
4. Na lista **Nome da tabela**, selecione a tabela que contém seus dados.
5. Coloque o token **Id da linha** na caixa **Id da linha**.
   
    ![arquivo da planilha](includes/media/new-step/delete-excel-row.png)

### <a name="name-the-flow-and-save-it"></a>Nomear e salvar o fluxo
1. Nomeie seu fluxo e selecione o botão **Criar fluxo**.
   
    ![salvar seu fluxo](./media/use-functions-in-conditions/name-and-save.png)

### <a name="run-the-flow-with-the-or-function"></a>Executar o fluxo com a função or
O fluxo é executado depois que você salvá-lo. Se você criou a planilha mostrada anteriormente neste passo a passo, ela terá essa aparência após a execução ser concluída:

![função or concluída](./media/use-functions-in-conditions/spreadsheet-table-after-or-function-runs.png)

Observe que todos os dados das linhas que tinham "concluído" ou "desnecessário" na coluna Status foram excluídos.

## <a name="use-the-and-function"></a>Usar a função and
Suponha que você tenha uma tabela da planilha com duas colunas. Os nomes das colunas são Status e Atribuído. Suponha também que você queira excluir todas as linhas se o valor da coluna Status for "bloqueado" e o valor da coluna Atribuído for "John Wonder".  Para realizar essa tarefa, siga todas as etapas anteriores neste passo a passo. No entanto, quando você editar o cartão **Condição** no modo avançado, use a função **and** mostrada abaixo:

````@and(equals(item()?['Status'], 'blocked'), equals(item()?['Assigned'], 'John Wonder'))````

O cartão **Condição** é semelhante a esta imagem:

![imagem da função and](./media/use-functions-in-conditions/and-function.png)

### <a name="run-the-flow-with-the-and-function"></a>Executar o fluxo com a função and
Se você tiver acompanhado o processo, a planilha será semelhante a esta imagem:

![antes de and ser executada](./media/use-functions-in-conditions/spreadsheet-table-before-and-function-runs.png)

Depois do fluxo ser executado, a planilha será semelhante a esta imagem:

![após and ser executada](./media/use-functions-in-conditions/spreadsheet-table-after-and-function-runs.png)

## <a name="use-the-empty-function"></a>Usar a função empty
Observe que agora, há várias linhas vazias na planilha. Para removê-las, use a função **empty** para identificar todas as linhas sem texto nas colunas Atribuído e Status.

Para realizar essa tarefa, siga todas as etapas listadas na seção **Usar a função and** anteriormente neste passo a passo, no entanto, quando você editar o cartão **Condição** no modo avançado, use a função empty da seguinte maneira:

````@and(empty(item()?['Status']), empty(item()?['Assigned']))````

O cartão **Condição** é semelhante a esta imagem:

![imagem da função empty](./media/use-functions-in-conditions/empty-function.png)

Depois do fluxo ser executado, a planilha será semelhante a esta imagem:

![após empty ser executada](./media/use-functions-in-conditions/spreadsheet-table-after-empty-function-runs.png)

Observe que as linhas extras foram removidas da tabela.

## <a name="use-the-greater-function"></a>Usar a função greater
Imagine que você tenha comprado ingressos para um jogo de baseball para seus colegas de trabalho e está usando uma planilha para garantir que será reembolsado por cada pessoa. Você pode criar rapidamente um fluxo que envia um email diário para cada pessoa que não pagou o valor total.

Use a função **greater** para identificar os funcionários que não pagaram o valor total. Em seguida, você pode enviar automaticamente um email de lembrete amigável para aqueles que não pagaram o total.

Veja uma exibição da planilha:

![exibição da planilha](./media/use-functions-in-conditions/tickets-spreadsheet-table.png)

Veja a implementação da função **greater** que identifica todas as pessoas que pagaram menos que quantidade devida:

````@greater(item()?['Due'], item()?['Paid'])````

## <a name="use-the-less-function"></a>Usar a função less
Imagine que você tenha comprado ingressos para um jogo de baseball para seus colegas de trabalho e está usando uma planilha para garantir que será reembolsado por cada pessoa na data que todos acordaram. Você pode criar um fluxo que envia um email de lembrete para cada pessoa que não pagou o valor total, caso a data atual seja menor que um dia antes da data de vencimento.

Use a função **and** juntamente com a função **less**, uma vez que há duas condições sendo validadas:

| Condição a validar | Função a usar | Exemplo |
| --- | --- | --- |
| O valor total devido foi pago? |greater |@greater(item()?['Due'], item()?['Paid']) |
| A data devida é menor que um dia? |less |@less(item()?['DueDate'], addDays(utcNow(),1)) |

## <a name="combine-the-greater-and-less-functions-in-an-and-function"></a>Combinar as funções greater e less em uma função and
Use a função **greater** para identificar os funcionários que pagaram menos que o valor total devido e use a função **less** para determinar se o vencimento data é menor que um dia antes da data atual. Então, você poderá usar a ação **Enviar um email** para enviar um email de lembrete amigável para aqueles que não pagaram tudo e cuja data de vencimento é menor que um dia.

Veja uma exibição da tabela da planilha:

![exibição da planilha](./media/use-functions-in-conditions/spreadsheet-table-due-date.png)

Veja a implementação da função **and** que identifica todas as pessoas que pagaram menos que o valor devido e a data de vencimento é menor que um dia antes da data atual:

````@and(greater(item()?['Due'], item()?['Paid']), less(item()?['dueDate'], addDays(utcNow(),1)))````

## <a name="learn-more"></a>Saiba mais
Saiba mais sobre outras [funções](https://docs.microsoft.com/azure/logic-apps/logic-apps-workflow-definition-language#functions)

