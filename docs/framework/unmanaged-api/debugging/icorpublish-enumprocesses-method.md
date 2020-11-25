---
title: ICorPublish::EnumProcesses メソッド
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
ms.openlocfilehash: 297f672097dd6561a971608f368369c623532907
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716916"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="d9df6-102">ICorPublish::EnumProcesses メソッド</span><span class="sxs-lookup"><span data-stu-id="d9df6-102">ICorPublish::EnumProcesses Method</span></span>

<span data-ttu-id="d9df6-103">このコンピューター上で実行されているマネージプロセスの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="d9df6-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9df6-104">構文</span><span class="sxs-lookup"><span data-stu-id="d9df6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9df6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d9df6-105">Parameters</span></span>  

 `Type`  
 <span data-ttu-id="d9df6-106">取得するプロセスの種類を指定する [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="d9df6-106">A value of the [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="d9df6-107">現在のバージョンでは、COR_PUB_MANAGEDONLY のみが有効です。</span><span class="sxs-lookup"><span data-stu-id="d9df6-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="d9df6-108">プロセスの列挙子である [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) インスタンスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d9df6-108">A pointer to the address of an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9df6-109">注釈</span><span class="sxs-lookup"><span data-stu-id="d9df6-109">Remarks</span></span>  

 <span data-ttu-id="d9df6-110">列挙子のプロセスのコレクションは、メソッドが呼び出されたときに実行されているプロセスのスナップショットに基づいてい `EnumProcesses` ます。</span><span class="sxs-lookup"><span data-stu-id="d9df6-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="d9df6-111">列挙子には、の呼び出しの前または後に終了するプロセスは含まれません `EnumProcesses` 。</span><span class="sxs-lookup"><span data-stu-id="d9df6-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="d9df6-112">`EnumProcesses`この[ICorPublish](icorpublish-interface.md)インスタンスでメソッドを複数回呼び出して、新しい最新のプロセスコレクションを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="d9df6-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="d9df6-113">既存のコレクションは、メソッドの後続の呼び出しの影響を受けません `EnumProcesses` 。</span><span class="sxs-lookup"><span data-stu-id="d9df6-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9df6-114">要件</span><span class="sxs-lookup"><span data-stu-id="d9df6-114">Requirements</span></span>  

 <span data-ttu-id="d9df6-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9df6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9df6-116">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="d9df6-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d9df6-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9df6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9df6-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9df6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9df6-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9df6-119">See also</span></span>

- [<span data-ttu-id="d9df6-120">ICorPublish インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d9df6-120">ICorPublish Interface</span></span>](icorpublish-interface.md)
