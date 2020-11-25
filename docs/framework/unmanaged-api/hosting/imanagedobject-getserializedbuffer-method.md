---
title: IManagedObject::GetSerializedBuffer メソッド
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
ms.openlocfilehash: 159ece09ae0b6a67780639da8aae8c0e4b412bb8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730696"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="176c2-102">IManagedObject::GetSerializedBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="176c2-102">IManagedObject::GetSerializedBuffer Method</span></span>

<span data-ttu-id="176c2-103">このマネージオブジェクトの文字列表現を取得します。</span><span class="sxs-lookup"><span data-stu-id="176c2-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="176c2-104">構文</span><span class="sxs-lookup"><span data-stu-id="176c2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="176c2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="176c2-105">Parameters</span></span>  

 `pBSTR`  
 <span data-ttu-id="176c2-106">入出力シリアル化されたオブジェクトである文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="176c2-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="176c2-107">注釈</span><span class="sxs-lookup"><span data-stu-id="176c2-107">Remarks</span></span>  

 <span data-ttu-id="176c2-108">メソッドは、 `GetSerializedBuffer` オブジェクトをシリアル化してクライアントにマーシャリングできるようにします。</span><span class="sxs-lookup"><span data-stu-id="176c2-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="176c2-109">要件</span><span class="sxs-lookup"><span data-stu-id="176c2-109">Requirements</span></span>  

 <span data-ttu-id="176c2-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="176c2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="176c2-111">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="176c2-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="176c2-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="176c2-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="176c2-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="176c2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="176c2-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="176c2-114">See also</span></span>

- [<span data-ttu-id="176c2-115">IManagedObject インターフェイス</span><span class="sxs-lookup"><span data-stu-id="176c2-115">IManagedObject Interface</span></span>](imanagedobject-interface.md)
