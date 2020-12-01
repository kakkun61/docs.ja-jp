---
title: 軽減策:Icon オブジェクトの PNG フレーム
description: .NET Framework 4.6 以降の新しい動作が望ましくない場合、アイコン オブジェクトの PNG フレームの動作を構成する方法について説明します。
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: a8bb4fca19a09f16c89ce8c5da08ebcae9a037ec
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276582"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="c1dd1-103">軽減策:Icon オブジェクトの PNG フレーム</span><span class="sxs-lookup"><span data-stu-id="c1dd1-103">Mitigation: PNG Frames in Icon Objects</span></span>

<span data-ttu-id="c1dd1-104">.NET Framework 4.6 以降では、 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> メソッドで、PNG フレームを含んだアイコンを正常に <xref:System.Drawing.Bitmap> オブジェクトに変換できます。</span><span class="sxs-lookup"><span data-stu-id="c1dd1-104">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="c1dd1-105">.NET Framework 4.5.2 以前のバージョンを対象としたアプリでは、 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> オブジェクトに PNG フレームが含まれていると、 <xref:System.ArgumentOutOfRangeException> メソッドが <xref:System.Drawing.Icon> の例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="c1dd1-105">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="c1dd1-106">影響</span><span class="sxs-lookup"><span data-stu-id="c1dd1-106">Impact</span></span>  

 <span data-ttu-id="c1dd1-107">この変更は、.NET Framework 4.6 を対象として再コンパイルされたアプリのうち、 <xref:System.ArgumentOutOfRangeException> オブジェクトに PNG フレームが含まれている場合は <xref:System.Drawing.Icon> をスローするように特別な処理が実装されているアプリに影響します。</span><span class="sxs-lookup"><span data-stu-id="c1dd1-107">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="c1dd1-108">.NET Framework 4.6 で実行している場合は、正常に変換が行われ、 <xref:System.ArgumentOutOfRangeException> がスローされることはないため、例外ハンドラーは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="c1dd1-108">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="c1dd1-109">軽減策</span><span class="sxs-lookup"><span data-stu-id="c1dd1-109">Mitigation</span></span>  

 <span data-ttu-id="c1dd1-110">この動作に不都合がある場合は、次に示す要素を app.config ファイルの [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) セクションに追加することで、以前の動作を維持できます。</span><span class="sxs-lookup"><span data-stu-id="c1dd1-110">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="c1dd1-111">app.config ファイルに既に `AppContextSwitchOverrides` 要素が含まれている場合は、次に示すように新しい値を `value` 属性にマージする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1dd1-111">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a><span data-ttu-id="c1dd1-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1dd1-112">See also</span></span>

- [<span data-ttu-id="c1dd1-113">アプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="c1dd1-113">Application compatibility</span></span>](application-compatibility.md)
