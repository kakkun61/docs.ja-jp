---
ms.openlocfilehash: 959d8cb6d3e52916f6777054f3e9b327dc8edb4e
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434933"
---
### <a name="global-assembly-cache-apis-are-obsolete"></a><span data-ttu-id="73b0a-101">グローバル アセンブリ キャッシュ API は旧型式</span><span class="sxs-lookup"><span data-stu-id="73b0a-101">Global assembly cache APIs are obsolete</span></span>

<span data-ttu-id="73b0a-102">.NET Core および .NET 5.0 以降のバージョンでは、.NET Framework に存在していたグローバル アセンブリ キャッシュ (GAC) の概念がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="73b0a-102">.NET Core and .NET 5.0 and later versions eliminate the concept of the global assembly cache (GAC) that was present in .NET Framework.</span></span> <span data-ttu-id="73b0a-103">そのため、GAC を処理するすべての .NET Core および .NET 5 以降の API は失敗するか、操作が実行されません。</span><span class="sxs-lookup"><span data-stu-id="73b0a-103">As such, all .NET Core and .NET 5+ APIs that deal with the GAC either fail or perform no operation.</span></span>

<span data-ttu-id="73b0a-104">開発者がこれらの API を使用しないようにするために、一部の GAC 関連の API は古いものとしてマークされており、コンパイル時に `SYSLIB0005` 警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="73b0a-104">To help steer developers away from these APIs, some GAC-related APIs are marked as obsolete, and generate a `SYSLIB0005` warning at compile time.</span></span> <span data-ttu-id="73b0a-105">これらの API は、将来のバージョンの .NET で削除される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="73b0a-105">These APIs may be removed in a future version of .NET.</span></span>

#### <a name="change-description"></a><span data-ttu-id="73b0a-106">変更内容</span><span class="sxs-lookup"><span data-stu-id="73b0a-106">Change description</span></span>

<span data-ttu-id="73b0a-107">次の API は古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="73b0a-107">The following APIs are marked obsolete.</span></span>

| <span data-ttu-id="73b0a-108">API</span><span class="sxs-lookup"><span data-stu-id="73b0a-108">API</span></span> | <span data-ttu-id="73b0a-109">古いものとしてマークされる対象</span><span class="sxs-lookup"><span data-stu-id="73b0a-109">Marked obsolete in...</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType> | <span data-ttu-id="73b0a-110">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="73b0a-110">5.0 RC1</span></span> |

<span data-ttu-id="73b0a-111">.NET Framework 2.x から 4.x では、クエリが実行されたアセンブリが GAC から読み込まれた場合は <xref:System.Reflection.Assembly.GlobalAssemblyCache> プロパティから `true` が返され、ディスク上の異なる場所から読み込まれた場合は `false` が返されます。</span><span class="sxs-lookup"><span data-stu-id="73b0a-111">In .NET Framework 2.x - 4.x, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property returns `true` if the queried assembly was loaded from the GAC, and `false` if it was loaded from a different location on disk.</span></span> <span data-ttu-id="73b0a-112">.NET Core 2.x から 3.x では、<xref:System.Reflection.Assembly.GlobalAssemblyCache> から常に `false` が返されます。これは、GAC が .NET Core に存在しないことを反映しています。</span><span class="sxs-lookup"><span data-stu-id="73b0a-112">In .NET Core 2.x - 3.x, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> always returns `false`, reflecting that the GAC does not exist in .NET Core.</span></span>

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'True' on .NET Framework, 'False' on .NET Core.
Console.WriteLine(asm.GlobalAssemblyCache);
```

<span data-ttu-id="73b0a-113">.NET 5.0 以降のバージョンでは、<xref:System.Reflection.Assembly.GlobalAssemblyCache> プロパティからは引き続き、常に `false` が返されます。</span><span class="sxs-lookup"><span data-stu-id="73b0a-113">In .NET 5.0 and later versions, the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property continues to always return `false`.</span></span> <span data-ttu-id="73b0a-114">しかし、プロパティ getter も、プロパティへのアクセスを停止する必要があることを呼び出し元に示すために、古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="73b0a-114">However, the property getter is also marked as obsolete to indicate to callers that they should stop accessing the property.</span></span> <span data-ttu-id="73b0a-115">ライブラリとアプリで実行時の動作を決定するために <xref:System.Reflection.Assembly.GlobalAssemblyCache> API を使用することはできません。これは、.NET Core および .NET 5.0 以降のバージョンでは常に `false` が返されるためです。</span><span class="sxs-lookup"><span data-stu-id="73b0a-115">Libraries and apps should not use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> API to make determinations about run-time behavior, as it always returns `false` in .NET Core and .NET 5.0 and later versions.</span></span>

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'False' on .NET 5.0+; also produces warning SYSLIB0005 at compile time.
Console.WriteLine(asm.GlobalAssemblyCache);
```

