---
title: Criar uma integração de locais
seo-title: Criar uma integração de locais
description: Informações sobre como criar uma integração com o Places.
seo-description: Informações sobre como criar uma integração com o Places.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Criar uma integração de locais {#create-places-integration}

Para criar uma integração de Locais, conclua as seguintes tarefas:

## Gerar um par de chaves públicas e privadas

Para criar uma integração de Locais, você precisa de um par de chaves públicas e privadas. Esses pares podem ser adquiridos ou você pode gerar suas próprias chaves autoassinadas.

Para gerar suas próprias chaves autoassinadas:

1. Em uma janela de terminal, copie e cole cada uma das seguintes linhas e pressione **[!UICONTROL Enter]** após colar cada linha:

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >Recomendamos que você nomeie suas chaves para facilitar a referência e armazene-as em uma pasta. Se você criar várias integrações, poderá identificar e gerenciar facilmente quais chaves pertencem a qual integração.

2. Digite as informações solicitadas pelo OpenSSL:

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

3. Navegue até o diretório onde os arquivos `.key` e `.crt` .

   Por exemplo, no iOS, vá para **[!UICONTROL Macintosh HD]** &gt; **[!UICONTROL users]** &gt; **[!UICONTROL (your user name)]** &gt; **[!UICONTROL Keys]**.

O vídeo a seguir guia você pelo processo de geração do par de chaves:

![](/help/assets/places_integration_video.gif)

## Criar uma integração de Locais no console de E/S da Adobe

Para criar uma integração de Locais:

1. Acesse [https://console.adobe.io](https://console.adobe.io) e faça logon com sua Adobe ID.
2. Se você tiver acesso a mais de uma organização da Experience Cloud, selecione a organização na lista suspensa à esquerda.
3. Clique em **[!UICONTROL New Integration]**.
4. Selecione **[!UICONTROL Access an API]** e clique em **[!UICONTROL Continue]**.
5. Em **[!UICONTROL Experience Cloud]**, selecione **[!UICONTROL Places]** o serviço Adobe ao qual deseja integrar e clique em **[!UICONTROL Continue]**.
6. Selecione **[!UICONTROL New integration]** e clique em **[!UICONTROL Continue]**.
7. Na tela *Criar uma nova integração* , digite um nome e uma descrição.
8. Arraste e solte seu `xxxx_public.crt` arquivo, criado acima, na área **[!UICONTROL Public keys certificates]** solta.
9. At the bottom of the page, click **[!UICONTROL Create integration]**.
10. Após alguns segundos, na tela *Integração criada* , verifique se a seguinte mensagem é exibida:

   `Your integration has been created.`

11. Clique em **[!UICONTROL Continue to integration details]**.

   Uma visão geral da integração com a chave da API, a ID da empresa, a ID da conta técnica e outros detalhes sobre as integrações são exibidos.

## Registre a ID da empresa e a chave da API

1. Na **[!UICONTROL Services]** guia, confirme se **[!UICONTROL Places]** é exibido.
2. Na **[!UICONTROL Overview]** guia, localize e registre a chave da API (ID do cliente) e a ID da organização.

   Essas IDs são necessárias para cada solicitação de API REST do Places.

![](/help/assets/places_orgid_api-key.png)

## Gerar um token JWT

Na **[!UICONTROL JWT]** guia, o console de E/S da Adobe permite que você teste sua integração gerando um JWT e fornecendo o URL de troca.

Para gerar um token JWT:

1. Em um editor de texto, abra seu `private.key` arquivo criado acima.
2. Na **[!UICONTROL JWT]** guia, copie o conteúdo da chave e cole-a no **[!UICONTROL Paste private key]** campo.
3. Clique em **[!UICONTROL Generate JWT]**.
4. Na **[!UICONTROL Sample CURL command]** seção, clique **[!UICONTROL Copy]** e cole o conteúdo no prompt de comando ou na janela terminal.
5. Execute o comando pressionando **[!UICONTROL Enter]** no teclado.
6. Localize o `"token_type": "bearer"` e o `"access_token"` valor.

   O valor do token de acesso do portador é o que você usará nas solicitações da API do Places.

>[!IMPORTANT]
>
>Os tokens de acesso da Adobe são válidos **apenas** por 24 horas, portanto, salve o comando CURL de amostra (etapa 5). Se o token de acesso não for mais válido, será necessário gerar o token novamente.

