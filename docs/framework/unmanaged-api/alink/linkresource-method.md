---
title: LinkResource メソッド
ms.date: 03/30/2017
api_name:
- IALink.LinkResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- LinkResource
helpviewer_keywords:
- LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type:
- apiref
ms.openlocfilehash: 4f2f13976dfd4e5601bf8b54bed7b851884fbb9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690448"
---
# <a name="linkresource-method"></a><span data-ttu-id="c9cff-102">LinkResource メソッド</span><span class="sxs-lookup"><span data-stu-id="c9cff-102">LinkResource Method</span></span>

<span data-ttu-id="c9cff-103">リソース内のリンク。</span><span class="sxs-lookup"><span data-stu-id="c9cff-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9cff-104">構文</span><span class="sxs-lookup"><span data-stu-id="c9cff-104">Syntax</span></span>  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9cff-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c9cff-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="c9cff-106">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="c9cff-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="c9cff-107">ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="c9cff-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="c9cff-108">省略可能な新しいファイル名。</span><span class="sxs-lookup"><span data-stu-id="c9cff-108">Optional new file name.</span></span> <span data-ttu-id="c9cff-109">NULL 以外の場合は、 `pszFileName` pszNewLocation にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="c9cff-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="c9cff-110">リソースの名前。</span><span class="sxs-lookup"><span data-stu-id="c9cff-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c9cff-111">やなどのアクセシビリティ `mrPublic` フラグ `mrPrivate` 。</span><span class="sxs-lookup"><span data-stu-id="c9cff-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="c9cff-112">このパラメーターは、 [DefineManifestResource メソッド](../metadata/imetadataassemblyemit-definemanifestresource-method.md)に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="c9cff-112">This parameter may be passed to [DefineManifestResource Method](../metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9cff-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="c9cff-113">Return Value</span></span>  

 <span data-ttu-id="c9cff-114">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="c9cff-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9cff-115">要件</span><span class="sxs-lookup"><span data-stu-id="c9cff-115">Requirements</span></span>  

 <span data-ttu-id="c9cff-116">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="c9cff-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9cff-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9cff-117">See also</span></span>

- [<span data-ttu-id="c9cff-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c9cff-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c9cff-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c9cff-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c9cff-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="c9cff-120">ALink API</span></span>](index.md)
