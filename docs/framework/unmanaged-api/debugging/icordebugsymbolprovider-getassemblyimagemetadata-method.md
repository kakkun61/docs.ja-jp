---
title: ICorDebugSymbolProvider::GetAssemblyImageMetadata メソッド
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
ms.openlocfilehash: 9644d1323660730d210bd0305c2785fce4174455
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709142"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="4190d-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata メソッド</span><span class="sxs-lookup"><span data-stu-id="4190d-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>

<span data-ttu-id="4190d-103">マージされたアセンブリのメタデータを返します。</span><span class="sxs-lookup"><span data-stu-id="4190d-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4190d-104">構文</span><span class="sxs-lookup"><span data-stu-id="4190d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4190d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4190d-105">Parameters</span></span>  

 `ppMemoryBuffer`  
 <span data-ttu-id="4190d-106">入出力マージされたアセンブリのメタデータのサイズとアドレスに関する情報を格納して [いる、のオブジェクトの](icordebugmemorybuffer-interface.md) アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4190d-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4190d-107">注釈</span><span class="sxs-lookup"><span data-stu-id="4190d-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4190d-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4190d-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4190d-109">要件</span><span class="sxs-lookup"><span data-stu-id="4190d-109">Requirements</span></span>  

 <span data-ttu-id="4190d-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4190d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4190d-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4190d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4190d-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4190d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4190d-113">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4190d-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4190d-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="4190d-114">See also</span></span>

- [<span data-ttu-id="4190d-115">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4190d-115">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="4190d-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="4190d-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
