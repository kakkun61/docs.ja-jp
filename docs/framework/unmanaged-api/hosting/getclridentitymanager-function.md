---
title: GetCLRIdentityManager 関数
ms.date: 03/30/2017
api_name:
- GetCLRIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetCLRIdentityManager
helpviewer_keywords:
- GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type:
- apiref
ms.openlocfilehash: 9d1196749e033c71b0c8923d0325eb4886122d1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733660"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="14b40-102">GetCLRIdentityManager 関数</span><span class="sxs-lookup"><span data-stu-id="14b40-102">GetCLRIdentityManager Function</span></span>

<span data-ttu-id="14b40-103">共通言語ランタイム (CLR) が id を管理できるようにするインターフェイスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="14b40-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="14b40-104">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="14b40-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14b40-105">構文</span><span class="sxs-lookup"><span data-stu-id="14b40-105">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14b40-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="14b40-106">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="14b40-107">から `REFIID` 取得するインターフェイスを指定する (インターフェイス識別子)。</span><span class="sxs-lookup"><span data-stu-id="14b40-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="14b40-108">この値は IID_ICLRAssemblyIdentityManager または IID_ICLRHostBindingPolicyManager のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="14b40-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="14b40-109">入出力 [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) または [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) オブジェクトのいずれかのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="14b40-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14b40-110">注釈</span><span class="sxs-lookup"><span data-stu-id="14b40-110">Remarks</span></span>  

 <span data-ttu-id="14b40-111">関数へのポインターを取得するには、 [GetRealProcAddress](getrealprocaddress-function.md) 関数を呼び出し `GetCLRIdentityManager` ます。</span><span class="sxs-lookup"><span data-stu-id="14b40-111">Call the [GetRealProcAddress](getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14b40-112">要件</span><span class="sxs-lookup"><span data-stu-id="14b40-112">Requirements</span></span>  

 <span data-ttu-id="14b40-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14b40-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14b40-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="14b40-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="14b40-115">**ライブラリ:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="14b40-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="14b40-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14b40-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14b40-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="14b40-117">See also</span></span>

- [<span data-ttu-id="14b40-118">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="14b40-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
