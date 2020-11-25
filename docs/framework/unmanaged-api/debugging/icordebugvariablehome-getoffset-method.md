---
title: 'いい変数 Home:: GetOffset メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
ms.openlocfilehash: c5d491b66e4ec64dffa4e19dabff876c9c473036
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711794"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="a8f53-102">いい変数 Home:: GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="a8f53-102">ICorDebugVariableHome::GetOffset Method</span></span>

<span data-ttu-id="a8f53-103">変数の基本レジスタからのオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="a8f53-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8f53-104">構文</span><span class="sxs-lookup"><span data-stu-id="a8f53-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8f53-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a8f53-105">Parameters</span></span>  

 `pOffset`  
 <span data-ttu-id="a8f53-106">入出力基本レジスタからのオフセット。</span><span class="sxs-lookup"><span data-stu-id="a8f53-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8f53-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="a8f53-107">Return Value</span></span>  

 <span data-ttu-id="a8f53-108">メソッドは、次の値を返します。</span><span class="sxs-lookup"><span data-stu-id="a8f53-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="a8f53-109">値</span><span class="sxs-lookup"><span data-stu-id="a8f53-109">Value</span></span>|<span data-ttu-id="a8f53-110">説明</span><span class="sxs-lookup"><span data-stu-id="a8f53-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="a8f53-111">変数は、レジスタ相対メモリの場所にあります。</span><span class="sxs-lookup"><span data-stu-id="a8f53-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="a8f53-112">変数がレジスタ相対メモリ位置にありません。</span><span class="sxs-lookup"><span data-stu-id="a8f53-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a8f53-113">要件</span><span class="sxs-lookup"><span data-stu-id="a8f53-113">Requirements</span></span>  

 <span data-ttu-id="a8f53-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8f53-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8f53-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8f53-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8f53-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8f53-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8f53-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8f53-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8f53-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8f53-118">See also</span></span>

- [<span data-ttu-id="a8f53-119">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a8f53-119">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
