---
title: ICLRDomainManager::SetPropertiesForDefaultAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
ms.openlocfilehash: b5577d0444caf14fb47d9d7e2de60a8399378db7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702135"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="d3afe-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="d3afe-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>

<span data-ttu-id="d3afe-103">既定のアプリケーションドメインを初期化するために使用されるプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="d3afe-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3afe-104">構文</span><span class="sxs-lookup"><span data-stu-id="d3afe-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3afe-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3afe-105">Parameters</span></span>  

 `nProperties`  
 <span data-ttu-id="d3afe-106">からとのエントリの数 `pwszPropertyNames` `pwszPropertyValues` 。</span><span class="sxs-lookup"><span data-stu-id="d3afe-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="d3afe-107">からプロパティ名の配列。プロパティがない場合は null。</span><span class="sxs-lookup"><span data-stu-id="d3afe-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="d3afe-108">現時点では、このメソッドによって認識される唯一のプロパティ名は "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" です。</span><span class="sxs-lookup"><span data-stu-id="d3afe-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="d3afe-109">からプロパティ値の配列。プロパティがない場合は null。</span><span class="sxs-lookup"><span data-stu-id="d3afe-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3afe-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3afe-110">Return Value</span></span>  

 <span data-ttu-id="d3afe-111">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="d3afe-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d3afe-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d3afe-112">HRESULT</span></span>|<span data-ttu-id="d3afe-113">説明</span><span class="sxs-lookup"><span data-stu-id="d3afe-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d3afe-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d3afe-114">S_OK</span></span>|<span data-ttu-id="d3afe-115">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="d3afe-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="d3afe-116">HRESULT_FROM_WIN32 (ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="d3afe-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="d3afe-117">`pwszPropertyNames` には、このメソッドで認識されないプロパティ名が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d3afe-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3afe-118">注釈</span><span class="sxs-lookup"><span data-stu-id="d3afe-118">Remarks</span></span>  

 <span data-ttu-id="d3afe-119">"PARTIAL_TRUST_VISIBLE_ASSEMBLIES" のプロパティ値は、条件付き (APTCA) 属性を持つアセンブリのリストです。このフラグは、 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> 既定のアプリケーションドメインの部分的に信頼された呼び出し元に対して表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3afe-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3afe-120">要件</span><span class="sxs-lookup"><span data-stu-id="d3afe-120">Requirements</span></span>  

 <span data-ttu-id="d3afe-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3afe-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3afe-122">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="d3afe-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d3afe-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d3afe-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3afe-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3afe-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3afe-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3afe-125">See also</span></span>

- [<span data-ttu-id="d3afe-126">ホスティング</span><span class="sxs-lookup"><span data-stu-id="d3afe-126">Hosting</span></span>](index.md)
- [<span data-ttu-id="d3afe-127">ICLRDomainManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d3afe-127">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)
