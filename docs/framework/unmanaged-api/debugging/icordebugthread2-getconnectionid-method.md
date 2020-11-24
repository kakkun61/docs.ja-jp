---
title: ICorDebugThread2::GetConnectionID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
ms.openlocfilehash: 1507715e80761c871dfdb0b8d25dc708a2130678
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678689"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="d3d5b-102">ICorDebugThread2::GetConnectionID メソッド</span><span class="sxs-lookup"><span data-stu-id="d3d5b-102">ICorDebugThread2::GetConnectionID Method</span></span>

<span data-ttu-id="d3d5b-103">この ICorDebugThread2 オブジェクトの接続識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="d3d5b-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3d5b-104">構文</span><span class="sxs-lookup"><span data-stu-id="d3d5b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3d5b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3d5b-105">Parameters</span></span>  

 `pdwConnectionId`  
 <span data-ttu-id="d3d5b-106">入出力 `CONNID` 接続識別子を表す。</span><span class="sxs-lookup"><span data-stu-id="d3d5b-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3d5b-107">注釈</span><span class="sxs-lookup"><span data-stu-id="d3d5b-107">Remarks</span></span>  

 <span data-ttu-id="d3d5b-108">`GetConnectionID` `pdwConnectionId` このスレッドが接続の一部でない場合、このメソッドはパラメーターで0を返します。</span><span class="sxs-lookup"><span data-stu-id="d3d5b-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="d3d5b-109">このスレッドが Microsoft SQL Server 2005 Analysis Services (SSAS) のインスタンスに接続されている場合、は `CONNID` サーバープロセス識別子 (SPID) にマップされます。</span><span class="sxs-lookup"><span data-stu-id="d3d5b-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3d5b-110">要件</span><span class="sxs-lookup"><span data-stu-id="d3d5b-110">Requirements</span></span>  

 <span data-ttu-id="d3d5b-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3d5b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3d5b-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3d5b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3d5b-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3d5b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3d5b-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3d5b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
