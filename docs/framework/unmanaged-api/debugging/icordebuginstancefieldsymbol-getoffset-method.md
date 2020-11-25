---
title: ICorDebugInstanceFieldSymbol::GetOffset メソッド
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 2d73de46bbb1023f20dd9023076630611c74be5d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724924"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="829bd-102">ICorDebugInstanceFieldSymbol::GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="829bd-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>

<span data-ttu-id="829bd-103">このインスタンス フィールドの親クラスにおける、このインスタンス フィールドのオフセット (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="829bd-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="829bd-104">構文</span><span class="sxs-lookup"><span data-stu-id="829bd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="829bd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="829bd-105">Parameters</span></span>  

 `pcbOffset`  
 <span data-ttu-id="829bd-106">このインスタンス フィールドの親クラスにおける、このフィールドのオフセットのバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="829bd-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="829bd-107">注釈</span><span class="sxs-lookup"><span data-stu-id="829bd-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="829bd-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="829bd-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="829bd-109">要件</span><span class="sxs-lookup"><span data-stu-id="829bd-109">Requirements</span></span>  

 <span data-ttu-id="829bd-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="829bd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="829bd-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="829bd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="829bd-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="829bd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="829bd-113">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="829bd-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="829bd-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="829bd-114">See also</span></span>

- [<span data-ttu-id="829bd-115">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="829bd-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="829bd-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="829bd-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
