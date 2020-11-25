---
title: ICoreClrDebugTarget インターフェイス
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
ms.openlocfilehash: 791bd2754a96b97a38e2509c0c61a644324857cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716955"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="566f8-102">ICoreClrDebugTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="566f8-102">ICoreClrDebugTarget Interface</span></span>

<span data-ttu-id="566f8-103">参照カウントを制御し、プロセスを列挙し、リモートの Macintosh Silverlight ターゲットにアタッチされているデバッガーに関連付けられているメモリを解放するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="566f8-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="566f8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="566f8-104">Syntax</span></span>  
  
```cpp  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="566f8-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="566f8-105">Methods</span></span>  
  
|<span data-ttu-id="566f8-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="566f8-106">Method</span></span>|<span data-ttu-id="566f8-107">説明</span><span class="sxs-lookup"><span data-stu-id="566f8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="566f8-108">ICoreClrDebugTarget::EnumProcesses メソッド</span><span class="sxs-lookup"><span data-stu-id="566f8-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="566f8-109">リモート コンピューターで実行されているプロセスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="566f8-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="566f8-110">ICoreClrDebugTarget::EnumRuntimes メソッド</span><span class="sxs-lookup"><span data-stu-id="566f8-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="566f8-111">リモートコンピューター上の指定されたプロセスの共通言語ランタイム (CLRs) を列挙します。</span><span class="sxs-lookup"><span data-stu-id="566f8-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="566f8-112">ICoreClrDebugTarget::FreeMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="566f8-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="566f8-113">このクラスの列挙メソッドによって割り当てられたメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="566f8-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="566f8-114">注釈</span><span class="sxs-lookup"><span data-stu-id="566f8-114">Remarks</span></span>  

 <span data-ttu-id="566f8-115">現在、この機能は、リモートの Macintosh コンピューターで実行されている Silverlight ベースのアプリケーションターゲットをデバッグする場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="566f8-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="566f8-116">要件</span><span class="sxs-lookup"><span data-stu-id="566f8-116">Requirements</span></span>  

 <span data-ttu-id="566f8-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="566f8-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="566f8-118">**ヘッダー:** Coreclrremoteデバッグインターフェイス .h</span><span class="sxs-lookup"><span data-stu-id="566f8-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="566f8-119">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="566f8-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="566f8-120">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="566f8-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="566f8-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="566f8-121">See also</span></span>

- [<span data-ttu-id="566f8-122">ICorDebugRemoteTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="566f8-122">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="566f8-123">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="566f8-123">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="566f8-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="566f8-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
