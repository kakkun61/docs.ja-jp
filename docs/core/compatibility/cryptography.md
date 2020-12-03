---
title: 暗号での破壊的変更
description: .NET Core 2.1 から 3.0 での暗号に関する破壊的変更の一覧を示します。
ms.date: 04/22/2020
ms.openlocfilehash: a4801bb4d5a859e2c8c2b536ee0597cb4db2f65d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682654"
---
# <a name="cryptography-breaking-changes-for-net-core-21-30"></a><span data-ttu-id="12795-103">.NET Core 2.1 から 3.0 での暗号に関する破壊的変更</span><span class="sxs-lookup"><span data-stu-id="12795-103">Cryptography breaking changes for .NET Core 2.1-3.0</span></span>

<span data-ttu-id="12795-104">このページでは、次の破壊的変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="12795-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="12795-105">互換性に影響する変更点</span><span class="sxs-lookup"><span data-stu-id="12795-105">Breaking change</span></span> | <span data-ttu-id="12795-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="12795-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="12795-107">Linux で BEGIN TRUSTED CERTIFICATE 構文がサポートされなくなった</span><span class="sxs-lookup"><span data-stu-id="12795-107">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="12795-108">3.0</span><span class="sxs-lookup"><span data-stu-id="12795-108">3.0</span></span> |
| [<span data-ttu-id="12795-109">EnvelopedCms で AES-256 暗号化を既定で使用</span><span class="sxs-lookup"><span data-stu-id="12795-109">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="12795-110">3.0</span><span class="sxs-lookup"><span data-stu-id="12795-110">3.0</span></span> |
| [<span data-ttu-id="12795-111">RSAOpenSsl キー生成の最小サイズの増加</span><span class="sxs-lookup"><span data-stu-id="12795-111">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="12795-112">3.0</span><span class="sxs-lookup"><span data-stu-id="12795-112">3.0</span></span> |
| [<span data-ttu-id="12795-113">.NET Core 3.0 では、OpenSSL 1.0.x よりも OpenSSL 1.1.x を優先する</span><span class="sxs-lookup"><span data-stu-id="12795-113">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="12795-114">3.0</span><span class="sxs-lookup"><span data-stu-id="12795-114">3.0</span></span> |
| [<span data-ttu-id="12795-115">CryptoStream.Dispose は書き込み時にのみ最後のブロックを変換する</span><span class="sxs-lookup"><span data-stu-id="12795-115">CryptoStream.Dispose transforms final block only when writing</span></span>](#cryptostreamdispose-transforms-final-block-only-when-writing) | <span data-ttu-id="12795-116">3.0</span><span class="sxs-lookup"><span data-stu-id="12795-116">3.0</span></span> |
| [<span data-ttu-id="12795-117">SignedCms.ComputeSignature のブール型パラメーターの尊重</span><span class="sxs-lookup"><span data-stu-id="12795-117">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="12795-118">2.1</span><span class="sxs-lookup"><span data-stu-id="12795-118">2.1</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="12795-119">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="12795-119">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

<span data-ttu-id="12795-120">\*\*_</span><span class="sxs-lookup"><span data-stu-id="12795-120">\*\*_</span></span>

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

_*_

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

_*_

[!INCLUDE [CryptoStream.Dispose transforms final block only when writing](~/includes/core-changes/cryptography/3.0/cryptography-cryptostream-dispose-final-block-write.md)]

_*_

## <a name="net-core-21"></a><span data-ttu-id="12795-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="12795-121">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

<span data-ttu-id="12795-122">_\*\*</span><span class="sxs-lookup"><span data-stu-id="12795-122">_\*\*</span></span>
