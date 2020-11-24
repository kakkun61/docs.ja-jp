---
title: CorMarkThreadInThreadPool 関数
ms.date: 03/30/2017
api_name:
- CorMarkThreadInThreadPool
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorMarkThreadInThreadPool
helpviewer_keywords:
- CorMarkThreadInThreadPool function [.NET Framework hosting]
ms.assetid: 3f958d41-e82e-4ec3-ae6f-16c7b3b31e3e
topic_type:
- apiref
ms.openlocfilehash: 69508e1ccab2e7aa98f33bf048ccfca5e6f70811
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688017"
---
# <a name="cormarkthreadinthreadpool-function"></a><span data-ttu-id="3dfa9-102">CorMarkThreadInThreadPool 関数</span><span class="sxs-lookup"><span data-stu-id="3dfa9-102">CorMarkThreadInThreadPool Function</span></span>

<span data-ttu-id="3dfa9-103">現在実行されているスレッド プールのスレッドに、マネージド コードの実行のマークを付けます。</span><span class="sxs-lookup"><span data-stu-id="3dfa9-103">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="3dfa9-104">.NET Framework Version 2.0 以降では、この関数に効力はありません。</span><span class="sxs-lookup"><span data-stu-id="3dfa9-104">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="3dfa9-105">必ずしも必要はありませんが、この関数はコードから削除できます。</span><span class="sxs-lookup"><span data-stu-id="3dfa9-105">It is not required, and can be removed from your code.</span></span> <span data-ttu-id="3dfa9-106">この関数は .NET Framework 4 では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="3dfa9-106">This function is deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dfa9-107">構文</span><span class="sxs-lookup"><span data-stu-id="3dfa9-107">Syntax</span></span>  
  
```cpp  
void CorMarkThreadInThreadPool ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="3dfa9-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="3dfa9-108">Requirements</span></span>  

 <span data-ttu-id="3dfa9-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dfa9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dfa9-110">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3dfa9-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3dfa9-111">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3dfa9-111">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3dfa9-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dfa9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dfa9-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="3dfa9-113">See also</span></span>

- [<span data-ttu-id="3dfa9-114">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="3dfa9-114">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
