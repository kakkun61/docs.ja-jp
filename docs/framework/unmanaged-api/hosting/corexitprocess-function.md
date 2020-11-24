---
title: CorExitProcess 関数
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
ms.openlocfilehash: f6d8114732a3b7c15d0a0258a28a362d661b030a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673629"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="13657-102">CorExitProcess 関数</span><span class="sxs-lookup"><span data-stu-id="13657-102">CorExitProcess Function</span></span>

<span data-ttu-id="13657-103">現在のアンマネージ プロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="13657-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="13657-104">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="13657-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="13657-105">代わりに [ICLRMetaHost:: ExitProcess](iclrmetahost-exitprocess-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="13657-105">Use the [ICLRMetaHost::ExitProcess](iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13657-106">構文</span><span class="sxs-lookup"><span data-stu-id="13657-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13657-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="13657-107">Parameters</span></span>  

 `exitCode`  
 <span data-ttu-id="13657-108">プロセス終了コードを指定する整数です。</span><span class="sxs-lookup"><span data-stu-id="13657-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13657-109">注釈</span><span class="sxs-lookup"><span data-stu-id="13657-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13657-110">.NET Framework 4 以降では、 `CorExitProcess` レガシ api がバインドされているランタイムだけでなく、プロセスで開始されたすべてのランタイムを終了します。</span><span class="sxs-lookup"><span data-stu-id="13657-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13657-111">要件</span><span class="sxs-lookup"><span data-stu-id="13657-111">Requirements</span></span>  

 <span data-ttu-id="13657-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13657-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13657-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="13657-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13657-114">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13657-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13657-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13657-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13657-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="13657-116">See also</span></span>

- [<span data-ttu-id="13657-117">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="13657-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
