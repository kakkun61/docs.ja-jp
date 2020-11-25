---
title: ISymUnmanagedNamespace::GetName メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
ms.openlocfilehash: eca1137fb607d64e8645de5b0afc7ca391eac763
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699262"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="61cf5-102">ISymUnmanagedNamespace::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="61cf5-102">ISymUnmanagedNamespace::GetName Method</span></span>

<span data-ttu-id="61cf5-103">この名前空間の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="61cf5-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61cf5-104">構文</span><span class="sxs-lookup"><span data-stu-id="61cf5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61cf5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="61cf5-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="61cf5-106">から `ULONG32` バッファーのサイズを示す `szName` 。</span><span class="sxs-lookup"><span data-stu-id="61cf5-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="61cf5-107">入出力 `ULONG32` Null 終了を含む、名前空間の名前を格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="61cf5-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="61cf5-108">入出力名前空間の名前を格納しているバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="61cf5-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61cf5-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="61cf5-109">Return Value</span></span>  

 <span data-ttu-id="61cf5-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="61cf5-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61cf5-111">要件</span><span class="sxs-lookup"><span data-stu-id="61cf5-111">Requirements</span></span>  

 <span data-ttu-id="61cf5-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="61cf5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61cf5-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="61cf5-113">See also</span></span>

- [<span data-ttu-id="61cf5-114">ISymUnmanagedNamespace インターフェイス</span><span class="sxs-lookup"><span data-stu-id="61cf5-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
