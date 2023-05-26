---
title: Visão geral da integração de Adobe I/O
description: Informações sobre como criar uma integração de Adobe I/O.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 5%

---

# Visão geral e pré-requisitos da integração {#integration-prereqs}

Estas informações mostram como criar uma integração de Adobe I/O e de Serviço do Places.

## Pré-requisitos para acesso do usuário

Verifique com o administrador do sistema da organização se as seguintes tarefas foram concluídas:

* O Places Core Service é exibido no Admin Console da sua organização.
* Você foi adicionado à organização.
* Você foi adicionado como usuário do Serviço principal do Places em sua organização.

   Para obter mais informações, consulte *Adicionar um usuário ou um desenvolvedor ao seu Places Service e perfis do Experience Platform Launch* in [Obter acesso ao Places Service](/help/places-gain-access.md).

* Você foi adicionado como um desenvolvedor do Places Core Service em sua organização.

   Para obter mais informações sobre como adicionar desenvolvedores, consulte *Adicionar um usuário ou um desenvolvedor ao seu Places Service e perfis do Experience Platform Launch* in [Obter acesso ao Places Service](/help/places-gain-access.md).

   Para obter mais informações sobre a função de desenvolvedor, consulte [Gerenciar desenvolvedores](https://helpx.adobe.com/br/enterprise/using/manage-developers.html).

### Solicitações de REST API

Cada solicitação para a API REST do Places Service requer os seguintes itens:

* Uma ID de organização
* Uma chave de API
* Um token de portador

Uma integração com o Adobe I/O fornece esses itens e uma maneira de solicitar o token de portador usando um JSON Web Token (JWT).

* Para obter mais informações sobre JWTs, consulte [Introdução a JSON Web Tokens](https://jwt.io/introduction/).
* Para criar uma integração para o Places Service, consulte *Criação de uma integração do Places Service* abaixo.
* Para entender a integração da chave de API, geração de um JWT e certificados de chave pública, consulte [Visão geral da autenticação Adobe I/O](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html).

>[!IMPORTANT]
>
>Se não conseguir fazer logon no console do Adobe I/O ou se o Places Service não for uma opção na *Criar página de integrações*, consulte *Requisitos da organização* in [Visão geral da API de serviços da Web](/help/web-service-api/places-web-services.md).

## Criar uma integração do Places Service

Para criar uma integração do Places Service, conclua as seguintes tarefas:

### Gerar um par de chaves públicas e privadas

Para criar uma integração do Places Service, você precisa de um par de chaves público e privado. Esses pares podem ser comprados ou você pode gerar suas próprias chaves autoassinadas.

Para gerar suas próprias chaves autoassinadas:

1. Em uma janela de terminal, copie e cole cada uma das linhas a seguir e pressione **[!UICONTROL Enter]** após colar cada linha:

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >Recomendamos que você nomeie suas chaves para facilitar a referência e armazene-as em uma pasta. Se você criar várias integrações, poderá identificar e gerenciar facilmente quais chaves pertencem a quais integrações.

1. Digite as informações solicitadas pelo OpenSSL:

   ```text
   Country Name (2 letter code:  // Example: US
   State or Province Name (full name):  // Example: California
   Locality Name (eg, city):  // Example: San Jose
   Organization Name (eg, company):  // Example: Places
   Organizational Unit Name (eg, section):  // Example: Engineering
   Common Name (eg, fully qualified host name):  // Example: places.com
   Email Address:  // Example:  poi@places.com
   ```

   Para obter mais informações sobre OpenSSL, consulte [OpenSSL](https://www.openssl.org/).

   >[!IMPORTANT]
   >
   >As informações fornecidas são incorporadas às chaves.

1. Navegue até o diretório onde o `.key` e `.crt` Os arquivos do estão localizados.

   Por exemplo, no MacOS, acesse **[!UICONTROL Macintosh HD]** > **[!UICONTROL usuários]** > **[!UICONTROL (seu nome de usuário)]** > **[!UICONTROL Chaves]**.

O vídeo a seguir orienta você pelo processo de geração do par de chaves:

![vídeo de integração](/help/assets/places_integration_video.gif)

### Criar uma integração do Places Service no console do Adobe I/O

Para criar uma integração do Places Service:

1. Ir para [https://console.adobe.io](https://console.adobe.io) e faça logon com sua Adobe ID.
1. No **Início rápido** clique em **Criar integração**.
1. Selecionar **[!UICONTROL Acessar uma API]** e clique em **[!UICONTROL Continuar]**.

   **[!UICONTROL Acessar uma API]** é o local padrão.

1. Se você tiver acesso a mais de uma organização de Experience Cloud, selecione a organização na lista suspensa na parte superior direita.
1. Em **[!UICONTROL Experience Cloud]**, selecione **[!UICONTROL Serviço de Places]** como o serviço da Adobe ao qual deseja integrar-se e clique em **[!UICONTROL Continuar]**.
1. Selecionar **[!UICONTROL Nova integração]** e clique em **[!UICONTROL Continuar]**.
1. Na tela Criar uma nova integração, digite um nome e uma descrição.
1. Arraste e solte o `xxxx_public.crt` arquivo, que você criou acima, para o **[!UICONTROL Certificados de chaves públicas]** área de lançamento.
1. Selecione um perfil de produto.

   Se não tiver certeza de qual perfil selecionar, entre em contato com o administrador do sistema.
1. Na parte inferior da página, clique em **[!UICONTROL Criar integração]**.
1. Após alguns segundos, no *Integração criada* , verifique se a seguinte mensagem é exibida:

   `Your integration has been created.`

1. A página de detalhes da integração é exibida com o nome da integração na parte superior.

   A variável **[!UICONTROL Visão geral]** é exibida por padrão e exibe a chave API, a ID da organização, a ID da conta técnica e outros detalhes sobre suas integrações.

### Registre a ID da organização e a chave de API

1. Na página de detalhes da integração, clique no link **[!UICONTROL Serviços]** e confirme se **[!UICONTROL Serviço de Places]** é exibido em **[!UICONTROL Serviços configurados]**.
1. No **[!UICONTROL Visão geral]** localize e registre a Chave da API (ID do cliente) e a ID da organização.

   Essas IDs são necessárias para cada solicitação da API REST do Places Service.

![](/help/assets/places_orgid_api-key.png)

### Gerar um token JWT

Na página de detalhes da integração, clique no link **[!UICONTROL JWT]** para testar a integração gerando um JWT e fornecendo o URL do Exchange.

Para gerar um token JWT:

1. Em um editor de texto, abra `private.key` arquivo criado acima.
1. Na guia **[!UICONTROL JWT]**, copie o conteúdo da chave e cole no campo **[!UICONTROL Colar chave privada]**.
1. Clique em **[!UICONTROL Gerar JWT]**.
1. Na seção de **[!UICONTROL comando CURL de amostra]**, clique em **[!UICONTROL Copiar]** e cole o conteúdo no prompt de comando ou na janela do terminal.
1. Execute o comando pressionando **[!UICONTROL Enter]** no teclado.
1. Localize o `"token_type": "bearer"` e a variável `"access_token"` valor.

   O valor do token de acesso do portador é o que você usará em suas solicitações de API do Places Service.

>[!IMPORTANT]
>
>Os tokens de acesso de Adobe são válidos **somente** por 24 horas, salve o comando CURL de amostra (etapa 5). Se o token de acesso não for mais válido, será necessário gerá-lo novamente.
