---
title: ICLRRuntimeInfo::LoadErrorString メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadErrorString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type:
- apiref
ms.openlocfilehash: 0e029aa848a6630ae00c834dd2b924dc4ebce537
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671773"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="d2ebd-102">ICLRRuntimeInfo::LoadErrorString メソッド</span><span class="sxs-lookup"><span data-stu-id="d2ebd-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>

<span data-ttu-id="d2ebd-103">HRESULT 値を、指定したカルチャの適切なエラーメッセージに変換します。</span><span class="sxs-lookup"><span data-stu-id="d2ebd-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="d2ebd-104">このメソッドは、次の関数を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d2ebd-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="d2ebd-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="d2ebd-105">LoadStringRC</span></span>](loadstringrc-function.md)  
  
- [<span data-ttu-id="d2ebd-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="d2ebd-106">LoadStringRCEx</span></span>](loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="d2ebd-107">構文</span><span class="sxs-lookup"><span data-stu-id="d2ebd-107">Syntax</span></span>  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2ebd-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d2ebd-108">Parameters</span></span>  

 `iResourceID`  
 <span data-ttu-id="d2ebd-109">から変換する HRESULT。</span><span class="sxs-lookup"><span data-stu-id="d2ebd-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="d2ebd-110">入出力指定した HRESULT に関連付けられているメッセージ文字列。</span><span class="sxs-lookup"><span data-stu-id="d2ebd-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="d2ebd-111">[入力、出力] `pwzbuffer` バッファーオーバーランを回避するためののサイズ。</span><span class="sxs-lookup"><span data-stu-id="d2ebd-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="d2ebd-112">`pwzbuffer`が null の場合、は、 `pcchBuffer` の予期されるサイズを提供して、事前割り当て `pwzbuffer` を可能にします。</span><span class="sxs-lookup"><span data-stu-id="d2ebd-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="d2ebd-113">からカルチャ識別子。</span><span class="sxs-lookup"><span data-stu-id="d2ebd-113">[in] The culture identifier.</span></span> <span data-ttu-id="d2ebd-114">既定のカルチャを使用するには、-1 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2ebd-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2ebd-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="d2ebd-115">Return Value</span></span>  

 <span data-ttu-id="d2ebd-116">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="d2ebd-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d2ebd-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d2ebd-117">HRESULT</span></span>|<span data-ttu-id="d2ebd-118">説明</span><span class="sxs-lookup"><span data-stu-id="d2ebd-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d2ebd-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="d2ebd-119">S_OK</span></span>|<span data-ttu-id="d2ebd-120">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="d2ebd-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="d2ebd-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d2ebd-121">E_POINTER</span></span>|<span data-ttu-id="d2ebd-122">`pcchBuffer` が null です。</span><span class="sxs-lookup"><span data-stu-id="d2ebd-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="d2ebd-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d2ebd-123">E_INVALIDARG</span></span>|<span data-ttu-id="d2ebd-124">`pwzBuffer` が null です。</span><span class="sxs-lookup"><span data-stu-id="d2ebd-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2ebd-125">要件</span><span class="sxs-lookup"><span data-stu-id="d2ebd-125">Requirements</span></span>  

 <span data-ttu-id="d2ebd-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2ebd-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2ebd-127">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="d2ebd-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d2ebd-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d2ebd-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2ebd-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2ebd-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ebd-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2ebd-130">See also</span></span>

- [<span data-ttu-id="d2ebd-131">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d2ebd-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="d2ebd-132">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d2ebd-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="d2ebd-133">ホスティング</span><span class="sxs-lookup"><span data-stu-id="d2ebd-133">Hosting</span></span>](index.md)
