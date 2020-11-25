---
title: StrongNameKeyGenEx 関数
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
ms.openlocfilehash: f28ee5767997240018d182b8303e4f65be81c702
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708544"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="aa9c3-102">StrongNameKeyGenEx 関数</span><span class="sxs-lookup"><span data-stu-id="aa9c3-102">StrongNameKeyGenEx Function</span></span>

<span data-ttu-id="aa9c3-103">厳密な名前の使用のために、指定されたキーサイズを持つ新しい公開/秘密キーのペアを生成します。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="aa9c3-104">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-104">This function has been deprecated.</span></span> <span data-ttu-id="aa9c3-105">代わりに [ICLRStrongName:: StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa9c3-106">構文</span><span class="sxs-lookup"><span data-stu-id="aa9c3-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa9c3-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa9c3-107">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="aa9c3-108">から要求されたキーコンテナー名。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-108">[in] The requested key container name.</span></span> <span data-ttu-id="aa9c3-109">`wszKeyContainer` は空でない文字列である必要があります。または、一時名を生成する場合は null にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="aa9c3-110">からキーを登録したままにするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="aa9c3-111">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="aa9c3-112">0x00000000- `wszKeyContainer` が null の場合に、一時キーコンテナー名を生成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="aa9c3-113">0x00000001 ( `SN_LEAVE_KEY` )-キーを登録したままにすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="aa9c3-114">から要求されたキーのサイズ (ビット単位)。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="aa9c3-115">入出力返された公開/秘密キーのペア。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="aa9c3-116">入出力のサイズ (バイト単位) `ppbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa9c3-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa9c3-117">Return Value</span></span>  

 <span data-ttu-id="aa9c3-118">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa9c3-119">注釈</span><span class="sxs-lookup"><span data-stu-id="aa9c3-119">Remarks</span></span>  

 <span data-ttu-id="aa9c3-120">.NET Framework バージョン1.0 および1.1 では、 `dwKeySize` 厳密な名前でアセンブリに署名するには1024ビットが必要です。バージョン2.0 では、2048ビットキーのサポートが追加されます。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="aa9c3-121">キーが取得されたら、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を呼び出して、割り当てられたメモリを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="aa9c3-122">関数が `StrongNameKeyGenEx` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa9c3-123">要件</span><span class="sxs-lookup"><span data-stu-id="aa9c3-123">Requirements</span></span>  

 <span data-ttu-id="aa9c3-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa9c3-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa9c3-125">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="aa9c3-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="aa9c3-126">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="aa9c3-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aa9c3-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa9c3-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa9c3-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa9c3-128">See also</span></span>

- [<span data-ttu-id="aa9c3-129">StrongNameKeyGenEx メソッド</span><span class="sxs-lookup"><span data-stu-id="aa9c3-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="aa9c3-130">StrongNameKeyGen メソッド</span><span class="sxs-lookup"><span data-stu-id="aa9c3-130">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="aa9c3-131">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aa9c3-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
