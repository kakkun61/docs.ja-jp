---
title: F# コンポーネント デザインのガイドライン
description: '他の呼び出し元による使用を目的とした F # コンポーネントを作成するためのガイドラインについて説明します。'
ms.date: 05/14/2018
ms.openlocfilehash: 24be2a422c97b9334f749e3d9dfcccd0feec219b
ms.sourcegitcommit: e395fabeeea5c705d243d246fa64446839ac85b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/03/2021
ms.locfileid: "97856108"
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="a1aaa-103">F# コンポーネント デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="a1aaa-103">F# component design guidelines</span></span>

<span data-ttu-id="a1aaa-104">このドキュメントは、f # コンポーネントの設計ガイドライン、v14、Microsoft Research、および最初に F # Software Foundation によって curated および保守されたバージョンに基づいて、F # プログラミングのコンポーネント設計ガイドラインのセットです。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and a version that was originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="a1aaa-105">このドキュメントでは、F # プログラミングに精通していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="a1aaa-106">F # コミュニティに感謝し、このガイドのさまざまなバージョンに関する投稿や役立つフィードバックをお寄せください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="a1aaa-107">概要</span><span class="sxs-lookup"><span data-stu-id="a1aaa-107">Overview</span></span>

<span data-ttu-id="a1aaa-108">このドキュメントでは、F # コンポーネントの設計とコーディングに関連するいくつかの問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="a1aaa-109">コンポーネントは、次のいずれかを意味します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="a1aaa-110">プロジェクト内の外部コンシューマーを持つ F # プロジェクト内のレイヤー。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="a1aaa-111">アセンブリ境界を越えて F # コードによる使用を目的としたライブラリ。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="a1aaa-112">アセンブリ境界を越えて .NET 言語による使用を目的としたライブラリ。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="a1aaa-113">[NuGet](https://nuget.org)などのパッケージリポジトリを使用した配布を目的としたライブラリ。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="a1aaa-114">この記事で説明する手法は、 [優れた F # コードの5つの原則](index.md#five-principles-of-good-f-code)に従っているため、必要に応じて機能とオブジェクトの両方のプログラミングを利用します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="a1aaa-115">どの方法論にもかかわらず、コンポーネントおよびライブラリデザイナーは、開発者が最も簡単に使用できる API を開発する際に、いくつかの実用的で prosaic の問題に直面しています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="a1aaa-116">[.Net ライブラリの設計ガイドライン](../../standard/design-guidelines/index.md)の Conscientious アプリケーションでは、使用してもよい api の一貫性のあるセットを作成することを目指しています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="a1aaa-117">一般的なガイドライン</span><span class="sxs-lookup"><span data-stu-id="a1aaa-117">General guidelines</span></span>

<span data-ttu-id="a1aaa-118">ライブラリの対象読者に関係なく、F # ライブラリに適用される汎用ガイドラインがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="a1aaa-119">.NET ライブラリのデザインガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="a1aaa-120">実行する F # のコードの種類に関係なく、 [.Net ライブラリのデザインガイドライン](../../standard/design-guidelines/index.md)に関する実用的な知識があることが重要です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="a1aaa-121">その他のほとんどの F # と .NET プログラマーは、これらのガイドラインについて理解し、.NET コードに準拠していることを期待しています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="a1aaa-122">.NET ライブラリの設計ガイドラインでは、名前付け、クラスとインターフェイスの設計、メンバーのデザイン (プロパティ、メソッド、イベントなど) などの一般的なガイダンスを提供し、さまざまな設計ガイダンスについて、最初に参考にします。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="a1aaa-123">XML ドキュメントコメントをコードに追加する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="a1aaa-124">パブリック Api に関する XML ドキュメントでは、これらの型とメンバーを使用するときに、ユーザーが優れた Intellisense と Quickinfo を取得し、ライブラリのドキュメントファイルのビルドを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-124">XML documentation on public APIs ensures that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="a1aaa-125">Xmldoc コメント内の追加のマークアップに使用できるさまざまな xml タグに関する [Xml ドキュメント](../language-reference/xml-documentation.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

