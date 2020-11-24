---
title: _EFN_GetManagedExcepStack 関数
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
ms.openlocfilehash: b86277836b1be48c9f8020d59071aba8c5b1e457
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676232"
---
# <a name="_efn_getmanagedexcepstack-function"></a><span data-ttu-id="74280-102">\_EFN \_ getmanagedexcepstack 関数</span><span class="sxs-lookup"><span data-stu-id="74280-102">\_EFN\_GetManagedExcepStack Function</span></span>

<span data-ttu-id="74280-103">指定したマネージド例外オブジェクトのアドレスに応じて、中に含まれているスタック トレースの文字列バージョンを返します。</span><span class="sxs-lookup"><span data-stu-id="74280-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74280-104">構文</span><span class="sxs-lookup"><span data-stu-id="74280-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74280-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="74280-105">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="74280-106">からデバッグ中のクライアント。</span><span class="sxs-lookup"><span data-stu-id="74280-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="74280-107">からから派生したマネージオブジェクトポインター <xref:System.Exception> 。</span><span class="sxs-lookup"><span data-stu-id="74280-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="74280-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="74280-108">szStackString</span></span>  
 <span data-ttu-id="74280-109">入出力返された文字列。</span><span class="sxs-lookup"><span data-stu-id="74280-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="74280-110">入出力文字列バッファーで使用できる文字数。</span><span class="sxs-lookup"><span data-stu-id="74280-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74280-111">注釈</span><span class="sxs-lookup"><span data-stu-id="74280-111">Remarks</span></span>  

 <span data-ttu-id="74280-112">現在コンテキスト内にあるスレッドにマネージコードがない場合、関数は、ファシリティ値が0xa0 でエラーコードが0x1000 の HRESULT SOS_E_NOMANAGEDCODE を返します。</span><span class="sxs-lookup"><span data-stu-id="74280-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74280-113">要件</span><span class="sxs-lookup"><span data-stu-id="74280-113">Requirements</span></span>  

 <span data-ttu-id="74280-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74280-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74280-115">**ヘッダー:** SOS_Stacktrace</span><span class="sxs-lookup"><span data-stu-id="74280-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="74280-116">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74280-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74280-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="74280-117">See also</span></span>

- [<span data-ttu-id="74280-118">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="74280-118">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
