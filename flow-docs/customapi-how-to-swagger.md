---
title: "Extensões de OpenAPI para conectores personalizados no Microsoft Flow | Microsoft Docs"
description: "Exiba as extensões do esquema necessárias pelo OpenAPI para trabalhar com o Microsoft Flow"
services: 
suite: flow
documentationcenter: 
author: sunaysv
manager: anneta
editor: sunaysv
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/19/2017
ms.author: sunayv
ms.openlocfilehash: b8fdc04c16701c876d84e9761a48093fa5fb195c
ms.sourcegitcommit: 4f2cb27d392f46aa1d8680d6278876780ed3871b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2017
---
# <a name="openapi-extensions-for-custom-connectors-in-microsoft-flow"></a>Extensões de OpenAPI para conectores personalizados no Microsoft Flow
## <a name="introduction"></a>Introdução
Para criar conectores personalizados no Microsoft Flow, Aplicativo Lógico do Azure ou Microsoft PowerApps, você deve fornecer um arquivo de definição OpenAPI, que é um documento legível pela máquina independente da linguagem que descreve as operações e os parâmetros da API. Juntamente com a funcionalidade pronta para uso do OpenAPI, você também pode incluir essas extensões do OpenAPI ao criar conectores personalizados para os Aplicativos Lógicos e para o Flow:

* `summary`
* `x-ms-summary`
* `description`
* `x-ms-visibility`
* `x-ms-dynamic-values`
* `x-ms-dynamic-schema`

Veja mais detalhes sobre essas extensões:

<a name="summary"></a>

## <a name="summary"></a>resumo
Especifica o título para a ação (operação). </br>
Aplica-se à: operações </br>
Recomendado: use *primeira letra da frase em maiúscula* para `summary`. </br>
Exemplo: "Quando um evento é adicionado ao calendário" ou "Enviar um email"

!["resumo" para cada operação](./media/custom-connector-openapi-extensions/summary.png)

``` json
"actions" {
  "Send_an_email": {
    /// Other action properties here...
    "summary": "Send an email",
    /// Other action properties here...
  }
},
```

## <a name="x-ms-summary"></a>x-ms-summary
Especifica o título de uma entidade. </br>
Aplica-se a: parâmetros, esquema de resposta </br>
Recomendado: use *primeira letra do título em maiúscula* para `x-ms-summary`. </br>
Exemplo: "ID do calendário", "Assunto", "Descrição do evento" e assim por diante

!["x-ms-summary" para cada entidade](./media/custom-connector-openapi-extensions/x-ms-summary.png)

``` json
"actions" {
  "Send_an_email": {
    /// Other action properties here...
    "parameters": [ 
      {
        /// Other parameters here...
        "x-ms-summary": "Subject",
        /// Other parameters here...
      }
    ]
  }
},
```
<a name="description"></a>

## <a name="description"></a>descrição
Especifica uma explicação detalhada da funcionalidade da operação ou formato e função da entidade. </br>
Aplica-se a: operações, parâmetros, esquema de resposta </br>
Recomendado: use *primeira letra da frase em maiúscula* para `description`. </br>
Exemplo: "Esta operação dispara quando um novo evento é adicionado ao calendário", "Especifique o assunto do email.", e assim por diante

!["descrição" para cada operação ou entidade](./media/custom-connector-openapi-extensions/description.png)

``` json
"actions" {
  "Send_an_email": {
     "description": "Specify the subject of the mail",
     /// Other action properties here...
  }
},
```

<a name="visibility"></a>

## <a name="x-ms-visibility"></a>x-ms-visibility
Especifica a visibilidade direcionada ao usuário para uma entidade. </br>
Valores possíveis: `important`, `advanced`, e `internal` </br>
Aplica-se a: operações, parâmetros, esquemas

* `important` operações e parâmetros são sempre exibidos para o usuário primeiro.
* `advanced` operações e parâmetros estão ocultos em um menu adicional.
* `internal` operações e parâmetros estão ocultos do usuário.

> [!NOTE]
> Para os parâmetros que são `internal` e `required`, você **deve** fornecer valores padrão para esses parâmetros.
> 
> 

Exemplo: o menu **Ver mais** e o menu **Mostrar opções avançadas** está ocultando `advanced` operações e parâmetros.

!["x-ms-visibility" para mostrar ou ocultar operações e parâmetros](./media/custom-connector-openapi-extensions/x-ms-visibility.png)

``` json
"actions" {
  "Send_an_email": {
     /// Other action properties here...
     "parameters:": [
         {
           "name": "Subject",
           "type": "string",
           "description": "Specify the subject of the mail",
           "x-ms-summary": "Subject",
           "x-ms-visibility": "important",
           /// Other parameter properties here
         }
     ]
     /// Other action properties here...
  }
},
```

