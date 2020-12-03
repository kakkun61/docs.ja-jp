---
title: 破壊的変更:Environment.OSVersion で正しいオペレーティング システム バージョンが返される
description: Environment.OSVersion から、たとえば、アプリケーションの互換性にために選択されている OS ではなく、オペレーティング システムの実際のバージョンが返されるという、コア .NET ライブラリの .NET 5.0 破壊的変更について学習します。
ms.date: 11/01/2020
ms.openlocfilehash: b78ca1c7be50f76b99b5558a976d8f00e2f560c3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760073"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a><span data-ttu-id="ade84-103">Environment.OSVersion で正しいオペレーティング システム バージョンが返される</span><span class="sxs-lookup"><span data-stu-id="ade84-103">Environment.OSVersion returns the correct operating system version</span></span>

<span data-ttu-id="ade84-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> で、アプリケーションの互換性のために選択される OS などではなく、オペレーティング システム (OS) の実際のバージョンが返されます。</span><span class="sxs-lookup"><span data-stu-id="ade84-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system (OS) instead of, for example, the OS that's selected for application compatibility.</span></span>

## <a name="change-description"></a><span data-ttu-id="ade84-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="ade84-105">Change description</span></span>

<span data-ttu-id="ade84-106">以前のバージョンの .NET では、アプリケーションが Windows 互換モードで実行されている場合、<xref:System.Environment.OSVersion?displayProperty=nameWithType> によって、正しくない可能性がある OS バージョンが返されます。</span><span class="sxs-lookup"><span data-stu-id="ade84-106">In previous .NET versions, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns an OS version that may be incorrect when an application runs under Windows compatibility mode.</span></span> <span data-ttu-id="ade84-107">詳細については、[GetVersionExA 関数の解説](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks)に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ade84-107">For more information, see [GetVersionExA function remarks](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span></span>

<span data-ttu-id="ade84-108">.NET 5.0 以降では、<xref:System.Environment.OSVersion?displayProperty=nameWithType> によってオペレーティング システムの実際のバージョンが返されます。</span><span class="sxs-lookup"><span data-stu-id="ade84-108">Starting in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="ade84-109">変更理由</span><span class="sxs-lookup"><span data-stu-id="ade84-109">Reason for change</span></span>

<span data-ttu-id="ade84-110">このプロパティのユーザーは、オペレーティング システムの実際のバージョンが返されることを期待しています。</span><span class="sxs-lookup"><span data-stu-id="ade84-110">Users of this property expect it to return the actual version of the operating system.</span></span> <span data-ttu-id="ade84-111">ほとんどの .NET アプリにより、アプリケーション マニフェストでサポートされているバージョンが指定されないため、dotnet ホストから既定でサポートされているバージョンが取得されます。</span><span class="sxs-lookup"><span data-stu-id="ade84-111">Most .NET apps don't specify their supported version in their application manifest, and thus get the default supported version from the dotnet host.</span></span> <span data-ttu-id="ade84-112">その結果、実行されているアプリでは互換性 shim はほとんど意味がなくなります。</span><span class="sxs-lookup"><span data-stu-id="ade84-112">As a result, the compatibility shim is rarely meaningful for the app that's running.</span></span> <span data-ttu-id="ade84-113">Windows で新しいバージョンがリリースされており、古い dotnet ホストがまだ使用されている場合は、これらのアプリの OS バージョンが正しくない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ade84-113">When Windows releases a new version and an older dotnet host is still in use, these apps may get an incorrect OS version.</span></span> <span data-ttu-id="ade84-114">実際のバージョンを返すことが、この API に対する開発者の期待により沿うことになります。</span><span class="sxs-lookup"><span data-stu-id="ade84-114">Returning the actual version is more inline with developers' expectations of this API.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ade84-115">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="ade84-115">Version introduced</span></span>

<span data-ttu-id="ade84-116">5.0</span><span class="sxs-lookup"><span data-stu-id="ade84-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ade84-117">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="ade84-117">Recommended action</span></span>

<span data-ttu-id="ade84-118"><xref:System.Environment.OSVersion?displayProperty=nameWithType> を使用するコードを確認してテストし、確実に期待どおりに動作するようにします。</span><span class="sxs-lookup"><span data-stu-id="ade84-118">Review and test any code that uses <xref:System.Environment.OSVersion?displayProperty=nameWithType> to ensure it behaves as desired.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="ade84-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="ade84-119">Affected APIs</span></span>

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->
