---
title: MSBuild 16.0 の新機能 | Microsoft Docs
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 48fc1a02ad34a3d5229ead0da79c0f6fa781670e
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2020
ms.locfileid: "88711652"
---
# <a name="whats-new-in-msbuild-160"></a>MSBuild 16.0 の新機能

この記事では、MSBuild 16.0 で更新された機能とプロパティについて説明します。 詳細なリリース ノートについては、「[MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831)」をご覧ください。

## <a name="changed-path"></a>変更されたパス

 MSBuild は Visual Studio の各バージョンの *\Current* フォルダーにインストールされ、実行可能ファイルは *\Bin* サブフォルダーにインストールされます。 たとえば、Visual Studio 2019 Community でインストールされた *MSBuild.exe* へのパスは *C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe* です。次の PowerShell モジュールを使用して MSBuild を配置することもできます: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell)。

## <a name="changed-properties"></a>変更されたプロパティ

 新しいバージョン番号に伴い、次の MSBuild プロパティが更新されました。

- `MSBuildToolsVersion`: このバージョンのツールでは "Current" になります。 アセンブリのバージョンは、Visual Studio 2017 と同じ (15.1.0.0) です。

- `VisualStudioVersion`: このバージョンのツールでは "16.0" になります。

## <a name="updates"></a>更新

MSBuild (および Visual Studio) では、.NET Framework 4.7.2 が対象とされるようになりました。 MSBuild API の新しい機能を使用したい場合は、ご利用のアセンブリもアップグレードする必要があります。ただし、既存のコードは引き続き機能します。

## <a name="see-also"></a>関連項目

- [MSBuild](../msbuild/msbuild.md)
