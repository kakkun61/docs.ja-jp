---
title: IMetaDataEmit2::SaveDeltaToMemory メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type:
- apiref
ms.openlocfilehash: a4dbe090987248ef77ce371b5bc6fb42d898f726
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705411"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="c95ca-102">IMetaDataEmit2::SaveDeltaToMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="c95ca-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>

<span data-ttu-id="c95ca-103">現在のエディットコンティニュセッションの変更をメモリに保存します。</span><span class="sxs-lookup"><span data-stu-id="c95ca-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c95ca-104">構文</span><span class="sxs-lookup"><span data-stu-id="c95ca-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c95ca-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c95ca-105">Parameters</span></span>  

 `pbData`  
 <span data-ttu-id="c95ca-106">入出力メタデータデルタの書き込みを開始するアドレス。</span><span class="sxs-lookup"><span data-stu-id="c95ca-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="c95ca-107">から変更のサイズ。</span><span class="sxs-lookup"><span data-stu-id="c95ca-107">[in] The size of the changes.</span></span> <span data-ttu-id="c95ca-108">サイズを確認するには、 [IMetaDataEmit2:: GetDeltaSaveSize](imetadataemit2-getdeltasavesize-method.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c95ca-108">Use [IMetaDataEmit2::GetDeltaSaveSize](imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c95ca-109">要件</span><span class="sxs-lookup"><span data-stu-id="c95ca-109">Requirements</span></span>  

 <span data-ttu-id="c95ca-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c95ca-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c95ca-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="c95ca-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c95ca-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="c95ca-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c95ca-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c95ca-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c95ca-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c95ca-114">See also</span></span>

- [<span data-ttu-id="c95ca-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c95ca-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="c95ca-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c95ca-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
