---
title: ISymUnmanagedENCUpdate::GetLocalVariables メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
ms.openlocfilehash: 9e907450b4ae985ee30d9958eec8baba797b495a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728603"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="811bd-102">ISymUnmanagedENCUpdate::GetLocalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="811bd-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>

<span data-ttu-id="811bd-103">ローカル変数を取得します。</span><span class="sxs-lookup"><span data-stu-id="811bd-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="811bd-104">構文</span><span class="sxs-lookup"><span data-stu-id="811bd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="811bd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="811bd-105">Parameters</span></span>  

 `mdMethodToken`  
 <span data-ttu-id="811bd-106">からメソッドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="811bd-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="811bd-107">から `ULONG` パラメーターのサイズを示す `rgLocals` 。</span><span class="sxs-lookup"><span data-stu-id="811bd-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="811bd-108">入出力返される [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) インスタンスの配列。</span><span class="sxs-lookup"><span data-stu-id="811bd-108">[out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="811bd-109">入出力 `ULONG` `rgLocals` ローカルを格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="811bd-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="811bd-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="811bd-110">Return Value</span></span>  

 <span data-ttu-id="811bd-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="811bd-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="811bd-112">要件</span><span class="sxs-lookup"><span data-stu-id="811bd-112">Requirements</span></span>  

 <span data-ttu-id="811bd-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="811bd-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="811bd-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="811bd-114">See also</span></span>

- [<span data-ttu-id="811bd-115">ISymUnmanagedENCUpdate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="811bd-115">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
