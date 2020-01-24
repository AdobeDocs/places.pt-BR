---
title: Relatório de dados de localização no Analytics Workspace
description: Esta seção fornece informações sobre como relatar os dados de localização no Analytics Workspace.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Relatório dos dados de localização na Analysis Workspace {#places-in-workspace}

Este documento mostra um exemplo de como relatar os dados de localização na Analysis Workspace. Cada etapa conterá um resumo de alto nível, com detalhes fornecidos por referência a outras páginas de documentação.

## Pré-requisitos

Este documento presume o seguinte:

1. A extensão Locais é implementada em seu aplicativo.

   Para obter mais informações sobre como implementar a extensão Locais, consulte Extensões [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Locais.

1. O usuário do Adobe Analytics é um administrador e tem acesso às regras de processamento.

   Para obter mais informações sobre regras de processamento, consulte [Visão geral das regras de processamento](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

1. Na propriedade Launch, os elementos de dados foram criados para as variáveis do Serviço de Locais desejadas.

   Para obter mais informações sobre elementos de dados no Launch, consulte [Definir um elemento](/help/use-places-launch-workflow/define-data-elements.md)de dados.


## 1. Criar uma regra de inicialização

Crie uma regra que fará com que o SDK envie dados para o Analytics quando o dispositivo entrar em um POI. A criação desse tipo de regra é descrita na página [Enviar dados de entrada e saída do POI para o Analytics](/help/use-places-with-other-solutions/places-adobe-analytics/use-places-adobe-analytics.md) .

Neste exemplo, a ação da regra tem os seguintes valores definidos para a solicitação do Analytics:

* **[!UICONTROL Action]**é fornecido um valor de**[!UICONTROL Places Entry]**.

* A chave de dados de contexto **[!UICONTROL poi.name]**é definida como o valor do elemento de dados**[!UICONTROL {%%POI Name%%}]**.

![&quot;definir uma ação&quot;](/help/assets/pt-setAction.png)

## 2. Criar variáveis do Analytics

Para mapear os dados de contexto (enviados na etapa 1), as variáveis devem primeiro ser criadas para o conjunto de relatórios do Analytics. Para obter mais informações sobre como criar variáveis no Analytics, consulte Variáveis [de conversão (eVars)](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-conversion-variables-evar.html).

Neste exemplo, uma variável de conversão, **[!UICONTROL Evar2]**, foi criada e nomeada**[!UICONTROL Places POI Name]**. Variáveis adicionais precisam ser criadas para cada variável de localização que você deseja expor nos relatórios.

![&quot;criar uma variável de análise&quot;](/help/assets/aa-evar.png)

## 3. Criar regras de processamento

Essa etapa é necessária para mapear dados de contexto (etapa 1) para as variáveis do Analytics (etapa 2). For more information on creating processing rules, see [Processing rules overview](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Neste exemplo, uma regra de processamento foi criada para mapear o valor de dados de contexto **[!UICONTROL poi.name]**para**[!UICONTROL Places POI Name (eVar2)]**. Regras de processamento adicionais precisam ser criadas para cada variável de localização criada.

![&quot;criar uma regra de processamento&quot;](/help/assets/aa-processing-rule.png)

## 4. Gerar um relatório no Workspace

Esta etapa mostra um relatório básico no Analytics Workspace para exibir os dados coletados nas etapas 1 a 3. Para obter mais informações sobre como usar o Analytics Workspace, consulte Visão geral [](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/analysis-workspace-features.html)do Analytics Workspace.

Neste exemplo, o relatório tem as seguintes configurações:

* Métrica - **[!UICONTROL Occurrences]**

* Dimensão - **[!UICONTROL Action Name]**

   * Analisado por dimensão - **[!UICONTROL Places POI Name]**

![&quot;criar um relatório no espaço de trabalho&quot;](/help/assets/aa-workspace.png)
