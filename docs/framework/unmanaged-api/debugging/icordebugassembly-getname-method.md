---
title: ICorDebugAssembly::GetName メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type:
- apiref
ms.openlocfilehash: 3794a3b308bd5c96a38337d8b81e61167e4dc988
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734050"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="be091-102">ICorDebugAssembly::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="be091-102">ICorDebugAssembly::GetName Method</span></span>

<span data-ttu-id="be091-103">このインスタンスが表すアセンブリの名前を取得し `ICorDebugAssembly` ます。</span><span class="sxs-lookup"><span data-stu-id="be091-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be091-104">構文</span><span class="sxs-lookup"><span data-stu-id="be091-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be091-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="be091-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="be091-106">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="be091-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="be091-107">入出力名前の実際の長さを指定する整数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="be091-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="be091-108">入出力名前を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="be091-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be091-109">注釈</span><span class="sxs-lookup"><span data-stu-id="be091-109">Remarks</span></span>  

 <span data-ttu-id="be091-110">メソッドは、 `GetName` アセンブリの完全なパスとファイル名を返します。</span><span class="sxs-lookup"><span data-stu-id="be091-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be091-111">要件</span><span class="sxs-lookup"><span data-stu-id="be091-111">Requirements</span></span>  

 <span data-ttu-id="be091-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be091-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be091-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be091-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be091-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be091-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be091-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be091-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
