---
title: ICorProfilerCallback::RemotingClientSendingMessage メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientSendingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type:
- apiref
ms.openlocfilehash: 2ef8f066831df1437bd0b6a6f155dd459cae1eb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676843"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="92b6b-102">ICorProfilerCallback::RemotingClientSendingMessage メソッド</span><span class="sxs-lookup"><span data-stu-id="92b6b-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>

<span data-ttu-id="92b6b-103">クライアントがサーバーに要求を送信していることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="92b6b-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92b6b-104">構文</span><span class="sxs-lookup"><span data-stu-id="92b6b-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92b6b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="92b6b-105">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="92b6b-106">から次の条件下で [ICorProfilerCallback:: RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) で指定された値に対応する値。</span><span class="sxs-lookup"><span data-stu-id="92b6b-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="92b6b-107">リモート処理 GUID クッキーはアクティブです。</span><span class="sxs-lookup"><span data-stu-id="92b6b-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="92b6b-108">チャネルは、メッセージの送信に成功します。</span><span class="sxs-lookup"><span data-stu-id="92b6b-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="92b6b-109">GUID クッキーはサーバー側のプロセスでアクティブです。</span><span class="sxs-lookup"><span data-stu-id="92b6b-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="92b6b-110">これにより、リモート処理呼び出しと論理呼び出し履歴の作成を簡単に組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="92b6b-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="92b6b-111">から `true` 呼び出しが非同期の場合は、それ以外の場合はとなる `false` 値。</span><span class="sxs-lookup"><span data-stu-id="92b6b-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92b6b-112">要件</span><span class="sxs-lookup"><span data-stu-id="92b6b-112">Requirements</span></span>  

 <span data-ttu-id="92b6b-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92b6b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92b6b-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="92b6b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92b6b-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92b6b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92b6b-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92b6b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b6b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="92b6b-117">See also</span></span>

- [<span data-ttu-id="92b6b-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="92b6b-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
