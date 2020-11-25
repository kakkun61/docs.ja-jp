---
title: StrongNameTokenFromAssembly 関数
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
ms.openlocfilehash: 0feb180befd575dce20a83ddc89ebf13f87f3810
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728551"
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="3cc7f-102">StrongNameTokenFromAssembly 関数</span><span class="sxs-lookup"><span data-stu-id="3cc7f-102">StrongNameTokenFromAssembly Function</span></span>

<span data-ttu-id="3cc7f-103">指定したアセンブリ ファイルから、厳密な名前トークンが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3cc7f-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="3cc7f-104">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="3cc7f-104">This function has been deprecated.</span></span> <span data-ttu-id="3cc7f-105">代わりに [ICLRStrongName:: StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="3cc7f-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cc7f-106">構文</span><span class="sxs-lookup"><span data-stu-id="3cc7f-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cc7f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3cc7f-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="3cc7f-108">からアセンブリのポータブル実行可能 (PE) ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="3cc7f-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="3cc7f-109">入出力返された厳密な名前トークン。</span><span class="sxs-lookup"><span data-stu-id="3cc7f-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="3cc7f-110">入出力厳密な名前トークンのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="3cc7f-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3cc7f-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="3cc7f-111">Return Value</span></span>  

 <span data-ttu-id="3cc7f-112">`true` 正常に完了した場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="3cc7f-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cc7f-113">注釈</span><span class="sxs-lookup"><span data-stu-id="3cc7f-113">Remarks</span></span>  

 <span data-ttu-id="3cc7f-114">厳密な名前トークンは、公開キーの短縮形です。</span><span class="sxs-lookup"><span data-stu-id="3cc7f-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="3cc7f-115">トークンは、アセンブリの署名に使用される公開キーから作成された64ビットのハッシュです。</span><span class="sxs-lookup"><span data-stu-id="3cc7f-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="3cc7f-116">トークンはアセンブリの厳密な名前の一部であり、アセンブリメタデータから読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="3cc7f-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="3cc7f-117">トークンが作成されたら、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を呼び出して、割り当てられたメモリを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cc7f-117">After the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="3cc7f-118">関数が `StrongNameTokenFromAssembly` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="3cc7f-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cc7f-119">要件</span><span class="sxs-lookup"><span data-stu-id="3cc7f-119">Requirements</span></span>  

 <span data-ttu-id="3cc7f-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3cc7f-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cc7f-121">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="3cc7f-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3cc7f-122">**ライブラリ:** mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3cc7f-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="3cc7f-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cc7f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc7f-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="3cc7f-124">See also</span></span>

- [<span data-ttu-id="3cc7f-125">StrongNameTokenFromAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="3cc7f-125">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="3cc7f-126">StrongNameTokenFromAssemblyEx メソッド</span><span class="sxs-lookup"><span data-stu-id="3cc7f-126">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="3cc7f-127">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3cc7f-127">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
