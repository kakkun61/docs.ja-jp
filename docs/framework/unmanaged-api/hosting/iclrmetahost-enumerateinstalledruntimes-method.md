---
title: ICLRMetaHost::EnumerateInstalledRuntimes メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateInstalledRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes
helpviewer_keywords:
- ICLRMetaHost::EnumerateInstalledRuntimes method [.NET Framework hosting]
- EnumerateInstalledRuntimes method [.NET Framework hosting]
ms.assetid: 9e359384-0d3d-451c-807e-5d7fcebf2be7
topic_type:
- apiref
ms.openlocfilehash: f8f67edde7f99878429ca0bbd89aaf52336aa79c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730449"
---
# <a name="iclrmetahostenumerateinstalledruntimes-method"></a><span data-ttu-id="e625f-102">ICLRMetaHost::EnumerateInstalledRuntimes メソッド</span><span class="sxs-lookup"><span data-stu-id="e625f-102">ICLRMetaHost::EnumerateInstalledRuntimes Method</span></span>

<span data-ttu-id="e625f-103">コンピューターにインストールされている共通言語ランタイム (CLR) の各バージョンの有効な [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスを含む列挙を返します。</span><span class="sxs-lookup"><span data-stu-id="e625f-103">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface for each version of the common language runtime (CLR) that is installed on a computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e625f-104">構文</span><span class="sxs-lookup"><span data-stu-id="e625f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateInstalledRuntimes (  
    [out, retval] IEnumUnknown **ppEnumerator);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e625f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e625f-105">Parameters</span></span>  

 `ppEnumerator`  
 <span data-ttu-id="e625f-106">入出力コンピューターにインストールされている CLR の各バージョンに対応する [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスの列挙体。</span><span class="sxs-lookup"><span data-stu-id="e625f-106">[out] An enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each version of the CLR that is installed on the computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e625f-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="e625f-107">Return Value</span></span>  

 <span data-ttu-id="e625f-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="e625f-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e625f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e625f-109">HRESULT</span></span>|<span data-ttu-id="e625f-110">説明</span><span class="sxs-lookup"><span data-stu-id="e625f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e625f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e625f-111">S_OK</span></span>|<span data-ttu-id="e625f-112">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="e625f-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="e625f-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="e625f-113">E_POINTER</span></span>|<span data-ttu-id="e625f-114">`ppEnumerator` が null です。</span><span class="sxs-lookup"><span data-stu-id="e625f-114">`ppEnumerator` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e625f-115">要件</span><span class="sxs-lookup"><span data-stu-id="e625f-115">Requirements</span></span>  

 <span data-ttu-id="e625f-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e625f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e625f-117">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="e625f-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e625f-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e625f-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e625f-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e625f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e625f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e625f-120">See also</span></span>

- [<span data-ttu-id="e625f-121">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e625f-121">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="e625f-122">ホスティング</span><span class="sxs-lookup"><span data-stu-id="e625f-122">Hosting</span></span>](index.md)
