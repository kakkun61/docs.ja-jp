---
title: IMetaDataEmit::SetModuleProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
ms.openlocfilehash: 1757662d2004dce3156182c35b37237ff91bae7f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730345"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="4b27a-102">IMetaDataEmit::SetModuleProps メソッド</span><span class="sxs-lookup"><span data-stu-id="4b27a-102">IMetaDataEmit::SetModuleProps Method</span></span>

<span data-ttu-id="4b27a-103">[IMetaDataEmit::D efinemoduleref](imetadataemit-definemoduleref-method.md)の前の呼び出しで定義されているモジュールへの参照を更新します。</span><span class="sxs-lookup"><span data-stu-id="4b27a-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b27a-104">構文</span><span class="sxs-lookup"><span data-stu-id="4b27a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b27a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4b27a-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="4b27a-106">からUnicode のモジュール名。</span><span class="sxs-lookup"><span data-stu-id="4b27a-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="4b27a-107">これはファイル名のみで、完全なパス名ではありません。</span><span class="sxs-lookup"><span data-stu-id="4b27a-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b27a-108">要件</span><span class="sxs-lookup"><span data-stu-id="4b27a-108">Requirements</span></span>  

 <span data-ttu-id="4b27a-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b27a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b27a-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="4b27a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4b27a-111">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b27a-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b27a-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b27a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b27a-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b27a-113">See also</span></span>

- [<span data-ttu-id="4b27a-114">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4b27a-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4b27a-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4b27a-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
