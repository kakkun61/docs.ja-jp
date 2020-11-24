---
title: ICorDebugProcess5::EnumerateGCReferences メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
ms.openlocfilehash: 0f2f5acfc6a23398b15af3a63345050eb0dfd5b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687191"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="97b33-102">ICorDebugProcess5::EnumerateGCReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="97b33-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>

<span data-ttu-id="97b33-103">プロセスでガベージコレクトされるすべてのオブジェクトの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="97b33-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97b33-104">構文</span><span class="sxs-lookup"><span data-stu-id="97b33-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97b33-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="97b33-105">Parameters</span></span>  

 `enumerateWeakReferences`  
 <span data-ttu-id="97b33-106">から弱い参照も列挙するかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="97b33-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="97b33-107">がの場合 `enumerateWeakReferences` `true` 、 `ppEnum` 列挙子には、厳密な参照と弱い参照の両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="97b33-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="97b33-108">がの場合 `enumerateWeakReferences` `false` 、列挙子には厳密な参照のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="97b33-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="97b33-109">入出力ガベージコレクションの対象となるオブジェクトの列挙子 [である、](icordebuggcreferenceenum-interface.md) ツールのアドレスへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="97b33-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97b33-110">注釈</span><span class="sxs-lookup"><span data-stu-id="97b33-110">Remarks</span></span>  

 <span data-ttu-id="97b33-111">このメソッドは、プロセス内の任意のマネージオブジェクトの完全なルートチェーンを確認する方法を提供し、オブジェクトがまだアクティブである理由を判断するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="97b33-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97b33-112">要件</span><span class="sxs-lookup"><span data-stu-id="97b33-112">Requirements</span></span>  

 <span data-ttu-id="97b33-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97b33-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97b33-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97b33-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97b33-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97b33-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97b33-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97b33-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97b33-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="97b33-117">See also</span></span>

- [<span data-ttu-id="97b33-118">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="97b33-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="97b33-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="97b33-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
