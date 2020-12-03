---
title: .NET ライブラリの破壊的変更
description: .NET Core バージョン 1.0-3.0 の Core .NET ライブラリにおける破壊的変更の一覧を示します。
ms.date: 07/27/2020
ms.openlocfilehash: 0f42429e44776fc70bb99ed3bdf346f0d5dbc9eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "96032044"
---
# <a name="core-net-libraries-breaking-changes-in-net-core-10-30"></a><span data-ttu-id="0cdf8-103">.NET Core 1.0-3.0 の Core .NET ライブラリの破壊的変更</span><span class="sxs-lookup"><span data-stu-id="0cdf8-103">Core .NET libraries breaking changes in .NET Core 1.0-3.0</span></span>

<span data-ttu-id="0cdf8-104">Core .NET ライブラリでは、.NET Core で使用されるプリミティブとその他の一般的な型が提供されます。</span><span class="sxs-lookup"><span data-stu-id="0cdf8-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="0cdf8-105">このページでは、次の破壊的変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="0cdf8-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="0cdf8-106">互換性に影響する変更点</span><span class="sxs-lookup"><span data-stu-id="0cdf8-106">Breaking change</span></span> | <span data-ttu-id="0cdf8-107">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="0cdf8-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="0cdf8-108">バージョンをレポートする API が、ファイル バージョンではなく製品をレポートするようになった</span><span class="sxs-lookup"><span data-stu-id="0cdf8-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="0cdf8-109">3.0</span><span class="sxs-lookup"><span data-stu-id="0cdf8-109">3.0</span></span> |
| [<span data-ttu-id="0cdf8-110">カスタム EncoderFallbackBuffer インスタンスが再帰的にフォールバックしない</span><span class="sxs-lookup"><span data-stu-id="0cdf8-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="0cdf8-111">3.0</span><span class="sxs-lookup"><span data-stu-id="0cdf8-111">3.0</span></span> |
| [<span data-ttu-id="0cdf8-112">浮動小数点の書式設定と解析の動作の変更</span><span class="sxs-lookup"><span data-stu-id="0cdf8-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="0cdf8-113">3.0</span><span class="sxs-lookup"><span data-stu-id="0cdf8-113">3.0</span></span> |
| [<span data-ttu-id="0cdf8-114">浮動小数点の解析操作が失敗したり OverflowException がスローされたりすることがなくなった</span><span class="sxs-lookup"><span data-stu-id="0cdf8-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="0cdf8-115">3.0</span><span class="sxs-lookup"><span data-stu-id="0cdf8-115">3.0</span></span> |
| [<span data-ttu-id="0cdf8-116">InvalidAsynchronousStateException を別のアセンブリに移動</span><span class="sxs-lookup"><span data-stu-id="0cdf8-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="0cdf8-117">3.0</span><span class="sxs-lookup"><span data-stu-id="0cdf8-117">3.0</span></span> |
| [<span data-ttu-id="0cdf8-118">Unicode のガイドラインに従って不適切な形式の UTF-8 バイト シーケンスを置き換える</span><span class="sxs-lookup"><span data-stu-id="0cdf8-118">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="0cdf8-119">3.0</span><span class="sxs-lookup"><span data-stu-id="0cdf8-119">3.0</span></span> |
| [<span data-ttu-id="0cdf8-120">TypeDescriptionProviderAttribute を別のアセンブリに移動</span><span class="sxs-lookup"><span data-stu-id="0cdf8-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="0cdf8-121">3.0</span><span class="sxs-lookup"><span data-stu-id="0cdf8-121">3.0</span></span> |
| [<span data-ttu-id="0cdf8-122">ZipArchiveEntry による、エントリ サイズに一貫性のないアーカイブ処理の中止</span><span class="sxs-lookup"><span data-stu-id="0cdf8-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="0cdf8-123">3.0</span><span class="sxs-lookup"><span data-stu-id="0cdf8-123">3.0</span></span> |
| [<span data-ttu-id="0cdf8-124">FieldInfo.SetValue で、静的な初期化専用フィールドに対する例外がスローされる</span><span class="sxs-lookup"><span data-stu-id="0cdf8-124">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="0cdf8-125">3.0</span><span class="sxs-lookup"><span data-stu-id="0cdf8-125">3.0</span></span> |
| [<span data-ttu-id="0cdf8-126">組み込みの構造体型に追加されたプライベート フィールド</span><span class="sxs-lookup"><span data-stu-id="0cdf8-126">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="0cdf8-127">2.1</span><span class="sxs-lookup"><span data-stu-id="0cdf8-127">2.1</span></span> |
| [<span data-ttu-id="0cdf8-128">UseShellExecute の既定値の変更</span><span class="sxs-lookup"><span data-stu-id="0cdf8-128">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="0cdf8-129">2.1</span><span class="sxs-lookup"><span data-stu-id="0cdf8-129">2.1</span></span> |
| [<span data-ttu-id="0cdf8-130">macOS 上の OpenSSL バージョン</span><span class="sxs-lookup"><span data-stu-id="0cdf8-130">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="0cdf8-131">2.1</span><span class="sxs-lookup"><span data-stu-id="0cdf8-131">2.1</span></span> |
| [<span data-ttu-id="0cdf8-132">FileSystemInfo.Attributes によってスローされる UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="0cdf8-132">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="0cdf8-133">1.0</span><span class="sxs-lookup"><span data-stu-id="0cdf8-133">1.0</span></span> |
| [<span data-ttu-id="0cdf8-134">プロセス破損状態例外の処理がサポートされない</span><span class="sxs-lookup"><span data-stu-id="0cdf8-134">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="0cdf8-135">1.0</span><span class="sxs-lookup"><span data-stu-id="0cdf8-135">1.0</span></span> |
| [<span data-ttu-id="0cdf8-136">UriBuilder のプロパティでは今後、先頭に文字が付加されない</span><span class="sxs-lookup"><span data-stu-id="0cdf8-136">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="0cdf8-137">1.0</span><span class="sxs-lookup"><span data-stu-id="0cdf8-137">1.0</span></span> |
| [<span data-ttu-id="0cdf8-138">開始されなかったプロセスについて Process.StartInfo が InvalidOperationException をスローする</span><span class="sxs-lookup"><span data-stu-id="0cdf8-138">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="0cdf8-139">1.0</span><span class="sxs-lookup"><span data-stu-id="0cdf8-139">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="0cdf8-140">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0cdf8-140">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

<span data-ttu-id="0cdf8-141">\*\*_</span><span class="sxs-lookup"><span data-stu-id="0cdf8-141">\*\*_</span></span>

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

_*_

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

_*_

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

_*_

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

_*_

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

_*_

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

_*_

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

_*_

## <a name="net-core-21"></a><span data-ttu-id="0cdf8-142">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0cdf8-142">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a><span data-ttu-id="0cdf8-143">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="0cdf8-143">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

<span data-ttu-id="0cdf8-144">_\*\*</span><span class="sxs-lookup"><span data-stu-id="0cdf8-144">_\*\*</span></span>
