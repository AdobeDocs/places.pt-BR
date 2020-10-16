---
title: POIs de upload em massa
description: Esta seção fornece informações sobre como fazer upload em massa dos POIs.
translation-type: tm+mt
source-git-commit: 462df20bb351795dc72009cc18d390cb45e262a8
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---


# Upload em massa de POIs {#bulk-upload-pois}

O botão **Importar POIs** no Serviço de Locais pode ser usado para fazer upload em massa de novos POIs usando um arquivo CSV. Um modelo de planilha de amostra é fornecido para mostrar quais colunas de dados são necessárias e como adicionar metadados personalizados opcionais.

![Tela de importação em massa](/help/assets/Bulk-import.png)

Assista a este vídeo que mostra o processo de importação em massa e edição em massa:

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Insere a importação em massa de serviços e edita POIs](https://www.youtube.com/watch?v=75qVtirsXhg)

## Scripts de API Python

Um conjunto de scripts Python foi criado para simplificar a importação em lote de POIs de um arquivo .csv para um banco de dados POI usando as APIs de serviço da Web. Esses scripts podem ser baixados deste [git repo](https://github.com/adobe/places-scripts)de código aberto.

Antes de executar esses scripts, para acessar as APIs de serviço da Web, consulte *Pré-requisitos para acesso* do usuário na visão geral e pré-requisitos [da](/help/web-service-api/adobe-i-o-integration.md)integração.

Estas são algumas informações sobre os scripts:

>[!TIP]
>
>Estas informações também estão incluídas num ficheiro readme no acordo de recompra [](https://github.com/adobe/places-scripts)git.

## Arquivo CSV

Um arquivo .csv de amostra `places_sample.csv`faz parte deste pacote e inclui os cabeçalhos necessários e uma linha de dados de amostra. Esses cabeçalhos estão todos em minúsculas e correspondem às chaves de metadados reservadas usadas no banco de dados Locais. As colunas que você adicionar ao arquivo .csv serão adicionadas ao banco de dados POI em uma seção de metadados separada para cada POI como pares de chave/valor, e o valor do cabeçalho será usado como a chave.

Esta é uma lista das colunas e dos valores que você precisa usar:

* `lib_id`

   Uma ID de biblioteca válida obtida do banco de dados POI.

* `type`

   O ponto é atualmente o único valor válido.

* `longitude`

   Um valor entre -180 e 180.

* `latitude`

   Um valor entre -85 e 85.

* `radius`

   Um valor entre 10 e 20.000.

### Valores da coluna

Os valores das seguintes colunas são usados na interface do usuário do Serviço de Locais:

* cor, que é usada como a cor do pino que representa o local do POI no mapa da interface do usuário do Serviço de Locais.
   * Os valores válidos são &quot;&quot;, #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B e #3DC8DE e &quot;&quot;.
   * Se o valor for deixado em branco, a interface do usuário do Places Service usará azul como a cor padrão.

      Os valores correspondem a azul (#3E76D0), roxo (#AA99E8), fuschia (#DC2ABA), laranja (#FC685B), laranja claro (#FC962E), amarelo (#F6C436), verde-claro (#BECE5D), verde (#6 1B56B) e azul claro (#3DC8DE), respectivamente.

* ícone, que é usado como o ícone no pino que representa o local do POI no mapa da interface do usuário do Serviço de Locais.

   * Os valores válidos são &quot;&quot;, loja, hotelbed, carro, avião, avião, trem, navio, estádio, parque de diversões, âncora, beaker, campainha, sino, bico, livro, caixa, pasta, browse, pincel, edifício, calculadora, câmera, relógio, relógio, luz, acompanhar, jogo, mulher, homem, presente, martelo, coração, casa, chave, lançamento, lâmpada, caixa de correio, dinheiro promover, fita, shoppingCart, estrela, público alvo, bule, thumbDown, thumbUp, armadilha, troféu, chave inglesa.

      Os valores dos ícones são listados na ordem em que aparecem na ilustração a seguir:

      ![ícones na interface do usuário](/help/assets/UI_icons.png)

   * Se o valor for deixado em branco, a interface do usuário usará star como o ícone padrão.

* As colunas que não são mencionadas podem ser deixadas em branco.

## Execução do script

1. Baixe arquivos do [git repo](https://github.com/adobe/places-scripts) para o diretório local.
1. Em um editor de texto, abra o `config.py` arquivo e preencha as seguintes tarefas:

   a. Edite os seguintes valores de variável como strings:

   * `csv_file_path`

      Este é o caminho para o seu `.csv` arquivo.

   * `access_code`

      Este é o código de acesso obtido da chamada para Adobe IMS. Para obter informações sobre como obter esse código de acesso, consulte *Pré-requisitos para acesso* do usuário na visão geral e pré-requisitos [da](/help/web-service-api/adobe-i-o-integration.md)integração.

   * `org_id`

      A Experience Cloud orgID na qual os POIs devem ser importados. Para obter informações sobre como obter a ID da organização, consulte *Pré-requisitos para acesso* do usuário na visão geral e pré-requisitos [da](/help/web-service-api/adobe-i-o-integration.md)integração.

   * `api_key`

      Esta é a chave da API REST do Places obtida da integração do Adobe I/O Places. Para obter informações sobre como obter a chave da API, consulte *Pré-requisitos para acesso* do usuário na visão geral e pré-requisitos [da](/help/web-service-api/adobe-i-o-integration.md)integração.
   b. Salve as alterações.

1. Em uma janela de terminal, navegue até o `…/places-scripts/import/` diretório.
1. Digite `python ./places_import.py` e pressione a tecla **[!UICONTROL enter]** (**[!UICONTROL return]**).


## Verificações CSV pré-importação

Inicialmente, o script conclui as seguintes verificações no arquivo .csv:

* Se um `.csv` arquivo foi especificado.
* Se o caminho do arquivo é válido.
* Se os cabeçalhos de metadados reservados estão incluídos.

   Os cabeçalhos de metadados reservados são lib_id, nome, descrição, tipo, longitude, latitude, raio, país, estado, cidade, rua, categoria, ícone e cor.

   >[!TIP]
   >
   >Os cabeçalhos estão todos em minúsculas e podem ser listados em qualquer ordem.

* Verifica os valores das colunas especificadas na seção do arquivo CSV.

Se forem encontrados erros, o script imprimirá os erros e será abortado. Se nenhum erro for encontrado, o script tentará importar os POIs em lotes de 1000. Se o lote for importado com êxito, o script reportará um código de status de 200. Se o lote não for importado com êxito, serão reportados erros.

## Testes de unidade

Os testes de unidade estão no `tests.py` arquivo, devem ser executados antes de cada solicitação e todos devem ser aprovados. Testes adicionais devem ser adicionados com um novo código. Para executar os testes, navegue até o `…/places-scripts/import/` diretório e insira `python ./places_import.py` no terminal.
