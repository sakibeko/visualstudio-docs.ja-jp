---
title: ClickOnce とアプリケーションの設定 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8e1ffe6d6f32cfad137d5890715a5a0032a29d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696690"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce とアプリケーション設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows フォームのアプリケーション設定を使用すると、クライアントでカスタムアプリケーションとユーザー設定を簡単に作成、保存、および保守できます。 次のドキュメントでは、ClickOnce アプリケーションでのアプリケーション設定ファイルの動作と、ユーザーが次のバージョンにアップグレードしたときに ClickOnce が設定を移行する方法について説明します。  
  
 以下の情報は、既定のアプリケーション設定プロバイダーであるクラスにのみ適用され <xref:System.Configuration.LocalFileSettingsProvider> ます。 カスタムプロバイダーを提供する場合、そのプロバイダーは、データの格納方法と、バージョン間での設定のアップグレード方法を決定します。 アプリケーション設定プロバイダーの詳細については、「 [アプリケーション設定のアーキテクチャ](https://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562)」を参照してください。  
  
## <a name="application-settings-files"></a>アプリケーション設定ファイル  
 アプリケーション設定は、 *アプリ*.exe.config と user.config の2つのファイルを使用します。 *app* は Windows フォームアプリケーションの名前です。 user.config は、アプリケーションでユーザースコープ設定を初めて保存するときに、クライアントで作成されます。 これに対して、設定の既定値を定義すると、*アプリ*.exe.config が展開の前に存在します。 このファイルは、 **Publish** コマンドを使用すると、Visual Studio によって自動的にインクルードされます。 Mage.exe または MageUI.exe を使用して ClickOnce アプリケーションを作成する場合は、アプリケーションマニフェストを設定するときに、このファイルがアプリケーションの他のファイルに含まれていることを確認する必要があります。  
  
 ClickOnce を使用して配置されていない Windows フォームアプリケーションでは、アプリケーションの *アプリ*.exe.config ファイルはアプリケーションディレクトリに格納され、user.config ファイルはユーザーの **Documents and Settings** フォルダーに格納されます。 ClickOnce アプリケーションでは、 *アプリ*.exe.config は clickonce アプリケーションキャッシュ内のアプリケーションディレクトリに存在し、user.config はそのアプリケーションの clickonce データディレクトリに存在します。  
  
 アプリケーションの配置方法に関係なく、アプリケーションの設定によって、 *アプリ*.exe.config に安全に読み取りアクセスでき、user.config への安全な読み取り/書き込みアクセスが保証されます。  
  
 ClickOnce アプリケーションでは、アプリケーション設定で使用される構成ファイルのサイズは、ClickOnce キャッシュのサイズによって制限されます。 詳細については、「 [ClickOnce キャッシュの概要](../deployment/clickonce-cache-overview.md)」を参照してください。  
  
## <a name="version-upgrades"></a>バージョンのアップグレード  
 ClickOnce アプリケーションの各バージョンが他のすべてのバージョンから分離されているのと同様に、ClickOnce アプリケーションのアプリケーション設定は、他のバージョンの設定からも分離されます。 ユーザーがアプリケーションの新しいバージョンにアップグレードすると、アプリケーションの設定によって、最新の (最も番号が付いた) バージョンの設定が更新されたバージョンで提供される設定と比較され、設定が新しい設定ファイルセットにマージされます。  
  
 次の表は、どの設定をコピーするかをアプリケーション設定が決定する方法を示しています。  
  
|変更の種類|アップグレード アクション|  
|--------------------|--------------------|  
|設定が *アプリ*.exe.config に追加されました|新しい設定は、現在のバージョンの *アプリ* にマージされ.exe.config|  
|設定が *アプリ* から削除されました.exe.config|以前の設定は、現在のバージョンの *アプリ* から削除され.exe.config|  
|設定の既定値が変更されました。ローカル設定は依然として [元の既定値] に設定さ user.config|設定は現在のバージョンの user.config にマージされ、新しい既定値が値として使用されます。|  
|設定の既定値が変更されました。user.config の既定値以外に設定|設定は、既定値以外の値を保持した状態で現在のバージョンの user.config にマージされます。|  
  
 独自のアプリケーション設定ラッパークラスを作成し、更新ロジックをカスタマイズしたい場合は、メソッドをオーバーライドでき <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> ます。  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce とローミングの設定  
 ClickOnce はローミング設定では機能しないため、設定ファイルはネットワーク上の複数のコンピューターにわたってフォローできます。 ローミング設定が必要な場合は、ネットワーク経由で設定を保存するアプリケーション設定プロバイダーを実装するか、リモートコンピューターに設定を格納するための独自のカスタム設定クラスを作成する必要があります。 設定プロバイダーの詳細については、「 [アプリケーション設定のアーキテクチャ](https://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)   
 [アプリケーション設定の概要](https://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc)   
 [ClickOnce キャッシュの概要](../deployment/clickonce-cache-overview.md)   
 [ClickOnce アプリケーションにおけるローカル データおよびリモート データへのアクセス](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
