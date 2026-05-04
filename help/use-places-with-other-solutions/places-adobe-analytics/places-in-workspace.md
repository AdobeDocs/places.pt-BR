---
title: Relatório sobre dados de localização no Analytics Workspace
description: Esta seção fornece informações sobre como criar relatórios sobre dados de localização no Analytics Workspace.
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
TQID: https://experienceleague.adobe.com/Xym9Ko8czyd3wYWVo22sQoK6gk-VvftGVHfIDUys06E
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e55547f1-a1ff-40c6-8978-026e40ab7fa4
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: b069d60e-95f3-44d6-95a8-ddc862a4bc38
  - id: c20d46e7-1c7d-476c-a50e-3961d4dce35f
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 483
ht-degree: 6%

---

# Relatório sobre dados de localização no Analytics Workspace {#places-in-workspace}

Este documento mostra um exemplo de como criar relatórios sobre os dados de localização no Analytics Workspace. Cada etapa conterá um resumo de alto nível, com detalhes fornecidos fazendo referência a outras páginas de documentação.

## Pré-requisitos

Este documento supõe o seguinte:

1. A extensão do Places é implementada em seu aplicativo.

   Para obter mais informações sobre como implementar a extensão do Places, consulte [Extensões do Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).

1. O usuário do Adobe Analytics é um administrador e tem acesso às regras de processamento.

   Para obter mais informações sobre regras de processamento, consulte [Visão geral das regras de processamento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=pt-BR).

1. Na propriedade do Launch, os elementos de dados foram criados para as variáveis de Serviço do Places desejadas.

   Para obter mais informações sobre elementos de dados no Launch, consulte [Definir um elemento de dados](/help/use-places-launch-workflow/define-data-elements.md).


## &#x200B;1. Criar uma regra do Launch

Crie uma regra que fará com que o SDK envie dados para o Analytics quando o dispositivo inserir um POI. A criação desse tipo de regra é descrita na página [Enviar dados de entrada e saída do POI para o Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

Neste exemplo, a ação da regra tem os seguintes valores definidos para a solicitação do Analytics:

* A **[!UICONTROL Ação]** recebeu um valor de **[!UICONTROL Entrada de Locais]**.

* A chave de dados de contexto **[!UICONTROL poi.name]** está definida com o valor do elemento de dados **[!UICONTROL {%%POI Name%}]**.

![&quot;definir uma ação&quot;](/help/assets/pt-setAction.png)

## &#x200B;2. Criar variáveis do Analytics

Para mapear os dados de contexto (enviados na etapa 1), as variáveis devem ser criadas primeiro para o conjunto de relatórios do Analytics. Para obter mais informações sobre como criar variáveis no Analytics, consulte [Variáveis de conversão (eVars)](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html?lang=pt-BR).

Neste exemplo, uma variável de conversão, **[!UICONTROL Evar2]**, foi criada e nomeada **[!UICONTROL Nome do POI do Places]**. Serão necessárias variáveis adicionais para cada variável de local que você deseja expor nos relatórios.

![&quot;criar uma variável de análise&quot;](/help/assets/aa-evar.png)

## &#x200B;3. Criar regras de processamento

Essa etapa é necessária para mapear dados de contexto (etapa 1) para variáveis do Analytics (etapa 2). Para obter mais informações sobre como criar regras de processamento, consulte [Visão geral das regras de processamento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=pt-BR).

Neste exemplo, uma regra de processamento foi criada para mapear o valor de dados de contexto **[!UICONTROL poi.name]** em **[!UICONTROL Nome do POI do Places (eVar2)]**. Regras de processamento adicionais precisarão ser criadas para cada variável de local criada.

![&quot;criar uma regra de processamento&quot;](/help/assets/aa-processing-rule.png)

## &#x200B;4. Gerar um relatório no Workspace

Esta etapa mostra um relatório básico no Analytics Workspace para exibir os dados coletados nas etapas 1 a 3. Para obter mais informações sobre como usar o Analytics Workspace, consulte [Visão geral do Analytics Workspace](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html?lang=pt-BR).

Neste exemplo, o relatório tem as seguintes configurações:

* Métrica - **[!UICONTROL Ocorrências]**

* Dimension - **[!UICONTROL Nome da Ação]**

   * Detalhado por Dimension - **[!UICONTROL Nome do POI do Places]**

![&quot;criar um relatório no espaço de trabalho&quot;](/help/assets/aa-workspace.png)
