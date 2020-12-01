---
ms.openlocfilehash: a4476fbff572c004632153e5a98812c241efca57
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032129"
---
### <a name="openssl-versions-on-macos"></a><span data-ttu-id="73d2b-101">macOS 上の OpenSSL バージョン</span><span class="sxs-lookup"><span data-stu-id="73d2b-101">OpenSSL versions on macOS</span></span>

<span data-ttu-id="73d2b-102">macOS 上の .NET Core 3.0 以降のランタイムでは <xref:System.Security.Cryptography.AesCcm>、<xref:System.Security.Cryptography.AesGcm>、<xref:System.Security.Cryptography.DSAOpenSsl>、<xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>、<xref:System.Security.Cryptography.ECDsaOpenSsl>、<xref:System.Security.Cryptography.RSAOpenSsl>、<xref:System.Security.Cryptography.SafeEvpPKeyHandle> の各型に対して OpenSSL 1.0.x バージョンよりも OpenSSL 1.1.x バージョンが優先されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="73d2b-102">The .NET Core 3.0 and later runtimes on macOS now prefer OpenSSL 1.1.x versions to OpenSSL 1.0.x versions for the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, and <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

<span data-ttu-id="73d2b-103">.NET Core 2.1 ランタイムでは、OpenSSL 1.1.x バージョンがサポートされるようになりましたが、OpenSSL 1.0.x バージョンが引き続き優先されます。</span><span class="sxs-lookup"><span data-stu-id="73d2b-103">The .NET Core 2.1 runtime now supports OpenSSL 1.1.x versions, but still prefers OpenSSL 1.0.x versions.</span></span>

#### <a name="change-description"></a><span data-ttu-id="73d2b-104">変更の説明</span><span class="sxs-lookup"><span data-stu-id="73d2b-104">Change description</span></span>

<span data-ttu-id="73d2b-105">以前、.NET Core ランタイムでは、macOS 上の OpenSSL 1.0.x バージョンは OpenSSL とやりとりする型に対して使用されていました。</span><span class="sxs-lookup"><span data-stu-id="73d2b-105">Previously, the .NET Core runtime used OpenSSL 1.0.x versions on macOS for types that interact with OpenSSL.</span></span> <span data-ttu-id="73d2b-106">最新の OpenSSL 1.0.x バージョンである OpenSSL 1.0.2 は現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="73d2b-106">The most recent OpenSSL 1.0.x version, OpenSSL 1.0.2, is now out of support.</span></span> <span data-ttu-id="73d2b-107">サポートされているバージョンの OpenSSL 上で OpenSSL を使用する型を維持するために、.NET Core 3.0 以降のランタイムでは macOS 上でより新しいバージョンの OpenSSL が使用されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="73d2b-107">To keep types that use OpenSSL on supported versions of OpenSSL, the .NET Core 3.0 and later runtimes now use newer versions of OpenSSL on macOS.</span></span>

<span data-ttu-id="73d2b-108">この変更により、macOS 上での .NET Core ランタイムの動作は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="73d2b-108">With this change, the behavior for the .NET Core runtimes on macOS is as follows:</span></span>

- <span data-ttu-id="73d2b-109">.NET Core 3.0 以降のバージョンのランタイムでは、使用可能な場合は OpenSSL 1.1.x が使用され、使用可能な 1.1.x バージョンがない場合にのみ OpenSSL 1.0.x にフォールバックします。</span><span class="sxs-lookup"><span data-stu-id="73d2b-109">The .NET Core 3.0 and later version runtimes use OpenSSL 1.1.x, if available, and fall back to OpenSSL 1.0.x only if there's no 1.1.x version available.</span></span>

  <span data-ttu-id="73d2b-110">カスタムの P/Invoke で OpenSSL 相互運用機能型を使用する呼び出し元については、<xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> の注釈にあるガイダンスに従ってください。</span><span class="sxs-lookup"><span data-stu-id="73d2b-110">For callers that use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span> <span data-ttu-id="73d2b-111"><xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> 値を確認しないと、ご利用のアプリがクラッシュする場合があります。</span><span class="sxs-lookup"><span data-stu-id="73d2b-111">Your app may crash if you don't check the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> value.</span></span>

- <span data-ttu-id="73d2b-112">.NET Core 2.1 以降のバージョンのランタイムでは、使用可能な場合は OpenSSL 1.0.x が使用され、使用可能な 1.0.x バージョンがない場合にのみ OpenSSL 1.1.x にフォールバックします。</span><span class="sxs-lookup"><span data-stu-id="73d2b-112">The .NET Core 2.1 runtime uses OpenSSL 1.0.x, if available, and falls back to OpenSSL 1.1.x if there's no 1.0.x version available.</span></span>

  <span data-ttu-id="73d2b-113">.NET Core 2.1 には <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> プロパティが存在しないため 2.1 ランタイムでは、以前のバージョンの OpenSSL が優先されます。結果として、実行時に OpenSSL のバージョンを確実に判断することができません。</span><span class="sxs-lookup"><span data-stu-id="73d2b-113">The 2.1 runtime prefers the earlier version of OpenSSL because the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property does not exist in .NET Core 2.1, so the OpenSSL version cannot be reliably determined at run time.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="73d2b-114">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="73d2b-114">Version introduced</span></span>

- <span data-ttu-id="73d2b-115">.NET Core 2.1.16</span><span class="sxs-lookup"><span data-stu-id="73d2b-115">.NET Core 2.1.16</span></span>
- <span data-ttu-id="73d2b-116">.NET Core 3.0.3</span><span class="sxs-lookup"><span data-stu-id="73d2b-116">.NET Core 3.0.3</span></span>
- <span data-ttu-id="73d2b-117">.NET Core 3.1.2</span><span class="sxs-lookup"><span data-stu-id="73d2b-117">.NET Core 3.1.2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="73d2b-118">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="73d2b-118">Recommended action</span></span>

- <span data-ttu-id="73d2b-119">OpenSSL バージョン 1.0.2 が不要になった場合はアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="73d2b-119">Uninstall OpenSSL version 1.0.2 if it's no longer needed.</span></span>

- <span data-ttu-id="73d2b-120"><xref:System.Security.Cryptography.AesCcm>、<xref:System.Security.Cryptography.AesGcm>、<xref:System.Security.Cryptography.DSAOpenSsl>、<xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>、<xref:System.Security.Cryptography.ECDsaOpenSsl>、<xref:System.Security.Cryptography.RSAOpenSsl>、または <xref:System.Security.Cryptography.SafeEvpPKeyHandle> の型を使用する場合は、OpenSSL 1.1.x をインストールします。</span><span class="sxs-lookup"><span data-stu-id="73d2b-120">Install OpenSSL 1.1.x if you use the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, or <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

- <span data-ttu-id="73d2b-121">カスタムの P/Invoke で OpenSSL 相互運用機能型を使用する場合は、<xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> の注釈にあるガイダンスに従ってください。</span><span class="sxs-lookup"><span data-stu-id="73d2b-121">If you use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span>

#### <a name="category"></a><span data-ttu-id="73d2b-122">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="73d2b-122">Category</span></span>

<span data-ttu-id="73d2b-123">Core .NET ライブラリ</span><span class="sxs-lookup"><span data-stu-id="73d2b-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="73d2b-124">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="73d2b-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
