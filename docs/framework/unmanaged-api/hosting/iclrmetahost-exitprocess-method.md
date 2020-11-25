---
title: ICLRMetaHost::ExitProcess メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
ms.openlocfilehash: 6d601ac3ece801353b630c74ed852c2657f25d7f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730464"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="e15cf-102">ICLRMetaHost::ExitProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="e15cf-102">ICLRMetaHost::ExitProcess Method</span></span>

<span data-ttu-id="e15cf-103">読み込まれたすべてのランタイムを正常にシャットダウンしてから、プロセスを終了しようとします。</span><span class="sxs-lookup"><span data-stu-id="e15cf-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="e15cf-104">[CorExitProcess](corexitprocess-function.md)関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="e15cf-104">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e15cf-105">構文</span><span class="sxs-lookup"><span data-stu-id="e15cf-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e15cf-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e15cf-106">Parameters</span></span>  

 `iExitCode`  
 <span data-ttu-id="e15cf-107">からプロセスの終了コード。</span><span class="sxs-lookup"><span data-stu-id="e15cf-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e15cf-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="e15cf-108">Return Value</span></span>  

 <span data-ttu-id="e15cf-109">このメソッドはを返しません。そのため、戻り値は未定義です。</span><span class="sxs-lookup"><span data-stu-id="e15cf-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e15cf-110">解説</span><span class="sxs-lookup"><span data-stu-id="e15cf-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e15cf-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="e15cf-111">Requirements</span></span>  

 <span data-ttu-id="e15cf-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e15cf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e15cf-113">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="e15cf-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e15cf-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e15cf-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e15cf-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e15cf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e15cf-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e15cf-116">See also</span></span>

- [<span data-ttu-id="e15cf-117">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e15cf-117">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="e15cf-118">ホスティング</span><span class="sxs-lookup"><span data-stu-id="e15cf-118">Hosting</span></span>](index.md)
