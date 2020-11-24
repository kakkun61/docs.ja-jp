---
title: IMetaDataEmit2::GetDeltaSaveSize メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
ms.openlocfilehash: 36021333c1efb61e23c16782d8ad721de62c2643
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674324"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="9b0bb-102">IMetaDataEmit2::GetDeltaSaveSize メソッド</span><span class="sxs-lookup"><span data-stu-id="9b0bb-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>

<span data-ttu-id="9b0bb-103">現在のエディットコンティニュセッションの結果として得られるメタデータサイズの変更を示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b0bb-104">構文</span><span class="sxs-lookup"><span data-stu-id="9b0bb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b0bb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9b0bb-105">Parameters</span></span>  

 `fSave`  
 <span data-ttu-id="9b0bb-106">から [CorSaveSize](corsavesize-enumeration.md) 値の1つ。必要な精度のレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-106">[in] One of the [CorSaveSize](corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="9b0bb-107">.NET Framework バージョン2.0 では、このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="9b0bb-108">入出力メタデータのサイズの変更。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b0bb-109">要件</span><span class="sxs-lookup"><span data-stu-id="9b0bb-109">Requirements</span></span>  

 <span data-ttu-id="9b0bb-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b0bb-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="9b0bb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b0bb-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="9b0bb-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9b0bb-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b0bb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b0bb-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b0bb-114">See also</span></span>

- [<span data-ttu-id="9b0bb-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b0bb-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="9b0bb-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b0bb-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