<span data-ttu-id="a1aaa-126">短い形式の XML コメント ( `/// comment` )、または標準の xml コメント () のいずれかを使用でき `///<summary>comment</summary>` ます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="a1aaa-127">安定したライブラリおよびコンポーネント Api に明示的な署名ファイル (fsi.exe) を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="a1aaa-128">F # ライブラリで明示的なシグネチャファイルを使用すると、パブリック API の簡潔な概要が提供されます。これにより、ライブラリの完全なパブリックサーフェスを確実に把握し、パブリックドキュメントと内部実装の詳細を明確に分離することができます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which helps to ensure that you know the full public surface of your library, and provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="a1aaa-129">シグネチャファイルは、実装ファイルと署名ファイルの両方で変更を行う必要があるため、パブリック API の変更に摩擦を追加します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-129">Signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="a1aaa-130">そのため、通常、署名ファイルは API が solidified になったときにのみ導入され、大幅に変更されることが予想されなくなります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="a1aaa-131">.NET で文字列を使用する場合は常にベストプラクティスに従う</span><span class="sxs-lookup"><span data-stu-id="a1aaa-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="a1aaa-132">.NET のガイダンス [で文字列を使用するためのベストプラクティス](../../standard/base-types/best-practices-strings.md) に従ってください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="a1aaa-133">特に、文字列の変換と比較には、常に *カルチャの意図* を明示的に指定します (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="a1aaa-134">F # に接続されるライブラリのガイドライン</span><span class="sxs-lookup"><span data-stu-id="a1aaa-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="a1aaa-135">このセクションでは、パブリックな F # 向けライブラリの開発に関する推奨事項を示します。つまり、F # 開発者が使用することを意図したパブリック Api を公開するライブラリです。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="a1aaa-136">特に F # には、ライブラリ設計に関するさまざまな推奨事項が適用されています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="a1aaa-137">以下の特定の推奨事項がない場合は、「.NET ライブラリの設計ガイドライン」がフォールバックガイダンスです。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="a1aaa-138">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="a1aaa-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="a1aaa-139">.NET の名前付け規則と大文字小文字の表記規則を使用する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="a1aaa-140">次の表は、.NET の名前付け規則と大文字小文字の表記規則に従っています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="a1aaa-141">F # コンストラクトも含まれています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="a1aaa-142">構成体</span><span class="sxs-lookup"><span data-stu-id="a1aaa-142">Construct</span></span> | <span data-ttu-id="a1aaa-143">ケース</span><span class="sxs-lookup"><span data-stu-id="a1aaa-143">Case</span></span> | <span data-ttu-id="a1aaa-144">パーツ</span><span class="sxs-lookup"><span data-stu-id="a1aaa-144">Part</span></span> | <span data-ttu-id="a1aaa-145">例</span><span class="sxs-lookup"><span data-stu-id="a1aaa-145">Examples</span></span> | <span data-ttu-id="a1aaa-146">Notes</span><span class="sxs-lookup"><span data-stu-id="a1aaa-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="a1aaa-147">具象型</span><span class="sxs-lookup"><span data-stu-id="a1aaa-147">Concrete types</span></span> | <span data-ttu-id="a1aaa-148">パスカルケース</span><span class="sxs-lookup"><span data-stu-id="a1aaa-148">PascalCase</span></span> | <span data-ttu-id="a1aaa-149">名詞/形容詞</span><span class="sxs-lookup"><span data-stu-id="a1aaa-149">Noun/ adjective</span></span> | <span data-ttu-id="a1aaa-150">List、Double、Complex</span><span class="sxs-lookup"><span data-stu-id="a1aaa-150">List, Double, Complex</span></span> | <span data-ttu-id="a1aaa-151">具象型は、構造体、クラス、列挙体、デリゲート、レコード、および共用体です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="a1aaa-152">OCaml では、型名は従来は小文字ですが、F # では型の .NET 名前付けスキームが採用されています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="a1aaa-153">DLL</span><span class="sxs-lookup"><span data-stu-id="a1aaa-153">DLLs</span></span>           | <span data-ttu-id="a1aaa-154">パスカルケース</span><span class="sxs-lookup"><span data-stu-id="a1aaa-154">PascalCase</span></span> |                 | <span data-ttu-id="a1aaa-155">Fabrikam.Core.dll</span><span class="sxs-lookup"><span data-stu-id="a1aaa-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="a1aaa-156">共用体タグ</span><span class="sxs-lookup"><span data-stu-id="a1aaa-156">Union tags</span></span>     | <span data-ttu-id="a1aaa-157">パスカルケース</span><span class="sxs-lookup"><span data-stu-id="a1aaa-157">PascalCase</span></span> | <span data-ttu-id="a1aaa-158">[名詞]</span><span class="sxs-lookup"><span data-stu-id="a1aaa-158">Noun</span></span> | <span data-ttu-id="a1aaa-159">Some、Add、Success</span><span class="sxs-lookup"><span data-stu-id="a1aaa-159">Some, Add, Success</span></span> | <span data-ttu-id="a1aaa-160">パブリック Api でプレフィックスを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="a1aaa-161">必要に応じて、内部でプレフィックスを使用します。たとえば、 `type Teams = TAlpha | TBeta | TDelta.`</span><span class="sxs-lookup"><span data-stu-id="a1aaa-161">Optionally use a prefix when internal, such as `type Teams = TAlpha | TBeta | TDelta.`</span></span> |
| <span data-ttu-id="a1aaa-162">イベント</span><span class="sxs-lookup"><span data-stu-id="a1aaa-162">Event</span></span>          | <span data-ttu-id="a1aaa-163">パスカルケース</span><span class="sxs-lookup"><span data-stu-id="a1aaa-163">PascalCase</span></span> | <span data-ttu-id="a1aaa-164">動詞</span><span class="sxs-lookup"><span data-stu-id="a1aaa-164">Verb</span></span> | <span data-ttu-id="a1aaa-165">ValueChanged/ValueChanging</span><span class="sxs-lookup"><span data-stu-id="a1aaa-165">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="a1aaa-166">例外</span><span class="sxs-lookup"><span data-stu-id="a1aaa-166">Exceptions</span></span>     | <span data-ttu-id="a1aaa-167">パスカルケース</span><span class="sxs-lookup"><span data-stu-id="a1aaa-167">PascalCase</span></span> |      | <span data-ttu-id="a1aaa-168">WebException</span><span class="sxs-lookup"><span data-stu-id="a1aaa-168">WebException</span></span> | <span data-ttu-id="a1aaa-169">名前は "Exception" で終わる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-169">Name should end with "Exception".</span></span> |
| <span data-ttu-id="a1aaa-170">フィールド</span><span class="sxs-lookup"><span data-stu-id="a1aaa-170">Field</span></span>          | <span data-ttu-id="a1aaa-171">パスカルケース</span><span class="sxs-lookup"><span data-stu-id="a1aaa-171">PascalCase</span></span> | <span data-ttu-id="a1aaa-172">[名詞]</span><span class="sxs-lookup"><span data-stu-id="a1aaa-172">Noun</span></span> | <span data-ttu-id="a1aaa-173">CurrentName</span><span class="sxs-lookup"><span data-stu-id="a1aaa-173">CurrentName</span></span>  | |
| <span data-ttu-id="a1aaa-174">インターフェイス型</span><span class="sxs-lookup"><span data-stu-id="a1aaa-174">Interface types</span></span> |  <span data-ttu-id="a1aaa-175">パスカルケース</span><span class="sxs-lookup"><span data-stu-id="a1aaa-175">PascalCase</span></span> | <span data-ttu-id="a1aaa-176">名詞/形容詞</span><span class="sxs-lookup"><span data-stu-id="a1aaa-176">Noun/ adjective</span></span> | <span data-ttu-id="a1aaa-177">IDisposable</span><span class="sxs-lookup"><span data-stu-id="a1aaa-177">IDisposable</span></span> | <span data-ttu-id="a1aaa-178">名前は "I" で始まる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-178">Name should start with "I".</span></span> |
| <span data-ttu-id="a1aaa-179">メソッド</span><span class="sxs-lookup"><span data-stu-id="a1aaa-179">Method</span></span> |  <span data-ttu-id="a1aaa-180">パスカルケース</span><span class="sxs-lookup"><span data-stu-id="a1aaa-180">PascalCase</span></span> |  <span data-ttu-id="a1aaa-181">動詞</span><span class="sxs-lookup"><span data-stu-id="a1aaa-181">Verb</span></span> | <span data-ttu-id="a1aaa-182">ToString</span><span class="sxs-lookup"><span data-stu-id="a1aaa-182">ToString</span></span> | |
| <span data-ttu-id="a1aaa-183">名前空間</span><span class="sxs-lookup"><span data-stu-id="a1aaa-183">Namespace</span></span> | <span data-ttu-id="a1aaa-184">パスカルケース</span><span class="sxs-lookup"><span data-stu-id="a1aaa-184">PascalCase</span></span> | | <span data-ttu-id="a1aaa-185">Fsharp.core</span><span class="sxs-lookup"><span data-stu-id="a1aaa-185">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="a1aaa-186">一般 `<Organization>.<Technology>[.<Subnamespace>]` に、テクノロジが組織に依存していない場合は、組織を削除します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-186">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="a1aaa-187">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a1aaa-187">Parameters</span></span> | <span data-ttu-id="a1aaa-188">キャメルケース</span><span class="sxs-lookup"><span data-stu-id="a1aaa-188">camelCase</span></span> | <span data-ttu-id="a1aaa-189">[名詞]</span><span class="sxs-lookup"><span data-stu-id="a1aaa-189">Noun</span></span> |  <span data-ttu-id="a1aaa-190">typeName、transform、range</span><span class="sxs-lookup"><span data-stu-id="a1aaa-190">typeName, transform, range</span></span> | |
| <span data-ttu-id="a1aaa-191">let 値 (内部)</span><span class="sxs-lookup"><span data-stu-id="a1aaa-191">let values (internal)</span></span> | <span data-ttu-id="a1aaa-192">キャメルケースまたはパスワードの大文字と小文字の区別</span><span class="sxs-lookup"><span data-stu-id="a1aaa-192">camelCase or PascalCase</span></span> | <span data-ttu-id="a1aaa-193">名詞/動詞</span><span class="sxs-lookup"><span data-stu-id="a1aaa-193">Noun/ verb</span></span> |  <span data-ttu-id="a1aaa-194">getValue、myTable</span><span class="sxs-lookup"><span data-stu-id="a1aaa-194">getValue, myTable</span></span> |
| <span data-ttu-id="a1aaa-195">let 値 (外部)</span><span class="sxs-lookup"><span data-stu-id="a1aaa-195">let values (external)</span></span> | <span data-ttu-id="a1aaa-196">キャメルケースまたはパスワードの大文字と小文字の区別</span><span class="sxs-lookup"><span data-stu-id="a1aaa-196">camelCase or PascalCase</span></span> | <span data-ttu-id="a1aaa-197">名詞/動詞</span><span class="sxs-lookup"><span data-stu-id="a1aaa-197">Noun/verb</span></span>  | <span data-ttu-id="a1aaa-198">List. map, Dates. 今日</span><span class="sxs-lookup"><span data-stu-id="a1aaa-198">List.map, Dates.Today</span></span> | <span data-ttu-id="a1aaa-199">従来の機能デザインパターンに従うと、多くの場合、let バインド値がパブリックになります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-199">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="a1aaa-200">ただし、通常は、他の .NET 言語から識別子を使用できる場合は、文字を使用します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-200">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="a1aaa-201">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a1aaa-201">Property</span></span>  | <span data-ttu-id="a1aaa-202">パスカルケース</span><span class="sxs-lookup"><span data-stu-id="a1aaa-202">PascalCase</span></span>  | <span data-ttu-id="a1aaa-203">名詞/形容詞</span><span class="sxs-lookup"><span data-stu-id="a1aaa-203">Noun/ adjective</span></span>  | <span data-ttu-id="a1aaa-204">IsEndOfFile、BackColor</span><span class="sxs-lookup"><span data-stu-id="a1aaa-204">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="a1aaa-205">通常、ブール型プロパティではを使用し、IsNotEndOfFile ではなく IsEndOfFile のように肯定を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-205">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="a1aaa-206">省略形を避ける</span><span class="sxs-lookup"><span data-stu-id="a1aaa-206">Avoid abbreviations</span></span>

