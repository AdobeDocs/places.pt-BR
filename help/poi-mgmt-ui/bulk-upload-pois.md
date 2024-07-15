---
title: POIs de upload em massa
description: Esta seção fornece informações sobre como fazer upload em massa dos POIs.
exl-id: 72704bfc-5837-4439-bdb2-e77ddf935639
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# Upload em massa de POIs {#bulk-upload-pois}

O botão **Importar POIs** no Serviço do Places pode ser usado para carregar novos POIs em massa usando um arquivo CSV. Um modelo de planilha de exemplo é fornecido para mostrar quais colunas de dados são necessárias e como adicionar metadados personalizados opcionais.

![Tela de Importação em Massa](/help/assets/Bulk-import.png)

Veja este vídeo que mostra o processo de importação e edição de itens em massa:

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Importação e Edição de POIs em Massa do Serviço Places](https://www.youtube.com/watch?v=75qVtirsXhg)

## Scripts da API Python

Um conjunto de scripts Python foi criado para simplificar a importação em lote de POIs de um arquivo .csv para um banco de dados de POI usando as APIs de serviço da Web. Estes scripts podem ser baixados deste repositório Git de código aberto [1}.](https://github.com/adobe/places-scripts)

Antes de executar esses scripts, para acessar as APIs de serviços Web, consulte *Pré-requisitos para acesso do usuário* em [Visão geral e pré-requisitos de integração](/help/web-service-api/adobe-i-o-integration.md).

Estas são algumas informações sobre os scripts:

>[!TIP]
>
>Essas informações também estão incluídas em um arquivo readme no [repositório Git](https://github.com/adobe/places-scripts).

## Arquivo CSV

Um arquivo .csv de exemplo, `places_sample.csv`, faz parte desse pacote e inclui os cabeçalhos necessários e uma linha de dados de exemplo. Todos esses cabeçalhos estão em minúsculas e correspondem às chaves de metadados reservadas usadas no banco de dados do Places. As colunas adicionadas ao arquivo .csv serão adicionadas ao banco de dados de POI em uma seção de metadados separada para cada POI como pares de chave/valor, e o valor do cabeçalho será usado como a chave.

Esta é uma lista das colunas e dos valores que você precisa usar:

* `lib_id`

  Uma ID de biblioteca válida obtida do banco de dados de POI.

* `type`

  O ponto é o único valor válido no momento.

* `longitude`

  Um valor entre -180 e 180.

* `latitude`

  Um valor entre -85 e 85.

* `radius`

  Um valor entre 10 e 20.000.

### Valores da coluna

Os valores das seguintes colunas são usados na interface do usuário do Places Service:

* cor, usada como a cor do pino que representa o local do POI no mapa da interface do usuário do Places Service.
   * Os valores válidos são &quot;&quot;, #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B, #3DC8DE e &quot;&quot;.
   * Se o valor for deixado em branco, a interface do usuário do Places Service usará azul como a cor padrão.

     Os valores correspondem a azul (#3E76D0), roxo (#AA99E8), fuschia (#DC2ABA), laranja (#FC685B), laranja claro (#FC962E), amarelo (#F6C436), verde claro (#BECE5D), verde (#61B56B) e azul claro (#3DC8DE), respectivamente.

* ícone, que é usado como o ícone no pino que representa o local do POI no mapa da interface do usuário do Places Service.

   * Os valores válidos são &quot;&quot;, loja, cama de hotel, carro, avião, trem, navio, estádio, parque de diversões, âncora, béquer, sino, lance, livro, caixa, pasta, navegação, escova, edifício, calculadora, câmera, relógio, educação, lanterna, seguir, jogo, feminino, masculino, presente, martelo, coração, casa, chave, lançamento, lâmpada, caixa de correio, dinheiro, pin, promover, fita, carrinho de compras, estrela, alvo, bule, thumbDown, thumbUp, armadilha, troféu, chave inglesa.

     Os valores de ícone são listados na ordem em que aparecem na seguinte ilustração:

     ![ícones na interface do usuário](/help/assets/UI_icons.png)

   * Se o valor for deixado em branco, a interface do usuário usará estrela como ícone padrão.

* As colunas que não são mencionadas podem ser deixadas em branco.

## Execução do script

1. Baixe os arquivos do [repositório Git](https://github.com/adobe/places-scripts) no diretório local.
1. Em um editor de texto, abra o arquivo `config.py` e conclua as seguintes tarefas:

   a. Edite os seguintes valores de variável como strings:

   * `csv_file_path`

     Este é o caminho para o seu arquivo `.csv`.

   * `access_code`

     Esse é o código de acesso que foi obtido da chamada para o Adobe IMS. Para obter informações sobre como obter este código de acesso, consulte *Pré-requisitos para acesso do usuário* em [Visão geral e pré-requisitos da integração](/help/web-service-api/adobe-i-o-integration.md).

   * `org_id`

     A Experience Cloud orgID para onde os POIs devem ser importados. Para obter informações sobre como obter a ID da organização, consulte *Pré-requisitos para acesso do usuário* em [Visão geral e pré-requisitos de integração](/help/web-service-api/adobe-i-o-integration.md).

   * `api_key`

     Esta é a chave da API REST do Places obtida por meio da integração do Adobe I/O Places. Para obter informações sobre como obter a chave de API, consulte *Pré-requisitos para acesso do usuário* em [Visão geral e pré-requisitos de integração](/help/web-service-api/adobe-i-o-integration.md).

   b. Salve as alterações.

1. Em uma janela de terminal, navegue até o diretório `…/places-scripts/import/`.
1. Digite `python ./places_import.py` e pressione a tecla **[!UICONTROL enter]** (**[!UICONTROL return]**).


## Verificações CSV de pré-importação

O script inicialmente conclui as seguintes verificações no arquivo .csv:

* Se um arquivo `.csv` foi especificado.
* Se o caminho do arquivo é válido.
* Se os cabeçalhos de metadados reservados estão incluídos.

  Os cabeçalhos de metadados reservados são lib_id, name, description, type, longitude, latitude, raio, país, estado, cidade, rua, categoria, ícone e cor.

  >[!TIP]
  >
  >Todos os cabeçalhos estão em minúsculas e podem ser listados em qualquer ordem.

* Verifica os valores das colunas especificadas na seção do arquivo CSV.

Se forem encontrados erros, o script imprimirá os erros e será abortado. Se nenhum erro for encontrado, o script tentará importar os POIs em lotes de 1000. Se o lote for importado com sucesso, o script relata um código de status 200. Se o lote não for importado com sucesso, serão relatados erros.

## Testes de unidade

Testes de unidade estão no arquivo `tests.py`, devem ser executados antes de cada solicitação de pull e todos devem passar. Testes adicionais devem ser adicionados com o novo código. Para executar os testes, navegue até o diretório `…/places-scripts/import/` e digite `python ./places_import.py` no terminal.
