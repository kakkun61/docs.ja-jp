---
title: <Directives> 要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 524c30872e218f6428491507bbfb4ca54b6061b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251101"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="9e316-102">\<Directives> 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="9e316-102">\<Directives> Element (.NET Native)</span></span>

<span data-ttu-id="9e316-103">.NET ネイティブのすべてのランタイムディレクティブファイルのルート要素。</span><span class="sxs-lookup"><span data-stu-id="9e316-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a><span data-ttu-id="9e316-104">構文</span><span class="sxs-lookup"><span data-stu-id="9e316-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="9e316-105">属性</span><span class="sxs-lookup"><span data-stu-id="9e316-105">Attributes</span></span>  
  
|<span data-ttu-id="9e316-106">属性</span><span class="sxs-lookup"><span data-stu-id="9e316-106">Attribute</span></span>|<span data-ttu-id="9e316-107">説明</span><span class="sxs-lookup"><span data-stu-id="9e316-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="9e316-108">XML 名前空間。</span><span class="sxs-lookup"><span data-stu-id="9e316-108">The XML namespace.</span></span> <span data-ttu-id="9e316-109">値は常に `http://schemas.microsoft.com/netfx/2013/01/metadata` です。</span><span class="sxs-lookup"><span data-stu-id="9e316-109">Its value is always `http://schemas.microsoft.com/netfx/2013/01/metadata`.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="9e316-110">子要素</span><span class="sxs-lookup"><span data-stu-id="9e316-110">Child elements</span></span>  
  
|<span data-ttu-id="9e316-111">要素</span><span class="sxs-lookup"><span data-stu-id="9e316-111">Element</span></span>|<span data-ttu-id="9e316-112">説明</span><span class="sxs-lookup"><span data-stu-id="9e316-112">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="9e316-113">リフレクションで使用可能なメタデータを持つアプリケーション全体の型と型のメンバーのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="9e316-113">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="9e316-114">実行時にメタデータを必要とする子型と型のメンバーを持つアセンブリを定義します。</span><span class="sxs-lookup"><span data-stu-id="9e316-114">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e316-115">解説</span><span class="sxs-lookup"><span data-stu-id="9e316-115">Remarks</span></span>  

 <span data-ttu-id="9e316-116">各ランタイム ディレクティブ ファイルには、`<Directives>` 要素を 1 つのみ含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9e316-116">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="9e316-117">要素には、 `<Directives>` 0 個または1個の要素と、0個以上の要素を含めることができ [\<Application>](application-element-net-native.md) [\<Library>](library-element-net-native.md) ます。</span><span class="sxs-lookup"><span data-stu-id="9e316-117">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e316-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e316-118">See also</span></span>

- [<span data-ttu-id="9e316-119">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="9e316-119">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="9e316-120">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="9e316-120">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
