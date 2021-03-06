---
title: Visual C++ コードの使用 (クラス デザイナー) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- Visual C++, Class Designer
- Class Designer, Visual C++ support
- Class Designer, limitations
- Class Designer, tasks in Visual C++
- Visual C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 020535ac73c48be74e56100c7b6f9c49b69e50dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851314"
---
# <a name="working-with-visual-c-code-class-designer"></a>Visual C++ コードの使用 (クラス デザイナー)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

クラス デザイナーは、*クラス ダイアグラム* と呼ばれるビジュアル デザイン サーフェイスを表示します。クラス ダイアグラムは、プロジェクトのコード要素を視覚的に表現するものです。 クラス ダイアグラムを使用して、プロジェクト内のクラスおよびその他の型を設計し、視覚化できます。

 クラス デザイナーは、次の C++ コード要素をサポートしています。

- クラス (マネージド クラスの図形に似ていますが、複数の継承関係を持つことができるという点が異なります)

- 匿名クラス (クラス ビューが匿名型に対して生成した名前を表示します)

- テンプレート クラス

- 構造体

- 列挙型

- マクロ (マクロの後処理ビューを表示します)

- Typedef

> [!NOTE]
> これは、モデリング プロジェクトで作成できる UML クラス図と同じではありません。 詳細については、「[UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md)」(UML クラス図: リファレンス) を参照してください。

## <a name="troubleshooting-type-resolution-and-display-issues"></a>型解決および表示の問題のトラブルシューティング

### <a name="location-of-source-files"></a>ソース ファイルの場所
 クラス デザイナーは、ソース ファイルの場所を追跡しません。 したがって、プロジェクト構造を変更するか、プロジェクト内でソース ファイルを移動すると、クラス デザイナーが型を見失うことがあります (特に typedef のソース型、基本クラス、または関連型の場合)。 **クラス デザイナーはこの型を表示できません**などのエラーが発生することがあります。 エラーが発生した場合は、変更または再配置したソース コードをもう一度クラス ダイアグラムにドラッグして再表示します。

### <a name="update-and-performance-issues"></a>更新およびパフォーマンスの問題
 Visual C++ プロジェクトの場合、ソース ファイルでの変更がクラス ダイアグラムに表示されるまでに 30 ～ 60 秒かかることがあります。 この遅延によって、クラス デザイナーで "**選択内で型が見つかりませんでした**" というエラーがスローされることもあります。 このようなエラーが発生した場合は、エラーメッセージで [ **キャンセル** ] をクリックし、クラスビューにコード要素が表示されるまで待ちます。 その後、クラス デザイナーが型を表示できるようになります。

 コードに加えた変更でクラス ダイアグラムが更新されない場合は、ダイアグラムを閉じて、再度開く必要がある場合があります。

### <a name="type-resolution-issues"></a>型解決の問題
 クラス デザイナーは、次のような理由により、型解決ができない場合があります。

- 型が、クラス ダイアグラムを含むプロジェクトから参照されていないプロジェクトまたはアセンブリ内にあります。 このエラーを修正するには、型を含むプロジェクトまたはアセンブリへの参照を追加します。 詳しくは、「[方法: [参照の追加] ダイアログ ボックスを使用して参照を追加または削除する](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)」を参照してください。

- 型が正しいスコープ内にないため、クラス デザイナーが型を見つけられません。 コードに `using` ステートメント、`imports` ステートメント、または `#include` ステートメントが欠落していないことを確認します。 また、型 (または関連する型) を最初に配置した名前空間の外に移動していないことも確認します。

- 型が存在しません (または、コメント アウトされています)。 このエラーを修正するには、型をコメント アウトまたは削除していないことを確認します。

- この型は、#import ディレクティブで参照されるライブラリに含まれます。 生成したコード (.tlh ファイル) をヘッダー ファイルの #include ディレクティブに追加する、という代替手段があります。

  型解決の問題が原因で発生する可能性が最も高いエラーは、 **クラスダイアグラム ' \<element> ' 内の1つ以上の図形に対してコードが見つかりませんでした**。 このエラー メッセージは、必ずしもコードがエラーであることを意味しません。 クラス デザイナーで、コードを表示できないことだけを示しています。 次の方法を試してください。

- 型がであることを確認します。 誤ってコメント アウトしたり、ソース コードを削除したりしていないことを確認します。

