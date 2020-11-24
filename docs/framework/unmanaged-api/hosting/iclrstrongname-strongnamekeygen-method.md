---
title: ICLRStrongName::StrongNameKeyGen メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
ms.openlocfilehash: 42a9fc1a05e97bbd893f0a2e77087e6524ad844f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674542"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="6575f-102">ICLRStrongName::StrongNameKeyGen メソッド</span><span class="sxs-lookup"><span data-stu-id="6575f-102">ICLRStrongName::StrongNameKeyGen Method</span></span>

<span data-ttu-id="6575f-103">厳密な名前を使用するために新しい公開/秘密キーの組が作成されます。</span><span class="sxs-lookup"><span data-stu-id="6575f-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6575f-104">構文</span><span class="sxs-lookup"><span data-stu-id="6575f-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6575f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6575f-105">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="6575f-106">から要求されたキーコンテナー名。</span><span class="sxs-lookup"><span data-stu-id="6575f-106">[in] The requested key container name.</span></span> <span data-ttu-id="6575f-107">`wszKeyContainer` は、空でない文字列であるか、または一時名を生成するために null である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6575f-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6575f-108">からキーを登録したままにするかどうかを示す値です。</span><span class="sxs-lookup"><span data-stu-id="6575f-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="6575f-109">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6575f-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="6575f-110">0x00000000- `wszKeyContainer` が null の場合に、一時キーコンテナー名を生成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6575f-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="6575f-111">0x00000001 ( `SN_LEAVE_KEY` )-キーを登録したままにすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="6575f-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="6575f-112">入出力返された公開/秘密キーのペア。</span><span class="sxs-lookup"><span data-stu-id="6575f-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="6575f-113">入出力のサイズ (バイト単位) `ppbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="6575f-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6575f-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="6575f-114">Return Value</span></span>  

 <span data-ttu-id="6575f-115">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="6575f-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6575f-116">注釈</span><span class="sxs-lookup"><span data-stu-id="6575f-116">Remarks</span></span>  

 <span data-ttu-id="6575f-117">[ICLRStrongName:: StrongNameKeyGen](iclrstrongname-strongnamekeygen-method.md)メソッドは、1024ビットのキーを作成します。</span><span class="sxs-lookup"><span data-stu-id="6575f-117">The [ICLRStrongName::StrongNameKeyGen](iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="6575f-118">キーを取得した後、 [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) メソッドを呼び出して、割り当てられたメモリを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6575f-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6575f-119">要件</span><span class="sxs-lookup"><span data-stu-id="6575f-119">Requirements</span></span>  

 <span data-ttu-id="6575f-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6575f-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6575f-121">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="6575f-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6575f-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6575f-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6575f-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6575f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6575f-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="6575f-124">See also</span></span>

- [<span data-ttu-id="6575f-125">StrongNameKeyGenEx メソッド</span><span class="sxs-lookup"><span data-stu-id="6575f-125">StrongNameKeyGenEx Method</span></span>](iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="6575f-126">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6575f-126">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
