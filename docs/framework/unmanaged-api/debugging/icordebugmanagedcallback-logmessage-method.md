---
title: ICorDebugManagedCallback::LogMessage メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
ms.openlocfilehash: 92b2a7f7f1dd98f0d847119a6431e3816c16d5da
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679573"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="08008-102">ICorDebugManagedCallback::LogMessage メソッド</span><span class="sxs-lookup"><span data-stu-id="08008-102">ICorDebugManagedCallback::LogMessage Method</span></span>

<span data-ttu-id="08008-103">共通言語ランタイム (CLR) マネージスレッドが、 <xref:System.Diagnostics.EventLog> イベントを記録するためにクラスのメソッドを呼び出したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="08008-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08008-104">構文</span><span class="sxs-lookup"><span data-stu-id="08008-104">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08008-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="08008-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="08008-106">からイベントを記録したマネージスレッドを含むアプリケーションドメインを表す、コードのオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="08008-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="08008-107">からマネージスレッドを表す、コードスレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="08008-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="08008-108">からイベントログに書き込まれた説明メッセージの重大度レベルを示す、ログ記録 [Levelenum](logginglevelenum-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="08008-108">[in] A value of the [LoggingLevelEnum](logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="08008-109">からトレーススイッチの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="08008-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="08008-110">からイベントログに書き込まれたメッセージへのポインター。</span><span class="sxs-lookup"><span data-stu-id="08008-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08008-111">要件</span><span class="sxs-lookup"><span data-stu-id="08008-111">Requirements</span></span>  

 <span data-ttu-id="08008-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08008-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08008-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08008-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08008-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08008-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08008-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08008-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08008-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="08008-116">See also</span></span>

- [<span data-ttu-id="08008-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08008-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