- クラス デザイナーが、入力した型をサポートしていることを確認します。 「[C++ コード要素の制限事項](#limitations)」を参照してください。

- 型の解決を試みます。 型は、クラス ダイアグラムを含むプロジェクトから参照されていないプロジェクトまたはアセンブリ内にある場合もあります。 このエラーを修正するには、型を含むプロジェクトまたはアセンブリへの参照を追加します。 詳しくは、「[方法: [参照の追加] ダイアログ ボックスを使用して参照を追加または削除する](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)」を参照してください。

- クラス デザイナーが型を検出できるように、型が正しいスコープ内にあることを確認します。 コードに `using` ステートメント、`imports` ステートメント、または `#include` ステートメントが欠落していないことを確認します。 また、型 (または関連する型) を最初に配置した名前空間の外に移動していないことも確認します。

### <a name="troubleshooting-other-error-messages"></a>その他のエラー メッセージのトラブルシューティング
 MSDN (Microsoft Developer Network) のパブリック フォーラムでは、エラーや警告のトラブルシューティングに役立つ情報を参照できます。 [Visual Studio クラス デザイナー フォーラム](https://social.msdn.microsoft.com/Forums/en-US/vsclassdesigner/threads?page=1)を参照してください。

## <a name="limitations-for-c-code-elements"></a><a name="limitations"></a> C++ コード要素の制限事項

- Visual C++ のプロジェクトがロードされるとき、クラス デザイナーは読み取り専用で機能します。 クラス ダイアグラムは変更できますが、クラス ダイアグラムから変更内容をソース コードに保存することはできません。

- クラス デザイナーは、ネイティブ C++ セマンティクスのみをサポートします。 マネージド コードにコンパイルされた Visual C++ プロジェクトでは、クラス デザイナーはネイティブ型のコード要素のみを視覚化します。 このため、プロジェクトにクラス ダイアグラムを追加することはできますが、クラス デザイナーでは、`IsManaged` プロパティが `true` に設定されている要素 (つまり、値型および参照型) を視覚化することはできません。

- Visual C++ プロジェクトでは、クラス デザイナーは型の定義のみを読み取ります。 たとえば、ヘッダー (.h) ファイルで型を定義して、実装 (.cpp) ファイルでメンバーを定義するとします。 実装ファイル (.cpp) で [クラス ダイアグラムで表示] を起動しても、クラス デザイナーには何も表示されません。 もう 1 つの例として、`#include` ステートメントを使用して他のファイルをインクルードし、実際のクラス定義は含まない .cpp ファイルで、[クラス ダイアグラムで表示] を起動する場合があります。この場合も、クラス デザイナーには何も表示されません。

- IDL (.idl) ファイルでは COM インターフェイスとタイプ ライブラリが定義されますが、このファイルはネイティブ C++ コードにコンパイルされない限り、ダイアグラムには表示されません。

- クラス デザイナーはグローバル関数とグローバル変数をサポートしていません。

- クラス デザイナーは共用体をサポートしていません。 共用体は、最大データ メンバーが必要とする量のメモリしか割り当てられない、特殊なタイプのクラスです。

- クラス デザイナーでは、`int` や `char` などの基本データ型は表示されません。

- 現在のプロジェクトの外部で定義された型への正しい参照がプロジェクトにない場合、これらの型はクラス デザイナーで表示されません。

- クラス デザイナーは、入れ子にされた型を表示することはできますが、入れ子にされた型とその他の型の間の関係は表示できません。

- クラス デザイナーでは、void 型または void 型から派生した型を表示できません。

## <a name="see-also"></a>参照
 クラス[と型の設計と表示](../ide/designing-and-viewing-classes-and-types.md)クラスと[その他の型の操作 (クラスデザイナー)](../ide/working-with-classes-and-other-types-class-designer.md) [クラスダイアグラムの操作 (クラスデザイナー)](../ide/working-with-class-diagrams-class-designer.md)クラス[と型のデザイン (クラスデザイナークラスデザイナー) クラスと型の設計 ()](../ide/designing-classes-and-types-class-designer.md) [Additional Information About Class Designer Errors](../ide/additional-information-about-class-designer-errors.md) Visual C++ の[クラスデザイナーの Visual C++](../ide/visual-cpp-classes-in-class-designer.md) [構造](../ide/visual-cpp-structures-in-class-designer.md)クラスデザイナー内の Visual C++ クラスデザイナー [typedef](../ide/visual-cpp-typedefs-in-class-designer.md) [の Visual C++](../ide/visual-cpp-enumerations-in-class-designer.md)の構造クラスデザイナー
