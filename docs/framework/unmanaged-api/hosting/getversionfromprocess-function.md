---
title: GetVersionFromProcess 関数
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
ms.openlocfilehash: da0d159da6eef7745c1fa7f7320d5e1355f6e413
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721882"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="5b6bc-102">GetVersionFromProcess 関数</span><span class="sxs-lookup"><span data-stu-id="5b6bc-102">GetVersionFromProcess Function</span></span>

<span data-ttu-id="5b6bc-103">指定したプロセスハンドルに関連付けられている共通言語ランタイム (CLR) のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="5b6bc-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="5b6bc-104">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="5b6bc-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b6bc-105">構文</span><span class="sxs-lookup"><span data-stu-id="5b6bc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b6bc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5b6bc-106">Parameters</span></span>  

 `hProcess`  
 <span data-ttu-id="5b6bc-107">からプロセスを処理するハンドル。</span><span class="sxs-lookup"><span data-stu-id="5b6bc-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="5b6bc-108">入出力メソッドが正常に完了したときのバージョン番号の文字列を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="5b6bc-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="5b6bc-109">からバージョンバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="5b6bc-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="5b6bc-110">入出力バージョン番号文字列の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5b6bc-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b6bc-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="5b6bc-111">Return Value</span></span>  

 <span data-ttu-id="5b6bc-112">このメソッドは、次の値に加えて、Winerror.h で定義されている標準のコンポーネントオブジェクトモデル (COM) エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="5b6bc-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="5b6bc-113">リターン コード</span><span class="sxs-lookup"><span data-stu-id="5b6bc-113">Return code</span></span>|<span data-ttu-id="5b6bc-114">説明</span><span class="sxs-lookup"><span data-stu-id="5b6bc-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="5b6bc-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="5b6bc-115">S_OK</span></span>|<span data-ttu-id="5b6bc-116">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="5b6bc-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="5b6bc-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5b6bc-117">E_INVALIDARG</span></span>|<span data-ttu-id="5b6bc-118">`pVersion` が null で `cchBuffer` あり、が null ではないか、またはその逆です。</span><span class="sxs-lookup"><span data-stu-id="5b6bc-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="5b6bc-119">- または -</span><span class="sxs-lookup"><span data-stu-id="5b6bc-119">-or-</span></span><br /><br /> <span data-ttu-id="5b6bc-120">`hProcess` は、プロセスへの有効なハンドルではありません。</span><span class="sxs-lookup"><span data-stu-id="5b6bc-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="5b6bc-121">- または -</span><span class="sxs-lookup"><span data-stu-id="5b6bc-121">-or-</span></span><br /><br /> <span data-ttu-id="5b6bc-122">CLR が読み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="5b6bc-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="5b6bc-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="5b6bc-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="5b6bc-124">`cchBuffer` が null であるか、またはバージョン文字列の長さを下回っています。</span><span class="sxs-lookup"><span data-stu-id="5b6bc-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="5b6bc-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="5b6bc-125">E_NOTIMPL</span></span>|<span data-ttu-id="5b6bc-126">この方法は、Microsoft Windows 95、Microsoft Windows 98、または Microsoft Windows Millennium Edition オペレーティングシステムでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="5b6bc-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5b6bc-127">要件</span><span class="sxs-lookup"><span data-stu-id="5b6bc-127">Requirements</span></span>  

 <span data-ttu-id="5b6bc-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b6bc-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b6bc-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5b6bc-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b6bc-130">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5b6bc-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b6bc-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b6bc-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b6bc-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b6bc-132">See also</span></span>

- [<span data-ttu-id="5b6bc-133">GetRequestedRuntimeInfo 関数</span><span class="sxs-lookup"><span data-stu-id="5b6bc-133">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="5b6bc-134">GetRequestedRuntimeVersion 関数</span><span class="sxs-lookup"><span data-stu-id="5b6bc-134">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="5b6bc-135">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="5b6bc-135">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
