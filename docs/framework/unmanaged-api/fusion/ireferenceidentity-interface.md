---
title: IReferenceIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
ms.openlocfilehash: 867c09caa3bd3aed50de21c2ef91a02782830be2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704553"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="74428-102">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="74428-102">IReferenceIdentity Interface</span></span>

<span data-ttu-id="74428-103">コードオブジェクトの一意の署名への参照を表します。</span><span class="sxs-lookup"><span data-stu-id="74428-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74428-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="74428-104">Methods</span></span>  
  
|<span data-ttu-id="74428-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="74428-105">Method</span></span>|<span data-ttu-id="74428-106">説明</span><span class="sxs-lookup"><span data-stu-id="74428-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="74428-107">`IReferenceIdentity` `IReferenceIdentity` 指定した属性の変更を除き、このと同一の新しいインスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="74428-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="74428-108">`IEnumIDENTITY_ATTRIBUTE`このに関連付けられている属性を格納しているインスタンスへのインターフェイスポインターを取得し `IReferenceIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="74428-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="74428-109">指定した名前を使用して、指定した名前空間の属性の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="74428-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="74428-110">指定した名前空間と指定した名前を持つ属性を、指定した値に設定します。</span><span class="sxs-lookup"><span data-stu-id="74428-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="74428-111">要件</span><span class="sxs-lookup"><span data-stu-id="74428-111">Requirements</span></span>  

 <span data-ttu-id="74428-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74428-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74428-113">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="74428-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="74428-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74428-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74428-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="74428-115">See also</span></span>

- [<span data-ttu-id="74428-116">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="74428-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="74428-117">IEnumIDENTITY_ATTRIBUTE インターフェイス</span><span class="sxs-lookup"><span data-stu-id="74428-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
