---
title: コマンド ライン キャプチャ ツール | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4d88e62b1520677ddac3ff66a6891eb805af30d
ms.sourcegitcommit: 3fe6bed9ef8fb1478106645f655c7472009ae43a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64808455"
---
# <a name="command-line-capture-tool"></a>コマンド ライン キャプチャ ツール
DXCap.exe は、グラフィックス診断のキャプチャと再生に使用されるコマンド ライン ツールです。 すべての機能レベルで、Direct3D 10 から Direct3D 12 をサポートしています。

## <a name="syntax"></a>構文

```cmd
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]
DXCap.exe -p [filename] -screenshot [-frame frames]
DXCap.exe -p [filename] -toXML [xml_filename]
DXCap.exe -v [-file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]
DXCap.exe -e [search_string]
DXCap.exe -info
```

#### <a name="parameters"></a>パラメーター
 `-file` `filename` キャプチャ モード (`-c`) の場合、`filename` では、グラフィックス情報の記録先となる、グラフィックス ログ ファイルの名前を指定します。 `filename` が指定されていない場合、グラフィックス情報は、既定で `<appname>-<date>-<time>.vsglog` という名前のファイルに記録されます。

 検証 (-v) モードの場合、`filename` には、検証するグラフィックス ログ ファイルの名前を指定します。 `filename` が指定されていない場合、最後に検証されたグラフィックス ログがもう一度使用されます。

 `-frame` `frames` キャプチャ モードの場合、`frames` では、キャプチャするフレームを指定します。 最初のフレームは 1 です。 コンマおよび範囲を使用して、複数のフレームを指定できます。 たとえば、`frames` が `2, 5, 7-9, 15` の場合、フレーム `2`、`5`、`7`、`8`、`9`、および `15` がキャプチャされます。

> [!TIP]
> `-frame` `manual` を使用して、Print Screen キーを押すことでフレームが手動でキャプチャされるように指定します。 フレームはアプリの起動時にキャプチャできます。フレームのキャプチャを停止するには、コマンド ライン インターフェイスに戻り、Enter キーを押します。

 `-period` `periods` キャプチャ モードの場合、`periods` では、フレームをキャプチャする時間の範囲を秒単位で指定します。 コンマおよび範囲を使用して、複数の期間を指定できます。 たとえば、`periods` が `2.1-5, 7.0-9.3` の場合、`2.1` から `5` 秒の間および `7` から `9.3` 秒の間にレンダリングされるフレームがキャプチャされます。

 `-c``app` [`args...`] キャプチャ モード。 キャプチャ モードの場合、`app` には、グラフィックス情報の取得元となるアプリの名前を指定します。`args...` には、そのアプリに対する追加のコマンド ライン パラメーターを指定します。

 `-p` [`filename`] 再生モード (`-p`)。 再生モードの場合、`filename` には、再生するグラフィックス ログ ファイルの名前を指定します。 `filename` が指定されていない場合、最後に再生されたグラフィックス ログがもう一度使用されます。

 `-debug` 再生モードの場合、`-debug` は、Direct3D デバッグ レイヤーを有効にした状態で再生を行う必要があることを指定します。

 `-warp` 再生モードの場合、`-warp` では、WARP ソフトウェア レンダラーを使用して再生を行う必要があることを指定します。

 `-hw` 再生モードの場合、`-hw` では、GPU ハードウェアを使用して再生を行う必要があることを指定します。

 `-config` 再生モードの場合、`-config` では、グラフィックス ログ ファイルのキャプチャに使用されたコンピューターに関するすべての情報が表示されます。

 `-rawmode` 再生モードの場合、`-rawmode` では、記録されたイベントを変更することなく、再生を行う必要があることを指定します。 再生モードの通常の動作では、デバッグを単純化し、再生を高速化するために、再生に若干の変更が加えられる場合があります。 たとえば、スワップ チェーンのコマンドを実行する代わりに、スワップ チェーンの出力をシミュレートする場合があります。 通常、この再生が問題になることはありませんが、場合によっては、記録されたイベントに対してより忠実に再生することもできます。 たとえば、このオプションを使用して、全画面モードでの実行中にキャプチャされたアプリに全画面レンダリング動作を復元できます。

 `-toXML` [`xml_filename`] 再生モードの場合、`xml_filename` には、再生の XML 表現の書き込み先となるファイルの名前を指定します。 `xml_filename` が指定されていない場合、XML 表現は、再生するファイルと同じ名前を持ち、`.xml` 拡張子が付けられたファイルに書き込まれます。

 `-v` 検証モード。 検証モードの場合、キャプチャしたフレームはハードウェアと WARP の両方で再生され、イメージ比較関数によって、それらの結果が比較されます。 この機能を使用すると、レンダリングに影響を与えるドライバーの問題をすばやく識別できます。

 `-examine` `events` 検証モードの場合、`events` では、直近の結果を比較する一連のグラフィックス イベントを指定します。 たとえば、`-examine present,draw,copy,clear` では、比較対象を、これらのカテゴリに属するイベントに限定します。

