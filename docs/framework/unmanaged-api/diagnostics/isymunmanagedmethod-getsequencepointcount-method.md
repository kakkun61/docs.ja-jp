---
title: ISymUnmanagedMethod::GetSequencePointCount メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePointCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type:
- apiref
ms.openlocfilehash: 44472c7beff72d24853b7fb9865071a9b15ef0e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699431"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="d3574-102">ISymUnmanagedMethod::GetSequencePointCount メソッド</span><span class="sxs-lookup"><span data-stu-id="d3574-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>

<span data-ttu-id="d3574-103">このメソッド内のシーケンスポイントの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="d3574-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3574-104">構文</span><span class="sxs-lookup"><span data-stu-id="d3574-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3574-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3574-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="d3574-106">入出力 `ULONG32` シーケンスポイントを格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3574-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3574-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3574-107">Return Value</span></span>  

 <span data-ttu-id="d3574-108">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="d3574-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3574-109">要件</span><span class="sxs-lookup"><span data-stu-id="d3574-109">Requirements</span></span>  

 <span data-ttu-id="d3574-110">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="d3574-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3574-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3574-111">See also</span></span>

- [<span data-ttu-id="d3574-112">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d3574-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
