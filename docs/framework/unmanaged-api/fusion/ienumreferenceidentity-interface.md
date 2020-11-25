---
title: IEnumReferenceIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
ms.openlocfilehash: bea357fe9a154ffb8f69228c7332c026dc2759e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728974"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="5a8c3-102">IEnumReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a8c3-102">IEnumReferenceIdentity Interface</span></span>

<span data-ttu-id="5a8c3-103">オブジェクトのコレクションの列挙子として機能し `IReferenceIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="5a8c3-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5a8c3-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="5a8c3-104">Methods</span></span>  
  
|<span data-ttu-id="5a8c3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5a8c3-105">Method</span></span>|<span data-ttu-id="5a8c3-106">説明</span><span class="sxs-lookup"><span data-stu-id="5a8c3-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="5a8c3-107">このと同じメンバーを含む新しいへのインターフェイスポインターを取得し `IEnumReferenceIdentity` `IEnumReferenceIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="5a8c3-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="5a8c3-108">現在の位置から開始して、指定した数の `IReferenceIdentity` オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="5a8c3-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="5a8c3-109">命令ポインターをこのの先頭に移動し `IEnumReferenceIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="5a8c3-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="5a8c3-110">現在位置を開始位置として、指定した要素数だけ前方に命令ポインターを移動します。</span><span class="sxs-lookup"><span data-stu-id="5a8c3-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5a8c3-111">要件</span><span class="sxs-lookup"><span data-stu-id="5a8c3-111">Requirements</span></span>  

 <span data-ttu-id="5a8c3-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a8c3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a8c3-113">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="5a8c3-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="5a8c3-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a8c3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a8c3-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a8c3-115">See also</span></span>

- [<span data-ttu-id="5a8c3-116">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a8c3-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="5a8c3-117">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a8c3-117">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
