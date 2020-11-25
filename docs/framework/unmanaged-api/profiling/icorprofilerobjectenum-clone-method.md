---
title: ICorProfilerObjectEnum::Clone メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
ms.openlocfilehash: df1d5881bccdb357b16c7f02cd090388e0f66273
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722805"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="ad321-102">ICorProfilerObjectEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="ad321-102">ICorProfilerObjectEnum::Clone Method</span></span>

<span data-ttu-id="ad321-103">この [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) インターフェイスのコピーへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="ad321-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad321-104">構文</span><span class="sxs-lookup"><span data-stu-id="ad321-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad321-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad321-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="ad321-106">入出力このインターフェイスのコピーを指すインターフェイスポインターへのポインター `ICorProfilerObjectEnum` 。</span><span class="sxs-lookup"><span data-stu-id="ad321-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="ad321-107">コピーは、このコピーとは別に独自の列挙状態を保持します。</span><span class="sxs-lookup"><span data-stu-id="ad321-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="ad321-108">ただし、コピーの初期カーソル位置は、この列挙子の現在のカーソル位置と同じになります。</span><span class="sxs-lookup"><span data-stu-id="ad321-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad321-109">要件</span><span class="sxs-lookup"><span data-stu-id="ad321-109">Requirements</span></span>  

 <span data-ttu-id="ad321-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad321-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad321-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ad321-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ad321-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad321-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad321-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad321-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad321-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad321-114">See also</span></span>

- [<span data-ttu-id="ad321-115">ICorProfilerObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad321-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
