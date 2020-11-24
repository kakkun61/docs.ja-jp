---
title: ICorPublishProcess::IsManaged メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: dfe247bda75c3695c7c09b85729b4e057c13c62d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692632"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="9abe6-102">ICorPublishProcess::IsManaged メソッド</span><span class="sxs-lookup"><span data-stu-id="9abe6-102">ICorPublishProcess::IsManaged Method</span></span>

<span data-ttu-id="9abe6-103">この [ICorPublishProcess](icorpublishprocess-interface.md) によって参照されるプロセスに、マネージコードがあることがわかっているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="9abe6-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9abe6-104">構文</span><span class="sxs-lookup"><span data-stu-id="9abe6-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9abe6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9abe6-105">Parameters</span></span>  

 `pbManaged`  
 <span data-ttu-id="9abe6-106">入出力プロセスにマネージコードがあるかどうかを示すブール値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9abe6-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="9abe6-107">`true`プロセスにマネージコードがある場合は、値はです。それ以外の場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="9abe6-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9abe6-108">注釈</span><span class="sxs-lookup"><span data-stu-id="9abe6-108">Remarks</span></span>  

 <span data-ttu-id="9abe6-109">現在のバージョンのでは `ICorPublishProcess` 、マネージコードを持つプロセスのみにアクセスが許可されるため、は `IsManaged` 常にを返し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="9abe6-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9abe6-110">要件</span><span class="sxs-lookup"><span data-stu-id="9abe6-110">Requirements</span></span>  

 <span data-ttu-id="9abe6-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9abe6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9abe6-112">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="9abe6-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9abe6-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9abe6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9abe6-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9abe6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9abe6-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="9abe6-115">See also</span></span>

- [<span data-ttu-id="9abe6-116">ICorPublishProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9abe6-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