> [!TIP]
> 最初は `-examine present,draw,copy,clear` から始めることをお勧めします。これにより、より広範な一連のイベントよりも大幅に短い時間で、ほとんどの問題を明らかにすることができます。 必要に応じて、より多くの、または異なる一連のイベントを指定して、それらのイベントを検証し、その他の種類の問題を明らかにすることもできます。

 `-haltonfail` 検証モードの場合、`-haltonfail` では、ハードウェアおよび WARP レンダラーの違いが検出されたときに、検証を停止します。 検証は、キーが押された後に再開されます。

 `-exitonfail` 検証モードの場合、`-exitonfail` では、ハードウェアおよび WARP レンダラーの違いが検出された直後に、検証を終了します。 この方法でプログラムが終了すると、環境に `0` が返されます。それ以外の場合、`1` が返されます。

 `-showprogress` 検証モードの場合、`-showprogress` では、検証セッションに関する進行状況の情報が表示されます。 WARP の進行状況が左側に表示され、ハードウェアの進行状況が右側に表示されます。

 `-e` `search_string` インストールされている UWP アプリを列挙します。 この情報を使用して、UWP アプリでコマンド ライン キャプチャを実行できます。

 `-info` コンピューターとキャプチャの DLL に関する情報を表示します。

## <a name="remarks"></a>Remarks
 DXCap.exe は 3 つのモードで動作します。

 キャプチャ モード (-c) 実行中のアプリからグラフィックス情報をキャプチャし、それをグラフィックス ログ ファイルに記録します。 キャプチャ機能とファイル形式は、Visual Studio と同じです。

 再生モード (-p) 既存のグラフィックス ログ ファイルから、以前にキャプチャされたグラフィックス イベントを再生します。 既定では、グラフィックス ログ ファイルが全画面アプリからキャプチャされた場合でも、再生はウィンドウ内で実行されます。 再生が全画面で実行されるのは、グラフィックス ログ ファイルが全画面アプリからキャプチャされ、`-rawmode` が指定されている場合のみです。

 検証モード (`-v`) ハードウェアと WARP の両方でキャプチャされたフレームを再生してから、イメージ比較関数を使用してそれらの結果を比較することによって、レンダリング動作を検証します。 この機能を使用すると、レンダリングに影響を与えるドライバーの問題をすばやく識別できます。

 これらのモードに加えて、dxcap.exe は、グラフィックス情報のキャプチャや再生を実行しない、他の 2 つの機能を実行します。

 列挙関数 (`-e`) コンピューターにインストールされている UWP アプリの詳細を表示します。 これらの詳細には、UWP アプリで実行可能ファイルを識別するパッケージ名とアプリ ID が含まれます。 DXCap.exe を使用して、Windows ストア アプリからグラフィックス情報をキャプチャするには、デスクトップ アプリをキャプチャするときに使用する実行可能ファイルの名前ではなく、このパッケージ名とアプリ ID を使用します。

 情報関数 (`-info)` コンピューターとキャプチャの DLL の詳細を表示します。

## <a name="examples"></a>使用例

### <a name="capture-graphics-information-from-a-desktop-app"></a>デスクトップ アプリからのグラフィックス情報のキャプチャ
 `-c` を使用して、グラフィックス情報のキャプチャ元となるアプリを指定します。

```cmd
DXCap.exe -c BasicHLSL11.exe
```

 既定では、グラフィックス情報は `<appname>-<date>-<time>.vsglog` という名前のファイルに記録されます。 記録先として別のファイルを指定するには、`-file` を使用します。

```cmd
DXCap.exe -file regression_test_12.vsglog -c BasicHLSL11.exe
```

 キャプチャ元のアプリに対する追加のコマンド ライン パラメーターを、そのアプリのファイル名の後に含めることによって指定します。

```cmd
DXCap.exe -c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"
```

 上記の例のコマンドでは、WebGL API を使用して 3-D コンテンツをレンダリングする、 www.fishgl.com にある Web ページの表示中に、Internet Explorer のデスクトップ バージョンからグラフィックス情報をキャプチャします。

> [!NOTE]
> アプリの後に指定したコマンド ライン引数はアプリに渡されるため、`-c` オプションを使用する前に、DXCap.exe の引数を指定する必要があります。

### <a name="capture-graphics-information-from-a-uwp-app"></a>UWP アプリからグラフィックス情報をキャプチャする
 UWP アプリからグラフィックス情報をキャプチャすることができます。

```cmd
DXCap.exe -c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps
```

 DXCap.exe を使用した UWP アプリからのキャプチャは、それを使用した Windows デスクトップ アプリからのキャプチャに似ていますが、デスクトップ アプリをそのファイル名で識別するのではなく、パッケージ名と、キャプチャ元のパッケージ内にある実行可能ファイルの名前または ID で、UWP アプリを識別します。 コンピューターにインストールされている UWP アプリを識別する方法をより簡単に確認するには、DXCap.exe で `-e` オプションを使用して、それらを列挙します。

```cmd
DXCap.exe -e
```

 オプションの検索文字列を指定して、探しているアプリの検索に役立てることもできます。 検索文字列が指定されている場合、DXCap.exe では、パッケージ名、アプリ名またはアプリ ID が検索文字列に一致する UWP アプリを列挙します。 検索では、大文字と小文字を区別しません。

```cmd
DXCap.exe -e map
```

 上記のコマンドでは、"map" に一致する UWP アプリが列挙されます。その出力は次のようになります。

 **パッケージ "Microsoft.BingMaps":** **InstallDirectory :C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe** **FullName         :Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe** **UserSID          :S-1-5-21-2127521184-1604012920-1887927527-5603533** **Name             :Microsoft.BingMaps** **Publisher        :CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US** **Version          :2.1.2914.1734** **Launchable Applications:** **ID:AppexMaps** **Exe:C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe** **IsWWA:No** **AppSpec (to launch):DXCap.exe -c Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps** 各列挙アプリの出力の最後の行には、グラフィックス情報をキャプチャするために使用できるコマンドが表示されます。

### <a name="capture-specific-frames-or-frames-between-specific-times"></a>特定のフレームまたは特定の期間のフレームのキャプチャ
 `-frame` を使用して、コンマと範囲を使ってキャプチャするフレームを指定します。

```cmd
DXCap.exe -frame 2,5,7-9,15 -c SimpleBezier11.exe
```

 または、`-period` を使用して、フレームをキャプチャする一連の時間範囲を指定します。 時間の範囲は秒単位で指定し、複数の範囲を指定することもできます。

```cmd
DXCap.exe -period 2.1-5, 7.0-9.3 -c SimpleBezier11.exe
```

### <a name="capture-frames-interactively"></a>フレームの対話的なキャプチャ
 `-manual` を使用して、フレームを対話的にキャプチャします。 Enter キーを押してキャプチャを開始し、もう一度 Enter キーを押して停止します。

```cmd
DXCap.exe -manual -c SimpleBezier11.exe
```

### <a name="play-back-a-graphic-log-file"></a>グラフィックス ログ ファイルを再生する
 `-p` を使用して、以前にキャプチャされたグラフィックス ログ ファイルを再生します。

```cmd
DXCap.exe -p regression_test_12.vsglog
```

 最後にキャプチャされたグラフィックス ログを再生する場合は、ファイル名を指定しません。

```cmd
DXCap.exe -p
```

### <a name="play-back-in-raw-mode"></a>Raw モードでの再生
 `-rawmode` を使用して、キャプチャされたコマンドを発生したとおりに再生します。 通常の再生では、特定のコマンドがエミュレートされます。たとえば、全画面アプリからキャプチャされたグラフィックス ログ ファイルは、ウィンドウ内で再生されます。Raw モードが有効になっている場合は、同じファイルの再生が全画面で試行されます。

```cmd
DXCap.exe -p regression_test_12.vsglog -rawmode
```

### <a name="play-back-using-warp-or-a-hardware-device"></a>WARP またはハードウェア デバイスの使用の再生
 ハードウェア デバイス上でキャプチャしたグラフィックス ログ ファイルの再生で、WARP を強制的に使用したり、WARP 上でキャプチャされたログの再生で、強制的にハードウェア デバイスを使用したりできます。 WARP を使って再生するには、`-warp` を使用します。

```cmd
DXCap.exe -p regression_test_12.vsglog -warp
```

 ハードウェアを使って再生するには、`-hw` を使用します。

```cmd
DXCap.exe -p regression_test_12.vsglog -hw
```

### <a name="validate-a-graphics-log-file-against-warp"></a>WARP に対するグラフィックス ログ ファイルの検証
 検証モードの場合、グラフィックス ログ ファイルはハードウェアと WARP の両方で再生され、その結果が比較されます。 これは、ドライバーが原因で発生するレンダリング エラーを識別するのに役立ちます。 -v を使用すると、WARP に対してグラフィックス ハードウェアが正しく動作するかどうかを検証できます。

```cmd
DXCap.exe -v regression_test_12.vsglog
```

 比較の量を減らすために、比較する検証用コマンドのサブセットを指定できます。この場合、他のコマンドは無視されます。 結果を比較するコマンドを指定するには、-examine を使用します。

```cmd
DXCap.exe -v regression_test_12.vsglog -examine present,draw,copy,clear
```

### <a name="convert-a-graphics-log-file-to-pngs"></a>PNG へのグラフィックス ログ ファイルの変換
 グラフィックス ログ ファイルのフレームを表示または分析するために、DXCap.exe は、キャプチャしたフレームを .png (ポータブル ネットワーク グラフィックス) イメージ ファイルとして保存できます。 キャプチャされたフレームを .png ファイルとして出力するには、再生モードで `-screenshot` を使用します。

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot
```

 出力するフレームを指定するには、`-screenshot` と共に `-frame` を使用します。

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot -frame 5, 7-9
```

### <a name="convert-a-graphics-log-file-to-xml"></a>XML へのグラフィックス ログ ファイルの変換
 FindStr や XSLT などの使い慣れたツールを使用して、グラフィックス ログを処理および分析するために、DXCap.exe はグラフィックス ログ ファイルを XML に変換できます。 ログを再生せずに XML に変換するには、再生モードで `-toXML` を使用します。

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML
```

 既定では、XML 出力は、グラフィックス ログと同じ名前を持ち、.xml 拡張子が付けられたファイルに書き込まれます。 上記の例では、XML ファイルの名前は **regression_test_12.xml** となります。 XML ファイルに別の名前を付けるには、それを `-toXML` の後に指定します。

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML temp.xml
```

 結果のファイルには、次のような XML が格納されます。

```xml
<Moment value="67"/>
<Method name="CreateDXGIFactory1" >
    <Return type="HRESULT" value="S_OK" />
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />
</Method>

<Moment value="167"/>
<Method name="D3D11CreateDevice" >
    <Return type="HRESULT" value="S_OK" />
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />
    <Parameter name="Software" type="HMODULE" value="pointer" />
    <Parameter name="Flags" type="UINT" value="0" />
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >
        <Element value="D3D_FEATURE_LEVEL_11_0" />
    </Parameter>
    <Parameter name="FeatureLevels" type="UINT" value="1" />
    <Parameter name="SDKVersion" type="UINT" value="7" />
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />
</Method>
```

## <a name="requirements"></a>必要条件