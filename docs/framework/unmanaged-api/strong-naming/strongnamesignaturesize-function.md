---
title: StrongNameSignatureSize 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
ms.openlocfilehash: 6a2b3afe66f1eaa358c5f80de50f14ceb730048b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708479"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="be092-102">StrongNameSignatureSize 関数</span><span class="sxs-lookup"><span data-stu-id="be092-102">StrongNameSignatureSize Function</span></span>

<span data-ttu-id="be092-103">厳密な名前の署名のサイズが返されます。</span><span class="sxs-lookup"><span data-stu-id="be092-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="be092-104">`StrongNameSignatureSize` は、通常、コンパイラによって使用され、遅延署名されたアセンブリを作成するときにファイルで予約する領域の量を決定します。</span><span class="sxs-lookup"><span data-stu-id="be092-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="be092-105">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="be092-105">This function has been deprecated.</span></span> <span data-ttu-id="be092-106">代わりに [ICLRStrongName:: StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="be092-106">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be092-107">構文</span><span class="sxs-lookup"><span data-stu-id="be092-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="be092-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="be092-108">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="be092-109">から厳密な名前の署名を生成するために使用されるキーペアの公開部分を格納する [Publickeyblob](publickeyblob-structure.md) 型の構造体。</span><span class="sxs-lookup"><span data-stu-id="be092-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="be092-110">からのサイズ (バイト単位) `pbPublicKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="be092-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="be092-111">から厳密な名前の署名を格納するために必要なバイト数。</span><span class="sxs-lookup"><span data-stu-id="be092-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be092-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="be092-112">Return Value</span></span>  

 <span data-ttu-id="be092-113">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="be092-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be092-114">注釈</span><span class="sxs-lookup"><span data-stu-id="be092-114">Remarks</span></span>  

 <span data-ttu-id="be092-115">関数が `StrongNameSignatureSize` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="be092-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be092-116">要件</span><span class="sxs-lookup"><span data-stu-id="be092-116">Requirements</span></span>  

 <span data-ttu-id="be092-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be092-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be092-118">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="be092-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="be092-119">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="be092-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be092-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be092-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be092-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="be092-121">See also</span></span>

- [<span data-ttu-id="be092-122">StrongNameSignatureSize メソッド</span><span class="sxs-lookup"><span data-stu-id="be092-122">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="be092-123">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be092-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
