---
title: Visão geral do projeto do Adobe Developer
description: Informações sobre como criar um projeto de API do Adobe Developer.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 3d477c6133b74a7e6380d0db1af5125aaa844035
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 1%

---

# Visão geral e pré-requisitos de acesso à API do Places {#developer-prereqs}

Essas informações mostram como criar um projeto no Adobe Developer Console e gerar um token de acesso para ser usado nas solicitações de API do Places.

## Pré-requisitos para acesso do usuário

Verifique com o administrador do sistema da organização se as seguintes tarefas foram concluídas:

* Você foi adicionado à organização.
* Você foi adicionado a um perfil na Adobe Experience Platform.

  Para obter mais informações, consulte *Adicionar um usuário ou um desenvolvedor ao Serviço do Places e aos perfis do Experience Platform Launch* em [Obter acesso ao Serviço do Places](/help/places-gain-access.md).

### Solicitações de REST API

Cada solicitação para a API REST do Places Service requer os seguintes itens:

* Uma ID de organização
* Uma chave de API (também chamada de ID do cliente)
* Segredo do cliente
* Um token de portador

Um Projeto com o [console Adobe Developer](https://developer.adobe.com/console) fornece esses itens.

* Para criar um projeto para a API de serviço do Places, consulte a seção *Criação de um projeto de serviço do Places* abaixo.

>[!IMPORTANT]
>
>Se não conseguir fazer logon no [console Adobe Developer](https://developer.adobe.com/console), ou se o Places Service não for uma opção na *página Criar integrações*, consulte *Requisitos da organização* na [Visão geral da API de serviços da Web](/help/web-service-api/places-web-services.md).

## Criação de um projeto da API de serviço do Places

Para criar um projeto para a API de serviço do Places, conclua o seguinte:

1. Faça logon no [site do Adobe Developer](https://developer.adobe.com) com sua Adobe ID.
2. Clique em **[!UICONTROL Console]** no canto superior direito da página.
3. Se você estiver atribuído a mais de uma organização de Adobe, selecione a organização correta na lista suspensa no canto superior direito da página.
4. Clique no botão **[!UICONTROL Criar novo projeto]**.
5. Clique no botão **[!UICONTROL Adicionar API]** na seção Introdução ao novo projeto.
6. Para selecionar a API do Places, role para baixo a página até o cartão Places e clique na caixa de seleção no canto superior direito do cartão.
7. Clique no botão **[!UICONTROL Next]**.
8. Selecione a opção OAuth Server-to-Server (se houver uma opção).
9. Nomeie a credencial e clique em **[!UICONTROL Avançar]**.
10. Selecione um perfil (qualquer um deve funcionar se houver mais de um).
11. Clique em **[!UICONTROL Salvar e configurar a API]**.
12. No painel esquerdo, clique no link **[!UICONTROL Servidor para servidor do OAuth]** em CREDENCIAIS
13. Essa página fornece o seguinte:
    * Uma maneira de gerar um token de acesso a ser usado nas solicitações de API REST do Places Service.
    * Veja um comando curl para ver um exemplo de como você pode gerar um token de acesso a partir de seu próprio código.
    * Visualizar a ID do cliente (também chamada de chave de API)
    * Exibir o segredo do cliente
    * Exibir a ID da organização
    * Todos são necessários nas solicitações para a API REST do Places Service.
14. É possível renomear o projeto para algo mais descritivo clicando no nome do projeto no caminho no canto superior esquerdo da janela
15. Em seguida, clique no botão **[!UICONTROL Editar projeto]** no canto superior direito da página.

>[!IMPORTANT]
>
>Os tokens de acesso Adobe são válidos **apenas** por 24 horas. Portanto, salve o comando CURL de amostra (etapa 5). Se o token de acesso não for mais válido, você deverá gerá-lo novamente.
