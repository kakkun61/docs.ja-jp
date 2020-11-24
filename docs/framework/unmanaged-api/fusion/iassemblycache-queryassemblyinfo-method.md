---
title: IAssemblyCache::QueryAssemblyInfo メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyCache.QueryAssemblyInfo
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::QueryAssemblyInfo
helpviewer_keywords:
- IAssemblyCache::QueryAssemblyInfo method [.NET Framework fusion]
- QueryAssemblyInfo method [.NET Framework fusion]
ms.assetid: 09313cb5-06f6-43bd-94f4-1055c6b0c99a
topic_type:
- apiref
ms.openlocfilehash: f764be9b80a8d4dcb15791d406412ece9e7e7c87
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670928"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="e65f2-102">IAssemblyCache::QueryAssemblyInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="e65f2-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>

<span data-ttu-id="e65f2-103">指定したアセンブリに関する要求されたデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="e65f2-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e65f2-104">構文</span><span class="sxs-lookup"><span data-stu-id="e65f2-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e65f2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e65f2-105">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="e65f2-106">からFusion に定義されているフラグ。</span><span class="sxs-lookup"><span data-stu-id="e65f2-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="e65f2-107">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e65f2-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="e65f2-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="e65f2-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
- <span data-ttu-id="e65f2-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="e65f2-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="e65f2-110">からデータの取得対象となるアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="e65f2-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="e65f2-111">[入力、出力]アセンブリに関するデータを格納する [ASSEMBLY_INFO](assembly-info-structure.md) 構造体。</span><span class="sxs-lookup"><span data-stu-id="e65f2-111">[in, out] An [ASSEMBLY_INFO](assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e65f2-112">要件</span><span class="sxs-lookup"><span data-stu-id="e65f2-112">Requirements</span></span>  

 <span data-ttu-id="e65f2-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e65f2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e65f2-114">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e65f2-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e65f2-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e65f2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e65f2-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e65f2-116">See also</span></span>

- [<span data-ttu-id="e65f2-117">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e65f2-117">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
