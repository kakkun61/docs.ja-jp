---
title: ICLRValidator::FormatEventInfo メソッド
ms.date: 03/30/2017
api_name:
- ICLRValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::FormatEventInfo
helpviewer_keywords:
- FormatEventInfo method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::FormatEventInfo method [.NET Framework hosting]
ms.assetid: 808e1f1d-52f4-47c4-83cc-dcf47d075219
topic_type:
- apiref
ms.openlocfilehash: a3f52deab4d0c8ca56fae2e65912217e51abe58a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715876"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="6f1f7-102">ICLRValidator::FormatEventInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="6f1f7-102">ICLRValidator::FormatEventInfo Method</span></span>

<span data-ttu-id="6f1f7-103">指定された検証エラーに関する詳細メッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="6f1f7-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f1f7-104">構文</span><span class="sxs-lookup"><span data-stu-id="6f1f7-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f1f7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6f1f7-105">Parameters</span></span>  

 `hVECode`  
 <span data-ttu-id="6f1f7-106">から検証エラーハンドラーに渡された HRESULT 値。</span><span class="sxs-lookup"><span data-stu-id="6f1f7-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="6f1f7-107">から `VEContext` 検証エラーに関するコンテキスト情報を格納しているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="6f1f7-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="6f1f7-108">[入力、出力]わかりやすいエラーメッセージ。</span><span class="sxs-lookup"><span data-stu-id="6f1f7-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="6f1f7-109">からエラーメッセージの最大長。</span><span class="sxs-lookup"><span data-stu-id="6f1f7-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="6f1f7-110">からメッセージで使用される追加パラメーターのセーフ配列。</span><span class="sxs-lookup"><span data-stu-id="6f1f7-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f1f7-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="6f1f7-111">Return Value</span></span>  
  
|<span data-ttu-id="6f1f7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f1f7-112">HRESULT</span></span>|<span data-ttu-id="6f1f7-113">説明</span><span class="sxs-lookup"><span data-stu-id="6f1f7-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f1f7-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f1f7-114">S_OK</span></span>|<span data-ttu-id="6f1f7-115">`FormatEventInfo` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="6f1f7-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="6f1f7-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6f1f7-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6f1f7-117">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="6f1f7-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6f1f7-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6f1f7-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6f1f7-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="6f1f7-119">The call timed out.</span></span>|  
|<span data-ttu-id="6f1f7-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6f1f7-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6f1f7-121">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="6f1f7-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6f1f7-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6f1f7-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6f1f7-123">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="6f1f7-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6f1f7-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6f1f7-124">E_FAIL</span></span>|<span data-ttu-id="6f1f7-125">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6f1f7-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6f1f7-126">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="6f1f7-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6f1f7-127">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="6f1f7-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f1f7-128">要件</span><span class="sxs-lookup"><span data-stu-id="6f1f7-128">Requirements</span></span>  

 <span data-ttu-id="6f1f7-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f1f7-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f1f7-130">**ヘッダー:** IValidator、IValidator</span><span class="sxs-lookup"><span data-stu-id="6f1f7-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="6f1f7-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6f1f7-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f1f7-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f1f7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f1f7-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f1f7-133">See also</span></span>

- [<span data-ttu-id="6f1f7-134">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6f1f7-134">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="6f1f7-135">ICLRValidator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6f1f7-135">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
