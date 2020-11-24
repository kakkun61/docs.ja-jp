---
title: ExportNestedType メソッド
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
ms.openlocfilehash: 69c99e2facfcb9077c3fc4131186ba3882c7cef6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684838"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="1c01f-102">ExportNestedType メソッド</span><span class="sxs-lookup"><span data-stu-id="1c01f-102">ExportNestedType Method</span></span>

<span data-ttu-id="1c01f-103">入れ子にされた型をエクスポート可能として指定します。</span><span class="sxs-lookup"><span data-stu-id="1c01f-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="1c01f-104">[Exporttype メソッド](exporttype-method.md)も入れ子になった型をエクスポートできますが、このメソッドの方が高速です。</span><span class="sxs-lookup"><span data-stu-id="1c01f-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c01f-105">構文</span><span class="sxs-lookup"><span data-stu-id="1c01f-105">Syntax</span></span>  
  
```cpp  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="1c01f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c01f-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="1c01f-107">エクスポート元のアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="1c01f-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="1c01f-108">エクスポート可能にする型を定義するファイルのトークンまたはアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="1c01f-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="1c01f-109">エクスポート可能にする型の型トークン。</span><span class="sxs-lookup"><span data-stu-id="1c01f-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="1c01f-110">親の種類のトークン。</span><span class="sxs-lookup"><span data-stu-id="1c01f-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="1c01f-111">エクスポートする完全修飾型名。</span><span class="sxs-lookup"><span data-stu-id="1c01f-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1c01f-112">`ComType``tdPublic`やなどのフラグ `tdNested` 。</span><span class="sxs-lookup"><span data-stu-id="1c01f-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="1c01f-113">この値は、この [メソッド](../metadata/imetadataassemblyemit-defineexportedtype-method.md)に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="1c01f-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="1c01f-114">エクスポートされた型のトークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="1c01f-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c01f-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="1c01f-115">Return Value</span></span>  

 <span data-ttu-id="1c01f-116">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="1c01f-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c01f-117">要件</span><span class="sxs-lookup"><span data-stu-id="1c01f-117">Requirements</span></span>  

 <span data-ttu-id="1c01f-118">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="1c01f-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c01f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c01f-119">See also</span></span>

- [<span data-ttu-id="1c01f-120">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1c01f-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="1c01f-121">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1c01f-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="1c01f-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="1c01f-122">ALink API</span></span>](index.md)
