---
title: StrongNameSignatureGeneration 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
ms.openlocfilehash: 78a89c07b9a7ddbccee9716de37c96d23635f87b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708531"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="59ca3-102">StrongNameSignatureGeneration 関数</span><span class="sxs-lookup"><span data-stu-id="59ca3-102">StrongNameSignatureGeneration Function</span></span>

<span data-ttu-id="59ca3-103">指定したアセンブリに対して厳密な名前の署名が生成されます。</span><span class="sxs-lookup"><span data-stu-id="59ca3-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="59ca3-104">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="59ca3-104">This function has been deprecated.</span></span> <span data-ttu-id="59ca3-105">代わりに [ICLRStrongName:: StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="59ca3-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59ca3-106">構文</span><span class="sxs-lookup"><span data-stu-id="59ca3-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59ca3-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="59ca3-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="59ca3-108">から厳密な名前の署名が生成されるアセンブリのマニフェストを含むファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="59ca3-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="59ca3-109">から公開キーと秘密キーのペアを格納するキーコンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="59ca3-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="59ca3-110">`pbKeyBlob`が null の場合、では、 `wszKeyContainer` 暗号化サービスプロバイダー (CSP) 内の有効なコンテナーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59ca3-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="59ca3-111">この場合、コンテナーに格納されているキーペアがファイルの署名に使用されます。</span><span class="sxs-lookup"><span data-stu-id="59ca3-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="59ca3-112">`pbKeyBlob`が null でない場合、キーペアは、バイナリラージオブジェクト (BLOB) に格納されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="59ca3-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="59ca3-113">キーは 1024-Rivest-shamir-adleman-Rivest-shamir-adleman (RSA) 署名キーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="59ca3-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="59ca3-114">この時点では、他の種類のキーはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="59ca3-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="59ca3-115">から公開/秘密キーのペアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="59ca3-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="59ca3-116">このペアは、Win32 関数によって作成される形式です `CryptExportKey` 。</span><span class="sxs-lookup"><span data-stu-id="59ca3-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="59ca3-117">`pbKeyBlob`が null の場合、によって指定されたキーコンテナーには、キーのペアが含まれていると `wszKeyContainer` 見なされます。</span><span class="sxs-lookup"><span data-stu-id="59ca3-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="59ca3-118">からのサイズ (バイト単位) `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="59ca3-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="59ca3-119">入出力共通言語ランタイムが署名を返す場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="59ca3-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="59ca3-120">`ppbSignatureBlob`が null の場合、ランタイムはによって指定されたファイルに署名を格納し `wszFilePath` ます。</span><span class="sxs-lookup"><span data-stu-id="59ca3-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="59ca3-121">`ppbSignatureBlob`が null でない場合は、共通言語ランタイムによって、署名を返す領域が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="59ca3-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="59ca3-122">呼び出し元は、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を使用してこの領域を解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59ca3-122">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="59ca3-123">入出力返されたシグネチャのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="59ca3-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59ca3-124">戻り値</span><span class="sxs-lookup"><span data-stu-id="59ca3-124">Return Value</span></span>  

 <span data-ttu-id="59ca3-125">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="59ca3-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59ca3-126">注釈</span><span class="sxs-lookup"><span data-stu-id="59ca3-126">Remarks</span></span>  

 <span data-ttu-id="59ca3-127">`wszFilePath`署名を作成せずに署名のサイズを計算するには、に null を指定します。</span><span class="sxs-lookup"><span data-stu-id="59ca3-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="59ca3-128">署名は、ファイルに直接格納するか、呼び出し元に返すことができます。</span><span class="sxs-lookup"><span data-stu-id="59ca3-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="59ca3-129">関数が `StrongNameSignatureGeneration` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="59ca3-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59ca3-130">要件</span><span class="sxs-lookup"><span data-stu-id="59ca3-130">Requirements</span></span>  

 <span data-ttu-id="59ca3-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59ca3-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59ca3-132">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="59ca3-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="59ca3-133">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="59ca3-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="59ca3-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59ca3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ca3-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="59ca3-135">See also</span></span>

- [<span data-ttu-id="59ca3-136">StrongNameSignatureGeneration メソッド</span><span class="sxs-lookup"><span data-stu-id="59ca3-136">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="59ca3-137">StrongNameSignatureGenerationEx メソッド</span><span class="sxs-lookup"><span data-stu-id="59ca3-137">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="59ca3-138">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="59ca3-138">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
