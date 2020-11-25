---
title: IMetaDataImport::EnumSignatures メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
ms.openlocfilehash: 3021124184ab0491337a07144e6f77b5bfea3681
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721973"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="31848-102">IMetaDataImport::EnumSignatures メソッド</span><span class="sxs-lookup"><span data-stu-id="31848-102">IMetaDataImport::EnumSignatures Method</span></span>

<span data-ttu-id="31848-103">現在のスコープ内のスタンドアロン シグネチャを表す Signature トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="31848-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31848-104">構文</span><span class="sxs-lookup"><span data-stu-id="31848-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31848-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="31848-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="31848-106">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="31848-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="31848-107">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="31848-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="31848-108">入出力署名トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="31848-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="31848-109">[in] `rSignatures` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="31848-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="31848-110">入出力で返された署名トークンの数 `rSignatures` 。</span><span class="sxs-lookup"><span data-stu-id="31848-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31848-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="31848-111">Return Value</span></span>  
  
|<span data-ttu-id="31848-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="31848-112">HRESULT</span></span>|<span data-ttu-id="31848-113">説明</span><span class="sxs-lookup"><span data-stu-id="31848-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="31848-114">`EnumSignatures` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="31848-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="31848-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="31848-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="31848-116">この場合、 `pcSignatures` は0になります。</span><span class="sxs-lookup"><span data-stu-id="31848-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31848-117">注釈</span><span class="sxs-lookup"><span data-stu-id="31848-117">Remarks</span></span>  

 <span data-ttu-id="31848-118">署名トークンは、 [IMetaDataEmit:: GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) メソッドによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="31848-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31848-119">要件</span><span class="sxs-lookup"><span data-stu-id="31848-119">Requirements</span></span>  

 <span data-ttu-id="31848-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31848-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31848-121">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="31848-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31848-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="31848-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="31848-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31848-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31848-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="31848-124">See also</span></span>

- [<span data-ttu-id="31848-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="31848-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="31848-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="31848-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
