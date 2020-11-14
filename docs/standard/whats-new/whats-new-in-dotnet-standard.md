---
title: .NET Standard の新機能
description: この記事では、.NET Standard の新しいバージョンごとに、組み込まれた新機能と機能強化をまとめます。
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 419988901923b890aaf0a540d155775214e62c52
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282110"
---
# <a name="whats-new-in-net-standard"></a><span data-ttu-id="8e4c4-103">.NET Standard の新機能</span><span class="sxs-lookup"><span data-stu-id="8e4c4-103">What's new in .NET Standard</span></span>

<span data-ttu-id="8e4c4-104">.NET Standard は、各バージョンの標準に準拠した .NET 実装で利用できる必要がある一連の API がバージョン管理され、定義された正式な仕様です。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-104">.NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="8e4c4-105">.NET Standard はライブラリ開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-105">.NET Standard is targeted at library developers.</span></span> <span data-ttu-id="8e4c4-106">あるバージョンの .NET Standard をターゲットとするライブラリは、そのバージョンの標準をサポートする .NET Framework、.NET Core、または Xamarin 実装で使用できます。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="8e4c4-107">.NET Standard は、.NET Core SDK に加えて、.NET Core ワークロードを選択する場合は Visual Studio にも含まれています。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-107">.NET Standard is included with the .NET Core SDK, as well as with Visual Studio when you select the .NET Core workload.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="8e4c4-108">サポートされている .NET 実装</span><span class="sxs-lookup"><span data-stu-id="8e4c4-108">Supported .NET implementations</span></span>

<span data-ttu-id="8e4c4-109">.NET Standard 2.0 は、次の .NET 実装でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-109">.NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="8e4c4-110">.NET Core 2.0 以降</span><span class="sxs-lookup"><span data-stu-id="8e4c4-110">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="8e4c4-111">.NET Framework 4.6.1 以降</span><span class="sxs-lookup"><span data-stu-id="8e4c4-111">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="8e4c4-112">Mono 5.4 以降</span><span class="sxs-lookup"><span data-stu-id="8e4c4-112">Mono 5.4 or later</span></span>
- <span data-ttu-id="8e4c4-113">Xamarin.iOS 10.14 以降</span><span class="sxs-lookup"><span data-stu-id="8e4c4-113">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="8e4c4-114">Xamarin.Mac 3.8 以降</span><span class="sxs-lookup"><span data-stu-id="8e4c4-114">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="8e4c4-115">Xamarin.Android 8.0 以降</span><span class="sxs-lookup"><span data-stu-id="8e4c4-115">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="8e4c4-116">ユニバーサル Windows プラットフォーム 10.0.16299 以降</span><span class="sxs-lookup"><span data-stu-id="8e4c4-116">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-net-standard-20"></a><span data-ttu-id="8e4c4-117">.NET Standard 2.0 の新機能</span><span class="sxs-lookup"><span data-stu-id="8e4c4-117">What's new in .NET Standard 2.0</span></span>

<span data-ttu-id="8e4c4-118">.NET Standard 2.0 には、次の新機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-118">.NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="8e4c4-119">大幅に拡張された一連の API</span><span class="sxs-lookup"><span data-stu-id="8e4c4-119">A vastly expanded set of APIs</span></span>

<span data-ttu-id="8e4c4-120">.NET Standard バージョン 1.6 には、比較的少数の API のサブセットが含まれていました。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-120">Through version 1.6, .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="8e4c4-121">除外された API の中には、.NET Framework または Xamarin で一般的に使用されていた多くの API がありました。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-121">Among those excluded were many APIs that were commonly used in .NET Framework or Xamarin.</span></span> <span data-ttu-id="8e4c4-122">その結果、複数の .NET 実装をターゲットとするアプリケーションやライブラリを開発する場合に、使い慣れた API に適した代替のものを開発者が見つけなければならないので、開発は複雑になります。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="8e4c4-123">.NET Standard 2.0 では、以前のバージョンの標準である .NET Standard 1.6 で使用できる API に 20,000 個を超える API を追加して、この制限に対処しています。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-123">.NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="8e4c4-124">.NET Standard 2.0 に追加された API の一覧については、「[.NET Standard 2.0 と 1.6 の比較](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-124">For a list of the APIs that have been added to .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="8e4c4-125">.NET Standard 2.0 の <xref:System> 名前空間には、以下のような追加がありました。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="8e4c4-126"><xref:System.AppDomain> クラスのサポート。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="8e4c4-127"><xref:System.Array> クラスに追加されたメンバーの配列操作のサポートを改善しました。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="8e4c4-128"><xref:System.Attribute> クラスに追加されたメンバーの属性操作のサポートを改善しました。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="8e4c4-129">カレンダーのサポートを改善し、<xref:System.DateTime> 値の書式設定オプションを追加しました。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="8e4c4-130"><xref:System.Decimal> の丸め処理機能を追加しました。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="8e4c4-131"><xref:System.Environment> クラスの機能を追加しました。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="8e4c4-132"><xref:System.GC> クラスによるガベージ コレクターの制御を強化しました。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="8e4c4-133"><xref:System.String> クラスの文字列の比較、列挙、正規化のサポートを強化しました。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="8e4c4-134"><xref:System.TimeZoneInfo.AdjustmentRule> クラスと <xref:System.TimeZoneInfo.TransitionTime> クラスでの夏時間の調整および移行時間のサポート。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="8e4c4-135"><xref:System.Type> クラスの機能が大幅に強化されました。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="8e4c4-136"><xref:System.Runtime.Serialization.SerializationInfo> および <xref:System.Runtime.Serialization.StreamingContext> パラメーターを使用する例外コンストラクターを追加することで、例外オブジェクトの逆シリアル化のサポートを改善しました。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="8e4c4-137">.NET Framework ライブラリのサポート</span><span class="sxs-lookup"><span data-stu-id="8e4c4-137">Support for .NET Framework libraries</span></span>

