---
title: ICLRErrorReportingManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
ms.openlocfilehash: d3816c8a3b6204b053505aa888eb28d696f8990b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677846"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="d4e60-102">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d4e60-102">ICLRErrorReportingManager Interface</span></span>

<span data-ttu-id="d4e60-103">エラー報告のためにホストがカスタムスタックダンプを構成できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d4e60-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d4e60-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="d4e60-104">Methods</span></span>  
  
|<span data-ttu-id="d4e60-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d4e60-105">Method</span></span>|<span data-ttu-id="d4e60-106">説明</span><span class="sxs-lookup"><span data-stu-id="d4e60-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d4e60-107">BeginCustomDump メソッド</span><span class="sxs-lookup"><span data-stu-id="d4e60-107">BeginCustomDump Method</span></span>](iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="d4e60-108">エラー報告用のカスタムスタックダンプの構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="d4e60-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="d4e60-109">EndCustomDump メソッド</span><span class="sxs-lookup"><span data-stu-id="d4e60-109">EndCustomDump Method</span></span>](iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="d4e60-110">以前のの呼び出しで設定されたカスタムスタックダンプ構成を消去し `BeginCustomDump` ます。</span><span class="sxs-lookup"><span data-stu-id="d4e60-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="d4e60-111">GetBucketParametersForCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="d4e60-111">GetBucketParametersForCurrentException Method</span></span>](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="d4e60-112">呼び出し元のスレッドで現在の例外の Watson バケットを取得します。</span><span class="sxs-lookup"><span data-stu-id="d4e60-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4e60-113">注釈</span><span class="sxs-lookup"><span data-stu-id="d4e60-113">Remarks</span></span>  

 <span data-ttu-id="d4e60-114">メソッドは、 `BeginCustomDump` カスタムスタックダンプ構成を設定します。</span><span class="sxs-lookup"><span data-stu-id="d4e60-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="d4e60-115">メソッドは、 `EndCustomDump` カスタムスタックダンプ構成をクリアし、関連付けられているすべての状態を解放します。</span><span class="sxs-lookup"><span data-stu-id="d4e60-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="d4e60-116">カスタムダンプの完了後に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4e60-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d4e60-117">を呼び出さない `EndCustomDump` と、メモリがリークします。</span><span class="sxs-lookup"><span data-stu-id="d4e60-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4e60-118">要件</span><span class="sxs-lookup"><span data-stu-id="d4e60-118">Requirements</span></span>  

 <span data-ttu-id="d4e60-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4e60-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4e60-120">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d4e60-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4e60-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d4e60-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4e60-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4e60-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4e60-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4e60-123">See also</span></span>

- [<span data-ttu-id="d4e60-124">ECustomDumpItemKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="d4e60-124">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="d4e60-125">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d4e60-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
