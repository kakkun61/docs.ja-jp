---
title: ICorDebugModule インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
ms.openlocfilehash: 86e17b48bc491c45f8b46be23ab626dc1f2a6962
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709844"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="3af71-102">ICorDebugModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3af71-102">ICorDebugModule Interface</span></span>

<span data-ttu-id="3af71-103">実行可能ファイルまたはダイナミックリンクライブラリ (DLL) のいずれかである共通言語ランタイム (CLR) モジュールを表します。</span><span class="sxs-lookup"><span data-stu-id="3af71-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3af71-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-104">Methods</span></span>  
  
|<span data-ttu-id="3af71-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-105">Method</span></span>|<span data-ttu-id="3af71-106">説明</span><span class="sxs-lookup"><span data-stu-id="3af71-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3af71-107">CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-107">CreateBreakpoint Method</span></span>](icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="3af71-108">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="3af71-108">Not implemented.</span></span>|  
|[<span data-ttu-id="3af71-109">EnableClassLoadCallbacks メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-109">EnableClassLoadCallbacks Method</span></span>](icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="3af71-110">このモジュールに対して、" [UnloadClass](icordebugmanagedcallback-unloadclass-method.md) " コール[バック:: loadclass](icordebugmanagedcallback-loadclass-method.md)との各コールバックを呼び出すかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="3af71-110">Determines whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="3af71-111">EnableJITDebugging メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-111">EnableJITDebugging Method</span></span>](icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="3af71-112">Just-in-time (JIT) コンパイラが、このモジュール内のメソッドのデバッグ情報を保持するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="3af71-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="3af71-113">GetAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-113">GetAssembly Method</span></span>](icordebugmodule-getassembly-method.md)|<span data-ttu-id="3af71-114">このモジュールの格納アセンブリを取得します。</span><span class="sxs-lookup"><span data-stu-id="3af71-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="3af71-115">GetBaseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-115">GetBaseAddress Method</span></span>](icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="3af71-116">モジュールのベースアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="3af71-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="3af71-117">GetClassFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-117">GetClassFromToken Method</span></span>](icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="3af71-118">メタデータから、このクラスを取得します。</span><span class="sxs-lookup"><span data-stu-id="3af71-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="3af71-119">GetEditAndContinueSnapshot メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-119">GetEditAndContinueSnapshot Method</span></span>](icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="3af71-120">非推奨。</span><span class="sxs-lookup"><span data-stu-id="3af71-120">Deprecated.</span></span>|  
|[<span data-ttu-id="3af71-121">GetFunctionFromRVA メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-121">GetFunctionFromRVA Method</span></span>](icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="3af71-122">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="3af71-122">Not implemented.</span></span>|  
|[<span data-ttu-id="3af71-123">GetFunctionFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-123">GetFunctionFromToken Method</span></span>](icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="3af71-124">メタデータトークンによって指定された関数を取得します。</span><span class="sxs-lookup"><span data-stu-id="3af71-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="3af71-125">GetGlobalVariableValue メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-125">GetGlobalVariableValue Method</span></span>](icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="3af71-126">指定したグローバル変数の値オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="3af71-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="3af71-127">GetMetaDataInterface メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-127">GetMetaDataInterface Method</span></span>](icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="3af71-128">モジュールのメタデータを調べるために使用できるメタデータインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="3af71-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="3af71-129">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-129">GetName Method</span></span>](icordebugmodule-getname-method.md)|<span data-ttu-id="3af71-130">モジュールのファイル名を取得します。</span><span class="sxs-lookup"><span data-stu-id="3af71-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="3af71-131">GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-131">GetProcess Method</span></span>](icordebugmodule-getprocess-method.md)|<span data-ttu-id="3af71-132">このモジュールの格納プロセスを取得します。</span><span class="sxs-lookup"><span data-stu-id="3af71-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="3af71-133">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-133">GetSize Method</span></span>](icordebugmodule-getsize-method.md)|<span data-ttu-id="3af71-134">モジュールのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="3af71-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="3af71-135">GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-135">GetToken Method</span></span>](icordebugmodule-gettoken-method.md)|<span data-ttu-id="3af71-136">このモジュールのテーブルエントリのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="3af71-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="3af71-137">IsDynamic メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-137">IsDynamic Method</span></span>](icordebugmodule-isdynamic-method.md)|<span data-ttu-id="3af71-138">モジュールが動的かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="3af71-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="3af71-139">IsInMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="3af71-139">IsInMemory Method</span></span>](icordebugmodule-isinmemory-method.md)|<span data-ttu-id="3af71-140">このモジュールがメモリ内にのみ存在するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="3af71-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3af71-141">注釈</span><span class="sxs-lookup"><span data-stu-id="3af71-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3af71-142">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="3af71-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3af71-143">要件</span><span class="sxs-lookup"><span data-stu-id="3af71-143">Requirements</span></span>  

 <span data-ttu-id="3af71-144">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3af71-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3af71-145">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3af71-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3af71-146">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3af71-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3af71-147">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3af71-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3af71-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="3af71-148">See also</span></span>

- [<span data-ttu-id="3af71-149">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3af71-149">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="3af71-150">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3af71-150">Debugging Interfaces</span></span>](debugging-interfaces.md)
