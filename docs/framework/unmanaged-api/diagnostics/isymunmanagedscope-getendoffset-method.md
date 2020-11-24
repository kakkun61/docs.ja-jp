---
title: ISymUnmanagedScope::GetEndOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
ms.openlocfilehash: 14e747e81e467019d464212e75513bdf98344916
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678364"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="eec09-102">ISymUnmanagedScope::GetEndOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="eec09-102">ISymUnmanagedScope::GetEndOffset Method</span></span>

<span data-ttu-id="eec09-103">このスコープの終了オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="eec09-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eec09-104">構文</span><span class="sxs-lookup"><span data-stu-id="eec09-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eec09-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eec09-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="eec09-106">入出力終了オフセットを受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="eec09-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eec09-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="eec09-107">Return Value</span></span>  

 <span data-ttu-id="eec09-108">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="eec09-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eec09-109">要件</span><span class="sxs-lookup"><span data-stu-id="eec09-109">Requirements</span></span>  

 <span data-ttu-id="eec09-110">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="eec09-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eec09-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="eec09-111">See also</span></span>

- [<span data-ttu-id="eec09-112">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eec09-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="eec09-113">GetStartOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="eec09-113">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)
