---
title: ICLRPolicyManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
ms.openlocfilehash: 7092a1c792fee7f6173dcde211b8e807f6ab02a3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725587"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="1c782-102">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1c782-102">ICLRPolicyManager Interface</span></span>

<span data-ttu-id="1c782-103">エラーやタイムアウトが発生した場合に実行されるポリシーアクションをホストが指定できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="1c782-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c782-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="1c782-104">Methods</span></span>  
  
|<span data-ttu-id="1c782-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1c782-105">Method</span></span>|<span data-ttu-id="1c782-106">説明</span><span class="sxs-lookup"><span data-stu-id="1c782-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c782-107">SetActionOnFailure メソッド</span><span class="sxs-lookup"><span data-stu-id="1c782-107">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="1c782-108">指定したエラーが発生したときに共通言語ランタイム (CLR) が実行するポリシーアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="1c782-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="1c782-109">SetActionOnTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="1c782-109">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="1c782-110">指定された操作がタイムアウトしたときに CLR が実行するポリシーアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="1c782-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="1c782-111">SetDefaultAction メソッド</span><span class="sxs-lookup"><span data-stu-id="1c782-111">SetDefaultAction Method</span></span>](iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="1c782-112">指定された操作が発生したときに CLR が実行するポリシーアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="1c782-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="1c782-113">SetTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="1c782-113">SetTimeout Method</span></span>](iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="1c782-114">指定された操作のタイムアウト値を設定します。</span><span class="sxs-lookup"><span data-stu-id="1c782-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="1c782-115">SetTimeoutAndAction メソッド</span><span class="sxs-lookup"><span data-stu-id="1c782-115">SetTimeoutAndAction Method</span></span>](iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="1c782-116">指定された操作のタイムアウト値を設定し、操作が発生したときに CLR が実行する必要があるポリシーアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="1c782-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="1c782-117">SetUnhandledExceptionPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="1c782-117">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="1c782-118">未処理の例外が発生した場合の CLR の動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c782-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1c782-119">要件</span><span class="sxs-lookup"><span data-stu-id="1c782-119">Requirements</span></span>  

 <span data-ttu-id="1c782-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c782-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c782-121">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1c782-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1c782-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1c782-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1c782-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c782-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c782-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c782-124">See also</span></span>

- [<span data-ttu-id="1c782-125">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="1c782-125">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="1c782-126">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="1c782-126">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="1c782-127">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="1c782-127">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="1c782-128">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1c782-128">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
