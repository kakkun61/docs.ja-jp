---
title: ICorDebugDataTarget2::GetImageFromPointer メソッド
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: 41385fe915733f052af67c82d984c8b9d853c579
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713822"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="d534d-102">ICorDebugDataTarget2::GetImageFromPointer メソッド</span><span class="sxs-lookup"><span data-stu-id="d534d-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>

<span data-ttu-id="d534d-103">モジュールのアドレスから、そのモジュールのベース アドレスとサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="d534d-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d534d-104">構文</span><span class="sxs-lookup"><span data-stu-id="d534d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,
   [out] CORDB_ADDRESS *pImageBase,
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d534d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d534d-105">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="d534d-106">モジュール内のアドレスを表す [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) 値。</span><span class="sxs-lookup"><span data-stu-id="d534d-106">A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="d534d-107">入出力モジュールのベースアドレスを表す [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) 値。</span><span class="sxs-lookup"><span data-stu-id="d534d-107">[out] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="d534d-108">モジュールのサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d534d-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d534d-109">注釈</span><span class="sxs-lookup"><span data-stu-id="d534d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d534d-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d534d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d534d-111">要件</span><span class="sxs-lookup"><span data-stu-id="d534d-111">Requirements</span></span>  

 <span data-ttu-id="d534d-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d534d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d534d-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d534d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d534d-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d534d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d534d-115">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d534d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d534d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d534d-116">See also</span></span>

- [<span data-ttu-id="d534d-117">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d534d-117">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="d534d-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d534d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
