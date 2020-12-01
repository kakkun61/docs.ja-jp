---
title: 軽減策:X509CertificateClaimSet.FindClaims メソッド
description: .NET Framework 4.6.1 を対象とするアプリで X509CertificateClaimSet.FindClaims メソッドがどのように変更されたかについて説明します。
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: ed9e345f9e48156f37f493caa78e6b3901cecf23
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253571"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="3b452-103">軽減策:X509CertificateClaimSet.FindClaims メソッド</span><span class="sxs-lookup"><span data-stu-id="3b452-103">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>

<span data-ttu-id="3b452-104">.NET Framework 4.6.1 以降を対象とするアプリの <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> メソッドでは、`claimType` 引数と SAN フィールド内のすべての DNS エントリの照合が試みられます。</span><span class="sxs-lookup"><span data-stu-id="3b452-104">Starting with apps that target .NET Framework 4.6.1, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="3b452-105">影響</span><span class="sxs-lookup"><span data-stu-id="3b452-105">Impact</span></span>  

 <span data-ttu-id="3b452-106">この変更によって影響を受けるのは、.NET Framework 4.6.1 以降のバージョンの .NET Framework を対象とするアプリのみです。</span><span class="sxs-lookup"><span data-stu-id="3b452-106">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="3b452-107">.NET Framework の以前のバージョンを対象とするアプリの場合、<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> メソッドは、`claimType` 引数と最後の DNS エントリのみの照合を試みます。</span><span class="sxs-lookup"><span data-stu-id="3b452-107">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="3b452-108">軽減策</span><span class="sxs-lookup"><span data-stu-id="3b452-108">Mitigation</span></span>  

 <span data-ttu-id="3b452-109">この変更が望ましくない場合は、.NET Framework 4.6.1 バージョン以降の .NET Framework を対象とするアプリで無効にできます。これは、そのアプリの構成ファイルの [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) セクションに次の構成設定を追加して行います。</span><span class="sxs-lookup"><span data-stu-id="3b452-109">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 <span data-ttu-id="3b452-110">また、以前のバージョンの .NET Framework を対象とするものの、.NET Framework 4.6.1 以降のバージョンで実行されているアプリでは、そのアプリの構成ファイルの [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) セクションに構成設定を追加して、この動作を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3b452-110">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b452-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b452-111">See also</span></span>

- [<span data-ttu-id="3b452-112">アプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="3b452-112">Application compatibility</span></span>](application-compatibility.md)
