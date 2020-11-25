---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod メソッド
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: 418a77855d1cb34a07f5957059b5a6f5a106c321
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707088"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="7a15d-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="7a15d-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>

<span data-ttu-id="7a15d-103">非同期操作を開始する開始メソッドを設定します。</span><span class="sxs-lookup"><span data-stu-id="7a15d-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a15d-104">構文</span><span class="sxs-lookup"><span data-stu-id="7a15d-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a15d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7a15d-105">Parameters</span></span>  
  
|<span data-ttu-id="7a15d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7a15d-106">Parameter</span></span>|<span data-ttu-id="7a15d-107">説明</span><span class="sxs-lookup"><span data-stu-id="7a15d-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="7a15d-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="7a15d-108">Return Value</span></span>  

 <span data-ttu-id="7a15d-109">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="7a15d-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a15d-110">要件</span><span class="sxs-lookup"><span data-stu-id="7a15d-110">Requirements</span></span>  

 <span data-ttu-id="7a15d-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="7a15d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a15d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a15d-112">See also</span></span>

- [<span data-ttu-id="7a15d-113">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a15d-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
