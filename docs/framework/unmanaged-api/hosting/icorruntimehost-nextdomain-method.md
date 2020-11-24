---
title: ICorRuntimeHost::NextDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
ms.openlocfilehash: 598c46d50d7b4a67c1b2c0d844c9b12deb12a428
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671370"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="12e9e-102">ICorRuntimeHost::NextDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="12e9e-102">ICorRuntimeHost::NextDomain Method</span></span>

<span data-ttu-id="12e9e-103">列挙体の次のドメインへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="12e9e-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12e9e-104">構文</span><span class="sxs-lookup"><span data-stu-id="12e9e-104">Syntax</span></span>  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12e9e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="12e9e-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="12e9e-106">から [Enumdomains](icorruntimehost-enumdomains-method.md)の呼び出しによって取得された列挙子。</span><span class="sxs-lookup"><span data-stu-id="12e9e-106">[in] The enumerator that was obtained through a call to [EnumDomains](icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="12e9e-107">入出力列挙体の次のドメインを表す型へのインターフェイスポインター <xref:System._AppDomain?displayProperty=nameWithType> 。または、他のドメインが存在しない場合は null。</span><span class="sxs-lookup"><span data-stu-id="12e9e-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12e9e-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="12e9e-108">Return Value</span></span>  
  
|<span data-ttu-id="12e9e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="12e9e-109">HRESULT</span></span>|<span data-ttu-id="12e9e-110">説明</span><span class="sxs-lookup"><span data-stu-id="12e9e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="12e9e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="12e9e-111">S_OK</span></span>|<span data-ttu-id="12e9e-112">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="12e9e-112">The operation was successful.</span></span>|  
|<span data-ttu-id="12e9e-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="12e9e-113">S_FALSE</span></span>|<span data-ttu-id="12e9e-114">操作を完了できなかったか、列挙にドメインがありません。</span><span class="sxs-lookup"><span data-stu-id="12e9e-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="12e9e-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="12e9e-115">E_FAIL</span></span>|<span data-ttu-id="12e9e-116">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="12e9e-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="12e9e-117">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="12e9e-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="12e9e-118">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="12e9e-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="12e9e-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="12e9e-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="12e9e-120">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="12e9e-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="12e9e-121">要件</span><span class="sxs-lookup"><span data-stu-id="12e9e-121">Requirements</span></span>  

 <span data-ttu-id="12e9e-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12e9e-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12e9e-123">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="12e9e-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="12e9e-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="12e9e-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12e9e-125">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="12e9e-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e9e-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="12e9e-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="12e9e-127">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="12e9e-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
