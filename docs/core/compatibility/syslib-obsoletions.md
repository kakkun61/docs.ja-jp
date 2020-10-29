---
title: .NET 5 以降の古い機能
description: SYSLIB コンパイラの警告を発生させる、.NET 5.0 以降のバージョンで古いものとしてマークされた API について説明します。
ms.date: 10/20/2020
ms.openlocfilehash: 13f5fb10cfe693ed621b3f45fc22e024875890c8
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333140"
---
# <a name="obsolete-features-in-net-5"></a><span data-ttu-id="31bd0-103">.NET 5 の古い機能</span><span class="sxs-lookup"><span data-stu-id="31bd0-103">Obsolete features in .NET 5</span></span>

<span data-ttu-id="31bd0-104">.NET 5.0 以降、新たに、古いものとしてマークされた一部の API によって、<xref:System.ObsoleteAttribute> の 2 つの新しいプロパティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="31bd0-104">Starting in .NET 5.0, some APIs that are newly marked as obsolete make use of two new properties on <xref:System.ObsoleteAttribute>.</span></span>

- <span data-ttu-id="31bd0-105"><xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType> プロパティは、カスタム診断 ID を使用してビルド警告を生成するようにコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="31bd0-105">The <xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType> property tells the compiler to generate build warnings using a custom diagnostic ID.</span></span> <span data-ttu-id="31bd0-106">カスタム ID を使用すると、旧型式であるという警告を明確に個別に分けて非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="31bd0-106">The custom ID allows for obsoletion warning to be suppressed specifically and separately from one another.</span></span> <span data-ttu-id="31bd0-107">.NET 5 以降の旧型式の場合、カスタム診断 ID の形式は `SYSLIBxxxx` です。</span><span class="sxs-lookup"><span data-stu-id="31bd0-107">In the case of the .NET 5+ obsoletions, the format for the custom diagnostic ID is `SYSLIBxxxx`.</span></span>

- <span data-ttu-id="31bd0-108"><xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType> プロパティは、旧型式の詳細について確認するために URL リンクを含めるようにコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="31bd0-108">The <xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType> property tells the compiler to include a URL link to learn more about the obsoletion.</span></span>

