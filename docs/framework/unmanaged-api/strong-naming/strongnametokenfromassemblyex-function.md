---
title: StrongNameTokenFromAssemblyEx 関数
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
ms.openlocfilehash: 566bba09f6bfac2f7616dc5caf32ef431f2e1e67
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719802"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="1711d-102">StrongNameTokenFromAssemblyEx 関数</span><span class="sxs-lookup"><span data-stu-id="1711d-102">StrongNameTokenFromAssemblyEx Function</span></span>

<span data-ttu-id="1711d-103">指定したアセンブリファイルから厳密な名前トークンを作成し、トークンが表す公開キーを返します。</span><span class="sxs-lookup"><span data-stu-id="1711d-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="1711d-104">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="1711d-104">This function has been deprecated.</span></span> <span data-ttu-id="1711d-105">代わりに [ICLRStrongName:: StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="1711d-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1711d-106">構文</span><span class="sxs-lookup"><span data-stu-id="1711d-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1711d-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1711d-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="1711d-108">からアセンブリのポータブル実行可能 (PE) ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="1711d-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="1711d-109">入出力返された厳密な名前トークン。</span><span class="sxs-lookup"><span data-stu-id="1711d-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="1711d-110">入出力厳密な名前トークンのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="1711d-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="1711d-111">入出力返された公開キー。</span><span class="sxs-lookup"><span data-stu-id="1711d-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="1711d-112">入出力公開キーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="1711d-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1711d-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="1711d-113">Return Value</span></span>  

 <span data-ttu-id="1711d-114">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="1711d-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1711d-115">注釈</span><span class="sxs-lookup"><span data-stu-id="1711d-115">Remarks</span></span>  

 <span data-ttu-id="1711d-116">厳密な名前トークンは、公開キーの短縮形です。</span><span class="sxs-lookup"><span data-stu-id="1711d-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="1711d-117">トークンは、アセンブリの署名に使用される公開キーから作成された64ビットのハッシュです。</span><span class="sxs-lookup"><span data-stu-id="1711d-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="1711d-118">トークンはアセンブリの厳密な名前の一部であり、アセンブリメタデータから読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="1711d-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="1711d-119">キーを取得してトークンを作成したら、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を呼び出して、割り当てられたメモリを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1711d-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="1711d-120">関数が `StrongNameTokenFromAssemblyEx` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="1711d-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1711d-121">要件</span><span class="sxs-lookup"><span data-stu-id="1711d-121">Requirements</span></span>  

 <span data-ttu-id="1711d-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1711d-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1711d-123">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="1711d-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="1711d-124">**ライブラリ:** mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1711d-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="1711d-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1711d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1711d-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="1711d-126">See also</span></span>

- [<span data-ttu-id="1711d-127">StrongNameTokenFromAssemblyEx メソッド</span><span class="sxs-lookup"><span data-stu-id="1711d-127">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="1711d-128">StrongNameTokenFromAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="1711d-128">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="1711d-129">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1711d-129">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
