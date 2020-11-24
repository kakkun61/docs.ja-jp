---
title: ICorDebugManagedCallback2::Exception メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
ms.openlocfilehash: c5be9231bcd5aaddfa0cf1b0051f8e1184faef04
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687633"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="86ff9-102">ICorDebugManagedCallback2::Exception メソッド</span><span class="sxs-lookup"><span data-stu-id="86ff9-102">ICorDebugManagedCallback2::Exception Method</span></span>

<span data-ttu-id="86ff9-103">例外ハンドラーの検索が開始されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="86ff9-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86ff9-104">構文</span><span class="sxs-lookup"><span data-stu-id="86ff9-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86ff9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="86ff9-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="86ff9-106">から例外がスローされたスレッドを含むアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="86ff9-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="86ff9-107">から例外がスローされたスレッドを表す、スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="86ff9-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="86ff9-108">からパラメーターによって決定される、フレームを表すテキストボックスオブジェクトへのポインター `dwEventType` 。</span><span class="sxs-lookup"><span data-stu-id="86ff9-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="86ff9-109">詳細については、「解説」の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86ff9-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="86ff9-110">からパラメーターによって決定されるオフセットを指定する整数 `dwEventType` 。</span><span class="sxs-lookup"><span data-stu-id="86ff9-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="86ff9-111">詳細については、「解説」の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86ff9-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="86ff9-112">からこの例外コールバックの種類を指定する Cordebugexceptioncallback Type 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="86ff9-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="86ff9-113">から例外に関する追加情報を指定する [Cordebugexceptionflags](cordebugexceptionflags-enumeration.md) 列挙値</span><span class="sxs-lookup"><span data-stu-id="86ff9-113">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86ff9-114">注釈</span><span class="sxs-lookup"><span data-stu-id="86ff9-114">Remarks</span></span>  

 <span data-ttu-id="86ff9-115">`Exception`コールバックは、例外処理プロセスの検索フェーズ中にさまざまなポイントで呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="86ff9-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="86ff9-116">つまり、例外のアンワインド中に複数回呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="86ff9-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="86ff9-117">処理されている例外は、パラメーターによって参照されているスレッドオブジェクトから取得でき `pThread` ます。</span><span class="sxs-lookup"><span data-stu-id="86ff9-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="86ff9-118">特定のフレームとオフセットは、パラメーターによって次のように決定され `dwEventType` ます。</span><span class="sxs-lookup"><span data-stu-id="86ff9-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="86ff9-119">`dwEventType` の値</span><span class="sxs-lookup"><span data-stu-id="86ff9-119">Value of `dwEventType`</span></span>|<span data-ttu-id="86ff9-120">`pFrame` の値</span><span class="sxs-lookup"><span data-stu-id="86ff9-120">Value of `pFrame`</span></span>|<span data-ttu-id="86ff9-121">`nOffset` の値</span><span class="sxs-lookup"><span data-stu-id="86ff9-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="86ff9-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="86ff9-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="86ff9-123">例外をスローしたフレーム。</span><span class="sxs-lookup"><span data-stu-id="86ff9-123">The frame that threw the exception.</span></span>|<span data-ttu-id="86ff9-124">フレーム内の命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="86ff9-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="86ff9-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="86ff9-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="86ff9-126">スローされた例外のポイントに最も近いユーザーコードフレーム。</span><span class="sxs-lookup"><span data-stu-id="86ff9-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="86ff9-127">フレーム内の命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="86ff9-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="86ff9-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="86ff9-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="86ff9-129">Catch ハンドラーを格納しているフレーム。</span><span class="sxs-lookup"><span data-stu-id="86ff9-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="86ff9-130">Catch ハンドラーの先頭の MSIL (Microsoft 中間言語) オフセット。</span><span class="sxs-lookup"><span data-stu-id="86ff9-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="86ff9-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="86ff9-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="86ff9-132">NULL</span><span class="sxs-lookup"><span data-stu-id="86ff9-132">NULL</span></span>|<span data-ttu-id="86ff9-133">未定義です。</span><span class="sxs-lookup"><span data-stu-id="86ff9-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86ff9-134">要件</span><span class="sxs-lookup"><span data-stu-id="86ff9-134">Requirements</span></span>  

 <span data-ttu-id="86ff9-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86ff9-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86ff9-136">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86ff9-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86ff9-137">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86ff9-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86ff9-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86ff9-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86ff9-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="86ff9-139">See also</span></span>

- [<span data-ttu-id="86ff9-140">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="86ff9-140">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="86ff9-141">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="86ff9-141">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
