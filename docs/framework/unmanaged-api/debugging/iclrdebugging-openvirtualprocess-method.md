---
title: ICLRDebugging::OpenVirtualProcess メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
ms.openlocfilehash: 2edd7f628e17c8dc6cbcbb577d06269ba8c64cb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723542"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="bf34e-102">ICLRDebugging::OpenVirtualProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="bf34e-102">ICLRDebugging::OpenVirtualProcess Method</span></span>

<span data-ttu-id="bf34e-103">プロセスに読み込まれた共通言語ランタイム (CLR) モジュールに対応する、コンポーネントインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="bf34e-103">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf34e-104">構文</span><span class="sxs-lookup"><span data-stu-id="bf34e-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf34e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bf34e-105">Parameters</span></span>  

 `moduleBaseAddress`  
 <span data-ttu-id="bf34e-106">からターゲットプロセス内のモジュールのベースアドレス。</span><span class="sxs-lookup"><span data-stu-id="bf34e-106">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="bf34e-107">指定したモジュールが CLR モジュールでない場合、COR_E_NOT_CLR が返されます。</span><span class="sxs-lookup"><span data-stu-id="bf34e-107">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="bf34e-108">からマネージデバッガーがプロセスの状態を検査できるデータターゲットの抽象化。</span><span class="sxs-lookup"><span data-stu-id="bf34e-108">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="bf34e-109">デバッガーでは、、のように、によっては、 [このインターフェイスを](icordebugdatatarget-interface.md) 実装してください。</span><span class="sxs-lookup"><span data-stu-id="bf34e-109">The debugger must implement the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="bf34e-110">デバッグ対象の CLR がコンピューターにローカルにインストールされていないシナリオをサポートするには、 [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf34e-110">You should implement the [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="bf34e-111">からライブラリプロバイダーのコールバックインターフェイス。バージョン固有のデバッグライブラリをオンデマンドで検索し、読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="bf34e-111">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="bf34e-112">このパラメーターは `ppProcess` 、または `pFlags` がではない場合にのみ必要です `null` 。</span><span class="sxs-lookup"><span data-stu-id="bf34e-112">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="bf34e-113">からこのデバッガーがデバッグできる CLR の最大バージョン。</span><span class="sxs-lookup"><span data-stu-id="bf34e-113">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="bf34e-114">このデバッガーでサポートされている最新の CLR バージョンからメジャー、マイナー、ビルドの各バージョンを指定し、将来の CLR サービスリリースに対応するためにリビジョン番号を65535に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf34e-114">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="bf34e-115">から取得するコード処理インターフェイスの ID。</span><span class="sxs-lookup"><span data-stu-id="bf34e-115">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="bf34e-116">現時点で許容される値は、IID_CORDEBUGPROCESS3、IID_CORDEBUGPROCESS2、および IID_CORDEBUGPROCESS だけです。</span><span class="sxs-lookup"><span data-stu-id="bf34e-116">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="bf34e-117">入出力によって識別される COM インターフェイスへのポインター `riidProcess` 。</span><span class="sxs-lookup"><span data-stu-id="bf34e-117">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="bf34e-118">[入力、出力]CLR のバージョン。</span><span class="sxs-lookup"><span data-stu-id="bf34e-118">[in, out] The version of the CLR.</span></span> <span data-ttu-id="bf34e-119">入力時には、この値をにすることができ `null` ます。</span><span class="sxs-lookup"><span data-stu-id="bf34e-119">On input, this value can be `null`.</span></span> <span data-ttu-id="bf34e-120">また、 [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) 構造体を指すこともできます。この場合、構造体の `wStructVersion` フィールドを 0 (ゼロ) に初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf34e-120">It can also point to a [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="bf34e-121">出力時には、返された `CLR_DEBUGGING_VERSION` 構造体に CLR のバージョン情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="bf34e-121">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="bf34e-122">入出力指定されたランタイムに関する情報フラグ。</span><span class="sxs-lookup"><span data-stu-id="bf34e-122">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="bf34e-123">フラグの説明については、 [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf34e-123">See the [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf34e-124">戻り値</span><span class="sxs-lookup"><span data-stu-id="bf34e-124">Return Value</span></span>  

 <span data-ttu-id="bf34e-125">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="bf34e-125">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bf34e-126">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bf34e-126">HRESULT</span></span>|<span data-ttu-id="bf34e-127">説明</span><span class="sxs-lookup"><span data-stu-id="bf34e-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf34e-128">S_OK</span><span class="sxs-lookup"><span data-stu-id="bf34e-128">S_OK</span></span>|<span data-ttu-id="bf34e-129">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="bf34e-129">The method completed successfully.</span></span>|  
|<span data-ttu-id="bf34e-130">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="bf34e-130">E_POINTER</span></span>|<span data-ttu-id="bf34e-131">`pDataTarget` が `null`です。</span><span class="sxs-lookup"><span data-stu-id="bf34e-131">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="bf34e-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="bf34e-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="bf34e-133">[ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)コールバックによってエラーが返されたか、有効なハンドルが提供されていません。</span><span class="sxs-lookup"><span data-stu-id="bf34e-133">The [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="bf34e-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="bf34e-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="bf34e-135">`pDataTarget` は、このバージョンのランタイムに必要なデータターゲットインターフェイスを実装していません。</span><span class="sxs-lookup"><span data-stu-id="bf34e-135">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="bf34e-136">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="bf34e-136">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="bf34e-137">指定されたモジュールは CLR モジュールではありません。</span><span class="sxs-lookup"><span data-stu-id="bf34e-137">The indicated module is not a CLR module.</span></span> <span data-ttu-id="bf34e-138">この HRESULT は、メモリが破損している、モジュールが使用できない、または CLR バージョンが shim バージョンより後であるために CLR モジュールが検出できない場合にも返されます。</span><span class="sxs-lookup"><span data-stu-id="bf34e-138">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="bf34e-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="bf34e-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="bf34e-140">このランタイムバージョンでは、このデバッグモデルはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="bf34e-140">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="bf34e-141">現時点では、.NET Framework 4 より前のバージョンの CLR では、デバッグモデルはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="bf34e-141">Currently, the debugging model is not supported by CLR versions before the .NET Framework 4.</span></span> <span data-ttu-id="bf34e-142">`pwszVersion`このエラーが発生すると、出力パラメーターは正しい値に設定されたままになります。</span><span class="sxs-lookup"><span data-stu-id="bf34e-142">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="bf34e-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="bf34e-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="bf34e-144">CLR のバージョンが、このデバッガーがサポートするために要求するバージョンよりも大きくなっています。</span><span class="sxs-lookup"><span data-stu-id="bf34e-144">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="bf34e-145">`pwszVersion`このエラーが発生すると、出力パラメーターは正しい値に設定されたままになります。</span><span class="sxs-lookup"><span data-stu-id="bf34e-145">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="bf34e-146">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="bf34e-146">E_NO_INTERFACE</span></span>|<span data-ttu-id="bf34e-147">`riidProcess`インターフェイスは使用できません。</span><span class="sxs-lookup"><span data-stu-id="bf34e-147">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="bf34e-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="bf34e-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="bf34e-149">`CLR_DEBUGGING_VERSION`構造体に、の認識された値がありません `wStructVersion` 。</span><span class="sxs-lookup"><span data-stu-id="bf34e-149">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="bf34e-150">現時点で許容される値は0のみです。</span><span class="sxs-lookup"><span data-stu-id="bf34e-150">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="bf34e-151">例外</span><span class="sxs-lookup"><span data-stu-id="bf34e-151">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf34e-152">解説</span><span class="sxs-lookup"><span data-stu-id="bf34e-152">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf34e-153">必要条件</span><span class="sxs-lookup"><span data-stu-id="bf34e-153">Requirements</span></span>  

 <span data-ttu-id="bf34e-154">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf34e-154">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf34e-155">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf34e-155">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf34e-156">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf34e-156">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf34e-157">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf34e-157">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf34e-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf34e-158">See also</span></span>

- [<span data-ttu-id="bf34e-159">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="bf34e-159">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="bf34e-160">デバッグ</span><span class="sxs-lookup"><span data-stu-id="bf34e-160">Debugging</span></span>](index.md)
