---
title: ICLRStrongName::StrongNameCompareAssemblies メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
ms.openlocfilehash: ddcbe84053aa7f4cafd81e905f8aef988f92875e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685702"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="963dd-102">ICLRStrongName::StrongNameCompareAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="963dd-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>

<span data-ttu-id="963dd-103">厳密な名前の署名に基づいて 2 つのアセンブリが異なるかどうかが判定されます。</span><span class="sxs-lookup"><span data-stu-id="963dd-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="963dd-104">構文</span><span class="sxs-lookup"><span data-stu-id="963dd-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="963dd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="963dd-105">Parameters</span></span>  

 `wszAssembly1`  
 <span data-ttu-id="963dd-106">から最初のアセンブリへのパス。</span><span class="sxs-lookup"><span data-stu-id="963dd-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="963dd-107">から2番目のアセンブリへのパス。</span><span class="sxs-lookup"><span data-stu-id="963dd-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="963dd-108">入出力次のいずれかの値です。</span><span class="sxs-lookup"><span data-stu-id="963dd-108">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="963dd-109">`SN_CMP_DIFFERENT` (0)-アセンブリに異なるデータが含まれることを指定します。</span><span class="sxs-lookup"><span data-stu-id="963dd-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="963dd-110">`SN_CMP_IDENTICAL` (1)-署名やチェックサムなど、アセンブリがまったく同じであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="963dd-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="963dd-111">`SN_CMP_SIGONLY` (2)-アセンブリが署名とチェックサムのみで異なることを指定します。</span><span class="sxs-lookup"><span data-stu-id="963dd-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="963dd-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="963dd-112">Return Value</span></span>  

 <span data-ttu-id="963dd-113">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="963dd-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="963dd-114">要件</span><span class="sxs-lookup"><span data-stu-id="963dd-114">Requirements</span></span>  

 <span data-ttu-id="963dd-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="963dd-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="963dd-116">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="963dd-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="963dd-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="963dd-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="963dd-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="963dd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="963dd-119">注釈</span><span class="sxs-lookup"><span data-stu-id="963dd-119">Remarks</span></span>  

 <span data-ttu-id="963dd-120">アセンブリの厳密な名前の署名は、アセンブリのテキスト名、バージョン、カルチャ、および公開キートークンで構成されます。</span><span class="sxs-lookup"><span data-stu-id="963dd-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="963dd-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="963dd-121">See also</span></span>

- [<span data-ttu-id="963dd-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="963dd-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
