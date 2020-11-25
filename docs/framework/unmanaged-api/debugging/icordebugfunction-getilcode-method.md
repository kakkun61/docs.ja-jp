---
title: ICorDebugFunction::GetILCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
ms.openlocfilehash: b7d3fbafaab6d43fa89d45855628dbd6b9ab81e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696220"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="dba48-102">ICorDebugFunction::GetILCode メソッド</span><span class="sxs-lookup"><span data-stu-id="dba48-102">ICorDebugFunction::GetILCode Method</span></span>

<span data-ttu-id="dba48-103">このオブジェクトに関連付けられている MSIL (Microsoft 中間言語) コードを表す、コードインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="dba48-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba48-104">構文</span><span class="sxs-lookup"><span data-stu-id="dba48-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dba48-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dba48-105">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="dba48-106">入出力インスタンスへのポインター。 `ICorDebugCode` 関数が MSIL にコンパイルされなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="dba48-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dba48-107">注釈</span><span class="sxs-lookup"><span data-stu-id="dba48-107">Remarks</span></span>  

 <span data-ttu-id="dba48-108">この関数でエディットコンティニュが許可されている場合、メソッドは、 `GetILCode` 共通言語ランタイム (CLR) で、この関数の編集されたバージョンのコードに対応する MSIL コードを取得します。</span><span class="sxs-lookup"><span data-stu-id="dba48-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dba48-109">要件</span><span class="sxs-lookup"><span data-stu-id="dba48-109">Requirements</span></span>  

 <span data-ttu-id="dba48-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dba48-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dba48-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dba48-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dba48-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dba48-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dba48-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dba48-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
