---
title: Init メソッド
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
ms.openlocfilehash: 25a1c29ab94a785304b83d5b1bcb2d7176742a68
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726019"
---
# <a name="init-method"></a><span data-ttu-id="973d0-102">Init メソッド</span><span class="sxs-lookup"><span data-stu-id="973d0-102">Init Method</span></span>

<span data-ttu-id="973d0-103">使用する [Ialink インターフェイス](ialink-interface.md) を実装するオブジェクトを準備します。</span><span class="sxs-lookup"><span data-stu-id="973d0-103">Prepares objects implementing the [IALink Interface](ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="973d0-104">構文</span><span class="sxs-lookup"><span data-stu-id="973d0-104">Syntax</span></span>  
  
```cpp  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="973d0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="973d0-105">Parameters</span></span>  

 `pDispenser`  
 <span data-ttu-id="973d0-106">[IMetaDataDispenserEx インターフェイス](../metadata/imetadatadispenserex-interface.md) のメタデータディスペンサーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="973d0-106">[IMetaDataDispenserEx Interface](../metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="973d0-107">[IMetaDataError インターフェイス](../metadata/imetadataerror-interface.md) は、省略可能なエラー処理インターフェイスへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="973d0-107">[IMetaDataError Interface](../metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="973d0-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="973d0-108">Return Value</span></span>  

 <span data-ttu-id="973d0-109">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="973d0-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="973d0-110">要件</span><span class="sxs-lookup"><span data-stu-id="973d0-110">Requirements</span></span>  

 <span data-ttu-id="973d0-111">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="973d0-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="973d0-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="973d0-112">See also</span></span>

- [<span data-ttu-id="973d0-113">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="973d0-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="973d0-114">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="973d0-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="973d0-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="973d0-115">ALink API</span></span>](index.md)
