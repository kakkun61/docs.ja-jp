---
title: 共有 Web ホストの最適化
ms.date: 03/30/2017
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: abab4ac451a70fbc81ac6d7c9da6f8d0123287a8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669030"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="7877c-102">共有 Web ホストの最適化</span><span class="sxs-lookup"><span data-stu-id="7877c-102">Optimization for Shared Web Hosting</span></span>

<span data-ttu-id="7877c-103">複数の小規模な Web サイトをホストして共有されているサーバーの管理者は、.NET ディレクトリの Aspnet.config ファイルの `runtime` ノードに次の `gcTrimCommitOnLowMemory` 設定を追加することで、パフォーマンスを最適化し、サイトの容量を増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="7877c-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> <span data-ttu-id="7877c-104">この設定は、共有 Web ホスティング シナリオの場合にのみお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7877c-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="7877c-105">ガベージ コレクターは将来の割り当てのためにメモリを保持するので、コミットされる領域は厳密に必要な領域を超える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7877c-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="7877c-106">この領域を減らすと、システム メモリにかかる負荷が高くなる時間に対応できます。</span><span class="sxs-lookup"><span data-stu-id="7877c-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="7877c-107">このコミットされる領域を減らすと、パフォーマンスが向上し、より多くのサイトをホストできるようになります。</span><span class="sxs-lookup"><span data-stu-id="7877c-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="7877c-108">`gcTrimCommitOnLowMemory` 設定が有効な場合、ガベージ コレクターはシステムのメモリ負荷を評価し、負荷が 90% に達するとトリミング モードに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="7877c-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="7877c-109">負荷が 85% 未満になるまでトリミング モードは維持されます。</span><span class="sxs-lookup"><span data-stu-id="7877c-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="7877c-110">条件を満たしている場合、`gcTrimCommitOnLowMemory` 設定で現在のアプリケーションを助けずに無視することをガベージ コレクターで決定することができます。</span><span class="sxs-lookup"><span data-stu-id="7877c-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7877c-111">例</span><span class="sxs-lookup"><span data-stu-id="7877c-111">Example</span></span>  

 <span data-ttu-id="7877c-112">次の XML フラグメントは、`gcTrimCommitOnLowMemory` 設定を有効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7877c-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="7877c-113">省略記号は、`runtime` ノード内のその他の設定を示します。</span><span class="sxs-lookup"><span data-stu-id="7877c-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7877c-114">参照</span><span class="sxs-lookup"><span data-stu-id="7877c-114">See also</span></span>

- [<span data-ttu-id="7877c-115">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="7877c-115">Garbage Collection</span></span>](index.md)
