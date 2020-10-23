---
title: 暗号での破壊的変更
description: .NET Core で暗号化に関連する破壊的変更の一覧を示します。
ms.date: 04/22/2020
ms.openlocfilehash: 6f37e5caacadc276562e63a728162c6b26f2e435
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159555"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="aa2e8-103">暗号での破壊的変更</span><span class="sxs-lookup"><span data-stu-id="aa2e8-103">Cryptography breaking changes</span></span>

<span data-ttu-id="aa2e8-104">このページでは、次の破壊的変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="aa2e8-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="aa2e8-105">互換性に影響する変更点</span><span class="sxs-lookup"><span data-stu-id="aa2e8-105">Breaking change</span></span> | <span data-ttu-id="aa2e8-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="aa2e8-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="aa2e8-107">暗号抽象化の既定の実装のインスタンス化はサポートされていない</span><span class="sxs-lookup"><span data-stu-id="aa2e8-107">Instantiating default implementations of cryptographic abstractions is not supported</span></span>](#instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported) | <span data-ttu-id="aa2e8-108">5.0</span><span class="sxs-lookup"><span data-stu-id="aa2e8-108">5.0</span></span> |
| [<span data-ttu-id="aa2e8-109">Linux 上の .NET 用の既定の TLS 暗号スイート</span><span class="sxs-lookup"><span data-stu-id="aa2e8-109">Default TLS cipher suites for .NET on Linux</span></span>](#default-tls-cipher-suites-for-net-on-linux) | <span data-ttu-id="aa2e8-110">5.0</span><span class="sxs-lookup"><span data-stu-id="aa2e8-110">5.0</span></span> |
| [<span data-ttu-id="aa2e8-111">Blazor WebAssembly で System.Security.Cryptography API がサポートされない</span><span class="sxs-lookup"><span data-stu-id="aa2e8-111">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly) | <span data-ttu-id="aa2e8-112">5.0</span><span class="sxs-lookup"><span data-stu-id="aa2e8-112">5.0</span></span> |
| [<span data-ttu-id="aa2e8-113">System.Security.Cryptography.Oid は機能的に初期化専用</span><span class="sxs-lookup"><span data-stu-id="aa2e8-113">System.Security.Cryptography.Oid is functionally init-only</span></span>](#systemsecuritycryptographyoid-is-functionally-init-only) | <span data-ttu-id="aa2e8-114">5.0</span><span class="sxs-lookup"><span data-stu-id="aa2e8-114">5.0</span></span> |
| [<span data-ttu-id="aa2e8-115">Linux で BEGIN TRUSTED CERTIFICATE 構文がサポートされなくなった</span><span class="sxs-lookup"><span data-stu-id="aa2e8-115">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="aa2e8-116">3.0</span><span class="sxs-lookup"><span data-stu-id="aa2e8-116">3.0</span></span> |
| [<span data-ttu-id="aa2e8-117">EnvelopedCms で AES-256 暗号化を既定で使用</span><span class="sxs-lookup"><span data-stu-id="aa2e8-117">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="aa2e8-118">3.0</span><span class="sxs-lookup"><span data-stu-id="aa2e8-118">3.0</span></span> |
| [<span data-ttu-id="aa2e8-119">RSAOpenSsl キー生成の最小サイズの増加</span><span class="sxs-lookup"><span data-stu-id="aa2e8-119">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="aa2e8-120">3.0</span><span class="sxs-lookup"><span data-stu-id="aa2e8-120">3.0</span></span> |
| [<span data-ttu-id="aa2e8-121">.NET Core 3.0 では、OpenSSL 1.0.x よりも OpenSSL 1.1.x を優先する</span><span class="sxs-lookup"><span data-stu-id="aa2e8-121">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="aa2e8-122">3.0</span><span class="sxs-lookup"><span data-stu-id="aa2e8-122">3.0</span></span> |
| [<span data-ttu-id="aa2e8-123">CryptoStream.Dispose は書き込み時にのみ最後のブロックを変換する</span><span class="sxs-lookup"><span data-stu-id="aa2e8-123">CryptoStream.Dispose transforms final block only when writing</span></span>](#cryptostreamdispose-transforms-final-block-only-when-writing) | <span data-ttu-id="aa2e8-124">3.0</span><span class="sxs-lookup"><span data-stu-id="aa2e8-124">3.0</span></span> |
| [<span data-ttu-id="aa2e8-125">SignedCms.ComputeSignature のブール型パラメーターの尊重</span><span class="sxs-lookup"><span data-stu-id="aa2e8-125">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="aa2e8-126">2.1</span><span class="sxs-lookup"><span data-stu-id="aa2e8-126">2.1</span></span> |

## <a name="net-50"></a><span data-ttu-id="aa2e8-127">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="aa2e8-127">.NET 5.0</span></span>

[!INCLUDE [instantiating-default-implementations-of-cryptographic-abstractions-not-supported](../../../includes/core-changes/cryptography/5.0/instantiating-default-implementations-of-cryptographic-abstractions-not-supported.md)]

***

[!INCLUDE [default-cipher-suites-for-tls-on-linux](../../../includes/core-changes/cryptography/5.0/default-cipher-suites-for-tls-on-linux.md)]

***

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

***

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="aa2e8-128">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="aa2e8-128">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

[!INCLUDE [CryptoStream.Dispose transforms final block only when writing](~/includes/core-changes/cryptography/3.0/cryptography-cryptostream-dispose-final-block-write.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="aa2e8-129">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="aa2e8-129">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
