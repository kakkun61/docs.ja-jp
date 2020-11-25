---
title: IMetaDataImport::EnumUnresolvedMethods メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
ms.openlocfilehash: 6b5e7bbe2303a200d7829fea12e228a513595f97
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716552"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="50a3f-102">IMetaDataImport::EnumUnresolvedMethods メソッド</span><span class="sxs-lookup"><span data-stu-id="50a3f-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>

<span data-ttu-id="50a3f-103">現在のメタデータ スコープ内の未解決のメソッドを表す MemberDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="50a3f-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50a3f-104">構文</span><span class="sxs-lookup"><span data-stu-id="50a3f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50a3f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50a3f-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="50a3f-106">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="50a3f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="50a3f-107">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="50a3f-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="50a3f-108">入出力MemberDef トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="50a3f-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="50a3f-109">[in] `rMethods` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="50a3f-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="50a3f-110">入出力で返された MemberDef トークンの数 `rMethods` 。</span><span class="sxs-lookup"><span data-stu-id="50a3f-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50a3f-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="50a3f-111">Return Value</span></span>  
  
|<span data-ttu-id="50a3f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50a3f-112">HRESULT</span></span>|<span data-ttu-id="50a3f-113">説明</span><span class="sxs-lookup"><span data-stu-id="50a3f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="50a3f-114">`EnumUnresolvedMethods` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="50a3f-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="50a3f-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="50a3f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="50a3f-116">この場合、 `pcTokens` は0になります。</span><span class="sxs-lookup"><span data-stu-id="50a3f-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50a3f-117">注釈</span><span class="sxs-lookup"><span data-stu-id="50a3f-117">Remarks</span></span>  

 <span data-ttu-id="50a3f-118">未解決のメソッドとは、宣言されていても実装されていないメソッドです。</span><span class="sxs-lookup"><span data-stu-id="50a3f-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="50a3f-119">メソッドがマークされ、 `miForwardRef` `mdPinvokeImpl` またはが0に設定されている場合、メソッドは列挙体に含まれ `miRuntime` ます。</span><span class="sxs-lookup"><span data-stu-id="50a3f-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="50a3f-120">つまり、未解決のメソッドは、とマークされているものの、 `miForwardRef` アンマネージコードでは実装されていない (PInvoke 経由で)、またはランタイム自体によって内部的に実装されていないクラスメソッドです。</span><span class="sxs-lookup"><span data-stu-id="50a3f-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="50a3f-121">列挙体には、モジュールスコープ (globals) またはインターフェイスまたは抽象クラスで定義されているすべてのメソッドが除外されます。</span><span class="sxs-lookup"><span data-stu-id="50a3f-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50a3f-122">要件</span><span class="sxs-lookup"><span data-stu-id="50a3f-122">Requirements</span></span>  

 <span data-ttu-id="50a3f-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50a3f-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50a3f-124">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="50a3f-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50a3f-125">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="50a3f-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50a3f-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50a3f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50a3f-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="50a3f-127">See also</span></span>

- [<span data-ttu-id="50a3f-128">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="50a3f-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="50a3f-129">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="50a3f-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
