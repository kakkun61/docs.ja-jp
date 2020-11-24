---
title: EClrUnhandledException 列挙型
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
ms.openlocfilehash: bccd44e1bead4feadf67929dc104557715904577
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686444"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="b1074-102">EClrUnhandledException 列挙型</span><span class="sxs-lookup"><span data-stu-id="b1074-102">EClrUnhandledException Enumeration</span></span>

<span data-ttu-id="b1074-103">ユーザーコードで処理されない例外を管理するために使用できるオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b1074-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1074-104">構文</span><span class="sxs-lookup"><span data-stu-id="b1074-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="b1074-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="b1074-105">Members</span></span>  
  
|<span data-ttu-id="b1074-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b1074-106">Member</span></span>|<span data-ttu-id="b1074-107">説明</span><span class="sxs-lookup"><span data-stu-id="b1074-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="b1074-108">既定の動作を実行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="b1074-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="b1074-109">プロセスが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="b1074-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="b1074-110">共通言語ランタイム (CLR) が未処理の例外を無視し、ホストがそれ以上のアクションを決定できるように指定します。</span><span class="sxs-lookup"><span data-stu-id="b1074-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1074-111">注釈</span><span class="sxs-lookup"><span data-stu-id="b1074-111">Remarks</span></span>  

 <span data-ttu-id="b1074-112">CLR が以前のバージョンと同じように動作するように指定するには、メンバーを使用し `eHostDeterminedPolicy` ます。</span><span class="sxs-lookup"><span data-stu-id="b1074-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1074-113">要件</span><span class="sxs-lookup"><span data-stu-id="b1074-113">Requirements</span></span>  

 <span data-ttu-id="b1074-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1074-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1074-115">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b1074-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1074-116">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b1074-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1074-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1074-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1074-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1074-118">See also</span></span>

- [<span data-ttu-id="b1074-119">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="b1074-119">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="b1074-120">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="b1074-120">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="b1074-121">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1074-121">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="b1074-122">SetUnhandledExceptionPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="b1074-122">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="b1074-123">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1074-123">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="b1074-124">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="b1074-124">Hosting Enumerations</span></span>](hosting-enumerations.md)
