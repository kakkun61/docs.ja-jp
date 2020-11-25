---
title: IMetaDataEmit::SetHandler メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
ms.openlocfilehash: 9b03dc5460875af3bb3e5e20799a4d26eb74da05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730371"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="02e98-102">IMetaDataEmit::SetHandler メソッド</span><span class="sxs-lookup"><span data-stu-id="02e98-102">IMetaDataEmit::SetHandler Method</span></span>

<span data-ttu-id="02e98-103">指定したポインターによって参照されるメソッドを、 `IUnknown` トークンリマップの通知コールバックとして設定します。</span><span class="sxs-lookup"><span data-stu-id="02e98-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02e98-104">構文</span><span class="sxs-lookup"><span data-stu-id="02e98-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02e98-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="02e98-105">Parameters</span></span>  

 `pUnk`  
 <span data-ttu-id="02e98-106">から登録するハンドラー。</span><span class="sxs-lookup"><span data-stu-id="02e98-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02e98-107">注釈</span><span class="sxs-lookup"><span data-stu-id="02e98-107">Remarks</span></span>  

 <span data-ttu-id="02e98-108">メタデータエンジンは、によって提供されるメソッドを使用して、最適化された `SetHandler` 方法でレコードを生成せず、保存されたレコードを最適化するコンパイラに通知を送信します。</span><span class="sxs-lookup"><span data-stu-id="02e98-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="02e98-109">コールバックメソッドがによって提供されていない場合 `SetHandler` 、 `IMapToken` 各スコープに対して merge on merge を使用して複数のインポートスコープがマージされている場合を除き、保存時に最適化は実行されません。</span><span class="sxs-lookup"><span data-stu-id="02e98-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02e98-110">要件</span><span class="sxs-lookup"><span data-stu-id="02e98-110">Requirements</span></span>  

 <span data-ttu-id="02e98-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02e98-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02e98-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="02e98-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02e98-113">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="02e98-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="02e98-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02e98-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02e98-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="02e98-115">See also</span></span>

- [<span data-ttu-id="02e98-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="02e98-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="02e98-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="02e98-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