<span data-ttu-id="a1aaa-207">.NET ガイドラインでは、省略形を使用しないようにしています (たとえば、"ではなく" を使用し `OnButtonClick` `OnBtnClick` ます)。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-207">The .NET guidelines discourage the use of abbreviations (for example, "use `OnButtonClick` rather than `OnBtnClick`").</span></span> <span data-ttu-id="a1aaa-208">"非同期" などの一般的な省略形 `Async` は許容されます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-208">Common abbreviations, such as `Async` for "Asynchronous", are tolerated.</span></span> <span data-ttu-id="a1aaa-209">このガイドラインは、関数型プログラミングでは無視されることがあります。たとえば、は `List.iter` "反復処理" の省略形を使用します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-209">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for "iterate".</span></span> <span data-ttu-id="a1aaa-210">このため、省略形を使用すると、F # から F # へのプログラミングにおいてより高い次数が許容されるようになりますが、一般に、パブリックコンポーネントの設計では回避できます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-210">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="a1aaa-211">名前の大文字と小文字の競合を避ける</span><span class="sxs-lookup"><span data-stu-id="a1aaa-211">Avoid casing name collisions</span></span>

<span data-ttu-id="a1aaa-212">.NET のガイドラインでは、一部のクライアント言語 (Visual Basic など) で大文字と小文字が区別されないため、名前の競合を明確に区別するために大文字と小文字を区別することはできません。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-212">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="a1aaa-213">必要に応じて頭字語を使用する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-213">Use acronyms where appropriate</span></span>

<span data-ttu-id="a1aaa-214">XML などの頭字語は省略形ではなく、.NET ライブラリでは Xml (xml) で広く使用されています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-214">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="a1aaa-215">よく知られている、広く認識されている頭字語だけを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-215">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="a1aaa-216">汎用パラメーター名には、文字を使用する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-216">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="a1aaa-217">パブリック Api のジェネリックパラメーター名には、(F # に対応するライブラリの場合を含む) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-217">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="a1aaa-218">特に、、、などの名前を `T` `U` `T1` `T2` 任意のジェネリックパラメーターに使用し、特定の名前が意味する場合は、F # に接続されたライブラリでは `Key` 、、 `Value` `Arg` (たとえば、ではなく) のような名前を使用し `TKey` ます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-218">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="a1aaa-219">F # モジュールのパブリック関数と値には、キャメルケースを使用します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-219">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="a1aaa-220">キャメルケースは、非修飾 (など) で使用するように設計されたパブリック関数、 `invalidArg` および "標準コレクション関数" (たとえば、List. map) に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-220">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the "standard collection functions" (for example, List.map).</span></span> <span data-ttu-id="a1aaa-221">どちらの場合も、関数名は言語のキーワードとよく似ています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-221">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="a1aaa-222">オブジェクト、型、およびモジュールのデザイン</span><span class="sxs-lookup"><span data-stu-id="a1aaa-222">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="a1aaa-223">名前空間またはモジュールを使用して、型とモジュールを含める</span><span class="sxs-lookup"><span data-stu-id="a1aaa-223">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="a1aaa-224">コンポーネント内の各 F # ファイルは、名前空間宣言またはモジュール宣言で始まる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-224">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="a1aaa-225">or</span><span class="sxs-lookup"><span data-stu-id="a1aaa-225">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="a1aaa-226">モジュールと名前空間を使用して最上位レベルでコードを整理する場合の違いは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-226">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="a1aaa-227">名前空間は複数のファイルにまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-227">Namespaces can span multiple files</span></span>
* <span data-ttu-id="a1aaa-228">内部モジュール内にある場合を除き、名前空間に F # 関数を含めることはできません</span><span class="sxs-lookup"><span data-stu-id="a1aaa-228">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="a1aaa-229">特定のモジュールのコードは、1つのファイル内に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-229">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="a1aaa-230">トップレベルモジュールには、内部モジュールを必要とせずに F # 関数を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-230">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="a1aaa-231">最上位レベルの名前空間またはモジュールのいずれかを選択すると、コードのコンパイルされた形式に影響します。したがって、API が F # コード外で最終的に使用される場合は、他の .NET 言語からのビューに影響します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-231">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="a1aaa-232">オブジェクトの種類に固有の操作に対してメソッドとプロパティを使用する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-232">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="a1aaa-233">オブジェクトを使用する場合は、使用できる機能がその型のメソッドとプロパティとして実装されていることを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-233">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="a1aaa-234">特定のメンバーの機能の多くは、必ずしもそのメンバーに実装する必要はありませんが、その機能の利用可能な部分はにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-234">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="a1aaa-235">クラスを使用して変更可能な状態をカプセル化する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-235">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="a1aaa-236">F # では、その状態が、クロージャ、シーケンス式、非同期計算などの別の言語構成体によってまだカプセル化されていない場合にのみ、この操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-236">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="a1aaa-237">インターフェイスを使用して関連する操作をグループ化する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-237">Use interfaces to group related operations</span></span>

