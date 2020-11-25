---
title: ICorDebugAssembly3::EnumerateContainedAssemblies メソッド
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 1e040453d5eb7a312f2e665974486492b99de16d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719685"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="f7be1-102">ICorDebugAssembly3::EnumerateContainedAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="f7be1-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>

<span data-ttu-id="f7be1-103">このアセンブリに含まれているアセンブリの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="f7be1-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7be1-104">構文</span><span class="sxs-lookup"><span data-stu-id="f7be1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7be1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f7be1-105">Parameters</span></span>  

 `ppAssemblies`  
 <span data-ttu-id="f7be1-106">[出力] 列挙子である ICorDebugAssemblyEnum インターフェイス オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f7be1-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7be1-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="f7be1-107">Return Value</span></span>  

 <span data-ttu-id="f7be1-108">この `S_OK` オブジェクトがコンテナーの場合は、`ICorDebugAssembly3`。それ以外の場合は、`S_FALSE` で、列挙子は空です。</span><span class="sxs-lookup"><span data-stu-id="f7be1-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7be1-109">注釈</span><span class="sxs-lookup"><span data-stu-id="f7be1-109">Remarks</span></span>  

 <span data-ttu-id="f7be1-110">含まれているアセンブリを列挙するためにシンボルが必要です。</span><span class="sxs-lookup"><span data-stu-id="f7be1-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="f7be1-111">シンボルがない場合、メソッドは `S_FALSE` を返し、有効な列挙子は提供されません。</span><span class="sxs-lookup"><span data-stu-id="f7be1-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7be1-112">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f7be1-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7be1-113">要件</span><span class="sxs-lookup"><span data-stu-id="f7be1-113">Requirements</span></span>  

 <span data-ttu-id="f7be1-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7be1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7be1-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7be1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7be1-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7be1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7be1-117">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7be1-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7be1-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7be1-118">See also</span></span>

- [<span data-ttu-id="f7be1-119">ICorDebugAssembly3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f7be1-119">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="f7be1-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f7be1-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
