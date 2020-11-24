---
title: ICLRStrongName::StrongNameKeyGenEx メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
ms.openlocfilehash: 9ba50616b25f9c7c592f19947c82a890ae6b5a4a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671682"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="3c100-102">ICLRStrongName::StrongNameKeyGenEx メソッド</span><span class="sxs-lookup"><span data-stu-id="3c100-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>

<span data-ttu-id="3c100-103">厳密な名前の使用のために、指定されたキーサイズを持つ新しい公開/秘密キーのペアを生成します。</span><span class="sxs-lookup"><span data-stu-id="3c100-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c100-104">構文</span><span class="sxs-lookup"><span data-stu-id="3c100-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c100-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3c100-105">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="3c100-106">から要求されたキーコンテナー名。</span><span class="sxs-lookup"><span data-stu-id="3c100-106">[in] The requested key container name.</span></span> <span data-ttu-id="3c100-107">`wszKeyContainer` は、空でない文字列であるか、または一時名を生成するために null である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c100-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3c100-108">からキーを登録したままにするかどうかを示す値です。</span><span class="sxs-lookup"><span data-stu-id="3c100-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="3c100-109">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3c100-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="3c100-110">0x00000000- `wszKeyContainer` が null の場合に、一時キーコンテナー名を生成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c100-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="3c100-111">0x00000001 ( `SN_LEAVE_KEY` )-キーを登録したままにすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="3c100-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="3c100-112">から要求されたキーのサイズ (ビット単位)。</span><span class="sxs-lookup"><span data-stu-id="3c100-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="3c100-113">入出力返された公開/秘密キーのペア。</span><span class="sxs-lookup"><span data-stu-id="3c100-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="3c100-114">入出力のサイズ (バイト単位) `ppbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="3c100-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c100-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="3c100-115">Return Value</span></span>  

 <span data-ttu-id="3c100-116">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="3c100-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c100-117">注釈</span><span class="sxs-lookup"><span data-stu-id="3c100-117">Remarks</span></span>  

 <span data-ttu-id="3c100-118">.NET Framework バージョン1.0 および1.1 では、 `dwKeySize` 厳密な名前でアセンブリに署名するには1024ビットが必要です。バージョン2.0 では、2048ビットキーのサポートが追加されます。</span><span class="sxs-lookup"><span data-stu-id="3c100-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="3c100-119">キーを取得した後、 [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) メソッドを呼び出して、割り当てられたメモリを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c100-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c100-120">要件</span><span class="sxs-lookup"><span data-stu-id="3c100-120">Requirements</span></span>  

 <span data-ttu-id="3c100-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c100-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c100-122">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="3c100-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3c100-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3c100-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c100-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c100-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c100-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c100-125">See also</span></span>

- [<span data-ttu-id="3c100-126">StrongNameKeyGen メソッド</span><span class="sxs-lookup"><span data-stu-id="3c100-126">StrongNameKeyGen Method</span></span>](iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="3c100-127">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c100-127">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
