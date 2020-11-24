---
title: IMetaDataEmit::DefineEvent メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
ms.openlocfilehash: 3c03497f48b8199da545d796637e5f8a5c532362
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675687"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="b1614-102">IMetaDataEmit::DefineEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="b1614-102">IMetaDataEmit::DefineEvent Method</span></span>

<span data-ttu-id="b1614-103">指定したメタデータシグネチャを持つイベントの定義を作成し、そのイベント定義へのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="b1614-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1614-104">構文</span><span class="sxs-lookup"><span data-stu-id="b1614-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineEvent (
    [in]  mdTypeDef    td,
    [in]  LPCWSTR      szEvent,
    [in]  DWORD        dwEventFlags,
    [in]  mdToken      tkEventType,
    [in]  mdMethodDef  mdAddOn,
    [in]  mdMethodDef  mdRemoveOn,
    [in]  mdMethodDef  mdFire,
    [in]  mdMethodDef  rmdOtherMethods[],
    [out] mdEvent      *pmdEvent
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1614-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b1614-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="b1614-106">からターゲットクラスまたはインターフェイスのトークン。</span><span class="sxs-lookup"><span data-stu-id="b1614-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="b1614-107">これは、 `mdTypeDef` またはトークンのいずれか `mdTypeDefNil` です。</span><span class="sxs-lookup"><span data-stu-id="b1614-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="b1614-108">からイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="b1614-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="b1614-109">からイベントフラグ。</span><span class="sxs-lookup"><span data-stu-id="b1614-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="b1614-110">からイベントクラスのトークン。</span><span class="sxs-lookup"><span data-stu-id="b1614-110">[in] The token for the event class.</span></span> <span data-ttu-id="b1614-111">これは `mdTypeDef` 、、、 `mdTypeRef` または `mdTokenNil` トークンです。</span><span class="sxs-lookup"><span data-stu-id="b1614-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="b1614-112">からイベントの定期受信に使用するメソッド、または null。</span><span class="sxs-lookup"><span data-stu-id="b1614-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="b1614-113">からイベントのサブスクリプションを解除するために使用するメソッド、または null。</span><span class="sxs-lookup"><span data-stu-id="b1614-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="b1614-114">からイベントを発生させるために (派生クラスによって) 使用されるメソッド。</span><span class="sxs-lookup"><span data-stu-id="b1614-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="b1614-115">からイベントに関連付けられている他のメソッドのトークンの配列。</span><span class="sxs-lookup"><span data-stu-id="b1614-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="b1614-116">配列がトークンで終了してい `mdMethodDefNil` ます。</span><span class="sxs-lookup"><span data-stu-id="b1614-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="b1614-117">入出力イベントに割り当てられたメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="b1614-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1614-118">要件</span><span class="sxs-lookup"><span data-stu-id="b1614-118">Requirements</span></span>  

 <span data-ttu-id="b1614-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1614-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1614-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="b1614-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1614-121">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b1614-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1614-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1614-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1614-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1614-123">See also</span></span>

- [<span data-ttu-id="b1614-124">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1614-124">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b1614-125">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1614-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
