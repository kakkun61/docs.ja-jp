---
title: StrongNameFreeBuffer 関数
ms.date: 03/30/2017
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
ms.openlocfilehash: d93bda046a79dbdec2195eee48fefc1e5538b2e4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732256"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="e431a-102">StrongNameFreeBuffer 関数</span><span class="sxs-lookup"><span data-stu-id="e431a-102">StrongNameFreeBuffer Function</span></span>

<span data-ttu-id="e431a-103">[StrongNameGetPublicKey](strongnamegetpublickey-function.md)、[StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)、または[StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md) などの厳密な名前の関数に対する前の呼び出しで割り当てられたメモリが解放されます。</span><span class="sxs-lookup"><span data-stu-id="e431a-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="e431a-104">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="e431a-104">This function has been deprecated.</span></span> <span data-ttu-id="e431a-105">代わりに [ICLRStrongName:: StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="e431a-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e431a-106">構文</span><span class="sxs-lookup"><span data-stu-id="e431a-106">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e431a-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e431a-107">Parameters</span></span>  

 `pbMemory`  
 <span data-ttu-id="e431a-108">から解放するメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e431a-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e431a-109">要件</span><span class="sxs-lookup"><span data-stu-id="e431a-109">Requirements</span></span>  

 <span data-ttu-id="e431a-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e431a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e431a-111">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="e431a-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e431a-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e431a-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e431a-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e431a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e431a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="e431a-114">See also</span></span>

- [<span data-ttu-id="e431a-115">StrongNameFreeBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="e431a-115">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="e431a-116">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e431a-116">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
