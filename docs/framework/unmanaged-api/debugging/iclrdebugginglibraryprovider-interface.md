---
title: ICLRDebuggingLibraryProvider インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider
helpviewer_keywords:
- ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type:
- apiref
ms.openlocfilehash: cd17cbc808b7f8381ac320bb55999c6b0466c3d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723539"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="58da2-102">ICLRDebuggingLibraryProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58da2-102">ICLRDebuggingLibraryProvider Interface</span></span>

<span data-ttu-id="58da2-103">には、提供 [ライブラリのメソッド](iclrdebugginglibraryprovider-providelibrary-method.md) メソッドが含まれています。このメソッドは、共通言語ランタイムのバージョン固有のデバッグライブラリをオンデマンドで検索して読み込むことができるようにする、ライブラリプロバイダーのコールバックインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="58da2-103">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58da2-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="58da2-104">Methods</span></span>  
  
|<span data-ttu-id="58da2-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="58da2-105">Method</span></span>|<span data-ttu-id="58da2-106">説明</span><span class="sxs-lookup"><span data-stu-id="58da2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58da2-107">ProvideLibrary メソッド</span><span class="sxs-lookup"><span data-stu-id="58da2-107">ProvideLibrary Method</span></span>](iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="58da2-108">デバッガーが、デバッグライブラリの読み込みに使用できるモジュールへのハンドルを提供できるようにします。</span><span class="sxs-lookup"><span data-stu-id="58da2-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="58da2-109">要件</span><span class="sxs-lookup"><span data-stu-id="58da2-109">Requirements</span></span>  

 <span data-ttu-id="58da2-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58da2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58da2-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58da2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58da2-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58da2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58da2-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58da2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58da2-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="58da2-114">See also</span></span>

- [<span data-ttu-id="58da2-115">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="58da2-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="58da2-116">デバッグ</span><span class="sxs-lookup"><span data-stu-id="58da2-116">Debugging</span></span>](index.md)
