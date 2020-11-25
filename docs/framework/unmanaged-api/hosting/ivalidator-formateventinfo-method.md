---
title: IValidator::FormatEventInfo メソッド
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
ms.openlocfilehash: c5c89e0eda6e93e34775c00d5ec8fb4ff0940707
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701017"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="3e1e6-102">IValidator::FormatEventInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="3e1e6-102">IValidator::FormatEventInfo Method</span></span>

<span data-ttu-id="3e1e6-103">指定した検証エラーに対応するエラーメッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="3e1e6-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e1e6-104">構文</span><span class="sxs-lookup"><span data-stu-id="3e1e6-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e1e6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3e1e6-105">Parameters</span></span>  

 `hVECode`  
 <span data-ttu-id="3e1e6-106">から検証エラーハンドラーに渡された HRESULT 値。</span><span class="sxs-lookup"><span data-stu-id="3e1e6-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="3e1e6-107">から `VEContext` 検証エラーに関するコンテキスト情報を格納しているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="3e1e6-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="3e1e6-108">[入力、出力]返されたエラーメッセージを含む文字列。</span><span class="sxs-lookup"><span data-stu-id="3e1e6-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="3e1e6-109">からエラーメッセージの最大長。</span><span class="sxs-lookup"><span data-stu-id="3e1e6-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="3e1e6-110">からエラーを説明する追加のパラメーターを格納しているセーフ配列。</span><span class="sxs-lookup"><span data-stu-id="3e1e6-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e1e6-111">要件</span><span class="sxs-lookup"><span data-stu-id="3e1e6-111">Requirements</span></span>  

 <span data-ttu-id="3e1e6-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e1e6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e1e6-113">**ヘッダー:** IValidator、IValidator</span><span class="sxs-lookup"><span data-stu-id="3e1e6-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="3e1e6-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3e1e6-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e1e6-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e1e6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