<span data-ttu-id="31bd0-109">古い API の使用によってビルドの警告またはエラーが発生した場合は、「[リファレンス](#reference)」セクションに記載されている診断 ID に関する具体的なガイダンスに従ってください。</span><span class="sxs-lookup"><span data-stu-id="31bd0-109">If you encounter build warnings or errors due to usage of an obsolete API, follow the specific guidance provided for the diagnostic ID listed in the [Reference](#reference) section.</span></span> <span data-ttu-id="31bd0-110">これらの古い警告またはエラーは、古い型またはメンバーに対して [標準診断 ID (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) を使用して非表示にすることは " *できません* "。代わりに、カスタム `SYSLIBxxxx` 診断 ID の値を使用してください。</span><span class="sxs-lookup"><span data-stu-id="31bd0-110">Warnings or errors for these obsoletions *can't* be suppressed using the [standard diagnostic ID (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) for obsolete types or members; use the custom `SYSLIBxxxx` diagnostic ID values instead.</span></span> <span data-ttu-id="31bd0-111">詳細については、「[警告を表示しない](#suppress-warnings)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31bd0-111">For more information, see [Suppress warnings](#suppress-warnings).</span></span>

## <a name="reference"></a><span data-ttu-id="31bd0-112">リファレンス</span><span class="sxs-lookup"><span data-stu-id="31bd0-112">Reference</span></span>

<span data-ttu-id="31bd0-113">次の表は、.NET 5 以降の `SYSLIBxxxx` 旧型式のインデックスを示しています。</span><span class="sxs-lookup"><span data-stu-id="31bd0-113">The following table provides an index to the `SYSLIBxxxx` obsoletions in .NET 5+.</span></span>

| <span data-ttu-id="31bd0-114">診断 ID</span><span class="sxs-lookup"><span data-stu-id="31bd0-114">Diagnostic ID</span></span> | <span data-ttu-id="31bd0-115">Description</span><span class="sxs-lookup"><span data-stu-id="31bd0-115">Description</span></span> |
| - | - |
| [<span data-ttu-id="31bd0-116">SYSLIB0001</span><span class="sxs-lookup"><span data-stu-id="31bd0-116">SYSLIB0001</span></span>](syslib0001.md) | <span data-ttu-id="31bd0-117">UTF-7 エンコードは安全ではないため、使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="31bd0-117">The UTF-7 encoding is insecure and should not be used.</span></span> <span data-ttu-id="31bd0-118">代わりに UTF-8 を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="31bd0-118">Consider using UTF-8 instead.</span></span> |
| [<span data-ttu-id="31bd0-119">SYSLIB0002</span><span class="sxs-lookup"><span data-stu-id="31bd0-119">SYSLIB0002</span></span>](syslib0002.md) | <span data-ttu-id="31bd0-120"><xref:System.Security.Permissions.PrincipalPermissionAttribute> はランタイムによって受け入れられず、使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="31bd0-120"><xref:System.Security.Permissions.PrincipalPermissionAttribute> is not honored by the runtime and must not be used.</span></span> |
| [<span data-ttu-id="31bd0-121">SYSLIB0003</span><span class="sxs-lookup"><span data-stu-id="31bd0-121">SYSLIB0003</span></span>](syslib0003.md) | <span data-ttu-id="31bd0-122">コード アクセス セキュリティ (CAS) はサポートされていないか、ランタイムによって受け入れられていません。</span><span class="sxs-lookup"><span data-stu-id="31bd0-122">Code access security (CAS) is not supported or honored by the runtime.</span></span> |
| [<span data-ttu-id="31bd0-123">SYSLIB0004</span><span class="sxs-lookup"><span data-stu-id="31bd0-123">SYSLIB0004</span></span>](syslib0004.md) | <span data-ttu-id="31bd0-124">制約された実行領域 (CER) 機能はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="31bd0-124">The constrained execution region (CER) feature is not supported.</span></span> |
| [<span data-ttu-id="31bd0-125">SYSLIB0005</span><span class="sxs-lookup"><span data-stu-id="31bd0-125">SYSLIB0005</span></span>](syslib0005.md) | <span data-ttu-id="31bd0-126">グローバル アセンブリ キャッシュ (GAC) はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="31bd0-126">The global assembly cache (GAC) is not supported.</span></span> |
| [<span data-ttu-id="31bd0-127">SYSLIB0006</span><span class="sxs-lookup"><span data-stu-id="31bd0-127">SYSLIB0006</span></span>](syslib0006.md) | <span data-ttu-id="31bd0-128"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> はサポートされていません。<xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="31bd0-128"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="31bd0-129">SYSLIB0007</span><span class="sxs-lookup"><span data-stu-id="31bd0-129">SYSLIB0007</span></span>](syslib0007.md) | <span data-ttu-id="31bd0-130">この暗号化アルゴリズムの既定の実装はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="31bd0-130">The default implementation of this cryptography algorithm is not supported.</span></span> |
| [<span data-ttu-id="31bd0-131">SYSLIB0008</span><span class="sxs-lookup"><span data-stu-id="31bd0-131">SYSLIB0008</span></span>](syslib0008.md) | <span data-ttu-id="31bd0-132"><xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API はサポートされていません。<xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="31bd0-132">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="31bd0-133">SYSLIB0009</span><span class="sxs-lookup"><span data-stu-id="31bd0-133">SYSLIB0009</span></span>](syslib0009.md) | <span data-ttu-id="31bd0-134"><xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> および <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> メソッドはサポートされていません。<xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="31bd0-134">The <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> and <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> methods are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="31bd0-135">SYSLIB0010</span><span class="sxs-lookup"><span data-stu-id="31bd0-135">SYSLIB0010</span></span>](syslib0010.md) | <span data-ttu-id="31bd0-136">一部のリモート処理 API はサポートされていません。<xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="31bd0-136">Some remoting APIs are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="31bd0-137">SYSLIB0011</span><span class="sxs-lookup"><span data-stu-id="31bd0-137">SYSLIB0011</span></span>](syslib0011.md) | <span data-ttu-id="31bd0-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> シリアル化は古いので使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="31bd0-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is obsolete and should not be used.</span></span> |
| [<span data-ttu-id="31bd0-139">SYSLIB0012</span><span class="sxs-lookup"><span data-stu-id="31bd0-139">SYSLIB0012</span></span>](syslib0012.md) | <span data-ttu-id="31bd0-140"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> と <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> は .NET Framework との互換性のためだけに含まれています。</span><span class="sxs-lookup"><span data-stu-id="31bd0-140"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> and <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> are only included for .NET Framework compatibility.</span></span> <span data-ttu-id="31bd0-141">代わりに、<xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> を使用してください。</span><span class="sxs-lookup"><span data-stu-id="31bd0-141">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span> |

## <a name="suppress-warnings"></a><span data-ttu-id="31bd0-142">警告を表示しない</span><span class="sxs-lookup"><span data-stu-id="31bd0-142">Suppress warnings</span></span>

<span data-ttu-id="31bd0-143">古い API を使用する必要があり、`SYSLIBxxxx` 診断がエラーとして表示されない場合は、コードまたはプロジェクト ファイルで警告を非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="31bd0-143">If you must use the obsolete APIs and the `SYSLIBxxxx` diagnostic does not surface as an error, you can suppress the warning in code or in your project file.</span></span>

<span data-ttu-id="31bd0-144">コードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="31bd0-144">In code:</span></span>

```csharp
// Disable the warning.
#pragma warning disable SYSLIB0001
// Code that uses obsolete API.
...
// Re-enable the warning.
#pragma warning restore SYSLIB0001
```

<span data-ttu-id="31bd0-145">プロジェクト ファイル:</span><span class="sxs-lookup"><span data-stu-id="31bd0-145">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
   <TargetFramework>net5.0</TargetFramework>
   <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
   <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
  </PropertyGroup>
</Project>
```

> [!NOTE]
> <span data-ttu-id="31bd0-146">この方法で警告を非表示にすると、特定の旧型式の警告のみが無効になります。</span><span class="sxs-lookup"><span data-stu-id="31bd0-146">Suppressing a warning in this way only disables that specific obsoletion warning.</span></span> <span data-ttu-id="31bd0-147">他の旧型式であるというも含め、他の警告は一切無効になりません。</span><span class="sxs-lookup"><span data-stu-id="31bd0-147">It doesn't disable any other warnings, including other obsoletion warnings.</span></span>