## <a name="x-ms-dynamic-values"></a>x-ms-dynamic-values
Mostra uma lista preenchida para o usuário para que ele possa selecionar os parâmetros de entrada para uma operação. </br>
Aplica-se a: parâmetros </br>
Como usar: adicionar `x-ms-dynamic-values` objetos à definição do parâmetro. Por exemplo, confira este [exemplo de OpenAPI](https://procsi.blob.core.windows.net/blog-images/sampleDynamicSwagger.json).

!["x-ms-dynamic-values" para a exibição de listas](./media/custom-connector-openapi-extensions/x-ms-dynamic-values.png)

### <a name="properties-for-x-ms-dynamic-values"></a>Propriedades de x-ms-dynamic-values
| Nome | Obrigatório ou opcional | Descrição |
| --- | --- | --- |
| **ID da operação** |Necessário |A operação para chamar para preencher a lista. |
| **value-path** |Necessário |Uma cadeia de caracteres de caminho em `value-collection` que se refere ao valor do parâmetro. Se `value-collection` não for especificado, a resposta é avaliada como uma matriz. |
| **value-title** |Opcional |Uma cadeia de caracteres de caminho em `value-collection` que se refere à descrição do valor. Se `value-collection` não for especificado, a resposta é avaliada como uma matriz. |
| **value-collection** |Opcional |Uma cadeia de caracteres de caminho que avalia uma matriz de objetos no conteúdo da resposta |
| **parâmetros** |Opcional |Um objeto cujas propriedades especificam os parâmetros de entrada necessários para invocar uma operação dynamic-values |

Veja um exemplo que mostra as propriedades em `x-ms-dynamic-values`

``` json
"x-ms-dynamic-values": {
  "operationId": "PopulateDropdown",
  "value-path": "name",
  "value-title": "properties/displayName",
  "value-collection": "value",
  "parameters": {
     "staticParameter": "{value}",
     "dynamicParameter": {
        "parameter": "{value-to-pass-to-dynamicParameter}"
     }
  }
}
```

## <a name="example-all-the-openapi-extensions-up-to-this-point"></a>Exemplo: todas as extensões de OpenAPI até este ponto
``` json
"/api/lists/{listID-dynamic}": {
    "get": {
        "description": "Get items from a single list - uses dynamic values and outputs dynamic schema",
        "summary": "Gets items from the selected list",
        "operationID": "GetListItems",
        "parameters": [
           {
             "name": "listID-dynamic",
             "type": "string",
             "in": "path",
             "description": "Select the list from where you want outputs",
             "required": true,
             "x-ms-summary": "Select List",
             "x-ms-dynamic-values": {
                "operationID": "GetLists",
                "value-path": "id",
                "value-title": "name"
             }
           }
        ]
    }
}
```

## <a name="x-ms-dynamic-schema"></a>x-ms-dynamic-schema
Indica que o esquema para o parâmetro atual ou resposta é dinâmico. Este objeto pode invocar uma operação que é definida pelo valor do campo, descobrir dinamicamente o esquema e exibir a interface do usuário apropriada para coletar entradas do usuário ou mostrar os campos disponíveis. 

Aplica-se a: parâmetros, resposta

Como usar: adicione o objeto `x-ms-dynamic-schema` a uma definição de corpo de resposta ou parâmetro de solicitação. Por exemplo, confira este [exemplo de OpenAPI](https://procsi.blob.core.windows.net/blog-images/sampleDynamicSwagger.json).

Este exemplo mostra como o formulário de entrada é alterado, com base no item que o usuário seleciona na lista suspensa:

!["x-ms-dynamic-schema" para parâmetros dinâmicos](./media/custom-connector-openapi-extensions/x-ms-dynamic-schema.png)

E este exemplo mostra como as saídas são alteradas, com base no item que o usuário seleciona na lista suspensa. Nesta versão, o usuário seleciona "Carros":

!["x-ms-dynamic-schema-response" para o item selecionado "Carros"](./media/custom-connector-openapi-extensions/x-ms-dynamic-schema-output1.png)

Nesta versão, o usuário seleciona "Comidas":

!["x-ms-dynamic-schema-response" para o item selecionado "Comida"](./media/custom-connector-openapi-extensions/x-ms-dynamic-schema-output2.png)

### <a name="properties-for-x-ms-dynamic-schema"></a>Propriedades de x-ms-dynamic-schema
| Nome | Obrigatório ou opcional | Descrição |
| --- | --- | --- |
| **ID da operação** |Necessário |A operação para chamar para buscar o esquema |
| **parâmetros** |Necessário |Um objeto cujas propriedades especificam os parâmetros de entrada necessários para invocar uma operação dynamic-schema |
| **value-path** |Opcional |Uma cadeia de caracteres de caminho que se refere à propriedade que tem o esquema. </br>Se não for especificado, a resposta é assumida para conter o esquema nas propriedades do objeto raiz. |
|  | | |

Veja um exemplo de um parâmetro dinâmico:

``` json
{
  "name": "dynamicListSchema",
  "in": "body",
  "description": "Dynamic schema for items in the selected list",
  "schema": {
    "type": "object",
    "x-ms-dynamic-schema": {
        "operationID": "GetListSchema",
        "parameters": {
          "listID": {
            "parameter": "listID-dynamic"
          }
        },
        "value-path": "items"
    }
  }
}
```

Veja um exemplo de uma resposta dinâmica:

``` json
"DynamicResponseGetListSchema": {
   "type": "object",
   "x-ms-dynamic-schema": {
      "operationID": "GetListSchema",
      "parameters": {
         "listID": {
            "parameter": "listID-dynamic"
         }
      },
      "value-path": "items"
    }
}
```

## <a name="next-steps"></a>Próximas etapas
[Registrar um conector personalizado](register-custom-api.md).

[Usar uma API Web do ASP.NET](customapi-web-api-tutorial.md).

[Registrar uma API do Azure Resource Manager](customapi-azure-resource-manager-tutorial.md).

