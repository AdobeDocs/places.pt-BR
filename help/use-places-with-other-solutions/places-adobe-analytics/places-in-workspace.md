---
title: Relatório sobre dados de localização no Analytics Workspace
description: Esta seção fornece informações sobre como criar relatórios sobre dados de localização no Analytics Workspace.
exl-id: 45ca3c80-71b7-41de-9b00-645504061935
source-git-commit: d5c216aebd99ffef01c37c17c62576835b52438b
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

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


## 1. Criar uma regra do Launch

Crie uma regra que fará com que o SDK envie dados para o Analytics quando o dispositivo inserir um POI. A criação desse tipo de regra é descrita na página [Enviar dados de entrada e saída do POI para o Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md).

Neste exemplo, a ação da regra tem os seguintes valores definidos para a solicitação do Analytics:

* A **[!UICONTROL Ação]** recebeu um valor de **[!UICONTROL Entrada de Locais]**.

* A chave de dados de contexto **[!UICONTROL poi.name]** está definida com o valor do elemento de dados **[!UICONTROL {%%POI Name%}]**.

![&quot;definir uma ação&quot;](/help/assets/pt-setAction.png)

## 2. Criar variáveis do Analytics

Para mapear os dados de contexto (enviados na etapa 1), as variáveis devem ser criadas primeiro para o conjunto de relatórios do Analytics. Para obter mais informações sobre como criar variáveis no Analytics, consulte [Variáveis de conversão (eVars)](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html?lang=pt-BR).

Neste exemplo, uma variável de conversão, **[!UICONTROL Evar2]**, foi criada e nomeada **[!UICONTROL Nome do POI do Places]**. Serão necessárias variáveis adicionais para cada variável de local que você deseja expor nos relatórios.

![&quot;criar uma variável de análise&quot;](/help/assets/aa-evar.png)

## 3. Criar regras de processamento

Essa etapa é necessária para mapear dados de contexto (etapa 1) para variáveis do Analytics (etapa 2). Para obter mais informações sobre como criar regras de processamento, consulte [Visão geral das regras de processamento](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/c-processing-rules/processing-rules.html?lang=pt-BR).

Neste exemplo, uma regra de processamento foi criada para mapear o valor de dados de contexto **[!UICONTROL poi.name]** em **[!UICONTROL Nome do POI do Places (eVar 2)]**. Regras de processamento adicionais precisarão ser criadas para cada variável de local criada.

![&quot;criar uma regra de processamento&quot;](/help/assets/aa-processing-rule.png)

## 4. Gerar um relatório no Workspace

Esta etapa mostra um relatório básico no Analytics Workspace para exibir os dados coletados nas etapas 1 a 3. Para obter mais informações sobre como usar o Analytics Workspace, consulte [Visão geral do Analytics Workspace](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html?lang=pt-BR).

Neste exemplo, o relatório tem as seguintes configurações:

* Métrica - **[!UICONTROL Ocorrências]**

* Dimension - **[!UICONTROL Nome da ação]**

   * Detalhado por Dimension - **[!UICONTROL Nome do POI do Places]**

![&quot;criar um relatório no espaço de trabalho&quot;](/help/assets/aa-workspace.png)