<span data-ttu-id="a1aaa-238">インターフェイス型を使用して、一連の操作を表します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-238">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="a1aaa-239">これは、関数の組や関数のレコードなど、他のオプションにも適しています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-239">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="a1aaa-240">次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-240">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

<span data-ttu-id="a1aaa-241">インターフェイスは .NET のファーストクラスの概念であり、通常どのような機能を提供するかを実現するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-241">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="a1aaa-242">また、プログラムに存在する型をエンコードするために使用することもできます。関数のレコードは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-242">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-that-act-on-collections"></a><span data-ttu-id="a1aaa-243">モジュールを使用して、コレクションに対して機能する関数をグループ化する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-243">Use a module to group functions that act on collections</span></span>

<span data-ttu-id="a1aaa-244">コレクション型を定義する場合は、 `CollectionType.map` `CollectionType.iter` 新しいコレクション型に対してやなどの標準的な操作のセットを提供することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-244">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="a1aaa-245">このようなモジュールを含める場合は、Fsharp.core で見つかった関数の標準的な名前付け規則に従います。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-245">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="a1aaa-246">モジュールを使用して、一般的な正規関数の関数をグループ化します。数学および DSL ライブラリでは特にそうです。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-246">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="a1aaa-247">たとえば、 `Microsoft.FSharp.Core.Operators` は、 `abs` `sin` FSharp.Core.dll によって提供されるトップレベル関数 (やなど) の自動オープンコレクションです。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-247">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="a1aaa-248">同様に、統計ライブラリには関数と関数を含むモジュールが含まれている場合があり `erf` `erfc` ます。このモジュールは、明示的に、または自動的に開くように設計されています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-248">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="a1aaa-249">RequireQualifiedAccess を使用して、AutoOpen 属性を慎重に適用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-249">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="a1aaa-250">モジュールに属性を追加すると、モジュールが `[<RequireQualifiedAccess>]` 開かれていないこと、およびモジュールの要素への参照に明示的な修飾アクセスが必要であることが示されます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-250">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="a1aaa-251">たとえば、モジュールに `Microsoft.FSharp.Collections.List` はこの属性があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-251">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="a1aaa-252">これは、モジュールの関数と値の名前が、他のモジュールの名前と競合する可能性がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-252">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="a1aaa-253">修飾されたアクセスを必要とすると、ライブラリの長期的な保守性と発展性を大幅に向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-253">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="a1aaa-254">`[<AutoOpen>]`モジュールに属性を追加すると、含まれている名前空間を開いたときにモジュールが開かれることを意味します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-254">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="a1aaa-255">アセンブリ `[<AutoOpen>]` を参照するときに自動的に開くモジュールを示すために、属性をアセンブリに適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-255">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="a1aaa-256">たとえば、統計ライブラリ **MathsHeaven** には、を `module MathsHeaven.Statistics.Operators` 含む関数とが含まれている場合があります。 `erf` `erfc`</span><span class="sxs-lookup"><span data-stu-id="a1aaa-256">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="a1aaa-257">このモジュールをとしてマークするのは妥当です `[<AutoOpen>]` 。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-257">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="a1aaa-258">また、 `open MathsHeaven.Statistics` このモジュールを開き、名前 `erf` とスコープをにすることもでき `erfc` ます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-258">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="a1aaa-259">のもう1つの優れた使用 `[<AutoOpen>]` 方法は、拡張メソッドを含むモジュールです。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-259">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="a1aaa-260">`[<AutoOpen>]`潜在顧客を汚染され名前空間に使用すると、属性を慎重に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-260">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="a1aaa-261">特定のドメイン内の特定のライブラリについては、を慎重 `[<AutoOpen>]` に使用することで、使いやすさを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-261">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="a1aaa-262">よく知られている演算子を使用する場合は、クラスに演算子メンバーを定義することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-262">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="a1aaa-263">ベクターなどの数学的構造をモデル化するために、クラスが使用されることがあります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-263">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="a1aaa-264">モデル化されているドメインに既知の演算子がある場合は、そのドメインをクラスに組み込まれているメンバーとして定義すると便利です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-264">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="a1aaa-265">このガイダンスは、これらの型の .NET の一般的なガイダンスに対応しています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-265">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="a1aaa-266">ただし、F # コーディングではさらに重要になることがあります。これにより、これらの型を、# sumBy などのメンバー制約を持つ F # 関数およびメソッドと組み合わせて使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-266">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="a1aaa-267">CompiledName を使用してを提供することを検討してください。他の .NET 言語コンシューマーの NET フレンドリ名</span><span class="sxs-lookup"><span data-stu-id="a1aaa-267">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="a1aaa-268">場合によっては、F # コンシューマーの1つのスタイル (たとえば、小文字の静的メンバー) に名前を付けて、アセンブリにコンパイルされるときに、名前に異なるスタイルを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-268">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="a1aaa-269">属性を使用して、 `[<CompiledName>]` F # 以外のコードでアセンブリを使用するための別のスタイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-269">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="a1aaa-270">を使用 `[<CompiledName>]` すると、アセンブリの F # 以外のコンシューマーに .net の名前付け規則を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-270">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="a1aaa-271">より単純な API を提供する場合は、メンバー関数に対してメソッドのオーバーロードを使用する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-271">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="a1aaa-272">メソッドのオーバーロードは、同様の機能を実行する必要があるが、異なるオプションや引数を使用して API を簡素化するための強力なツールです。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-272">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="a1aaa-273">F # では、引数の型ではなく、引数の数に対してオーバーロードする方が一般的です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-273">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="a1aaa-274">これらの型の設計が進化する可能性が高い場合に、レコードと共用体型の表現を非表示にする</span><span class="sxs-lookup"><span data-stu-id="a1aaa-274">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="a1aaa-275">オブジェクトの具象表現が明らかにならないようにします。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-275">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="a1aaa-276">たとえば、値の具象表現 <xref:System.DateTime> は、.net ライブラリデザインの外部のパブリック API では公開されません。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-276">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="a1aaa-277">実行時に共通言語ランタイムは、実行全体で使用されるコミット済みの実装を認識します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-277">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="a1aaa-278">ただし、コンパイルされたコード自体は、具象表現の依存関係を取得しません。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-278">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="a1aaa-279">拡張機能の実装継承の使用を回避する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-279">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="a1aaa-280">F # では、実装の継承はほとんど使用されません。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-280">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="a1aaa-281">また、多くの場合、継承階層は複雑で、新しい要件が発生したときに変更するのは困難です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-281">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="a1aaa-282">互換性のために F # には継承の実装が存在しますが、問題の解決策として最適なソリューションであることがありますが、インターフェイスの実装など、ポリモーフィズムを設計する際には、F # プログラムで代替手法を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-282">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="a1aaa-283">関数とメンバーのシグネチャ</span><span class="sxs-lookup"><span data-stu-id="a1aaa-283">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="a1aaa-284">複数の関連性のない値の数が少ない場合に、戻り値に組を使用する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-284">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="a1aaa-285">戻り値の型で組を使用する場合の適切な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-285">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="a1aaa-286">多くのコンポーネントを含む戻り値の型、またはコンポーネントが1つの特定可能なエンティティに関連する場合は、タプルではなく名前付きの型を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-286">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="a1aaa-287">`Async<T>`F # API の境界で非同期プログラミングに使用する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-287">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="a1aaa-288">という名前の同期操作があり、それによってが返される場合、 `Operation` 非同期操作は、を返す場合は、それが返される場合 `T` はという名前にする必要があり `AsyncOperation` `Async<T>` `OperationAsync` `Task<T>` ます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-288">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="a1aaa-289">Begin/End メソッドを公開する一般的に使用される .NET 型については、を使用して、 `Async.FromBeginEnd` その .Net api に F # の非同期プログラミングモデルを提供するための拡張メソッドをファサードとして記述することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-289">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

