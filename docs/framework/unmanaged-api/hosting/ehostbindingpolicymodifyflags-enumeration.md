---
title: EHostBindingPolicyModifyFlags 列挙型
ms.date: 03/30/2017
api_name:
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
ms.openlocfilehash: ec64f9bec0ee9b63796958b17c7f10b87692f1d0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686148"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="f1df1-102">EHostBindingPolicyModifyFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="f1df1-102">EHostBindingPolicyModifyFlags Enumeration</span></span>

<span data-ttu-id="f1df1-103">ソースアセンブリからターゲットアセンブリにポリシー変更を適用するときに、共通言語ランタイム (CLR) が実行するリダイレクトの種類をホストが指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f1df1-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1df1-104">構文</span><span class="sxs-lookup"><span data-stu-id="f1df1-104">Syntax</span></span>  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="f1df1-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="f1df1-105">Members</span></span>  
  
|<span data-ttu-id="f1df1-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f1df1-106">Member</span></span>|<span data-ttu-id="f1df1-107">説明</span><span class="sxs-lookup"><span data-stu-id="f1df1-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="f1df1-108">CLR がソースアセンブリのポリシー値をターゲットアセンブリのポリシー値に連結するように指定します。</span><span class="sxs-lookup"><span data-stu-id="f1df1-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="f1df1-109">CLR が既定のアクションを実行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="f1df1-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="f1df1-110">CLR がターゲットアセンブリのポリシー値を最大値に設定することを指定します。</span><span class="sxs-lookup"><span data-stu-id="f1df1-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="f1df1-111">CLR がターゲットアセンブリのポリシー値をソースアセンブリのポリシー値に置き換えることを指定します。</span><span class="sxs-lookup"><span data-stu-id="f1df1-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1df1-112">注釈</span><span class="sxs-lookup"><span data-stu-id="f1df1-112">Remarks</span></span>  

 <span data-ttu-id="f1df1-113">[ICLRHostBindingPolicyManager:: ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)メソッドは、型のパラメーターを受け取り `EHostBindingPolicyModifyFlags` ます。</span><span class="sxs-lookup"><span data-stu-id="f1df1-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1df1-114">要件</span><span class="sxs-lookup"><span data-stu-id="f1df1-114">Requirements</span></span>  

 <span data-ttu-id="f1df1-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1df1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1df1-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f1df1-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1df1-117">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f1df1-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1df1-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1df1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1df1-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1df1-119">See also</span></span>

- [<span data-ttu-id="f1df1-120">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1df1-120">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="f1df1-121">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="f1df1-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
