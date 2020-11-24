---
title: IAssemblyCache::UninstallAssembly メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyCache.UninstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::UninstallAssembly
helpviewer_keywords:
- UninstallAssembly method [.NET Framework fusion]
- IAssemblyCache::UninstallAssembly method [.NET Framework fusion]
ms.assetid: 973b2c44-8dfc-40c1-9035-10f4846627e9
topic_type:
- apiref
ms.openlocfilehash: 36a2a609e95740ffc45722635a7e1f09e0ed5601
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670785"
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="b7239-102">IAssemblyCache::UninstallAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="b7239-102">IAssemblyCache::UninstallAssembly Method</span></span>

<span data-ttu-id="b7239-103">指定したアセンブリをグローバルアセンブリキャッシュからアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="b7239-103">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7239-104">構文</span><span class="sxs-lookup"><span data-stu-id="b7239-104">Syntax</span></span>  
  
```cpp  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7239-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b7239-105">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="b7239-106">からFusion に定義されているフラグ。</span><span class="sxs-lookup"><span data-stu-id="b7239-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="b7239-107">からアンインストールするアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="b7239-107">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="b7239-108">からアセンブリのインストールデータを格納する [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) 構造体。</span><span class="sxs-lookup"><span data-stu-id="b7239-108">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="b7239-109">[out、省略可能]Fusion で定義されている配置値の1つ。</span><span class="sxs-lookup"><span data-stu-id="b7239-109">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="b7239-110">次の値があります。</span><span class="sxs-lookup"><span data-stu-id="b7239-110">Possible values include the following:</span></span>  
  
- <span data-ttu-id="b7239-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span><span class="sxs-lookup"><span data-stu-id="b7239-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
- <span data-ttu-id="b7239-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span><span class="sxs-lookup"><span data-stu-id="b7239-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
- <span data-ttu-id="b7239-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span><span class="sxs-lookup"><span data-stu-id="b7239-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
- <span data-ttu-id="b7239-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span><span class="sxs-lookup"><span data-stu-id="b7239-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
- <span data-ttu-id="b7239-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span><span class="sxs-lookup"><span data-stu-id="b7239-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
- <span data-ttu-id="b7239-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span><span class="sxs-lookup"><span data-stu-id="b7239-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7239-117">要件</span><span class="sxs-lookup"><span data-stu-id="b7239-117">Requirements</span></span>  

 <span data-ttu-id="b7239-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7239-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7239-119">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b7239-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b7239-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7239-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7239-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7239-121">See also</span></span>

- [<span data-ttu-id="b7239-122">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7239-122">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
