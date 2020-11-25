---
title: IReferenceAppId インターフェイス
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
ms.openlocfilehash: 9aa7173d81d84d9080d90b0890769ffeaee6a738
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728616"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="bfed9-102">IReferenceAppId インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfed9-102">IReferenceAppId Interface</span></span>

<span data-ttu-id="bfed9-103">現在のスコープ内のアプリケーションの一意の識別子への参照を表します。</span><span class="sxs-lookup"><span data-stu-id="bfed9-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bfed9-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="bfed9-104">Methods</span></span>  
  
|<span data-ttu-id="bfed9-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="bfed9-105">Method</span></span>|<span data-ttu-id="bfed9-106">説明</span><span class="sxs-lookup"><span data-stu-id="bfed9-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="bfed9-107">このによって参照されるアプリケーションのコード識別子の文字列形式へのポインターを取得し `IReferenceAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="bfed9-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="bfed9-108">このによって参照されるアプリケーションのコード識別子を設定し `IReferenceAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="bfed9-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="bfed9-109">`IEnumReferenceIdentity`こののメンバーを表すインスタンスを格納しているインスタンスへのインターフェイスポインターを取得し `IReferenceIdentity` `IReferenceAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="bfed9-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="bfed9-110">このに対するサブスクリプションのトークン識別子の文字列形式へのポインターを取得し `IReferenceAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="bfed9-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="bfed9-111">サブスクリプションのトークン識別子を `IReferenceAppId` 指定された文字列値に設定します。</span><span class="sxs-lookup"><span data-stu-id="bfed9-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bfed9-112">要件</span><span class="sxs-lookup"><span data-stu-id="bfed9-112">Requirements</span></span>  

 <span data-ttu-id="bfed9-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfed9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfed9-114">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="bfed9-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="bfed9-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfed9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfed9-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="bfed9-116">See also</span></span>

- [<span data-ttu-id="bfed9-117">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfed9-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="bfed9-118">IEnumReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfed9-118">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)
- [<span data-ttu-id="bfed9-119">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfed9-119">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
