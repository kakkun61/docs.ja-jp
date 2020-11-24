---
title: EmbedResource メソッド
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
ms.openlocfilehash: 34439b7c01dee7d7789d989b58e8944c6282b71b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676388"
---
# <a name="embedresource-method"></a><span data-ttu-id="bc29a-102">EmbedResource メソッド</span><span class="sxs-lookup"><span data-stu-id="bc29a-102">EmbedResource Method</span></span>

<span data-ttu-id="bc29a-103">埋め込みリソースを宣言します。</span><span class="sxs-lookup"><span data-stu-id="bc29a-103">Declares an embedded resource.</span></span> <span data-ttu-id="bc29a-104">このメソッドは、実際にはリソースを埋め込みません。</span><span class="sxs-lookup"><span data-stu-id="bc29a-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc29a-105">構文</span><span class="sxs-lookup"><span data-stu-id="bc29a-105">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc29a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bc29a-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="bc29a-107">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="bc29a-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="bc29a-108">リソースが含まれているファイルのファイルトークンまたはアセンブリ ID。</span><span class="sxs-lookup"><span data-stu-id="bc29a-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="bc29a-109">リソースの名前。</span><span class="sxs-lookup"><span data-stu-id="bc29a-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="bc29a-110">RVA からのリソースのオフセット。</span><span class="sxs-lookup"><span data-stu-id="bc29a-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="bc29a-111">やなどのアクセシビリティ `mrPublic` フラグ `mrPrivate` 。</span><span class="sxs-lookup"><span data-stu-id="bc29a-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="bc29a-112">これらのフラグは、を使用して、この [メソッド](../metadata/imetadataassemblyemit-defineexportedtype-method.md)に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="bc29a-112">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc29a-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="bc29a-113">Return Value</span></span>  

 <span data-ttu-id="bc29a-114">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="bc29a-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc29a-115">要件</span><span class="sxs-lookup"><span data-stu-id="bc29a-115">Requirements</span></span>  

 <span data-ttu-id="bc29a-116">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="bc29a-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc29a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc29a-117">See also</span></span>

- [<span data-ttu-id="bc29a-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bc29a-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="bc29a-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bc29a-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="bc29a-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="bc29a-120">ALink API</span></span>](index.md)
