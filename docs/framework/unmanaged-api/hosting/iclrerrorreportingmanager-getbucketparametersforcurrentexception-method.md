---
title: ICLRErrorReportingManager::GetBucketParametersForCurrentException メソッド
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.GetBucketParametersForCurrentException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException
helpviewer_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException method [.NET Framework hosting]
- GetBucketParametersForCurrentException method [.NET Framework hosting]
ms.assetid: a13ec8a6-8e18-4acb-8054-77f5b1a0e0b9
topic_type:
- apiref
ms.openlocfilehash: 33927cc0e3a3cdaad70d437f9dd5ca5dfdcdc46b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673561"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="72aed-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="72aed-102">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>

<span data-ttu-id="72aed-103">呼び出し元のスレッドで現在の例外の Watson バケットを取得します。</span><span class="sxs-lookup"><span data-stu-id="72aed-103">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="72aed-104">*バケット* は、同じコード障害に関連するエラーデータのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="72aed-104">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="72aed-105">*Watson* は、例外に関連付けられているデータを収集および分析するための一連のテクノロジを指します。</span><span class="sxs-lookup"><span data-stu-id="72aed-105">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72aed-106">構文</span><span class="sxs-lookup"><span data-stu-id="72aed-106">Syntax</span></span>  
  
```cpp  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72aed-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="72aed-107">Parameters</span></span>  

 `pParams`  
 <span data-ttu-id="72aed-108">入出力例外のエラーデータを格納している [BucketParameters](bucketparameters-structure.md) 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="72aed-108">[out] A pointer to a [BucketParameters](bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72aed-109">要件</span><span class="sxs-lookup"><span data-stu-id="72aed-109">Requirements</span></span>  

 <span data-ttu-id="72aed-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72aed-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72aed-111">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="72aed-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72aed-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="72aed-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72aed-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72aed-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72aed-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="72aed-114">See also</span></span>

- [<span data-ttu-id="72aed-115">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72aed-115">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
