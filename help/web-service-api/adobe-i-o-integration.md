---
title: Visão geral do projeto do Adobe Developer
description: Informações sobre como criar um projeto de API do Adobe Developer.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 3d477c6133b74a7e6380d0db1af5125aaa844035
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 2%

---

# Visão geral e pré-requisitos de acesso à API do Places {#developer-prereqs}

Essas informações mostram como criar um projeto no Console do Adobe Developer e gerar um token de acesso para ser usado nas solicitações de API do Places.

## Pré-requisitos para acesso do usuário

Verifique com o administrador do sistema da organização se as seguintes tarefas foram concluídas:

* Você foi adicionado à organização.
* Você foi adicionado a um perfil na Adobe Experience Platform.

  Para obter mais informações, consulte *Adicionar um usuário ou um desenvolvedor ao seu Places Service e perfis do Experience Platform Launch* in [Obter acesso ao Places Service](/help/places-gain-access.md).

### Solicitações de REST API

Cada solicitação para a API REST do Places Service requer os seguintes itens:

* Uma ID de organização
* Uma chave de API (também chamada de ID do cliente)
* Segredo do cliente
* Um token de portador

Um projeto com a [Console do Adobe Developer](https://developer.adobe.com/console) O fornece esses itens.

* Para criar um projeto para a API de serviço do Places, consulte a *Criação de um projeto do Places Service* abaixo.

>[!IMPORTANT]
>
>Se não conseguir fazer logon no [Console do Adobe Developer](https://developer.adobe.com/console), ou se o Places Service não for uma opção no *Criar página de integrações*, consulte *Requisitos da organização* in [Visão geral da API de serviços da Web](/help/web-service-api/places-web-services.md).

## Criação de um projeto da API de serviço do Places

Para criar um projeto para a API de serviço do Places, conclua o seguinte:

1. Efetue logon no [Site do Adobe Developer](https://developer.adobe.com) com sua Adobe ID.
2. Clique em **[!UICONTROL Console]** no canto superior direito da página.
3. Se você estiver atribuído a mais de uma organização de Adobe, selecione a organização correta na lista suspensa no canto superior direito da página.
4. Clique em **[!UICONTROL Criar novo projeto]** botão.
5. Clique em **[!UICONTROL Adicionar API]** na seção Introdução ao novo projeto.
6. Para selecionar a API do Places, role para baixo a página até o cartão Places e clique na caixa de seleção no canto superior direito do cartão.
7. Clique no botão **[!UICONTROL Avançar.]**
8. Selecione a opção OAuth Server-to-Server (se houver uma opção).
9. Nomeie a credencial e clique em **[!UICONTROL Próxima]**.
10. Selecione um perfil (qualquer um deve funcionar se houver mais de um).
11. Clique em **[!UICONTROL Salvar e configurar API]**.
12. No painel esquerdo, clique na guia **[!UICONTROL Servidor OAuth para servidor]** link em CREDENCIAIS
13. Essa página fornece o seguinte:
   * Uma maneira de gerar um token de acesso a ser usado nas solicitações de API REST do Places Service.
   * Veja um comando curl para ver um exemplo de como você pode gerar um token de acesso a partir de seu próprio código.
   * Visualizar a ID do cliente (também chamada de chave de API)
   * Exibir o segredo do cliente
   * Exibir a ID da organização
   * Todos são necessários nas solicitações para a API REST do Places Service.
14. É possível renomear o projeto para algo mais descritivo clicando no nome do projeto no caminho no canto superior esquerdo da janela
15. Em seguida, clique no link **[!UICONTROL Editar projeto]** no canto superior direito da página.

>[!IMPORTANT]
>
>Os tokens de acesso de Adobe são válidos **somente** por 24 horas, salve o comando CURL de amostra (etapa 5). Se o token de acesso não for mais válido, você deverá gerá-lo novamente.
