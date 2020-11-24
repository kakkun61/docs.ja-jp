---
title: ICorPublishEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
ms.openlocfilehash: 492d4b727ce507340fec47d30a791aa49d0cecb6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693347"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="6227d-102">ICorPublishEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6227d-102">ICorPublishEnum Interface</span></span>

<span data-ttu-id="6227d-103">プロセスおよびアプリケーションドメインに関する情報の公開に使用される列挙子の抽象基本インターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="6227d-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6227d-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="6227d-104">Methods</span></span>  
  
|<span data-ttu-id="6227d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6227d-105">Method</span></span>|<span data-ttu-id="6227d-106">説明</span><span class="sxs-lookup"><span data-stu-id="6227d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6227d-107">Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="6227d-107">Clone Method</span></span>](icorpublishenum-clone-method.md)|<span data-ttu-id="6227d-108">この `ICorPublishEnum` オブジェクトのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="6227d-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="6227d-109">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="6227d-109">GetCount Method</span></span>](icorpublishenum-getcount-method.md)|<span data-ttu-id="6227d-110">列挙に含まれる項目の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="6227d-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="6227d-111">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="6227d-111">Reset Method</span></span>](icorpublishenum-reset-method.md)|<span data-ttu-id="6227d-112">のカーソルを列挙体の先頭に移動します。</span><span class="sxs-lookup"><span data-stu-id="6227d-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="6227d-113">Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="6227d-113">Skip Method</span></span>](icorpublishenum-skip-method.md)|<span data-ttu-id="6227d-114">指定した数の項目だけ、列挙内でカーソルを前方に移動します。</span><span class="sxs-lookup"><span data-stu-id="6227d-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6227d-115">注釈</span><span class="sxs-lookup"><span data-stu-id="6227d-115">Remarks</span></span>  

 <span data-ttu-id="6227d-116">次の列挙子は、から派生し `ICorPublishEnum` ます。</span><span class="sxs-lookup"><span data-stu-id="6227d-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
- [<span data-ttu-id="6227d-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="6227d-117">ICorPublishAppDomainEnum</span></span>](icorpublishappdomainenum-interface.md)  
  
- [<span data-ttu-id="6227d-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="6227d-118">ICorPublishProcessEnum</span></span>](icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="6227d-119">要件</span><span class="sxs-lookup"><span data-stu-id="6227d-119">Requirements</span></span>  

 <span data-ttu-id="6227d-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6227d-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6227d-121">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="6227d-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6227d-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6227d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6227d-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6227d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6227d-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="6227d-124">See also</span></span>

- [<span data-ttu-id="6227d-125">CorpubPublish コクラス</span><span class="sxs-lookup"><span data-stu-id="6227d-125">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
- [<span data-ttu-id="6227d-126">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6227d-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