```fsharp
type SomeType =
    member this.Compute(x:int): int =
        ...
    member this.AsyncCompute(x:int): Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a><span data-ttu-id="a1aaa-290">例外</span><span class="sxs-lookup"><span data-stu-id="a1aaa-290">Exceptions</span></span>

<span data-ttu-id="a1aaa-291">例外、結果、およびオプションの適切な使用方法については、「 [エラー管理](conventions.md#error-management) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-291">See [Error Management](conventions.md#error-management) to learn about appropriate use of exceptions, results, and options.</span></span>

### <a name="extension-members"></a><span data-ttu-id="a1aaa-292">拡張メンバー</span><span class="sxs-lookup"><span data-stu-id="a1aaa-292">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="a1aaa-293">F # から f # のコンポーネントに F # 拡張メンバーを慎重に適用する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-293">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="a1aaa-294">F # 拡張メンバーは、一般に使用されているほとんどのモードの型に関連付けられている組み込み操作を終了する操作にのみ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-294">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="a1aaa-295">一般的な用途の1つは、さまざまな .NET 型に対して F # に慣用的なする Api を提供することです。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-295">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="a1aaa-296">共用体型</span><span class="sxs-lookup"><span data-stu-id="a1aaa-296">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="a1aaa-297">ツリー構造データのクラス階層の代わりに判別共用体を使用する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-297">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="a1aaa-298">ツリーのような構造体は再帰的に定義されます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-298">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="a1aaa-299">これは継承には不便ですが、判別共用体を使用すると洗練されています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-299">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="a1aaa-300">また、判別共用体を使用してツリーのようなデータを表すことで、パターンマッチングで exhaustiveness を活用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-300">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="a1aaa-301">`[<RequireQualifiedAccess>]`ケース名が十分に一意でない共用体型で使用する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-301">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="a1aaa-302">判別共用体のケースなど、さまざまな項目に対して、同じ名前が最適な名前であるドメインが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-302">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="a1aaa-303">を使用すると `[<RequireQualifiedAccess>]` 、ステートメントの順序に依存するシャドウが原因で混乱エラーが発生しないようにするために、ケース名を明確にすることができます。 `open`</span><span class="sxs-lookup"><span data-stu-id="a1aaa-303">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="a1aaa-304">これらの型の設計が進化する可能性がある場合は、バイナリ互換の Api の判別共用体の表現を非表示にします</span><span class="sxs-lookup"><span data-stu-id="a1aaa-304">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="a1aaa-305">共用体の型は、簡潔なプログラミングモデルの F # パターンマッチングフォームに依存しています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-305">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="a1aaa-306">前述のように、これらの型の設計が進化する可能性がある場合は、具象データ表現が明らかにならないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-306">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="a1aaa-307">たとえば、判別共用体の表現は、プライベートまたは内部の宣言を使用して、または署名ファイルを使用して非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-307">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="a1aaa-308">判別共用体をむやみに明らかにすると、ユーザーコードを壊さずにライブラリのバージョンを作成することが困難になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-308">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="a1aaa-309">代わりに、1つまたは複数のアクティブパターンを明らかにして、型の値に対するパターンマッチングを許可することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-309">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="a1aaa-310">アクティブパターンを使用すると、f # のコンシューマーにパターンマッチングを提供する代わりに、F # 共用体型を直接公開しないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-310">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="a1aaa-311">インライン関数とメンバー制約</span><span class="sxs-lookup"><span data-stu-id="a1aaa-311">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="a1aaa-312">暗黙的なメンバー制約と静的に解決されるジェネリック型を持つインライン関数を使用して、汎用数値アルゴリズムを定義します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-312">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="a1aaa-313">算術メンバー制約と F # 比較制約は、F # プログラミングの標準です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-313">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="a1aaa-314">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-314">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="a1aaa-315">この関数の型は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-315">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="a1aaa-316">これは、数学的ライブラリのパブリック API に適した関数です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-316">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="a1aaa-317">型クラスとアヒル型のシミュレーションにメンバー制約を使用しない</span><span class="sxs-lookup"><span data-stu-id="a1aaa-317">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="a1aaa-318">F # メンバー制約を使用して "アヒル入力" をシミュレートすることができます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-318">It is possible to simulate "duck typing" using F# member constraints.</span></span> <span data-ttu-id="a1aaa-319">ただし、このを使用するメンバーは、F #-F # ライブラリの設計では一般的に使用されません。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-319">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="a1aaa-320">これは、不明または非標準の暗黙的な制約に基づくライブラリデザインが、ユーザーコードが柔軟性を持たなくなり、1つの特定のフレームワークパターンに関連付けられる可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-320">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="a1aaa-321">また、このような方法でメンバー制約を多用すると、コンパイル時間が非常に長くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-321">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="a1aaa-322">演算子の定義</span><span class="sxs-lookup"><span data-stu-id="a1aaa-322">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="a1aaa-323">カスタムのシンボリック演算子を定義しない</span><span class="sxs-lookup"><span data-stu-id="a1aaa-323">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="a1aaa-324">カスタム演算子は、状況によっては不可欠であり、大規模な数値表記の実装コード内でデバイスを使用すると非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-324">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="a1aaa-325">ライブラリの新しいユーザーには、多くの場合、名前付き関数を使用する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-325">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="a1aaa-326">さらに、カスタムのシンボリック演算子をドキュメント化するのは難しい場合があります。また、ユーザーは、IDE や検索エンジンの既存の制限事項により、演算子のヘルプを検索するのが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-326">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="a1aaa-327">そのため、機能を名前付きの関数やメンバーとして公開することをお勧めします。また、この機能のための演算子を公開するのは、数値表記の利点がドキュメントとそれを持つ認知コストを上回る場合に限られます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-327">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="a1aaa-328">測定単位</span><span class="sxs-lookup"><span data-stu-id="a1aaa-328">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="a1aaa-329">F # コードでタイプセーフを追加するために、測定単位を慎重に使用する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-329">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="a1aaa-330">測定単位の追加の入力情報は、他の .NET 言語で表示すると消去されます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-330">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="a1aaa-331">.NET のコンポーネント、ツール、およびリフレクションでは、種類が san 単位であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-331">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="a1aaa-332">たとえば、C# のコンシューマーはで `float` はなくを参照し `float<kg>` ます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-332">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="a1aaa-333">型略称</span><span class="sxs-lookup"><span data-stu-id="a1aaa-333">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="a1aaa-334">F # コードを簡略化するために型略称を慎重に使用する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-334">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="a1aaa-335">.NET のコンポーネント、ツール、およびリフレクションでは、型の省略名は表示されません。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-335">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="a1aaa-336">また、型の省略形を頻繁に使用することで、ドメインを実際のより複雑にすることもできます。これにより、コンシューマーを混乱させる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-336">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="a1aaa-337">メンバーとプロパティは、省略されている型で使用できるものと本質的に異なる必要があるパブリック型の型略称を避けてください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-337">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="a1aaa-338">この場合、省略されている型は、定義されている実際の型の表現に関してあまり多くを意味します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-338">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="a1aaa-339">代わりに、クラス型または単一ケースの判別共用体の省略形をラップすることを検討してください (または、パフォーマンスが重要な場合は、構造体型を使用して省略形をラップすることを検討してください)。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-339">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="a1aaa-340">たとえば、次のように、F # マップの特殊なケースとしてマルチマップを定義することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-340">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="a1aaa-341">ただし、この型の論理ドット表記演算は、マップ上の操作と同じではありません。たとえば、lookup 操作では適切です。[key] 例外を発生させるのではなく、キーがディクショナリに含まれていない場合は、空のリストを返します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-341">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="a1aaa-342">他の .NET 言語から使用するためのライブラリのガイドライン</span><span class="sxs-lookup"><span data-stu-id="a1aaa-342">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="a1aaa-343">他の .NET 言語で使用するためのライブラリを設計する場合は、 [.Net ライブラリのデザインガイドライン](../../standard/design-guidelines/index.md)に従うことが重要です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-343">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="a1aaa-344">このドキュメントでは、これらのライブラリには、制限なしで F # のコンストラクトを使用する F # 向けのライブラリではなく、バニラ .NET ライブラリというラベルが付けられています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-344">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="a1aaa-345">バニラ .NET ライブラリの設計は、パブリック API で F # 固有の構造を使用することを最小限にすることで、使い慣れた Api と慣用的な Api を他の .NET Framework と一貫性のあるものにすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-345">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="a1aaa-346">これらの規則については、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-346">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="a1aaa-347">名前空間と型のデザイン (他の .NET 言語から使用するライブラリ用)</span><span class="sxs-lookup"><span data-stu-id="a1aaa-347">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="a1aaa-348">コンポーネントのパブリック API に .NET の名前付け規則を適用する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-348">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="a1aaa-349">省略名と .NET の大文字と小文字のガイドラインを使用することに特に注意してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-349">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="a1aaa-350">コンポーネントの主要な組織構造として名前空間、型、およびメンバーを使用する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-350">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="a1aaa-351">パブリック機能を含むすべてのファイルは、宣言で始まる必要があり `namespace` ます。また、名前空間の公開されているエンティティは型だけです。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-351">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="a1aaa-352">F # モジュールは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-352">Do not use F# modules.</span></span>

<span data-ttu-id="a1aaa-353">非パブリックモジュールを使用して、実装コード、ユーティリティの種類、およびユーティリティ関数を保持します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-353">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="a1aaa-354">オーバーロードや、F # モジュール内で使用できないその他の .NET API デザインの概念を使用するように API を将来進化させることができるため、モジュールよりも静的な型を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-354">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="a1aaa-355">たとえば、次のパブリック API の代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-355">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="a1aaa-356">代わりに、次の点を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-356">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="a1aaa-357">型の設計が進化しない場合は、バニラ .NET Api で F # のレコード型を使用する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-357">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="a1aaa-358">F # のレコード型は、単純な .NET クラスにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-358">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="a1aaa-359">これらは、Api のいくつかの単純な安定した型に適しています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-359">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="a1aaa-360">`[<NoEquality>]` `[<NoComparison>]` インターフェイスの自動生成を抑制するには、属性と属性を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-360">Consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="a1aaa-361">また、バニラ .NET Api では、パブリックフィールドを公開するため、変更可能なレコードフィールドを使用しないようにします。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-361">Also avoid using mutable record fields in vanilla .NET APIs as these expose a public field.</span></span> <span data-ttu-id="a1aaa-362">クラスが将来の API の進化に対してより柔軟なオプションを提供するかどうかを常に検討してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-362">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="a1aaa-363">たとえば、次の F # コードでは、パブリック API を C# コンシューマーに公開しています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-363">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="a1aaa-364">F#: </span><span class="sxs-lookup"><span data-stu-id="a1aaa-364">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
```