<span data-ttu-id="8e4c4-138">多くのライブラリで、.NET Standard ではなく .NET Framework がターゲットになっています。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-138">Many libraries target .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="8e4c4-139">ただし、このようなライブラリの呼び出しのほとんどは、.NET Standard 2.0 に含まれている API に対するものです。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-139">However, most of the calls in those libraries are to APIs that are included in .NET Standard 2.0.</span></span> <span data-ttu-id="8e4c4-140">.NET Standard 2.0 以降、[互換性 shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification) を使用して .NET Standard ライブラリから .NET Framework ライブラリにアクセスできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-140">Starting with .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="8e4c4-141">この互換レイヤーは開発者に対して透過的です。 .NET Framework ライブラリを利用するために必要なことはありません。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="8e4c4-142">唯一の要件は、.NET Framework クラス ライブラリから呼び出される API が .NET Standard 2.0 に含まれている必要があることです。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-142">The single requirement is that the APIs called by the .NET Framework class library must be included in .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="8e4c4-143">Visual Basic のサポート</span><span class="sxs-lookup"><span data-stu-id="8e4c4-143">Support for Visual Basic</span></span>

<span data-ttu-id="8e4c4-144">Visual Basic で .NET Standard ライブラリを開発できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="8e4c4-145">.NET Core ワークロードがインストールされた Visual Studio 2019 と Visual Studio 2017 バージョン 15.3 以降には、.NET Standard クラス ライブラリ テンプレートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-145">Visual Studio 2019 and Visual Studio 2017 version 15.3 or later with the .NET Core workload installed include a .NET Standard Class Library template.</span></span> <span data-ttu-id="8e4c4-146">他の開発ツールと環境を使用している Visual Basic 開発者の場合、[dotnet new](../../core/tools/dotnet-new.md) コマンドを使用して .NET Standard ライブラリ プロジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="8e4c4-147">詳細については、「[.NET Standard ライブラリのツールのサポート](#tooling-support-for-net-standard-libraries)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="8e4c4-148">.NET Standard ライブラリのツールのサポート</span><span class="sxs-lookup"><span data-stu-id="8e4c4-148">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="8e4c4-149">.NET Core 2.0 と .NET Standard 2.0 がリリースされ、Visual Studio 2017 と [.NET Core CLI](../../core/tools/index.md) の両方に .NET Standard ライブラリの作成をサポートするツールが追加されました。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core CLI](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="8e4c4-150">**.NET Core クロスプラットフォーム開発** ワークロードを使用して Visual Studio をインストールする場合は、次の図に示すように、プロジェクト テンプレートを使用して .NET Standard 2.0 ライブラリ プロジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="8e4c4-151">C#</span><span class="sxs-lookup"><span data-stu-id="8e4c4-151">C#</span></span>](#tab/csharp)

![新しい .NET Standard ライブラリ プロジェクトを追加する](./media/std-project-cs.png)

<span data-ttu-id="8e4c4-153">.NET Core CLI を使用している場合、次の [dotnet new](../../core/tools/dotnet-new.md) コマンドによって、.NET Standard 2.0 をターゲットとするクラス ライブラリ プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-153">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[<span data-ttu-id="8e4c4-154">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e4c4-154">Visual Basic</span></span>](#tab/vb)

![新しい .NET Standard ライブラリ プロジェクトを追加する](./media/std-project-vb.png)

<span data-ttu-id="8e4c4-156">.NET Core CLI を使用している場合、次の [dotnet new](../../core/tools/dotnet-new.md) コマンドによって、.NET Standard 2.0 をターゲットとするクラス ライブラリ プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8e4c4-156">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="8e4c4-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e4c4-157">See also</span></span>

- [<span data-ttu-id="8e4c4-158">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="8e4c4-158">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="8e4c4-159">.NET Standard の概要</span><span class="sxs-lookup"><span data-stu-id="8e4c4-159">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
