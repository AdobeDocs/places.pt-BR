---
title: Visão geral da integração de E/S da Adobe
description: Informações sobre como criar uma integração de E/S da Adobe.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Visão geral e pré-requisitos da integração {#integration-prereqs}

Estas informações mostram como criar uma integração de E/S da Adobe e de um local.

## Pré-requisitos para acesso do usuário

Verifique com o administrador do sistema de sua organização se as seguintes tarefas foram concluídas:

* O Local Core Service é exibido no console de administração da sua organização.
* Você foi adicionado à organização.
* Você foi adicionado como um Usuário ao Serviço Principal do Places em sua organização.

   Para obter mais informações, consulte *Adicionar um usuário ou desenvolvedor aos perfis* do Serviço de localização e do Experience Platform Launch em perguntas [](/help/places-faqs.md)frequentes.

* Você foi adicionado como desenvolvedor ao Places Core Service em sua organização.

   Para obter mais informações sobre como adicionar desenvolvedores, consulte *Adicionar um usuário ou desenvolvedor aos perfis* do Serviço de localização e do Launch da plataforma Experience em perguntas [](/help/places-faqs.md)frequentes.

   Para obter mais informações sobre a função de desenvolvedor, consulte [Gerenciar desenvolvedores](https://helpx.adobe.com/enterprise/using/manage-developers.html).

### Solicitações REST API

Cada solicitação para a API REST do Places requer os seguintes itens:

* Uma ID da organização
* Uma chave de API
* Um token do portador

Uma integração com a E/S da Adobe fornece esses itens e uma maneira de solicitar o token do portador usando um JSON Web Token (JWT).

* Para obter mais informações sobre JWTs, consulte [Introdução aos tokens](https://jwt.io/introduction/)da Web JSON.
* Para criar uma integração para locais, consulte a seção *Criação de uma integração* de locais abaixo.
* Para entender a integração de chave da API, gerando um JWT e certificados de chave pública, consulte Visão geral [da autenticação de E/S da](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html)Adobe.

>[!IMPORTANT]
>
>Se você não conseguir fazer logon no console de E/S da Adobe ou se o Serviço de localização da plataforma de experiência não for uma opção na página ** Criar integrações, consulte Requisitos *da* organização na visão geral [da API de serviços](/help/web-service-api/places-web-services.md)da Web.

## Criar uma integração de locais

Para criar uma integração de Locais, conclua as seguintes tarefas:

### Gerar um par de chaves públicas e privadas

Para criar uma integração de Locais, você precisa de um par de chaves públicas e privadas. Esses pares podem ser adquiridos ou você pode gerar suas próprias chaves autoassinadas.

Para gerar suas próprias chaves autoassinadas:

1. Em uma janela de terminal, copie e cole cada uma das seguintes linhas e pressione **[!UICONTROL Enter]**após colar cada linha:

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >Recomendamos que você nomeie suas chaves para facilitar a referência e armazene-as em uma pasta. Se você criar várias integrações, poderá identificar e gerenciar facilmente quais chaves pertencem a qual integração.

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

   Para obter mais informações sobre o OpenSSL, consulte [OpenSSL](https://www.openssl.org/).

   >[!IMPORTANT]
   >
   >As informações fornecidas são incorporadas às chaves.

1. Navegue até o diretório onde os arquivos `.key` e `.crt` .

   Por exemplo, no iOS, vá para **[!UICONTROL Macintosh HD]**>**[!UICONTROL users]** > **[!UICONTROL (your user name)]**>**[!UICONTROL Keys]**.

O vídeo a seguir guia você pelo processo de geração do par de chaves:

![vídeo de integração](/help/assets/places_integration_video.gif)

### Criar uma integração de Locais no console de E/S da Adobe

Para criar uma integração de Locais:

1. Acesse [https://console.adobe.io](https://console.adobe.io) e faça logon com sua Adobe ID.
1. Na seção **Início** rápido, clique em **Criar integração**.
1. Selecione **[!UICONTROL Access an API]**e clique em**[!UICONTROL Continue]**.

   **[!UICONTROL Access an API]**é o local padrão.

1. Se você tiver acesso a mais de uma organização da Experience Cloud, selecione-a na lista suspensa no canto superior direito.
1. Under **[!UICONTROL Experience Cloud]**, select**[!UICONTROL Places]** as the Adobe service to which you want to integrate and click **[!UICONTROL Continue]**.
1. Selecione **[!UICONTROL New integration]**e clique em**[!UICONTROL Continue]**.
1. Na tela Criar uma nova integração, digite um nome e uma descrição.
1. Arraste e solte seu `xxxx_public.crt` arquivo, criado acima, na área **[!UICONTROL Public keys certificates]**solta.
1. Selecione um perfil de produto.

   Se não tiver certeza de qual perfil selecionar, entre em contato com o administrador do sistema.
1. At the bottom of the page, click **[!UICONTROL Create integration]**.
1. Após alguns segundos, na tela *Integração criada* , verifique se a seguinte mensagem é exibida:

   `Your integration has been created.`

1. A página de detalhes da integração é exibida com o nome da integração na parte superior.

   A **[!UICONTROL Overview]**guia é exibida por padrão e exibe a chave da API, a ID da organização, a ID da conta técnica e outros detalhes sobre as integrações.

### Registre a ID da empresa e a chave da API

1. Na página de detalhes da integração, clique na **[!UICONTROL Services]**guia e confirme se ela**[!UICONTROL Places]** é exibida em **[!UICONTROL Configured Services]**.
1. Na **[!UICONTROL Overview]**guia, localize e registre a chave da API (ID do cliente) e a ID da organização.

   Essas IDs são necessárias para cada solicitação de API REST do Places.

![](/help/assets/places_orgid_api-key.png)

### Gerar um token JWT

Na página de detalhes da integração, clique na **[!UICONTROL JWT]**guia para que você possa testar sua integração gerando um JWT e fornecendo o URL de troca.

Para gerar um token JWT:

1. Em um editor de texto, abra seu `private.key` arquivo criado acima.
1. On the **[!UICONTROL JWT]**tab, copy the contents of the key and paste it in the**[!UICONTROL Paste private key]** field.
1. Clique em **[!UICONTROL Generate JWT]**.
1. In the **[!UICONTROL Sample CURL command]**section, click**[!UICONTROL Copy]** and paste the contents in your command prompt or terminal window.
1. Execute o comando pressionando **[!UICONTROL Enter]**no teclado.
1. Localize o `"token_type": "bearer"` e o `"access_token"` valor.

   O valor do token de acesso do portador é o que você usará nas solicitações da API do Places.

>[!IMPORTANT]
>
>Os tokens de acesso da Adobe são válidos **apenas** por 24 horas, portanto, salve o comando CURL de amostra (etapa 5). Se o token de acesso não for mais válido, é necessário regenerar o token.