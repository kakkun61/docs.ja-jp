---
title: IMetaDataImport::EnumTypeSpecs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
ms.openlocfilehash: 38c9f8df12b0fc83a236d2cb7c32d1198be7096d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719815"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="63af1-102">IMetaDataImport::EnumTypeSpecs メソッド</span><span class="sxs-lookup"><span data-stu-id="63af1-102">IMetaDataImport::EnumTypeSpecs Method</span></span>

<span data-ttu-id="63af1-103">現在のメタデータ スコープに定義されている TypeSpec トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="63af1-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63af1-104">構文</span><span class="sxs-lookup"><span data-stu-id="63af1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63af1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="63af1-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="63af1-106">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="63af1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="63af1-107">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="63af1-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="63af1-108">入出力TypeSpec トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="63af1-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="63af1-109">[in] `rTypeSpecs` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="63af1-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="63af1-110">入出力で返された TypeSpec トークンの数 `rTypeSpecs` 。</span><span class="sxs-lookup"><span data-stu-id="63af1-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63af1-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="63af1-111">Return Value</span></span>  
  
|<span data-ttu-id="63af1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="63af1-112">HRESULT</span></span>|<span data-ttu-id="63af1-113">説明</span><span class="sxs-lookup"><span data-stu-id="63af1-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="63af1-114">`EnumTypeSpecs` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="63af1-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="63af1-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="63af1-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="63af1-116">この場合、 `pcTypeSpecs` は0になります。</span><span class="sxs-lookup"><span data-stu-id="63af1-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63af1-117">注釈</span><span class="sxs-lookup"><span data-stu-id="63af1-117">Remarks</span></span>  

 <span data-ttu-id="63af1-118">TypeSpec トークンは、 [IMetaDataEmit:: GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) メソッドによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="63af1-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63af1-119">要件</span><span class="sxs-lookup"><span data-stu-id="63af1-119">Requirements</span></span>  

 <span data-ttu-id="63af1-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63af1-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63af1-121">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="63af1-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63af1-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="63af1-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="63af1-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63af1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63af1-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="63af1-124">See also</span></span>

- [<span data-ttu-id="63af1-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63af1-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="63af1-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63af1-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
