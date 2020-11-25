---
title: LoadStringRCEx 関数
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
ms.openlocfilehash: 1aa5c9f5dd7dd63e69c2eed1f6dd8ad6f007f01f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727537"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="57ab5-102">LoadStringRCEx 関数</span><span class="sxs-lookup"><span data-stu-id="57ab5-102">LoadStringRCEx Function</span></span>

<span data-ttu-id="57ab5-103">HRESULT 値を、指定したカルチャの適切なエラー メッセージに変換します。</span><span class="sxs-lookup"><span data-stu-id="57ab5-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="57ab5-104">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="57ab5-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57ab5-105">構文</span><span class="sxs-lookup"><span data-stu-id="57ab5-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,
    [in]  UINT    iResouceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet,
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57ab5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="57ab5-106">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="57ab5-107">からカルチャ識別子。</span><span class="sxs-lookup"><span data-stu-id="57ab5-107">[in] A culture identifier.</span></span> <span data-ttu-id="57ab5-108">既定のカルチャを使用するには、に-1 を渡し `lcid` ます。</span><span class="sxs-lookup"><span data-stu-id="57ab5-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="57ab5-109">からHRESULT。</span><span class="sxs-lookup"><span data-stu-id="57ab5-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="57ab5-110">入出力正常に完了したときのエラーメッセージを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="57ab5-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="57ab5-111">からエラーメッセージバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="57ab5-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="57ab5-112">から無効.</span><span class="sxs-lookup"><span data-stu-id="57ab5-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="57ab5-113">入出力エラーメッセージの長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="57ab5-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57ab5-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="57ab5-114">Return Value</span></span>  

 <span data-ttu-id="57ab5-115">このメソッドは、次の値に加えて、Winerror.h で定義されている標準の COM エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="57ab5-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="57ab5-116">リターン コード</span><span class="sxs-lookup"><span data-stu-id="57ab5-116">Return code</span></span>|<span data-ttu-id="57ab5-117">説明</span><span class="sxs-lookup"><span data-stu-id="57ab5-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="57ab5-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="57ab5-118">S_OK</span></span>|<span data-ttu-id="57ab5-119">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="57ab5-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="57ab5-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="57ab5-120">E_INVALIDARG</span></span>|<span data-ttu-id="57ab5-121">`szBuffer` が null であるか、または `iMax` がゼロ (0) です。</span><span class="sxs-lookup"><span data-stu-id="57ab5-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57ab5-122">注釈</span><span class="sxs-lookup"><span data-stu-id="57ab5-122">Remarks</span></span>  

 <span data-ttu-id="57ab5-123">メソッドが正常に完了しなかった場合、には `szBuffer` 空の文字列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="57ab5-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57ab5-124">要件</span><span class="sxs-lookup"><span data-stu-id="57ab5-124">Requirements</span></span>  

 <span data-ttu-id="57ab5-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57ab5-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57ab5-126">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="57ab5-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57ab5-127">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57ab5-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57ab5-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57ab5-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ab5-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="57ab5-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="57ab5-130">LoadStringRC 関数</span><span class="sxs-lookup"><span data-stu-id="57ab5-130">LoadStringRC Function</span></span>](loadstringrc-function.md)
- [<span data-ttu-id="57ab5-131">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="57ab5-131">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
