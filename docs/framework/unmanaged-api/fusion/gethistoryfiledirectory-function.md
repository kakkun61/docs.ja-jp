---
title: GetHistoryFileDirectory 関数
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
ms.openlocfilehash: 484adf288356b9955fe0cac0bb30002ec1f012d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724439"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="f5de8-102">GetHistoryFileDirectory 関数</span><span class="sxs-lookup"><span data-stu-id="f5de8-102">GetHistoryFileDirectory Function</span></span>

<span data-ttu-id="f5de8-103">アプリケーション履歴ディレクトリのパスを取得します。</span><span class="sxs-lookup"><span data-stu-id="f5de8-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5de8-104">構文</span><span class="sxs-lookup"><span data-stu-id="f5de8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5de8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f5de8-105">Parameters</span></span>  

 `wzDir`  
 <span data-ttu-id="f5de8-106">入出力アプリケーション履歴ディレクトリへのパスを保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="f5de8-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="f5de8-107">[入力、出力]バッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="f5de8-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5de8-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="f5de8-108">Return Value</span></span>  

 <span data-ttu-id="f5de8-109">このメソッドは、Winerror.h ファイルで定義されているように、次の値に加えて、標準の COM エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="f5de8-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="f5de8-110">リターン コード</span><span class="sxs-lookup"><span data-stu-id="f5de8-110">Return code</span></span>|<span data-ttu-id="f5de8-111">説明</span><span class="sxs-lookup"><span data-stu-id="f5de8-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f5de8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5de8-112">S_OK</span></span>|<span data-ttu-id="f5de8-113">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="f5de8-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="f5de8-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f5de8-114">E_INVALIDARG</span></span>|<span data-ttu-id="f5de8-115">`wzDir` または `pdwSize` が null であるか、またはバージョン文字列が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="f5de8-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5de8-116">注釈</span><span class="sxs-lookup"><span data-stu-id="f5de8-116">Remarks</span></span>  

 <span data-ttu-id="f5de8-117">正常に完了すると、 `pdwSize` 引数はパス文字列の長さに設定されます。</span><span class="sxs-lookup"><span data-stu-id="f5de8-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5de8-118">要件</span><span class="sxs-lookup"><span data-stu-id="f5de8-118">Requirements</span></span>  

 <span data-ttu-id="f5de8-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5de8-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5de8-120">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f5de8-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f5de8-121">**Library:** Fusion.dll し、Mscorwks.dll します。</span><span class="sxs-lookup"><span data-stu-id="f5de8-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="f5de8-122">Mscorwks.dll ではなく Fusion.dll を使用して、正しいバージョンの .NET Framework を対象にするようにします。</span><span class="sxs-lookup"><span data-stu-id="f5de8-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="f5de8-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5de8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5de8-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5de8-124">See also</span></span>

- [<span data-ttu-id="f5de8-125">CreateHistoryReader 関数</span><span class="sxs-lookup"><span data-stu-id="f5de8-125">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="f5de8-126">NukeDownloadedCache 関数</span><span class="sxs-lookup"><span data-stu-id="f5de8-126">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)
- [<span data-ttu-id="f5de8-127">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="f5de8-127">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
