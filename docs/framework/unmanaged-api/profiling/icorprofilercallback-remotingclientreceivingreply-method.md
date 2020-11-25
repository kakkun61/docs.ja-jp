---
title: ICorProfilerCallback::RemotingClientReceivingReply メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
ms.openlocfilehash: 058c66af85da6c902e3d628e1b1479bb88c4fa85
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704852"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="f32f5-102">ICorProfilerCallback::RemotingClientReceivingReply メソッド</span><span class="sxs-lookup"><span data-stu-id="f32f5-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>

<span data-ttu-id="f32f5-103">リモート処理呼び出しのサーバー側の部分が完了し、クライアントが応答を受信および処理するようになったことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="f32f5-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f32f5-104">構文</span><span class="sxs-lookup"><span data-stu-id="f32f5-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a><span data-ttu-id="f32f5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f32f5-105">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="f32f5-106">から次の条件下で [ICorProfilerCallback:: RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) で指定された値に対応する値。</span><span class="sxs-lookup"><span data-stu-id="f32f5-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="f32f5-107">リモート処理 GUID クッキーはアクティブです。</span><span class="sxs-lookup"><span data-stu-id="f32f5-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="f32f5-108">チャネルは、メッセージの送信に成功します。</span><span class="sxs-lookup"><span data-stu-id="f32f5-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="f32f5-109">GUID クッキーはサーバー側のプロセスでアクティブです。</span><span class="sxs-lookup"><span data-stu-id="f32f5-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="f32f5-110">これにより、リモート処理呼び出しを簡単に組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="f32f5-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="f32f5-111">から `true` 呼び出しが非同期の場合は、それ以外の場合はとなる `false` 値。</span><span class="sxs-lookup"><span data-stu-id="f32f5-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f32f5-112">要件</span><span class="sxs-lookup"><span data-stu-id="f32f5-112">Requirements</span></span>  

 <span data-ttu-id="f32f5-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f32f5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f32f5-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f32f5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f32f5-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f32f5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f32f5-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f32f5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f32f5-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f32f5-117">See also</span></span>

- [<span data-ttu-id="f32f5-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f32f5-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
