---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset メソッド
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: a37d319a39b959700944f9e111d2945e286c99ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707140"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="10f45-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="10f45-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>

<span data-ttu-id="10f45-103">非同期メソッドをラップする、コンパイラによって生成される catch ハンドラーの IL オフセットを設定します。</span><span class="sxs-lookup"><span data-stu-id="10f45-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="10f45-104">生成された catch の IL オフセットは、ユーザーコードメソッドで発生する可能性があっても、ユーザーコード以外のコードであると仮定して、catch を処理するためにデバッガーによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="10f45-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="10f45-105">特に、 **CatchHandlerFound** exception イベントに応答して使用されます。</span><span class="sxs-lookup"><span data-stu-id="10f45-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10f45-106">構文</span><span class="sxs-lookup"><span data-stu-id="10f45-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10f45-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="10f45-107">Parameters</span></span>  
  
|<span data-ttu-id="10f45-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="10f45-108">Parameter</span></span>|<span data-ttu-id="10f45-109">説明</span><span class="sxs-lookup"><span data-stu-id="10f45-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="10f45-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="10f45-110">Return Value</span></span>  

 <span data-ttu-id="10f45-111">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="10f45-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10f45-112">要件</span><span class="sxs-lookup"><span data-stu-id="10f45-112">Requirements</span></span>  

 <span data-ttu-id="10f45-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="10f45-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10f45-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="10f45-114">See also</span></span>

- [<span data-ttu-id="10f45-115">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10f45-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
