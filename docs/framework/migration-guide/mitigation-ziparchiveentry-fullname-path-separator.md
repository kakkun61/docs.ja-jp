---
title: 軽減策:ZipArchiveEntry.FullName パスの区切り文字
description: .NET Framework 4.6.1 を対象とするアプリ以降、ZipArchiveEntry.FullName プロパティのパス区切り文字がどのように変更されたかについて説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 6e2c0908098f8487f7d429274fe7ad797bedfda1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283446"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="e2db9-103">軽減策:ZipArchiveEntry.FullName パスの区切り文字</span><span class="sxs-lookup"><span data-stu-id="e2db9-103">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>

<span data-ttu-id="e2db9-104">.NET Framework 4.6.1 を対象とするアプリから、<xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> プロパティで使用されるパスの区切り文字は、以前のバージョンの .NET Framework で使用されていた円記号 ("\\") からスラッシュ ("/") に変更されています。</span><span class="sxs-lookup"><span data-stu-id="e2db9-104">Starting with apps that target the .NET Framework 4.6.1, the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of .NET Framework to a forward slash ("/").</span></span> <span data-ttu-id="e2db9-105"><xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> メソッドのオーバーロードのいずれかを呼び出すことで、<xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e2db9-105"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="e2db9-106">影響</span><span class="sxs-lookup"><span data-stu-id="e2db9-106">Impact</span></span>  

 <span data-ttu-id="e2db9-107">この変更によって、.NET の実装が [.ZIP ファイル形式の仕様](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT)のセクション 4.4.17.1 に準拠するようになったほか、Windows 以外のシステムで ZIP アーカイブを圧縮解除できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e2db9-107">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="e2db9-108">MacOS などの Windows 以外のオペレーティング システムで以前のバージョンの .NET Framework を対象とするアプリで作成された zip ファイルを圧縮解除すると、ディレクトリ構造を保持できません。</span><span class="sxs-lookup"><span data-stu-id="e2db9-108">Decompressing a zip file created by an app that targets a previous version of .NET Framework on non-Windows operating systems such as MacOS fails to preserve the directory structure.</span></span> <span data-ttu-id="e2db9-109">たとえば、MacOS で、ディレクトリ パス、円記号 ("\\")、ファイル名が連結された名前を持つ一連のファイルを作成するとします。</span><span class="sxs-lookup"><span data-stu-id="e2db9-109">For example, on MacOS, it creates a set of files whose file name concatenates the directory path, any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="e2db9-110">その場合、圧縮解除されたファイルのディレクトリ構造は保持されません。</span><span class="sxs-lookup"><span data-stu-id="e2db9-110">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="e2db9-111">.NET Framework <xref:System.IO> 名前空間の API によって、Windows オペレーティング システムで展開される .zip ファイルでは、この変更の影響は最小限になるはずです。これらの API では、スラッシュ ("/") または円記号 ("\\") をパスの区切り文字としてシームレスに処理できるためです。</span><span class="sxs-lookup"><span data-stu-id="e2db9-111">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="e2db9-112">軽減策</span><span class="sxs-lookup"><span data-stu-id="e2db9-112">Mitigation</span></span>  

 <span data-ttu-id="e2db9-113">この動作が望ましくない場合は、アプリケーション構成ファイルの [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) セクションに構成設定を追加して、無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e2db9-113">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="e2db9-114">以下は、`<runtime>` セクションと無効への切り替えの両方を示しています。</span><span class="sxs-lookup"><span data-stu-id="e2db9-114">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="e2db9-115">また、以前のバージョンの .NET Framework を対象とするものの、.NET Framework 4.6.1 以降のバージョンで実行されているアプリでは、アプリケーション構成ファイルの [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) セクションに構成設定を追加して、この動作を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e2db9-115">In addition, apps that target previous versions of .NET Framework but are running on .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="e2db9-116">以下は、`<runtime>` セクションと有効への切り替えの両方を示しています。</span><span class="sxs-lookup"><span data-stu-id="e2db9-116">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2db9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2db9-117">See also</span></span>

- [<span data-ttu-id="e2db9-118">アプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="e2db9-118">Application compatibility</span></span>](application-compatibility.md)
