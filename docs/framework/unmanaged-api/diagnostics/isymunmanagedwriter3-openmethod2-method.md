---
title: ISymUnmanagedWriter3::OpenMethod2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
ms.openlocfilehash: 39235c5c26cb168dfc995de97f72b80dccb6b818
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720296"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="d371a-102">ISymUnmanagedWriter3::OpenMethod2 メソッド</span><span class="sxs-lookup"><span data-stu-id="d371a-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>

<span data-ttu-id="d371a-103">メソッドを開き、イメージ内の実際のセクションオフセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="d371a-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d371a-104">構文</span><span class="sxs-lookup"><span data-stu-id="d371a-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d371a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d371a-105">Parameters</span></span>  

 `method`  
 <span data-ttu-id="d371a-106">から開くメソッドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="d371a-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="d371a-107">からイメージ内のセクションオフセット。</span><span class="sxs-lookup"><span data-stu-id="d371a-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="d371a-108">からイメージ内のオフセット。</span><span class="sxs-lookup"><span data-stu-id="d371a-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d371a-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="d371a-109">Return Value</span></span>  

 <span data-ttu-id="d371a-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="d371a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d371a-111">要件</span><span class="sxs-lookup"><span data-stu-id="d371a-111">Requirements</span></span>  

 <span data-ttu-id="d371a-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="d371a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d371a-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="d371a-113">See also</span></span>

- [<span data-ttu-id="d371a-114">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d371a-114">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="d371a-115">OpenMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="d371a-115">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
