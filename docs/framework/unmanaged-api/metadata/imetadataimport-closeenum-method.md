---
title: IMetaDataImport::CloseEnum メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CloseEnum
helpviewer_keywords:
- IMetaDataImport::CloseEnum method [.NET Framework metadata]
- CloseEnum method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 727819d5-1dab-4ebb-ac25-950b4111dc72
topic_type:
- apiref
ms.openlocfilehash: f418b48f1b62ae8093197d64ca44b2ef659990a3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701719"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="406cb-102">IMetaDataImport::CloseEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="406cb-102">IMetaDataImport::CloseEnum Method</span></span>

<span data-ttu-id="406cb-103">指定したハンドルによって識別される列挙子を閉じます。</span><span class="sxs-lookup"><span data-stu-id="406cb-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="406cb-104">構文</span><span class="sxs-lookup"><span data-stu-id="406cb-104">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="406cb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="406cb-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="406cb-106">から閉じる列挙子のハンドル。</span><span class="sxs-lookup"><span data-stu-id="406cb-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="406cb-107">注釈</span><span class="sxs-lookup"><span data-stu-id="406cb-107">Remarks</span></span>  

 <span data-ttu-id="406cb-108">によって指定されたハンドル `hEnum` は、前 `Enum` の *名前* の呼び出し (たとえば、 [IMetaDataImport:: enumtypedefs](imetadataimport-enumtypedefs-method.md)) から取得されます。</span><span class="sxs-lookup"><span data-stu-id="406cb-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="406cb-109">要件</span><span class="sxs-lookup"><span data-stu-id="406cb-109">Requirements</span></span>  

 <span data-ttu-id="406cb-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="406cb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="406cb-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="406cb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="406cb-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="406cb-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="406cb-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="406cb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="406cb-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="406cb-114">See also</span></span>

- [<span data-ttu-id="406cb-115">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="406cb-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="406cb-116">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="406cb-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
