---
title: ASP.NET Core Docker コンテナーを Docker Hub にデプロイする | Microsoft Docs
description: Visual Studio コンテナー ツールを使用して、ASP.NET Core Web アプリを Docker Hub にデプロイする方法を説明します
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 07/23/2019
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 2a6db2771525010d73fdeeea12ff4aebd99a1bd2
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2020
ms.locfileid: "89485139"
---
# <a name="deploy-to-docker-hub"></a>Docker Hub に配置する

Docker Hub によって、便利なホスティング サービスがイメージ リポジトリに提供されます。 Docker Hub は、Visual Studio から手動で簡単にデプロイできます。

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Docker アカウントと Docker Hub リポジトリを作成する

まだアカウントを持っていない場合は、Docker アカウントに[サインアップ](https://hub.docker.com/signup)してください。

Docker Hub リポジトリを持っていない場合は、[Docker Hub](https://hub.docker.com/) で作成します。

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>1 つのプロジェクトのイメージを Docker Hub に発行する

1. プロジェクト ノードを右クリックし、 **[発行]** を選択します。デプロイ オプションを示す画面が表示されます。

   ![デプロイ オプションのスクリーンショット](media/container-tools/vs-2019/docker-container-registry.png)

1. **[Docker コンテナー レジストリ]** を選択し、 **[Docker Hub]** を選択します。

   ![発行ダイアログのスクリーンショット - [Docker Hub] を選択する](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. Docker 資格情報を入力します。

   ![[Docker Hub] ダイアログのスクリーンショット](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. 自分のリポジトリ (組織の一部ではない) に接続する場合は、 **[個人のレポジトリに発行する]** チェックボックスをオンのままにします。 リポジトリが組織によって所有されている場合は、チェックボックスをオフにして、組織名を入力します。 接続しているリポジトリへのアクセス許可を持つ Docker アカウントの Docker ユーザー名とパスワードを入力して、 **[保存]** を選択します。  

   Visual Studio では、Docker Hub へのイメージのデプロイが試行されます。  成功した場合、 **[発行]** 画面に、リポジトリ イメージの URL、イメージ タグ、リポジトリ、ビルド構成 (**リリース**など) が表示されます。

   ![[発行] 画面のスクリーンショット](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. このページの **[発行]** ボタンをクリックすると、いつでもイメージを更新できます。  または、URL の下にあるリンクを使用して、プロファイルを変更または削除することもできます。

## <a name="next-steps"></a>次の手順

[Azure Container Registry へのデプロイ](hosting-web-apps-in-docker.md) に関するページに記載されている手順を行い、[Azure Container Registry](/azure/container-registry/) に発行します。

[Azure Pipelines](/azure/devops/pipelines/?view=azure-devops) を使用して、継続的インテグレーションおよび継続的配信 (CI/CD) を設定します。

## <a name="see-also"></a>関連項目

[Azure App Service への発行](deploy-app-service.md)
[Visual Studio コンテナー ツール](./index.yml).