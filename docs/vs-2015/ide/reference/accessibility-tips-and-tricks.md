---
title: アクセシビリティのヒントとテクニック | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b4c7777600f66f4044588ccae91910143e567f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670240"
---
# <a name="accessibility-tips-and-tricks"></a>アクセシビリティのヒントとテクニック
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] にはアクセシビリティ機能が組み込まれているため、簡単にキーボードで作業したり、スクリーン リーダーやその他の支援技術デバイスを使用したりすることができます。 ここでは、便利なショートカット キーのいくつかの組み合わせのほか、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のアクセシビリティを向上するために最適化する場合の推奨事項についてもいくつか示します。

> [!NOTE]
> 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。

## <a name="save-your-ide-settings"></a>IDE 設定を保存する
 ウィンドウのレイアウト、キーボード マップ スキーム、およびその他の設定を保存することにより、IDE エクスペリエンスをカスタマイズできます。 詳細については、「[Visual Studio での開発設定のカスタマイズ](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。

## <a name="common-windows-shortcut-key-combinations"></a>一般的な Windows のショートカット キーの組み合わせ
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] で作業を行う場合、標準的な Windows のショートカット キーの組み合わせの多くを使用することができます。 これらのショートカット キーの組み合わせのいくつかを以下に示します。

|説明|キーの組み合わせ|
|-----------------|---------------------|
|ハイ コントラストのオンとオフを切り替えます。|左 **ALT + 左 SHIFT + PRINTSCREEN**|
|ダイアログ ボックスのチェック ボックス オプションをオンまたはオフにします。|**+**|
|選択されている項目のプロパティを表示します。 たとえば、フォームが選択されている場合はプロパティ ウィンドウにフォーカスが移動し、プロジェクトが選択されている場合は [プロパティ ページ] ダイアログ ボックスが開きます。|**ALT + ENTER**|
|ダイアログ ボックスに、ドロップダウン リストなどのアクティブ リストの項目が表示されます。|**Alt** + ↓|
|グリッド内のアクティブ ドロップダウン リストの項目が表示されます。|**SHIFT**  + **ALT**  + **下方向キー**|

## <a name="hidden-visual-studio-shortcut-key-combinations"></a>Visual Studio の表示されないショートカット キーの組み合わせ
 一部の機能には、[オプション] ダイアログ ボックス内の [環境] の [キーボード] ウィンドウには表示されなくても、使用可能なショートカット キーがあります。 これらのショートカット キーの組み合わせには次のようなものがあります。

|機能|説明|キーの組み合わせ|
|-------------|-----------------|---------------------|
|[ツールボックス] ウィンドウ|[ツールボックス] のタブを移動します。|**CTRL**  + **Uparrow**<br /><br /> および<br /><br /> **CTRL**  + **下矢印**|
|[ツールボックス] ウィンドウ|[ツールボックス] からフォームまたはデザイナーにコントロールを追加します。|**を入力し**|
|[キーボード]\([オプション] ダイアログ ボックス - [環境])|**[ショートカットキー** ] オプションで入力したキーの組み合わせを削除します。|**行頭**|
|すべてのツール ウィンドウ|ウィンドウのツール バーにある最初のボタンを選択します。|**SHIFT**  + **ALT**|
|IDE ツール バー|標準ツール バーの最初のボタンを選択します。|**Alt**、**Ctrl** + **Tab。** **注:** 次の IDE ツール バーの最初のボタンを選択する場合は、**Ctrl** + **Tab** キーをもう一度押します。|

## <a name="see-also"></a>参照
 [Visual Studio のユーザー補助機能](../../ide/reference/accessibility-features-of-visual-studio.md)
