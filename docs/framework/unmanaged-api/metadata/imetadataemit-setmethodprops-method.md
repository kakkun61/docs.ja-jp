---
title: IMetaDataEmit::SetMethodProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
ms.openlocfilehash: c461582cc22f7185ee2707db91be83bc1aa0ba4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706841"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="c7fd9-102">IMetaDataEmit::SetMethodProps メソッド</span><span class="sxs-lookup"><span data-stu-id="c7fd9-102">IMetaDataEmit::SetMethodProps Method</span></span>

<span data-ttu-id="c7fd9-103">[IMetaDataEmit::D efinemethod](imetadataemit-definemethod-method.md)の前の呼び出しで定義されたメソッドの、指定した相対仮想アドレスに格納されている機能を設定または更新します。</span><span class="sxs-lookup"><span data-stu-id="c7fd9-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7fd9-104">構文</span><span class="sxs-lookup"><span data-stu-id="c7fd9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7fd9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c7fd9-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="c7fd9-106">から変更するメソッドのトークン。</span><span class="sxs-lookup"><span data-stu-id="c7fd9-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="c7fd9-107">からメンバー属性。</span><span class="sxs-lookup"><span data-stu-id="c7fd9-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="c7fd9-108">からコードのアドレス。</span><span class="sxs-lookup"><span data-stu-id="c7fd9-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="c7fd9-109">からメソッドの実装フラグ。</span><span class="sxs-lookup"><span data-stu-id="c7fd9-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7fd9-110">要件</span><span class="sxs-lookup"><span data-stu-id="c7fd9-110">Requirements</span></span>  

 <span data-ttu-id="c7fd9-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7fd9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7fd9-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="c7fd9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7fd9-113">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="c7fd9-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7fd9-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7fd9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7fd9-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7fd9-115">See also</span></span>

- [<span data-ttu-id="c7fd9-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c7fd9-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c7fd9-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c7fd9-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