<span data-ttu-id="a1aaa-365">C#:</span><span class="sxs-lookup"><span data-stu-id="a1aaa-365">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="a1aaa-366">バニラ .NET Api で F # 共用体型の表現を非表示にする</span><span class="sxs-lookup"><span data-stu-id="a1aaa-366">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="a1aaa-367">F # から F # へのコーディングでも、f # の共用体型は、コンポーネントの境界を越えて使用されることはよくありません。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-367">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="a1aaa-368">これらは、コンポーネントおよびライブラリ内で内部的に使用される場合に、優れた実装デバイスです。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-368">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="a1aaa-369">バニラ .NET API を設計するときは、プライベート宣言または署名ファイルを使用して、共用体型の表現を非表示にすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-369">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="a1aaa-370">また、共用体表現をメンバーで内部的に使用する型を拡張して、必要なを提供することもできます。NET に接続する API。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-370">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True

    /// A public member for use from C#
    member x.Evaluate =
        match x with
        | And(a,b) -> a.Evaluate && b.Evaluate
        | Not a -> not a.Evaluate
        | True -> true

    /// A public member for use from C#
    static member CreateAnd(a,b) = And(a,b)
```

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="a1aaa-371">フレームワークの設計パターンを使用した GUI とその他のコンポーネントの設計</span><span class="sxs-lookup"><span data-stu-id="a1aaa-371">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="a1aaa-372">.NET 内には、WinForms、WPF、ASP.NET など、さまざまなフレームワークが用意されています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-372">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="a1aaa-373">これらのフレームワークで使用するコンポーネントを設計する場合は、それぞれの名前付けと設計規則を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-373">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="a1aaa-374">たとえば、WPF プログラミングでは、設計するクラスの WPF デザインパターンを採用します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-374">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="a1aaa-375">ユーザーインターフェイスプログラミングのモデルの場合は、イベントや、にあるような通知ベースのコレクションなどのデザインパターンを使用し <xref:System.Collections.ObjectModel> ます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-375">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="a1aaa-376">オブジェクトとメンバーのデザイン (他の .NET 言語から使用するためのライブラリ用)</span><span class="sxs-lookup"><span data-stu-id="a1aaa-376">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="a1aaa-377">CLIEvent 属性を使用して .NET イベントを公開する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-377">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="a1aaa-378">`DelegateEvent`オブジェクトと (既定では型を使用するのではなく) を受け取る特定の .net デリゲート型を使用してを構築し `EventArgs` `Event` `FSharpHandler` ます。これにより、イベントが他の .net 言語になじみのある方法で公開されるようになります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-378">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x: int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-that-return-net-tasks"></a><span data-ttu-id="a1aaa-379">.NET タスクを返すメソッドとしての非同期操作の公開</span><span class="sxs-lookup"><span data-stu-id="a1aaa-379">Expose asynchronous operations as methods that return .NET tasks</span></span>

<span data-ttu-id="a1aaa-380">タスクは、アクティブな非同期計算を表すために .NET で使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-380">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="a1aaa-381">タスクは `Async<T>` 、"既に実行中" のタスクを表し、並列合成を実行する方法でまとめて構成することも、キャンセルシグナルやその他のコンテキストパラメーターの伝達を非表示にすることもできないため、F # のオブジェクトよりも一般的にはありません。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-381">Tasks are in general less compositional than F# `Async<T>` objects, since they represent "already executing" tasks and can't be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="a1aaa-382">ただし、このような場合でも、タスクを返すメソッドは、.NET での非同期プログラミングの標準的な表現です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-382">However, despite this, methods that return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="a1aaa-383">また、明示的なキャンセルトークンを使用することもよくあります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-383">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="a1aaa-384">F # 関数型の代わりに .NET デリゲート型を使用する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-384">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="a1aaa-385">ここで "F # の関数型" は、のような型 `int -> int` を意味します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-385">Here "F# function types" mean "arrow" types like `int -> int`.</span></span>

<span data-ttu-id="a1aaa-386">次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-386">Instead of this:</span></span>

```fsharp
member this.Transform(f: int->int) =
    ...
