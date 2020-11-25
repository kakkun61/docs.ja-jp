---
title: IMetaDataEmit::DefineModuleRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineModuleRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type:
- apiref
ms.openlocfilehash: 96d24705d80dabcda691edec497a4a30b6d37dc4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719555"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="925a3-102">IMetaDataEmit::DefineModuleRef メソッド</span><span class="sxs-lookup"><span data-stu-id="925a3-102">IMetaDataEmit::DefineModuleRef Method</span></span>

<span data-ttu-id="925a3-103">指定された名前を持つモジュールのメタデータシグネチャを作成します。</span><span class="sxs-lookup"><span data-stu-id="925a3-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="925a3-104">構文</span><span class="sxs-lookup"><span data-stu-id="925a3-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (
    [in]  LPCWSTR           szName,
    [out] mdModuleRef       *pmur
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="925a3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="925a3-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="925a3-106">から他のメタデータファイルの名前 (通常は DLL)。</span><span class="sxs-lookup"><span data-stu-id="925a3-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="925a3-107">これはファイル名のみです。</span><span class="sxs-lookup"><span data-stu-id="925a3-107">This is the file name only.</span></span> <span data-ttu-id="925a3-108">完全なパス名は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="925a3-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="925a3-109">入出力割り当てられた `mdModuleRef` トークン。</span><span class="sxs-lookup"><span data-stu-id="925a3-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="925a3-110">要件</span><span class="sxs-lookup"><span data-stu-id="925a3-110">Requirements</span></span>  

 <span data-ttu-id="925a3-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="925a3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="925a3-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="925a3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="925a3-113">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="925a3-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="925a3-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="925a3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="925a3-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="925a3-115">See also</span></span>

- [<span data-ttu-id="925a3-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="925a3-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="925a3-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="925a3-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
