---
title: IMetaDataError インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError
helpviewer_keywords:
- IMetaDataError interface [.NET Framework metadata]
ms.assetid: 0020b62c-ea88-40c7-a9ee-16b064f81624
topic_type:
- apiref
ms.openlocfilehash: 5f5e04787ce0ab0e1c8ecf3c19ba37e76ba38bfe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701927"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="d705a-102">IMetaDataError インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d705a-102">IMetaDataError Interface</span></span>

<span data-ttu-id="d705a-103">メタデータのマージ中にエラーを報告するためのコールバックメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="d705a-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d705a-104">インターフェイスは、 `IMetaDataError` クライアントによって実装される必要があります。</span><span class="sxs-lookup"><span data-stu-id="d705a-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d705a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d705a-105">Methods</span></span>  
  
|<span data-ttu-id="d705a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d705a-106">Method</span></span>|<span data-ttu-id="d705a-107">説明</span><span class="sxs-lookup"><span data-stu-id="d705a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d705a-108">OnError メソッド</span><span class="sxs-lookup"><span data-stu-id="d705a-108">OnError Method</span></span>](imetadataerror-onerror-method.md)|<span data-ttu-id="d705a-109">メタデータのマージ中に発生したエラーの通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="d705a-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d705a-110">要件</span><span class="sxs-lookup"><span data-stu-id="d705a-110">Requirements</span></span>  

 <span data-ttu-id="d705a-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d705a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d705a-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="d705a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d705a-113">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="d705a-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d705a-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d705a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d705a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="d705a-115">See also</span></span>

- [<span data-ttu-id="d705a-116">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d705a-116">Metadata Interfaces</span></span>](metadata-interfaces.md)
