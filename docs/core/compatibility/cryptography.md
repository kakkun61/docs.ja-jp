---
title: 暗号に関する破壊的変更 - .NET Core
description: .NET Core での暗号に関連する破壊的変更の一覧を示します。
ms.date: 09/20/2019
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80b62f9b32487e88a309ea7686f78d68af8f2e0a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216985"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="82559-103">暗号での破壊的変更</span><span class="sxs-lookup"><span data-stu-id="82559-103">Cryptography breaking changes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="82559-104">この記事は作成中です。</span><span class="sxs-lookup"><span data-stu-id="82559-104">This article is under construction.</span></span> <span data-ttu-id="82559-105">これは、.NET Core の破壊的変更の完全なリストではありません。</span><span class="sxs-lookup"><span data-stu-id="82559-105">This is not a complete list of .NET Core breaking changes.</span></span> <span data-ttu-id="82559-106">.NET Core の破壊的変更の詳細については、GitHub の dotnet/docs リポジトリで個別の[破壊的変更の問題](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change)について調べてください。</span><span class="sxs-lookup"><span data-stu-id="82559-106">For more information on .NET Core breaking changes, you can examine individual [breaking changes issues](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) in the dotnet/docs repository on GitHub.</span></span> 

<span data-ttu-id="82559-107">.NET Core のバージョンごとに暗号に関する破壊的変更の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="82559-107">The following is a list of cryptography-related breaking changes by .NET Core version.</span></span>

## <a name="net-core-30-preview-9"></a><span data-ttu-id="82559-108">.NET Core 3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="82559-108">.NET Core 3.0 Preview 9</span></span>

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

## <a name="net-core-30"></a><span data-ttu-id="82559-109">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="82559-109">.NET Core 3.0</span></span>

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/net-core-3-0-prefers-openssl-1-1-x.md)]