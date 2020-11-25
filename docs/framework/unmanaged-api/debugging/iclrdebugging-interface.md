---
title: ICLRDebugging インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
ms.openlocfilehash: 6eea7f6c222b8e30376ec72ee0c193a68c23f0d0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723559"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="74fa3-102">ICLRDebugging インターフェイス</span><span class="sxs-lookup"><span data-stu-id="74fa3-102">ICLRDebugging Interface</span></span>

<span data-ttu-id="74fa3-103">デバッグ用にモジュールの読み込みとアンロードを処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="74fa3-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74fa3-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="74fa3-104">Methods</span></span>  
  
|<span data-ttu-id="74fa3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="74fa3-105">Method</span></span>|<span data-ttu-id="74fa3-106">説明</span><span class="sxs-lookup"><span data-stu-id="74fa3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74fa3-107">OpenVirtualProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="74fa3-107">OpenVirtualProcess Method</span></span>](iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="74fa3-108">プロセスに読み込まれた共通言語ランタイム (CLR) モジュールに対応する "のプロセス" インターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="74fa3-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="74fa3-109">CanUnloadNow メソッド</span><span class="sxs-lookup"><span data-stu-id="74fa3-109">CanUnloadNow Method</span></span>](iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="74fa3-110">[ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)インターフェイスによって提供されたライブラリがまだ使用中であるか、またはアンロードできるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="74fa3-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74fa3-111">注釈</span><span class="sxs-lookup"><span data-stu-id="74fa3-111">Remarks</span></span>  

 <span data-ttu-id="74fa3-112">インターフェイスのインスタンスを取得する `ICLRDebugging` には、 [clrcreateinstance](../hosting/clrcreateinstance-function.md) 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="74fa3-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74fa3-113">要件</span><span class="sxs-lookup"><span data-stu-id="74fa3-113">Requirements</span></span>  

 <span data-ttu-id="74fa3-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74fa3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74fa3-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74fa3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74fa3-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74fa3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74fa3-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74fa3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74fa3-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="74fa3-118">See also</span></span>

- [<span data-ttu-id="74fa3-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="74fa3-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="74fa3-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="74fa3-120">Debugging</span></span>](index.md)