<span data-ttu-id="73b0a-116">これは、コンパイル時のみの変更です。</span><span class="sxs-lookup"><span data-stu-id="73b0a-116">This is a compile-time only change.</span></span> <span data-ttu-id="73b0a-117">実行時については、以前のバージョンの .NET Core からの変更はありません。</span><span class="sxs-lookup"><span data-stu-id="73b0a-117">There is no run-time change from previous versions of .NET Core.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="73b0a-118">変更理由</span><span class="sxs-lookup"><span data-stu-id="73b0a-118">Reason for change</span></span>

<span data-ttu-id="73b0a-119">.NET Core および .NET 5.0 以降のバージョンでは、グローバル アセンブリ キャッシュ (GAC) は概念として存在しません。</span><span class="sxs-lookup"><span data-stu-id="73b0a-119">The global assembly cache (GAC) does not exist as a concept in .NET Core and .NET 5.0 and later versions.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="73b0a-120">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="73b0a-120">Version introduced</span></span>

<span data-ttu-id="73b0a-121">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="73b0a-121">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="73b0a-122">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="73b0a-122">Recommended action</span></span>

- <span data-ttu-id="73b0a-123">アプリケーションによって <xref:System.Reflection.Assembly.GlobalAssemblyCache> プロパティのクエリが実行される場合は、呼び出しを削除することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="73b0a-123">If your application queries the <xref:System.Reflection.Assembly.GlobalAssemblyCache> property, consider removing the call.</span></span> <span data-ttu-id="73b0a-124"><xref:System.Reflection.Assembly.GlobalAssemblyCache> 値を使用して、実行時に "GAC のアセンブリ" フローと "GAC に存在しないアセンブリ" フローのどちらかを選択する場合は、フローが .NET Core または .NET 5.0 以降のアプリケーションで引き続き意味を持つかどうかを再検討してください。</span><span class="sxs-lookup"><span data-stu-id="73b0a-124">If you use the <xref:System.Reflection.Assembly.GlobalAssemblyCache> value to choose between an "assembly in the GAC"-flow vs. an "assembly not in the GAC"-flow at run time, reconsider whether the flow still makes sense for a .NET Core or .NET 5.0+ application.</span></span>

- <span data-ttu-id="73b0a-125">古い API を引き続き使用する必要がある場合は、コードで `SYSLIB0005` 警告を抑制することができます。</span><span class="sxs-lookup"><span data-stu-id="73b0a-125">If you must continue to use the obsolete APIs, you can suppress the `SYSLIB0005` warning in code.</span></span>

  ```csharp
  Assembly asm = typeof(object).Assembly;
  #pragma warning disable SYSLIB0005 // Disable the warning.
  // Prints 'False' on .NET 5.0+.
  Console.WriteLine(asm.GlobalAssemblyCache);
  #pragma warning restore SYSLIB0005 // Re-enable the warning.
  ```

  <span data-ttu-id="73b0a-126">プロジェクト ファイルで警告を抑制することもできます。これにより、プロジェクト内のすべてのソース ファイルに対して警告が無効になります。</span><span class="sxs-lookup"><span data-stu-id="73b0a-126">You can also suppress the warning in your project file, which disables the warning for all source files in the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0005 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0005</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="73b0a-127">`SYSLIB0005` を抑制すると、<xref:System.Reflection.Assembly.GlobalAssemblyCache> が旧型式であるという警告のみが無効になります。</span><span class="sxs-lookup"><span data-stu-id="73b0a-127">Suppressing `SYSLIB0005` disables only the <xref:System.Reflection.Assembly.GlobalAssemblyCache> obsoletion warning.</span></span> <span data-ttu-id="73b0a-128">それ以外の警告は無効になりません。</span><span class="sxs-lookup"><span data-stu-id="73b0a-128">It does not disable any other warnings.</span></span>

#### <a name="category"></a><span data-ttu-id="73b0a-129">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="73b0a-129">Category</span></span>

<span data-ttu-id="73b0a-130">Core .NET ライブラリ</span><span class="sxs-lookup"><span data-stu-id="73b0a-130">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="73b0a-131">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="73b0a-131">Affected APIs</span></span>

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Reflection.Assembly.GlobalAssemblyCache`

-->
