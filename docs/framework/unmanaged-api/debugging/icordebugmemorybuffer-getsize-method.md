---
title: ICorDebugMemoryBuffer::GetSize メソッド
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 7f5458dd12ca83c1a5190bbf7fab0f8e5d06a0e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710761"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="5a660-102">ICorDebugMemoryBuffer::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="5a660-102">ICorDebugMemoryBuffer::GetSize Method</span></span>

<span data-ttu-id="5a660-103">メモリ バッファーのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="5a660-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a660-104">構文</span><span class="sxs-lookup"><span data-stu-id="5a660-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a660-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5a660-105">Parameters</span></span>  

 `pcbBufferLength`  
 <span data-ttu-id="5a660-106">[out] メモリ バッファーのサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5a660-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a660-107">注釈</span><span class="sxs-lookup"><span data-stu-id="5a660-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a660-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="5a660-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a660-109">要件</span><span class="sxs-lookup"><span data-stu-id="5a660-109">Requirements</span></span>  

 <span data-ttu-id="5a660-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a660-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a660-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a660-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a660-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a660-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a660-113">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a660-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a660-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a660-114">See also</span></span>

- [<span data-ttu-id="5a660-115">ICorDebugMemoryBuffer インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a660-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="5a660-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a660-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
