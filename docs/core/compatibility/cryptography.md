---
title: 暗号での破壊的変更
description: .NET Core で暗号化に関連する破壊的変更の一覧を示します。
ms.date: 04/22/2020
ms.openlocfilehash: b755876624a7709cfe08b5993655e78be9f8e1f2
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888614"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="bbba2-103">暗号での破壊的変更</span><span class="sxs-lookup"><span data-stu-id="bbba2-103">Cryptography breaking changes</span></span>

<span data-ttu-id="bbba2-104">このページでは、次の破壊的変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="bbba2-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="bbba2-105">互換性に影響する変更点</span><span class="sxs-lookup"><span data-stu-id="bbba2-105">Breaking change</span></span> | <span data-ttu-id="bbba2-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="bbba2-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="bbba2-107">TripleDES.Create で作成されるインスタンスの既定の FeedbackSize 値の変更</span><span class="sxs-lookup"><span data-stu-id="bbba2-107">Default FeedbackSize value for instances created by TripleDES.Create changed</span></span>](#default-feedbacksize-value-for-instances-created-by-tripledescreate-changed) | <span data-ttu-id="bbba2-108">5.0</span><span class="sxs-lookup"><span data-stu-id="bbba2-108">5.0</span></span> |
| [<span data-ttu-id="bbba2-109">暗号抽象化の既定の実装のインスタンス化はサポートされていない</span><span class="sxs-lookup"><span data-stu-id="bbba2-109">Instantiating default implementations of cryptographic abstractions is not supported</span></span>](#instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported) | <span data-ttu-id="bbba2-110">5.0</span><span class="sxs-lookup"><span data-stu-id="bbba2-110">5.0</span></span> |
| [<span data-ttu-id="bbba2-111">Linux 上の .NET 用の既定の TLS 暗号スイート</span><span class="sxs-lookup"><span data-stu-id="bbba2-111">Default TLS cipher suites for .NET on Linux</span></span>](#default-tls-cipher-suites-for-net-on-linux) | <span data-ttu-id="bbba2-112">5.0</span><span class="sxs-lookup"><span data-stu-id="bbba2-112">5.0</span></span> |
| [<span data-ttu-id="bbba2-113">Blazor WebAssembly で System.Security.Cryptography API がサポートされない</span><span class="sxs-lookup"><span data-stu-id="bbba2-113">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly) | <span data-ttu-id="bbba2-114">5.0</span><span class="sxs-lookup"><span data-stu-id="bbba2-114">5.0</span></span> |
| [<span data-ttu-id="bbba2-115">System.Security.Cryptography.Oid は機能的に初期化専用</span><span class="sxs-lookup"><span data-stu-id="bbba2-115">System.Security.Cryptography.Oid is functionally init-only</span></span>](#systemsecuritycryptographyoid-is-functionally-init-only) | <span data-ttu-id="bbba2-116">5.0</span><span class="sxs-lookup"><span data-stu-id="bbba2-116">5.0</span></span> |
| [<span data-ttu-id="bbba2-117">Linux で BEGIN TRUSTED CERTIFICATE 構文がサポートされなくなった</span><span class="sxs-lookup"><span data-stu-id="bbba2-117">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="bbba2-118">3.0</span><span class="sxs-lookup"><span data-stu-id="bbba2-118">3.0</span></span> |
| [<span data-ttu-id="bbba2-119">EnvelopedCms で AES-256 暗号化を既定で使用</span><span class="sxs-lookup"><span data-stu-id="bbba2-119">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="bbba2-120">3.0</span><span class="sxs-lookup"><span data-stu-id="bbba2-120">3.0</span></span> |
| [<span data-ttu-id="bbba2-121">RSAOpenSsl キー生成の最小サイズの増加</span><span class="sxs-lookup"><span data-stu-id="bbba2-121">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="bbba2-122">3.0</span><span class="sxs-lookup"><span data-stu-id="bbba2-122">3.0</span></span> |
| [<span data-ttu-id="bbba2-123">.NET Core 3.0 では、OpenSSL 1.0.x よりも OpenSSL 1.1.x を優先する</span><span class="sxs-lookup"><span data-stu-id="bbba2-123">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="bbba2-124">3.0</span><span class="sxs-lookup"><span data-stu-id="bbba2-124">3.0</span></span> |
| [<span data-ttu-id="bbba2-125">CryptoStream.Dispose は書き込み時にのみ最後のブロックを変換する</span><span class="sxs-lookup"><span data-stu-id="bbba2-125">CryptoStream.Dispose transforms final block only when writing</span></span>](#cryptostreamdispose-transforms-final-block-only-when-writing) | <span data-ttu-id="bbba2-126">3.0</span><span class="sxs-lookup"><span data-stu-id="bbba2-126">3.0</span></span> |
| [<span data-ttu-id="bbba2-127">SignedCms.ComputeSignature のブール型パラメーターの尊重</span><span class="sxs-lookup"><span data-stu-id="bbba2-127">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="bbba2-128">2.1</span><span class="sxs-lookup"><span data-stu-id="bbba2-128">2.1</span></span> |

## <a name="net-50"></a><span data-ttu-id="bbba2-129">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="bbba2-129">.NET 5.0</span></span>

[!INCLUDE [tripledes-default-feedback-size-change](../../../includes/core-changes/cryptography/5.0/tripledes-default-feedback-size-change.md)]

***

[!INCLUDE [instantiating-default-implementations-of-cryptographic-abstractions-not-supported](../../../includes/core-changes/cryptography/5.0/instantiating-default-implementations-of-cryptographic-abstractions-not-supported.md)]

<span data-ttu-id="bbba2-130">\*\*_</span><span class="sxs-lookup"><span data-stu-id="bbba2-130">\*\*_</span></span>

[!INCLUDE [default-cipher-suites-for-tls-on-linux](../../../includes/core-changes/cryptography/5.0/default-cipher-suites-for-tls-on-linux.md)]

_*_

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

_*_

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

_*_

## <a name="net-core-30"></a><span data-ttu-id="bbba2-131">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="bbba2-131">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

_*_

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

_*_

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

_*_

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

_*_

[!INCLUDE [CryptoStream.Dispose transforms final block only when writing](~/includes/core-changes/cryptography/3.0/cryptography-cryptostream-dispose-final-block-write.md)]

_*_

## <a name="net-core-21"></a><span data-ttu-id="bbba2-132">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bbba2-132">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

<span data-ttu-id="bbba2-133">_\*\*</span><span class="sxs-lookup"><span data-stu-id="bbba2-133">_\*\*</span></span>
