---
title: IEnumIDENTITY_ATTRIBUTE インターフェイス
ms.date: 03/30/2017
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
ms.openlocfilehash: 71a6ea9f593da093985a4420e690f1bdd7f9d139
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728993"
---
# <a name="ienumidentity_attribute-interface"></a><span data-ttu-id="958cf-102">IEnumIDENTITY_ATTRIBUTE インターフェイス</span><span class="sxs-lookup"><span data-stu-id="958cf-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>

<span data-ttu-id="958cf-103">現在のスコープ内のコードオブジェクトの属性の列挙子として機能します。</span><span class="sxs-lookup"><span data-stu-id="958cf-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="958cf-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="958cf-104">Methods</span></span>  
  
|<span data-ttu-id="958cf-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="958cf-105">Method</span></span>|<span data-ttu-id="958cf-106">説明</span><span class="sxs-lookup"><span data-stu-id="958cf-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="958cf-107">このと同じメンバーを含む新しいへのインターフェイスポインターを取得し `IEnumIDENTITY_ATTRIBUTE` `IEnumIDENTITY_ATTRIBUTE` ます。</span><span class="sxs-lookup"><span data-stu-id="958cf-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="958cf-108">このの要素に格納されているデータ `IEnumIDENTITY_ATTRIBUTE` を、指定したデータバッファーに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="958cf-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="958cf-109">指定した数の属性を、現在の位置から開始して取得します。</span><span class="sxs-lookup"><span data-stu-id="958cf-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="958cf-110">命令ポインターをこのの先頭に移動し `IEnumIDENTITY_ATTRIBUTE` ます。</span><span class="sxs-lookup"><span data-stu-id="958cf-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="958cf-111">現在位置を開始位置として、指定した要素数だけ前方に命令ポインターを移動します。</span><span class="sxs-lookup"><span data-stu-id="958cf-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="958cf-112">要件</span><span class="sxs-lookup"><span data-stu-id="958cf-112">Requirements</span></span>  

 <span data-ttu-id="958cf-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="958cf-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="958cf-114">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="958cf-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="958cf-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="958cf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="958cf-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="958cf-116">See also</span></span>

- [<span data-ttu-id="958cf-117">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="958cf-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
