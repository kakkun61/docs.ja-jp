---
title: ISymUnmanagedSourceServerModule::GetSourceServerData メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
ms.openlocfilehash: c76c8b23e707b530cbf1c28d03fbf2f84d424482
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734011"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="c41da-102">ISymUnmanagedSourceServerModule::GetSourceServerData メソッド</span><span class="sxs-lookup"><span data-stu-id="c41da-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>

<span data-ttu-id="c41da-103">モジュールのソースサーバーデータを返します。</span><span class="sxs-lookup"><span data-stu-id="c41da-103">Returns the source server data for the module.</span></span> <span data-ttu-id="c41da-104">呼び出し元は、を使用してリソースを解放する必要があり `CoTaskMemFree` ます。</span><span class="sxs-lookup"><span data-stu-id="c41da-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c41da-105">構文</span><span class="sxs-lookup"><span data-stu-id="c41da-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c41da-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c41da-106">Parameters</span></span>  

 `pDataByteCount`  
 <span data-ttu-id="c41da-107">入出力 `ULONG32` 転送元サーバーのデータのサイズ (バイト単位) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c41da-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="c41da-108">入出力戻り値へのポインター `pDataByteCount` 。</span><span class="sxs-lookup"><span data-stu-id="c41da-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c41da-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="c41da-109">Return Value</span></span>  

 <span data-ttu-id="c41da-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="c41da-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c41da-111">要件</span><span class="sxs-lookup"><span data-stu-id="c41da-111">Requirements</span></span>  

 <span data-ttu-id="c41da-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="c41da-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c41da-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c41da-113">See also</span></span>

- [<span data-ttu-id="c41da-114">ISymUnmanagedSourceServerModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c41da-114">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)
