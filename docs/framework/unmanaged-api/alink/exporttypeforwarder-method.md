---
title: ExportTypeForwarder メソッド
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
ms.openlocfilehash: 4e6ceabf37056bfc25247266be2c7801cb0e13e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684773"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="59d3b-102">ExportTypeForwarder メソッド</span><span class="sxs-lookup"><span data-stu-id="59d3b-102">ExportTypeForwarder Method</span></span>

<span data-ttu-id="59d3b-103">指定されたアセンブリの型テーブルに型フォワーダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="59d3b-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59d3b-104">構文</span><span class="sxs-lookup"><span data-stu-id="59d3b-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="59d3b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="59d3b-105">Parameters</span></span>  

 `tkAssemblyRef`  
 <span data-ttu-id="59d3b-106">型フォワーダーが参照するアセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="59d3b-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="59d3b-107">エクスポートする完全修飾型名。</span><span class="sxs-lookup"><span data-stu-id="59d3b-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="59d3b-108">`ComType``tdPublic`やなどのフラグ `tdNested` 。</span><span class="sxs-lookup"><span data-stu-id="59d3b-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="59d3b-109">この値は、この [メソッド](../metadata/imetadataassemblyemit-defineexportedtype-method.md)に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="59d3b-109">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="59d3b-110">エクスポートされた型のトークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="59d3b-110">Receives the token of the exported type.</span></span> <span data-ttu-id="59d3b-111">これは、入れ子にされた型を出力する場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="59d3b-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59d3b-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="59d3b-112">Return Value</span></span>  

 <span data-ttu-id="59d3b-113">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="59d3b-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59d3b-114">要件</span><span class="sxs-lookup"><span data-stu-id="59d3b-114">Requirements</span></span>  

 <span data-ttu-id="59d3b-115">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="59d3b-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59d3b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="59d3b-116">See also</span></span>

- [<span data-ttu-id="59d3b-117">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="59d3b-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="59d3b-118">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="59d3b-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="59d3b-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="59d3b-119">ALink API</span></span>](index.md)