```

<span data-ttu-id="a1aaa-387">これを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-387">Do this:</span></span>

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

<span data-ttu-id="a1aaa-388">F # の関数型は、 `class FSharpFunc<T,U>` 他の .net 言語と同様に表示され、デリゲート型を理解する言語の機能やツールには適していません。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-388">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understands delegate types.</span></span> <span data-ttu-id="a1aaa-389">.NET Framework 3.5 以上を対象とする高階メソッドを作成する場合、 `System.Func` `System.Action` .net 開発者が低摩擦方式でこれらの api を使用できるようにするために、とデリゲートは発行する適切な api です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-389">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="a1aaa-390">(.NET Framework 2.0 を対象とする場合、システム定義のデリゲート型の方が制限されます。などの定義済みデリゲート型を使用する `System.Converter<T,U>` か、特定のデリゲート型を定義することを検討してください。)</span><span class="sxs-lookup"><span data-stu-id="a1aaa-390">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="a1aaa-391">フリップ側では、.NET デリゲートは F # 向けのライブラリに対しては自然なものではありません (F # に接続されたライブラリについては、次のセクションを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-391">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="a1aaa-392">そのため、バニラ .NET ライブラリの高階メソッドを開発する際には、一般的な実装方法として、F # の関数型を使用してすべての実装を作成し、その後、実際の F # 実装の上にあるシンファサードとしてデリゲートを使用してパブリック API を作成します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-392">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="a1aaa-393">F # のオプション値を返すのではなく、TryGetValue パターンを使用し、引数として F # オプションの値を取得するためにメソッドのオーバーロードを優先します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-393">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="a1aaa-394">Api での F # オプション型の一般的な使用パターンは、標準の .NET 設計手法を使用して、バニラ .NET Api での実装がより適切です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-394">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="a1aaa-395">F # オプションの値を返す代わりに、bool の戻り値の型と out パラメーターを "TryGetValue" パターンのように使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-395">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="a1aaa-396">F # オプションの値をパラメーターとして使用するのではなく、メソッドのオーバーロードまたは省略可能な引数を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-396">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal: byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x: int, y: int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x: int) = x

member this.ParamOverload(x: int, y: int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="a1aaa-397">\<T\> \<Key,Value\> パラメーターと戻り値には、.net コレクションインターフェイスの型 IEnumerable および IDictionary を使用します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-397">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="a1aaa-398">.NET 配列 `T[]` 、F # 型、などの具象コレクション型やなどの `list<T>` `Map<Key,Value>` `Set<T>` .net 具象コレクション型は使用しないようにして `Dictionary<Key,Value>` ください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-398">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="a1aaa-399">.NET ライブラリの設計ガイドラインでは、などのさまざまなコレクション型を使用するタイミングに関するアドバイスがあり `IEnumerable<T>` ます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-399">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="a1aaa-400">一部の `T[]` 状況では、パフォーマンス grounds で配列 () を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-400">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="a1aaa-401">特に `seq<T>` 、はの F # エイリアスであるため、 `IEnumerable<T>` seq は通常はバニラ .net API に適した型です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-401">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="a1aaa-402">F # リストの代わりに、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-402">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names: string list) =
    ...
```

<span data-ttu-id="a1aaa-403">F # のシーケンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-403">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="a1aaa-404">ゼロ引数メソッドを定義するメソッドの唯一の入力型として、または void を返すメソッドを定義する唯一の戻り値の型として、単位の種類を使用します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-404">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="a1aaa-405">ユニットの種類の他の用途は避けてください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-405">Avoid other uses of the unit type.</span></span> <span data-ttu-id="a1aaa-406">次のような方法があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-406">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

<span data-ttu-id="a1aaa-407">これは問題です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-407">This is bad:</span></span>

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="a1aaa-408">バニラ .NET API の境界で null 値を確認する</span><span class="sxs-lookup"><span data-stu-id="a1aaa-408">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="a1aaa-409">F # の実装コードでは、変更できないデザインパターンと F # 型の null リテラルの使用に関する制限があるため、null 値が少なくなる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-409">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="a1aaa-410">その他の .NET 言語では、多くの場合、値として null が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-410">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="a1aaa-411">このため、バニラ .NET API を公開する F # コードは、API の境界で null のパラメーターをチェックし、これらの値が F # の実装コードに深く流れないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-411">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="a1aaa-412">`isNull`パターンに対する関数またはパターンマッチングを `null` 使用できます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-412">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="a1aaa-413">戻り値としてタプルを使用しない</span><span class="sxs-lookup"><span data-stu-id="a1aaa-413">Avoid using tuples as return values</span></span>

