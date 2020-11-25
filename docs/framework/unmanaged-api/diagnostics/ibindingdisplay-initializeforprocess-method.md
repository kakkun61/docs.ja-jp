---
title: IBindingDisplay::InitializeForProcess メソッド
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
ms.openlocfilehash: f9e65b49c9a3b506cba3493d81a40f2759dca781
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725149"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="60f94-102">IBindingDisplay::InitializeForProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="60f94-102">IBindingDisplay::InitializeForProcess Method</span></span>

<span data-ttu-id="60f94-103">[IBindingDisplay](ibindingdisplay-interface.md)オブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="60f94-103">Initializes the [IBindingDisplay](ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60f94-104">構文</span><span class="sxs-lookup"><span data-stu-id="60f94-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60f94-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60f94-105">Parameters</span></span>  

 `pid`  
 <span data-ttu-id="60f94-106">からプロセス識別子。</span><span class="sxs-lookup"><span data-stu-id="60f94-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60f94-107">注釈</span><span class="sxs-lookup"><span data-stu-id="60f94-107">Remarks</span></span>  

 <span data-ttu-id="60f94-108">デバッガーは、 `InitializeForProcess` 作成時にメソッドを呼び出して、バインド表示を初期化します。</span><span class="sxs-lookup"><span data-stu-id="60f94-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="60f94-109">`InitializeForProcess` の他のメソッドが呼び出される前に、作成時にを呼び出す必要があり `IBindingDisplay` ます。</span><span class="sxs-lookup"><span data-stu-id="60f94-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60f94-110">要件</span><span class="sxs-lookup"><span data-stu-id="60f94-110">Requirements</span></span>  

 <span data-ttu-id="60f94-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60f94-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60f94-112">**ヘッダー:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="60f94-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="60f94-113">**ライブラリ:** BindingDisplay .idl</span><span class="sxs-lookup"><span data-stu-id="60f94-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="60f94-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60f94-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60f94-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="60f94-115">See also</span></span>

- [<span data-ttu-id="60f94-116">IBindingDisplay インターフェイス</span><span class="sxs-lookup"><span data-stu-id="60f94-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
