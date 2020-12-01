---
title: '軽減策: パスのコロン チェック'
description: 適切なドライブ区切り構文 (コロン) のチェックをサポートする目的で .NET Framework 4.6.2 で行われた変更について説明します。
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: 03f1c7249549aae7e3bef986c97fb5f320fbeb2f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283459"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="da01c-103">軽減策:パスのコロン チェック</span><span class="sxs-lookup"><span data-stu-id="da01c-103">Mitigation: Path Colon Checks</span></span>

<span data-ttu-id="da01c-104">.NET Framework 4.6.2 以降を対象とするアプリから、以前はサポートされていなかったパスをサポートするために (長さと形式の両方について) 数多くの変更が加えられました。</span><span class="sxs-lookup"><span data-stu-id="da01c-104">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="da01c-105">具体的には、適切なドライブの区切り構文 (コロン) のチェックがより正しく行われるようになりました。</span><span class="sxs-lookup"><span data-stu-id="da01c-105">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="da01c-106">影響</span><span class="sxs-lookup"><span data-stu-id="da01c-106">Impact</span></span>  

 <span data-ttu-id="da01c-107">これらの変更は、以前は <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> メソッドと <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> メソッドでサポートされていた一部の URI のパスをブロックします。</span><span class="sxs-lookup"><span data-stu-id="da01c-107">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="da01c-108">軽減策</span><span class="sxs-lookup"><span data-stu-id="da01c-108">Mitigation</span></span>  

 <span data-ttu-id="da01c-109"><xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> メソッドや <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> メソッドでサポートされなくなった、以前は受け入れられていたパスの問題を回避するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="da01c-109">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="da01c-110">URL からスキームを手動で削除します。</span><span class="sxs-lookup"><span data-stu-id="da01c-110">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="da01c-111">たとえば、URL から `file://` を削除します。</span><span class="sxs-lookup"><span data-stu-id="da01c-111">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="da01c-112"><xref:System.Uri> コンストラクターに URI を渡し、<xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> プロパティの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="da01c-112">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="da01c-113">`Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> を `true` に切り替えて、新しいパスの正規化を無効にします。</span><span class="sxs-lookup"><span data-stu-id="da01c-113">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="da01c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="da01c-114">See also</span></span>

- [<span data-ttu-id="da01c-115">アプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="da01c-115">Application compatibility</span></span>](application-compatibility.md)