<span data-ttu-id="a1aaa-414">代わりに、集計データを保持する名前付きの型を返すか、out パラメーターを使用して複数の値を返すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-414">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="a1aaa-415">タプルと構造体の組は .NET に存在しますが (構造体の組に対する C# 言語のサポートを含む)、ほとんどの場合、.NET 開発者にとって理想的で期待される API を提供しません。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-415">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="a1aaa-416">パラメーターのカリー化を使用しないようにする</span><span class="sxs-lookup"><span data-stu-id="a1aaa-416">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="a1aaa-417">代わりに、.NET の呼び出し規約を使用して `Method(arg1,arg2,…,argN)` ください。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-417">Instead, use .NET calling conventions `Method(arg1,arg2,…,argN)`.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="a1aaa-418">ヒント: 任意の .NET 言語で使用するためのライブラリを設計する場合、実際には、いくつかの試験的な C# および Visual Basic プログラミングを行って、これらの言語からライブラリが正しく動作するようにするための代替手段はありません。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-418">Tip: If you're designing libraries for use from any .NET language, then there's no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="a1aaa-419">.NET リフレクターや Visual Studio オブジェクトブラウザーなどのツールを使用して、ライブラリとそのドキュメントが開発者に期待どおりに表示されるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-419">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="a1aaa-420">付録</span><span class="sxs-lookup"><span data-stu-id="a1aaa-420">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="a1aaa-421">他の .NET 言語で使用する F # コードを設計するためのエンドツーエンドの例</span><span class="sxs-lookup"><span data-stu-id="a1aaa-421">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="a1aaa-422">次のクラスについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-422">Consider the following class:</span></span>

```fsharp
open System

type Point1(angle,radius) =
    new() = Point1(angle=0.0, radius=0.0)
    member x.Angle = angle
    member x.Radius = radius
    member x.Stretch(l) = Point1(angle=x.Angle, radius=x.Radius * l)
    member x.Warp(f) = Point1(angle=f(x.Angle), radius=x.Radius)
    static member Circle(n) =
        [ for i in 1..n -> Point1(angle=2.0*Math.PI/float(n), radius=1.0) ]
```

<span data-ttu-id="a1aaa-423">このクラスの推定 F # 型は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-423">The inferred F# type of this class is as follows:</span></span>

```fsharp
type Point1 =
    new : unit -> Point1
    new : angle:double * radius:double -> Point1
    static member Circle : n:int -> Point1 list
    member Stretch : l:double -> Point1
    member Warp : f:(double -> double) -> Point1
    member Angle : double
    member Radius : double
```

<span data-ttu-id="a1aaa-424">この F # の型が、プログラマに別の .NET 言語を使用してどのように表示されるかを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-424">Let's take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="a1aaa-425">たとえば、C# のおおよその "シグニチャ" は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-425">For example, the approximate C# "signature" is as follows:</span></span>

```csharp
// C# signature for the unadjusted Point1 class
public class Point1
{
    public Point1();

    public Point1(double angle, double radius);

    public static Microsoft.FSharp.Collections.List<Point1> Circle(int count);

    public Point1 Stretch(double factor);

    public Point1 Warp(Microsoft.FSharp.Core.FastFunc<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="a1aaa-426">ここでは、F # がコンストラクトを表す方法について注意する必要がある重要な点がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-426">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="a1aaa-427">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-427">For example:</span></span>

* <span data-ttu-id="a1aaa-428">引数名などのメタデータは保持されています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-428">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="a1aaa-429">2つの引数を受け取る F # メソッドは、2つの引数を受け取る C# メソッドになります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-429">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="a1aaa-430">関数とリストは、F # ライブラリ内の対応する型への参照になります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-430">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="a1aaa-431">次のコードは、このコードを調整してこれらの処理を考慮する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-431">The following code shows how to adjust this code to take these things into account.</span></span>

```fsharp
namespace SuperDuperFSharpLibrary.Types

type RadialPoint(angle:double, radius:double) =

    /// Return a point at the origin
    new() = RadialPoint(angle=0.0, radius=0.0)

    /// The angle to the point, from the x-axis
    member x.Angle = angle

    /// The distance to the point, from the origin
    member x.Radius = radius

    /// Return a new point, with radius multiplied by the given factor
    member x.Stretch(factor) =
        RadialPoint(angle=angle, radius=radius * factor)

    /// Return a new point, with angle transformed by the function
    member x.Warp(transform:Func<_,_>) =
        RadialPoint(angle=transform.Invoke angle, radius=radius)

    /// Return a sequence of points describing an approximate circle using
    /// the given count of points
    static member Circle(count) =
        seq { for i in 1..count ->
                RadialPoint(angle=2.0*Math.PI/float(count), radius=1.0) }
```

<span data-ttu-id="a1aaa-432">コードの推論された F # の型は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-432">The inferred F# type of the code is as follows:</span></span>

```fsharp
type RadialPoint =
    new : unit -> RadialPoint
    new : angle:double * radius:double -> RadialPoint
    static member Circle : count:int -> seq<RadialPoint>
    member Stretch : factor:double -> RadialPoint
    member Warp : transform:System.Func<double,double> -> RadialPoint
    member Angle : double
    member Radius : double
```

<span data-ttu-id="a1aaa-433">C# のシグネチャは、次のようになりました。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-433">The C# signature is now as follows:</span></span>

```csharp
public class RadialPoint
{
    public RadialPoint();

    public RadialPoint(double angle, double radius);

    public static System.Collections.Generic.IEnumerable<RadialPoint> Circle(int count);

    public RadialPoint Stretch(double factor);

    public RadialPoint Warp(System.Func<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="a1aaa-434">バニラ .NET ライブラリの一部として使用するために、この型を準備するために行われた修正は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-434">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="a1aaa-435">いくつかの名前が調整されました。、、 `Point1` `n` `l` 、およびは `f` `RadialPoint` 、それぞれ、、、 `count` `factor` および `transform` です。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-435">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="a1aaa-436">を使用する `seq<RadialPoint>` `RadialPoint list` シーケンス構造を使用して、を使用してリストの構築を変更することで、ではなく戻り値の型を使用していま `[ ... ]` `IEnumerable<RadialPoint>` した。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-436">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="a1aaa-437">F # 関数型ではなく、.NET デリゲート型を使用して `System.Func` います。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-437">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="a1aaa-438">これにより、C# コードでの使用がはるかに簡単になります。</span><span class="sxs-lookup"><span data-stu-id="a1aaa-438">This makes it far nicer to consume in C# code.</span></span>
