---
title: ExportType メソッド
ms.date: 03/30/2017
api_name:
- IALink.ExportType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportType
helpviewer_keywords:
- ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type:
- apiref
ms.openlocfilehash: b8db08b22765bac0ed2fe058db49d6882b8d22df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684799"
---
# <a name="exporttype-method"></a><span data-ttu-id="728ce-102">ExportType メソッド</span><span class="sxs-lookup"><span data-stu-id="728ce-102">ExportType Method</span></span>

<span data-ttu-id="728ce-103">型がエクスポート可能であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="728ce-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="728ce-104">構文</span><span class="sxs-lookup"><span data-stu-id="728ce-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="728ce-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="728ce-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="728ce-106">エクスポート元のアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="728ce-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="728ce-107">エクスポート可能な型を定義するファイルのファイルトークンまたはアセンブリ ID。</span><span class="sxs-lookup"><span data-stu-id="728ce-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="728ce-108">エクスポート可能にする型のトークン。</span><span class="sxs-lookup"><span data-stu-id="728ce-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="728ce-109">エクスポート可能にする完全修飾型名。</span><span class="sxs-lookup"><span data-stu-id="728ce-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="728ce-110">`ComType``tdPublic`やなどのフラグ `tdNested` 。</span><span class="sxs-lookup"><span data-stu-id="728ce-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="728ce-111">このパラメーターは、この [メソッド](../metadata/imetadataassemblyemit-defineexportedtype-method.md)に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="728ce-111">This parameter may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="728ce-112">エクスポートされた型のトークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="728ce-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="728ce-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="728ce-113">Return Value</span></span>  

 <span data-ttu-id="728ce-114">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="728ce-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="728ce-115">要件</span><span class="sxs-lookup"><span data-stu-id="728ce-115">Requirements</span></span>  

 <span data-ttu-id="728ce-116">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="728ce-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="728ce-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="728ce-117">See also</span></span>

- [<span data-ttu-id="728ce-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="728ce-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="728ce-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="728ce-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="728ce-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="728ce-120">ALink API</span></span>](index.md)
