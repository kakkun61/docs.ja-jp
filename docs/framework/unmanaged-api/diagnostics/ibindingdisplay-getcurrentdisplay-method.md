---
title: IBindingDisplay::GetCurrentDisplay メソッド
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
ms.openlocfilehash: d52f089923d16f93345444c07ff8e0619644f2eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725156"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="5ff1b-102">IBindingDisplay::GetCurrentDisplay メソッド</span><span class="sxs-lookup"><span data-stu-id="5ff1b-102">IBindingDisplay::GetCurrentDisplay Method</span></span>

<span data-ttu-id="5ff1b-103">現在のバインディング表示情報を返します。</span><span class="sxs-lookup"><span data-stu-id="5ff1b-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ff1b-104">構文</span><span class="sxs-lookup"><span data-stu-id="5ff1b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ff1b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5ff1b-105">Parameters</span></span>  

 `display`  
 <span data-ttu-id="5ff1b-106">[out, retval]バインディング表示情報を格納している safearray へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5ff1b-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ff1b-107">注釈</span><span class="sxs-lookup"><span data-stu-id="5ff1b-107">Remarks</span></span>  

 <span data-ttu-id="5ff1b-108">[IBindingDisplay:: InitializeForProcess](ibindingdisplay-initializeforprocess-method.md)メソッドが既に成功しており、プログラムがデバッガーによって停止されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ff1b-108">The [IBindingDisplay::InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="5ff1b-109">呼び出し元は、SafeArrayDestroy を使用して、返されたメモリの割り当てを解除する必要があり `SAFEARRAY` ます。 [SafeArrayDestroy](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy)</span><span class="sxs-lookup"><span data-stu-id="5ff1b-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ff1b-110">要件</span><span class="sxs-lookup"><span data-stu-id="5ff1b-110">Requirements</span></span>  

 <span data-ttu-id="5ff1b-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ff1b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ff1b-112">**ヘッダー:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="5ff1b-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="5ff1b-113">**ライブラリ:** BindingDisplay .idl</span><span class="sxs-lookup"><span data-stu-id="5ff1b-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="5ff1b-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ff1b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ff1b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ff1b-115">See also</span></span>

- [<span data-ttu-id="5ff1b-116">IBindingDisplay インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ff1b-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
- [<span data-ttu-id="5ff1b-117">InitializeForProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="5ff1b-117">InitializeForProcess Method</span></span>](ibindingdisplay-initializeforprocess-method.md)
