---
title: POIs de upload em massa
seo-title: POIs de upload em massa
description: Esta seção fornece informações sobre como fazer upload em massa dos POIs.
seo-description: Esta seção fornece informações sobre como fazer upload em massa dos POIs.
translation-type: tm+mt
source-git-commit: 3a9653dcc7f5d18b717c4bb59424b8cad7104dd7

---


# Upload em massa de POIs {#bulk-upload-pois}

Um conjunto de scripts Python foi criado para simplificar a importação em lote de POIs de um arquivo .csv para um banco de dados POI usando as APIs de serviço da Web. Esses scripts podem ser baixados deste [git repo](https://github.com/adobe/places-scripts)de código aberto.

Antes de executar esses scripts, para garantir o acesso às APIs de serviço da Web, consulte *Pré-requisitos para acesso* do usuário na visão geral [de integração de E/S da](/help/web-service-api/adobe-i-o-integration.md)Adobe.

Estas são algumas informações sobre os scripts:

>[!TIP]
>
>Estas informações também estão incluídas num ficheiro readme no acordo de recompra [](https://github.com/adobe/places-scripts)git.

## Arquivo CSV

Um arquivo .csv de amostra `places_sample.csv`faz parte deste pacote e inclui os cabeçalhos necessários e uma linha de dados de amostra. Esses cabeçalhos estão todos em minúsculas e correspondem às chaves de metadados reservadas usadas no banco de dados Locais. Quando você adiciona cabeçalhos, as colunas adicionais são adicionadas ao banco de dados POI em uma seção de metadados separada para cada POI como pares de chave/valor.

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

   Um valor entre 10 e 2000.

### Valores da coluna

Os valores das seguintes colunas são usados na interface do usuário do Serviço de Localização:

* cor, que é usada como a cor do pino que representa a localização do POI no mapa da interface do usuário do Serviço de localização.
   * Os valores válidos são "", #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B e #3DC8DE.
   * Se o valor for deixado em branco, a interface do usuário do Serviço de localização usará azul como a cor padrão.

      Os valores correspondem a azul, roxo, fuschia, laranja, laranja claro, amarelo, verde claro, verde e azul claro, respectivamente.

* ícone, que é usado como o ícone no pino que representa o local do POI no mapa da interface do usuário do Serviço de Localização
   * Os valores válidos são "", âncora, beaker, bell, browmer, book, pincel, edifício, calculadora, câmera, shopping, clock, box, flashlight, follow, bid, faixa, Education, hammer, coração, casa, chave, mailbox, masculino, promove, dinheiro, armadilha, jogo, presente, lançamento, estrela, lâmpada, pin, alvo, bule, thumbDown, thumbUp, pasta, troféu, fêmea e chave inglesa.
   * Se o valor for deixado em branco, a interface do usuário usará star como o ícone padrão.

* As colunas não mencionadas podem ser deixadas em branco.

## Execução do script

1. Baixe os arquivos no diretório apropriado.
1. Em um editor de texto, abra o `config.py` arquivo e conclua as seguintes tarefas:

   a. Edite os seguintes valores de variável como strings:

   * `csv_file_path`

      O caminho para o seu `.csv` arquivo.

   * `access_code`

      Esse é o código de acesso obtido da chamada para o Adobe IMS.

   * `org_id`

      A orgID da Experience Cloud na qual os POIs devem ser importados.

   * `api_key`

      Esta é a chave da API REST do Places obtida da Integração de E/S do Adobe.
   b.Salve as alterações.

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



