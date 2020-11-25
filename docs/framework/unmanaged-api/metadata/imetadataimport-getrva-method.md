---
title: IMetaDataImport::GetRVA メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: b4e7209c357f21a3f0de5770b483b673d5a5570b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729214"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="86df9-102">IMetaDataImport::GetRVA メソッド</span><span class="sxs-lookup"><span data-stu-id="86df9-102">IMetaDataImport::GetRVA Method</span></span>

<span data-ttu-id="86df9-103">指定したトークンによって表されるメソッドまたはフィールドの相対仮想アドレス (RVA) および実装フラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="86df9-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86df9-104">構文</span><span class="sxs-lookup"><span data-stu-id="86df9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86df9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="86df9-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="86df9-106">からRVA を返すコードオブジェクトを表す MethodDef または FieldDef のメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="86df9-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="86df9-107">トークンが FieldDef の場合、フィールドはグローバル変数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="86df9-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="86df9-108">入出力トークンによって表されるコードオブジェクトの相対仮想アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="86df9-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="86df9-109">入出力メソッドの実装フラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="86df9-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="86df9-110">この値は [Cormethodimpl](cormethodimpl-enumeration.md) 列挙子のビットマスクです。</span><span class="sxs-lookup"><span data-stu-id="86df9-110">This value is a bitmask from the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="86df9-111">の値は、 `pdwImplFlags` `tk` が MethodDef トークンの場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="86df9-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86df9-112">要件</span><span class="sxs-lookup"><span data-stu-id="86df9-112">Requirements</span></span>  

 <span data-ttu-id="86df9-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86df9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86df9-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="86df9-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86df9-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="86df9-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="86df9-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86df9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86df9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="86df9-117">See also</span></span>

- [<span data-ttu-id="86df9-118">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="86df9-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="86df9-119">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="86df9-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
