---
title: ICorDebugFunction2::EnumerateNativeCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.EnumerateNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::EnumerateNativeCode
helpviewer_keywords:
- ICorDebugFunction2::EnumerateNativeCode method [.NET Framework debugging]
- EnumerateNativeCode method [.NET Framework debugging]
ms.assetid: d383f5cc-1144-4b6d-b57a-db34d9134ab2
topic_type:
- apiref
ms.openlocfilehash: 2cac4a3120e842bde9ad708a251682421fd4ca93
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696077"
---
# <a name="icordebugfunction2enumeratenativecode-method"></a><span data-ttu-id="05af3-102">ICorDebugFunction2::EnumerateNativeCode メソッド</span><span class="sxs-lookup"><span data-stu-id="05af3-102">ICorDebugFunction2::EnumerateNativeCode Method</span></span>

<span data-ttu-id="05af3-103">この ICorDebugFunction2 オブジェクトによって参照される関数内のネイティブコードステートメントを格納している、コードのオブジェクトへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="05af3-103">Gets an interface pointer to an ICorDebugCodeEnum object that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05af3-104">`EnumerateNativeCode` は、.NET Framework の現在のバージョンでは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="05af3-104">`EnumerateNativeCode` is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05af3-105">構文</span><span class="sxs-lookup"><span data-stu-id="05af3-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="05af3-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="05af3-106">Requirements</span></span>  

 <span data-ttu-id="05af3-107">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05af3-107">**Header:** CorDebug.idl, CorDebug.h</span></span>
