---
title: ICorDebugGuidToTypeEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
ms.openlocfilehash: 68f548705213da7d715ae569116abae0cd24129d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705658"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="3c504-102">ICorDebugGuidToTypeEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="3c504-102">ICorDebugGuidToTypeEnum::Next Method</span></span>

<span data-ttu-id="3c504-103">Guid を型情報にマップする、指定された数の [Cordebugguidtotypemapping](cordebugguidtotypemapping-structure.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="3c504-103">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c504-104">構文</span><span class="sxs-lookup"><span data-stu-id="3c504-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c504-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3c504-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="3c504-106">から取得する GUID から型へのマッピングオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="3c504-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="3c504-107">入出力ポインターの配列。それぞれのポインターが [Cordebugguidtotypemapping](cordebugguidtotypemapping-structure.md) オブジェクトを指します。これは、Windows ランタイム GUID を対応するテキストオブジェクトにマップします。</span><span class="sxs-lookup"><span data-stu-id="3c504-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3c504-108">入出力実際にで返される [Cordebugguidtotypemapping](cordebugguidtotypemapping-structure.md) オブジェクトの数へのポインター `values` 。</span><span class="sxs-lookup"><span data-stu-id="3c504-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c504-109">解説</span><span class="sxs-lookup"><span data-stu-id="3c504-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c504-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="3c504-110">Requirements</span></span>  

 <span data-ttu-id="3c504-111">**プラットフォーム:** Windows ランタイム</span><span class="sxs-lookup"><span data-stu-id="3c504-111">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="3c504-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c504-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c504-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c504-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c504-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c504-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c504-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c504-115">See also</span></span>

- [<span data-ttu-id="3c504-116">ICorDebugGuidToTypeEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c504-116">ICorDebugGuidToTypeEnum Interface</span></span>](icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="3c504-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c504-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
