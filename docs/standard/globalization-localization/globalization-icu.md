---
title: グローバリゼーションと ICU
ms.date: 05/21/2020
helpviewer_keywords:
- globalization [.NET], about globalization
- global applications, globalization
- international applications [.NET], globalization
- world-ready applications, globalization
- application development [.NET], globalization
- culture, globalization
- icu, icu on windows, ms-icu
ms.openlocfilehash: d0361ba41b3a10d6a316341fcdacb869e7a35d26
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827114"
---
# <a name="net-globalization-and-icu"></a><span data-ttu-id="48780-102">.NET グローバリゼーションと ICU</span><span class="sxs-lookup"><span data-stu-id="48780-102">.NET globalization and ICU</span></span>

<span data-ttu-id="48780-103">.NET グローバリゼーション API は、これまで、プラットフォームごとに別の基になるライブラリを使用していました。</span><span class="sxs-lookup"><span data-stu-id="48780-103">In the past, the .NET globalization APIs used different underlying libraries on different platforms.</span></span> <span data-ttu-id="48780-104">この API は、Unix では、[ICU (International Components for Unicode)](http://site.icu-project.org/home) を使用し、Windows では、[各国語サポート (NLS)](/windows/win32/intl/national-language-support) を使用していました。</span><span class="sxs-lookup"><span data-stu-id="48780-104">On Unix, the APIs used [International Components for Unicode (ICU)](http://site.icu-project.org/home), and on Windows, they used [National Language Support (NLS)](/windows/win32/intl/national-language-support).</span></span> <span data-ttu-id="48780-105">これにより、アプリケーションを実行するとき、いくつかのグローバリゼーション API の動作がプラットフォームによって違うことがありました。</span><span class="sxs-lookup"><span data-stu-id="48780-105">This resulted in some behavioral differences in a handful of globalization APIs when running applications on different platforms.</span></span> <span data-ttu-id="48780-106">次の領域で、動作が違うことがわかっています。</span><span class="sxs-lookup"><span data-stu-id="48780-106">Behavior differences were evident in these areas:</span></span>

- <span data-ttu-id="48780-107">カルチャとカルチャ データ</span><span class="sxs-lookup"><span data-stu-id="48780-107">Cultures and culture data</span></span>
- <span data-ttu-id="48780-108">文字の大文字小文字</span><span class="sxs-lookup"><span data-stu-id="48780-108">String casing</span></span>
- <span data-ttu-id="48780-109">文字の並べ替えと検索</span><span class="sxs-lookup"><span data-stu-id="48780-109">String sorting and searching</span></span>
- <span data-ttu-id="48780-110">並べ替えキー</span><span class="sxs-lookup"><span data-stu-id="48780-110">Sort keys</span></span>
- <span data-ttu-id="48780-111">文字の正規化</span><span class="sxs-lookup"><span data-stu-id="48780-111">String normalization</span></span>
- <span data-ttu-id="48780-112">国際化ドメイン名 (IDN) のサポート</span><span class="sxs-lookup"><span data-stu-id="48780-112">Internationalized Domain Names (IDN) support</span></span>
- <span data-ttu-id="48780-113">Linux のタイム ゾーンの表示名</span><span class="sxs-lookup"><span data-stu-id="48780-113">Time zone display name on Linux</span></span>

<span data-ttu-id="48780-114">.NET 5.0 以降では、プラットフォームによってアプリケーションに違いがでることがないよう、開発者が基になるライブラリをより制御できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="48780-114">Starting with .NET 5.0, developers have more control over which underlying library is used, enabling applications to avoid differences across platforms.</span></span>

## <a name="icu-on-windows"></a><span data-ttu-id="48780-115">Windows 上の ICU</span><span class="sxs-lookup"><span data-stu-id="48780-115">ICU on Windows</span></span>

<span data-ttu-id="48780-116">Windows 10 の 2019 年 5 月更新プログラム以降では、OS の一部として [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) が含まれるようになり、.NET 5.0 以降のバージョンでは、既定で ICU が使用されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="48780-116">Windows 10 May 2019 Update and later versions include [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) as part of the OS, and .NET 5.0 and later versions use ICU by default.</span></span> <span data-ttu-id="48780-117">.NET 5.0 以降のバージョンを Windows で実行する場合、`icu.dll` の読み込みが試行され、存在する場合、グローバリゼーションの実装で使用されます。</span><span class="sxs-lookup"><span data-stu-id="48780-117">When running on Windows, .NET 5.0 and later versions try to load `icu.dll` and, if it's available, use it for the globalization implementation.</span></span> <span data-ttu-id="48780-118">Windows の古いバージョンを実行している場合などで、ICU ライブラリを見つけたり、読み込んだりすることができない場合、.NET 5.0 以降のバージョンは NLS ベースの実装に戻ります。</span><span class="sxs-lookup"><span data-stu-id="48780-118">If the ICU library can't be found or loaded, such as when running on older versions of Windows, .NET 5.0 and later versions fall back to the NLS-based implementation.</span></span>

> [!NOTE]
> <span data-ttu-id="48780-119">ICU が使用されている場合でも、Windows オペレーティング システム API では、ユーザーが設定している場合は、`CurrentCulture`、`CurrentUICulture`、および `CurrentRegion` のメンバーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="48780-119">Even when using ICU, the `CurrentCulture`, `CurrentUICulture`, and `CurrentRegion` members still use Windows operating system APIs to honor user settings.</span></span>

### <a name="behavioral-differences"></a><span data-ttu-id="48780-120">動作の違い</span><span class="sxs-lookup"><span data-stu-id="48780-120">Behavioral differences</span></span>

<span data-ttu-id="48780-121">.NET 5 を対象にするようにアプリをアップグレードすると、グローバリゼーション機能を使用していることを認識していない場合でも、アプリでの変更に気付くことがあります。</span><span class="sxs-lookup"><span data-stu-id="48780-121">If you upgrade your app to target .NET 5, you might see changes in your app even if you don't realize you're using globalization facilities.</span></span> <span data-ttu-id="48780-122">ここでは、気付く可能性のある動作の変更を 1 つ示しますが、他にもあります。</span><span class="sxs-lookup"><span data-stu-id="48780-122">This section lists one of the behavioral changes you might see, but there are others too.</span></span>

##### <a name="stringindexof"></a><span data-ttu-id="48780-123">String.IndexOf</span><span class="sxs-lookup"><span data-stu-id="48780-123">String.IndexOf</span></span>

<span data-ttu-id="48780-124">文字列内の改行文字のインデックスを調べるために <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> を呼び出す次のコードについて考えます。</span><span class="sxs-lookup"><span data-stu-id="48780-124">Consider the following code that calls <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> to find the index of the newline character in a string.</span></span>

```csharp
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);
```

- <span data-ttu-id="48780-125">Windows 上の以前のバージョンの .NET では、スニペットにより `6` と出力されます。</span><span class="sxs-lookup"><span data-stu-id="48780-125">In previous versions of .NET on Windows, the snippet prints `6`.</span></span>
- <span data-ttu-id="48780-126">Windows 10 May 2019 Update 以降のバージョン上の .NET 5.0 以降のバージョンでは、スニペットにより `-1` と出力されます。</span><span class="sxs-lookup"><span data-stu-id="48780-126">In .NET 5.0 and later versions on Windows 10 May 2019 Update and later versions, the snippet prints `-1`.</span></span>

<span data-ttu-id="48780-127">カルチャ依存検索ではなく序数検索を実行してこのコードを修正するには、<xref:System.String.IndexOf(System.String,System.StringComparison)> のオーバーロードを呼び出し、<xref:System.StringComparison.Ordinal?displayProperty=nameWithType> を引数として渡します。</span><span class="sxs-lookup"><span data-stu-id="48780-127">To fix this code by conducting an ordinal search instead of a culture-sensitive search, call the <xref:System.String.IndexOf(System.String,System.StringComparison)> overload and pass in <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> as an argument.</span></span>

<span data-ttu-id="48780-128">コード分析規則 [CA1307: 明確化のために StringComparison を指定する](../../../docs/fundamentals/code-analysis/quality-rules/ca1307.md)および [CA1309: 順序に基づく StringComparison を使用する](../../../docs/fundamentals/code-analysis/quality-rules/ca1309.md)を実行して、コード内でのこれらの呼び出しサイトを検索できます。</span><span class="sxs-lookup"><span data-stu-id="48780-128">You can run code analysis rules [CA1307: Specify StringComparison for clarity](../../../docs/fundamentals/code-analysis/quality-rules/ca1307.md) and [CA1309: Use ordinal StringComparison](../../../docs/fundamentals/code-analysis/quality-rules/ca1309.md) to find these call sites in your code.</span></span>

<span data-ttu-id="48780-129">詳細については、「[.NET 5 以降で文字列を比較するときの動作の変更](../base-types/string-comparison-net-5-plus.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48780-129">For more information, see [Behavior changes when comparing strings on .NET 5+](../base-types/string-comparison-net-5-plus.md).</span></span>

### <a name="use-nls-instead-of-icu"></a><span data-ttu-id="48780-130">ICU の代わりに NLS を使用する</span><span class="sxs-lookup"><span data-stu-id="48780-130">Use NLS instead of ICU</span></span>

<span data-ttu-id="48780-131">NLS の代わりに ICU を使用すると、一部のグローバリゼーション関連の操作で動作が違ってしまうことがあります。</span><span class="sxs-lookup"><span data-stu-id="48780-131">Using ICU instead of NLS may result in behavioral differences with some globalization-related operations.</span></span> <span data-ttu-id="48780-132">開発者は、NLS を使用するように、ICU の実装を戻すことを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="48780-132">To revert back to using NLS, a developer can opt out of the ICU implementation.</span></span> <span data-ttu-id="48780-133">アプリケーションでは、次のいずれかの方法で NLS モードを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="48780-133">Applications can enable NLS mode in any of the following ways:</span></span>

- <span data-ttu-id="48780-134">プロジェクト ファイルで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="48780-134">In the project file:</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Globalization.UseNls" Value="true" />
  </ItemGroup>
  ```

- <span data-ttu-id="48780-135">`runtimeconfig.json` ファイルで次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="48780-135">In the `runtimeconfig.json` file:</span></span>

  ```json
  {
    "runtimeOptions": {
       "configProperties": {
         "System.Globalization.UseNls": true
        }
    }
  }
  ```

- <span data-ttu-id="48780-136">環境変数 `DOTNET_SYSTEM_GLOBALIZATION_USENLS` の値を `true` または `1` に設定します。</span><span class="sxs-lookup"><span data-stu-id="48780-136">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_USENLS` to the value `true` or `1`.</span></span>

> [!NOTE]
> <span data-ttu-id="48780-137">プロジェクトまたは `runtimeconfig.json` に設定された値が環境変数に優先されます。</span><span class="sxs-lookup"><span data-stu-id="48780-137">A value set in the project or in the `runtimeconfig.json` file takes precedence over the environment variable.</span></span>

<span data-ttu-id="48780-138">詳細については、[ランタイムの構成設定](../../core/run-time-config/globalization.md#nls)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="48780-138">For more information, see [Run-time config settings](../../core/run-time-config/globalization.md#nls).</span></span>

## <a name="app-local-icu"></a><span data-ttu-id="48780-139">アプリローカル ICU</span><span class="sxs-lookup"><span data-stu-id="48780-139">App-local ICU</span></span>

<span data-ttu-id="48780-140">ICU の各リリースには、バグ修正と、世界の言語が記述された更新された共通ロケール データ リポジトリ (CLDR) データが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="48780-140">Each release of ICU may bring with it bug fixes as well as updated Common Locale Data Repository (CLDR) data that describes the world's languages.</span></span> <span data-ttu-id="48780-141">ICU のバージョンを変えると、グローバリゼーション関連の操作でアプリの動作がわずかに影響を受ける場合があります。</span><span class="sxs-lookup"><span data-stu-id="48780-141">Moving between versions of ICU can subtly impact app behavior when it comes to globalization-related operations.</span></span> <span data-ttu-id="48780-142">.NET 5.0 以降のバージョンでは、独自の ICU のコピーが Windows と Unix の両方上のアプリに含まれ使用されになっており、アプリケーション開発者が、配置したすべてのアプリで整合性を保てるようになっています。</span><span class="sxs-lookup"><span data-stu-id="48780-142">To help application developers ensure consistency across all deployments, .NET 5.0 and later versions enable apps on both Windows and Unix to carry and use their own copy of ICU.</span></span>

<span data-ttu-id="48780-143">アプリケーションでは、次のいずれかの方法で、アプリローカル ICU が実装されるモードをオプトインできます。</span><span class="sxs-lookup"><span data-stu-id="48780-143">Applications can opt in to an app-local ICU implementation mode in any of the following ways:</span></span>

- <span data-ttu-id="48780-144">プロジェクト ファイルで次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="48780-144">In  the project file:</span></span>

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Globalization.AppLocalIcu" Value="<suffix>:<version> or <version>" />
  </ItemGroup>
  ```

- <span data-ttu-id="48780-145">`runtimeconfig.json` ファイルで次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="48780-145">In the `runtimeconfig.json` file:</span></span>

  ```json
  {
    "runtimeOptions": {
       "configProperties": {
         "System.Globalization.AppLocalIcu": "<suffix>:<version> or <version>"
       }
    }
  }
  ```

- <span data-ttu-id="48780-146">環境変数 `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` の値を `<suffix>:<version>` または `<version>` に設定します。</span><span class="sxs-lookup"><span data-stu-id="48780-146">By setting the environment variable `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` to the value `<suffix>:<version>` or `<version>`.</span></span>

  <span data-ttu-id="48780-147">`<suffix>`: 公開されている ICU パッケージ規則に従った、長さが 36 文字未満の省略可能なサフィックス。</span><span class="sxs-lookup"><span data-stu-id="48780-147">`<suffix>`: Optional suffix of fewer than 36 characters in length, following the public ICU packaging conventions.</span></span> <span data-ttu-id="48780-148">ICU をカスタマイズして構築する場合、`libicuucmyapp` のように、ライブラリ名とエクスポートされたシンボル名にサフィックスが含まれるようにカスタマイズできます。ここでは、`myapp` がサフィックスです。</span><span class="sxs-lookup"><span data-stu-id="48780-148">When building a custom ICU, you can customize it to produce the lib names and exported symbol names to contain a suffix, for example, `libicuucmyapp`, where `myapp` is the suffix.</span></span>

  <span data-ttu-id="48780-149">`<version>`:67.1 などの有効な ICU のバージョン。</span><span class="sxs-lookup"><span data-stu-id="48780-149">`<version>`: A valid ICU version, for example, 67.1.</span></span> <span data-ttu-id="48780-150">このバージョンは、バイナリを読み込み、エクスポートされたシンボルを取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="48780-150">This version is used to load the binaries and to get the exported symbols.</span></span>

<span data-ttu-id="48780-151">.NET では、アプリローカルのスイッチが設定されている場合に ICU を読み込むために、複数のパスをプローブする <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> メソッドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="48780-151">To load ICU when the app-local switch is set, .NET uses the <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> method, which probes multiple paths.</span></span> <span data-ttu-id="48780-152">このメソッドでは、まず `NATIVE_DLL_SEARCH_DIRECTORIES` プロパティからライブラリが検索されます。このプロパティは、アプリの `deps.json` ファイルに基づき dotnet ホストが作成します。</span><span class="sxs-lookup"><span data-stu-id="48780-152">The method first tries to find the library in the `NATIVE_DLL_SEARCH_DIRECTORIES` property, which is created by the dotnet host based on the `deps.json` file for the app.</span></span> <span data-ttu-id="48780-153">詳細については、「[既定のプローブ](../../core/dependency-loading/default-probing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48780-153">For more information, see [Default probing](../../core/dependency-loading/default-probing.md).</span></span>

<span data-ttu-id="48780-154">自己完結型アプリの場合は、ICU がアプリのディレクトリ内にあることを確認する以外に、ユーザーが特別に行う操作はありません (自己完結型アプリの場合、既定の作業ディレクトリは `NATIVE_DLL_SEARCH_DIRECTORIES` です)。</span><span class="sxs-lookup"><span data-stu-id="48780-154">For self-contained apps, no special action is required by the user, other than making sure ICU is in the app directory (for self-contained apps, the working directory defaults to `NATIVE_DLL_SEARCH_DIRECTORIES`).</span></span>

<span data-ttu-id="48780-155">NuGet パッケージの ICU を使用している場合は、フレームワークに依存するアプリケーションでこのようになります。</span><span class="sxs-lookup"><span data-stu-id="48780-155">If you're consuming ICU via a NuGet package, this works in framework-dependent applications.</span></span> <span data-ttu-id="48780-156">NuGet はネイティブ資産を解決し、`deps.json` ファイルと `runtimes` ディレクトリ下のアプリケーションの出力ディレクトリにそれを格納します。</span><span class="sxs-lookup"><span data-stu-id="48780-156">NuGet resolves the native assets and includes them in the `deps.json` file and in the output directory for the application under the `runtimes` directory.</span></span> <span data-ttu-id="48780-157">.NET はそこからこれを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="48780-157">.NET loads it from there.</span></span>

<span data-ttu-id="48780-158">ローカル ビルドから ICU が使用されるフレームワーク依存のアプリの場合は、手順を追加で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48780-158">For framework-dependent apps (not self contained) where ICU is consumed from a local build, you must take additional steps.</span></span> <span data-ttu-id="48780-159">.NET SDK には、"ルース" ネイティブ バイナリを `deps.json` に組み込む機能がまだありません ([この SDK の問題](https://github.com/dotnet/sdk/issues/11373)を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="48780-159">The .NET SDK doesn't yet have a feature for "loose" native binaries to be incorporated into `deps.json` (see [this SDK issue](https://github.com/dotnet/sdk/issues/11373)).</span></span> <span data-ttu-id="48780-160">代わりに、アプリケーションのプロジェクト ファイルに情報を追加して有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="48780-160">Instead, you can enable this by adding additional information into the application's project file.</span></span> <span data-ttu-id="48780-161">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="48780-161">For example:</span></span>

```xml
<ItemGroup>
  <IcuAssemblies Include="icu\*.so*" />
  <RuntimeTargetsCopyLocalItems Include="@(IcuAssemblies)" AssetType="native" CopyLocal="true" DestinationSubDirectory="runtimes/linux-x64/native/" DestinationSubPath="%(FileName)%(Extension)" RuntimeIdentifier="linux-x64" NuGetPackageId="System.Private.Runtime.UnicodeData" />
</ItemGroup>
```

<span data-ttu-id="48780-162">これは、サポートされているランタイムのすべての ICU バイナリに対して実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48780-162">This must be done for all the ICU binaries for the supported runtimes.</span></span> <span data-ttu-id="48780-163">また、`RuntimeTargetsCopyLocalItems` 項目グループの `NuGetPackageId` メタデータが、プロジェクトが実際に参照する NuGet パッケージと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="48780-163">Also, the `NuGetPackageId` metadata in the `RuntimeTargetsCopyLocalItems` item group needs to match a NuGet package that the project actually references.</span></span>

### <a name="macos-behavior"></a><span data-ttu-id="48780-164">macOS の動作</span><span class="sxs-lookup"><span data-stu-id="48780-164">macOS behavior</span></span>

<span data-ttu-id="48780-165">`macOS` が `match-o` ファイルで指定した読み込みコマンドから依存しているダイナミック ライブラリを解決する動作は、Linux ローダーの動作とは異なります。</span><span class="sxs-lookup"><span data-stu-id="48780-165">`macOS` has a different behavior for resolving dependent dynamic libraries from the load commands specified in the `match-o` file than the Linux loader.</span></span> <span data-ttu-id="48780-166">Linux ローダーでは、ICU 依存関係グラフに従い、.NET が `libicudata`、`libicuuc`、および `libicui18n` を (この順序で) 試行します。</span><span class="sxs-lookup"><span data-stu-id="48780-166">In the Linux loader, .NET can try `libicudata`, `libicuuc`, and `libicui18n` (in that order) to satisfy ICU dependency graph.</span></span> <span data-ttu-id="48780-167">ただし、これは macOS では機能しません。</span><span class="sxs-lookup"><span data-stu-id="48780-167">However, on macOS, this doesn't work.</span></span> <span data-ttu-id="48780-168">macOS で ICU を構築する場合、ユーザーは既定でこれらの読み込みコマンドで、`libicuuc` にダイナミック ライブラリを取得します。</span><span class="sxs-lookup"><span data-stu-id="48780-168">When building ICU on macOS, you, by default, get a dynamic library with these load commands in `libicuuc`.</span></span> <span data-ttu-id="48780-169">次のスニペットに例を示します。</span><span class="sxs-lookup"><span data-stu-id="48780-169">The following snippet shows an example.</span></span>

```sh
~/ % otool -L /Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib
/Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib:
 libicuuc.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 libicudata.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1281.100.1)
 /usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 902.1.0)
```

<span data-ttu-id="48780-170">これらのコマンドでは、ICU の他のコンポーネントの依存ライブラリの名前のみを参照します。</span><span class="sxs-lookup"><span data-stu-id="48780-170">These commands just reference the name of the dependent libraries for the other components of ICU.</span></span> <span data-ttu-id="48780-171">ローダーは、`dlopen` 表記規則に従って検索を実行します。このとき、これらのライブラリはシステム ディレクトリに配置されているか、`LD_LIBRARY_PATH` 環境変数が設定されているか、アプリレベル ディレクトリに ICU がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="48780-171">The loader performs the search following the `dlopen` conventions, which involves having these libraries in the system directories or setting the `LD_LIBRARY_PATH` env vars, or having ICU at the app-level directory.</span></span> <span data-ttu-id="48780-172">`LD_LIBRARY_PATH` を設定できない場合、または ICU バイナリがアプリレベルのディレクトリにない可能性がある場合は、作業を追加で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="48780-172">If you can't set `LD_LIBRARY_PATH` or ensure that ICU binaries are at the app-level directory, you will need to do some extra work.</span></span>

<span data-ttu-id="48780-173">ローダーには、その読み込みコマンドでバイナリと同じディレクトリから、その依存関係を検索するように指示する、`@loader_path` などのディレクティブがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="48780-173">There are some directives for the loader, like `@loader_path`, which tell the loader to search for that dependency in the same directory as the binary with that load command.</span></span> <span data-ttu-id="48780-174">これを実現する方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="48780-174">There are two ways to achieve this:</span></span>

- `install_name_tool -change`

  <span data-ttu-id="48780-175">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="48780-175">Run the following commands:</span></span>

  ```bash
  install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicuuc.67.1.dylib
  install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicui18n.67.1.dylib
  install_name_tool -change "libicuuc.67.dylib" "@loader_path/libicuuc.67.dylib" /path/to/libicui18n.67.1.dylib
  ```

- <span data-ttu-id="48780-176">`@loader_path` が使用されたインストール名が作成されるよう、ICU をパッチします。</span><span class="sxs-lookup"><span data-stu-id="48780-176">Patch ICU to produce the install names with `@loader_path`</span></span>

  <span data-ttu-id="48780-177">autoconf (`./runConfigureICU`) を実行する前に、[これらの行](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37)を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="48780-177">Before running autoconf (`./runConfigureICU`), change [these lines](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) to:</span></span>

  ```
  LD_SONAME = -Wl,-compatibility_version -Wl,$(SO_TARGET_VERSION_MAJOR) -Wl,-current_version -Wl,$(SO_TARGET_VERSION) -install_name @loader_path/$(notdir $(MIDDLE_SO_TARGET))
  ```

## <a name="icu-on-webassembly"></a><span data-ttu-id="48780-178">WebAssembly での ICU</span><span class="sxs-lookup"><span data-stu-id="48780-178">ICU on WebAssembly</span></span>

<span data-ttu-id="48780-179">WebAssembly ワークロード専用の ICU バージョンを利用できます。</span><span class="sxs-lookup"><span data-stu-id="48780-179">A version of ICU is available that's specifically for WebAssembly workloads.</span></span> <span data-ttu-id="48780-180">このバージョンでは、デスクトップ プロファイルとのグローバリゼーションの互換性が提供されます。</span><span class="sxs-lookup"><span data-stu-id="48780-180">This version provides globalization compatibility with desktop profiles.</span></span> <span data-ttu-id="48780-181">ICU データ ファイルのサイズを 24 MB から 1.4 MB (Brotli で圧縮する場合は約 0.3 MB) に減らすため、このワークロードにはいくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="48780-181">To reduce the ICU data file size from 24 MB to 1.4 MB (or ~0.3 MB if compressed with Brotli), this workload has a handful of limitations.</span></span>

<span data-ttu-id="48780-182">次の API はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="48780-182">The following APIs are not supported:</span></span>

- <xref:System.Globalization.CultureInfo.EnglishName?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.NativeName?displayProperty=nameWithType>
- <xref:System.Globalization.DateTimeFormatInfo.NativeCalendarName?displayProperty=nameWithType>
- <xref:System.Globalization.RegionInfo.NativeName?displayProperty=nameWithType>

<span data-ttu-id="48780-183">次の API は、制限付きでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="48780-183">The following APIs are supported with limitations:</span></span>

- <span data-ttu-id="48780-184"><xref:System.String.Normalize(System.Text.NormalizationForm)?displayProperty=nameWithType> と <xref:System.String.IsNormalized(System.Text.NormalizationForm)?displayProperty=nameWithType> では、使用頻度の低い <xref:System.Text.NormalizationForm.FormKC> と <xref:System.Text.NormalizationForm.FormKD> 形式はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="48780-184"><xref:System.String.Normalize(System.Text.NormalizationForm)?displayProperty=nameWithType> and <xref:System.String.IsNormalized(System.Text.NormalizationForm)?displayProperty=nameWithType> don't support the rarely used <xref:System.Text.NormalizationForm.FormKC> and <xref:System.Text.NormalizationForm.FormKD> forms.</span></span>
- <span data-ttu-id="48780-185"><xref:System.Globalization.RegionInfo.CurrencyNativeName?displayProperty=nameWithType> からは <xref:System.Globalization.RegionInfo.CurrencyEnglishName?displayProperty=nameWithType> と同じ値が返されます。</span><span class="sxs-lookup"><span data-stu-id="48780-185"><xref:System.Globalization.RegionInfo.CurrencyNativeName?displayProperty=nameWithType> returns the same value as <xref:System.Globalization.RegionInfo.CurrencyEnglishName?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="48780-186">また、サポートされているロケールの一覧については、[dotnet/icu リポジトリ](https://github.com/dotnet/icu/blob/0f49268ddfd3331ca090f1c51d2baa2f75f6c6c0/icu-filters/optimal.json#L6-L54)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48780-186">In addition, a list of supported locales can be found on the [dotnet/icu repo](https://github.com/dotnet/icu/blob/0f49268ddfd3331ca090f1c51d2baa2f75f6c6c0/icu-filters/optimal.json#L6-L54).</span></span>
