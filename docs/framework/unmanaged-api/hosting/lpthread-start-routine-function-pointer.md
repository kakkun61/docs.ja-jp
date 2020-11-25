---
title: LPTHREAD_START_ROUTINE 関数ポインター
ms.date: 03/30/2017
api_name:
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
ms.openlocfilehash: c86b65e136869603f93253678108b2ffa9d388e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730072"
---
# <a name="lpthread_start_routine-function-pointer"></a><span data-ttu-id="01c51-102">LPTHREAD_START_ROUTINE 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="01c51-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>

<span data-ttu-id="01c51-103">スレッドの実行を開始したことをホストに通知する関数を指します。</span><span class="sxs-lookup"><span data-stu-id="01c51-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="01c51-104">この関数ポインターは .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="01c51-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01c51-105">構文</span><span class="sxs-lookup"><span data-stu-id="01c51-105">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01c51-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="01c51-106">Parameters</span></span>  

 `lpThreadParameter`  
 <span data-ttu-id="01c51-107">から実行を開始したコードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="01c51-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01c51-108">注釈</span><span class="sxs-lookup"><span data-stu-id="01c51-108">Remarks</span></span>  

 <span data-ttu-id="01c51-109">`LPTHREAD_START_ROUTINE`ポイントがコールバック関数であり、ホストアプリケーションのライターによって実装されている必要がある関数。</span><span class="sxs-lookup"><span data-stu-id="01c51-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01c51-110">要件</span><span class="sxs-lookup"><span data-stu-id="01c51-110">Requirements</span></span>  

 <span data-ttu-id="01c51-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01c51-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01c51-112">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="01c51-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01c51-113">**ライブラリ:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="01c51-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="01c51-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01c51-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01c51-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="01c51-115">See also</span></span>

- [<span data-ttu-id="01c51-116">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="01c51-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
