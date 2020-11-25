---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo メソッド
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: f8c77e44183fd92704aa91ca1cfd7e3fa68aa27f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719620"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="bc0b8-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="bc0b8-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>

<span data-ttu-id="bc0b8-103">現在のメソッドで非同期 await 操作のグループを定義します。</span><span class="sxs-lookup"><span data-stu-id="bc0b8-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="bc0b8-104">各 yield オフセットは await の戻り命令に一致し、潜在的な yield を識別します。</span><span class="sxs-lookup"><span data-stu-id="bc0b8-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="bc0b8-105">各 `breakpointMethod` / `breakpointOffset` ペアは、非同期操作が再開される場所を示します。これは、別の方法で実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bc0b8-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc0b8-106">構文</span><span class="sxs-lookup"><span data-stu-id="bc0b8-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc0b8-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bc0b8-107">Parameters</span></span>  
  
|<span data-ttu-id="bc0b8-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bc0b8-108">Parameter</span></span>|<span data-ttu-id="bc0b8-109">説明</span><span class="sxs-lookup"><span data-stu-id="bc0b8-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="bc0b8-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="bc0b8-110">Return Value</span></span>  

 <span data-ttu-id="bc0b8-111">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="bc0b8-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc0b8-112">要件</span><span class="sxs-lookup"><span data-stu-id="bc0b8-112">Requirements</span></span>  

 <span data-ttu-id="bc0b8-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="bc0b8-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc0b8-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc0b8-114">See also</span></span>

- [<span data-ttu-id="bc0b8-115">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bc0b8-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
