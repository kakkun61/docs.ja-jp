---
title: ICLRStrongName::StrongNameGetPublicKey メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: 5bd314b2b63474d2a1d159f74564e2d4ca13aef6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725548"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="58385-102">ICLRStrongName::StrongNameGetPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="58385-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>

<span data-ttu-id="58385-103">公開キーと秘密キーのペアから公開キーを取得します。</span><span class="sxs-lookup"><span data-stu-id="58385-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="58385-104">キーペアは、暗号化サービスプロバイダー (CSP) 内のキーコンテナー名として、またはバイトの未加工コレクションとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="58385-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58385-105">構文</span><span class="sxs-lookup"><span data-stu-id="58385-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58385-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="58385-106">Parameters</span></span>  

 `szKeyContainer`  
 <span data-ttu-id="58385-107">から公開キーと秘密キーのペアを格納するキーコンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="58385-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="58385-108">`pbKeyBlob`が null の場合、は `szKeyContainer` CSP 内の有効なコンテナーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58385-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="58385-109">この場合、 [ICLRStrongName:: StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md) メソッドは、コンテナーに格納されているキーペアから公開キーを抽出します。</span><span class="sxs-lookup"><span data-stu-id="58385-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="58385-110">`pbKeyBlob`が null でない場合、キーペアは、バイナリラージオブジェクト (BLOB) に格納されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="58385-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="58385-111">キーは 1024-Rivest-shamir-adleman-Rivest-shamir-adleman (RSA) 署名キーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="58385-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="58385-112">この時点では、他の種類のキーはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="58385-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="58385-113">から公開/秘密キーのペアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="58385-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="58385-114">このペアは、Win32 関数によって作成される形式です `CryptExportKey` 。</span><span class="sxs-lookup"><span data-stu-id="58385-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="58385-115">`pbKeyBlob`が null の場合、によって指定されたキーコンテナーには、キーのペアが含まれていると `szKeyContainer` 見なされます。</span><span class="sxs-lookup"><span data-stu-id="58385-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="58385-116">からのサイズ (バイト単位) `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="58385-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="58385-117">入出力返された公開キー BLOB。</span><span class="sxs-lookup"><span data-stu-id="58385-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="58385-118">パラメーターは、 `ppbPublicKeyBlob` 共通言語ランタイムによって割り当てられ、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="58385-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="58385-119">呼び出し元は、 [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) メソッドを使用して、メモリを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58385-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="58385-120">入出力返される公開キー BLOB のサイズ。</span><span class="sxs-lookup"><span data-stu-id="58385-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58385-121">戻り値</span><span class="sxs-lookup"><span data-stu-id="58385-121">Return Value</span></span>  

 <span data-ttu-id="58385-122">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="58385-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58385-123">注釈</span><span class="sxs-lookup"><span data-stu-id="58385-123">Remarks</span></span>  

 <span data-ttu-id="58385-124">公開キーは [Publickeyblob](../strong-naming/publickeyblob-structure.md) 構造に含まれています。</span><span class="sxs-lookup"><span data-stu-id="58385-124">The public key is contained in a [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58385-125">要件</span><span class="sxs-lookup"><span data-stu-id="58385-125">Requirements</span></span>  

 <span data-ttu-id="58385-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58385-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58385-127">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="58385-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="58385-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="58385-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58385-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58385-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58385-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="58385-130">See also</span></span>

- [<span data-ttu-id="58385-131">StrongNameTokenFromPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="58385-131">StrongNameTokenFromPublicKey Method</span></span>](iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="58385-132">PublicKeyBlob 構造体</span><span class="sxs-lookup"><span data-stu-id="58385-132">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="58385-133">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58385-133">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
