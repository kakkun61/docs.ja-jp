---
title: StrongNameGetBlob 関数
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
ms.openlocfilehash: 8f5cb89294004dfb1f020627ceb1edb58735f72c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732282"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="8a8ba-102">StrongNameGetBlob 関数</span><span class="sxs-lookup"><span data-stu-id="8a8ba-102">StrongNameGetBlob Function</span></span>

<span data-ttu-id="8a8ba-103">指定したアドレスにある実行可能ファイルのバイナリ表現が、指定したバッファーに入れられます。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="8a8ba-104">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-104">This function has been deprecated.</span></span> <span data-ttu-id="8a8ba-105">代わりに [ICLRStrongName:: StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-105">Use the [ICLRStrongName::StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a8ba-106">構文</span><span class="sxs-lookup"><span data-stu-id="8a8ba-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a8ba-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a8ba-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="8a8ba-108">から読み込む実行可能ファイルへの有効なパス。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="8a8ba-109">から実行可能ファイルの読み込み先のバッファー。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="8a8ba-110">[入力、出力]要求された最大サイズ (バイト単位) `pbBlob` 。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="8a8ba-111">戻り時に、の実際のサイズ (バイト単位) `pbBlob` 。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a8ba-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="8a8ba-112">Return Value</span></span>  

 <span data-ttu-id="8a8ba-113">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a8ba-114">注釈</span><span class="sxs-lookup"><span data-stu-id="8a8ba-114">Remarks</span></span>  

 <span data-ttu-id="8a8ba-115">関数が `StrongNameGetBlob` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a8ba-116">要件</span><span class="sxs-lookup"><span data-stu-id="8a8ba-116">Requirements</span></span>  

 <span data-ttu-id="8a8ba-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a8ba-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a8ba-118">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="8a8ba-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="8a8ba-119">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8a8ba-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a8ba-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a8ba-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a8ba-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a8ba-121">See also</span></span>

- [<span data-ttu-id="8a8ba-122">StrongNameGetBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="8a8ba-122">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="8a8ba-123">StrongNameGetBlobFromImage メソッド</span><span class="sxs-lookup"><span data-stu-id="8a8ba-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="8a8ba-124">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8a8ba-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
