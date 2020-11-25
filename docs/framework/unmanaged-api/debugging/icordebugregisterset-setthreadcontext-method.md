---
title: ICorDebugRegisterSet::SetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type:
- apiref
ms.openlocfilehash: 66e8cf3f73e92f58765b1fa98b3eef11b976094c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712275"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="bfd10-102">ICorDebugRegisterSet::SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="bfd10-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>

<span data-ttu-id="bfd10-103">`SetThreadContext` は .NET Framework バージョン2.0 では実装されていません。</span><span class="sxs-lookup"><span data-stu-id="bfd10-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="bfd10-104">このメソッドは呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="bfd10-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bfd10-105">スレッドのコンテキストを設定するには、高レベルの操作の [テキストフレーム:: SetIP](icordebugnativeframe-setip-method.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="bfd10-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfd10-106">構文</span><span class="sxs-lookup"><span data-stu-id="bfd10-106">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="bfd10-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="bfd10-107">Requirements</span></span>  

 <span data-ttu-id="bfd10-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfd10-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfd10-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bfd10-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bfd10-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfd10-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfd10-111">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="bfd10-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd10-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="bfd10-112">See also</span></span>

- [<span data-ttu-id="bfd10-113">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfd10-113">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="bfd10-114">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bfd10-114">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
