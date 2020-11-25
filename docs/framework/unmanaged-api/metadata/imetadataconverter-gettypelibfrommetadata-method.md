---
title: IMetaDataConverter::GetTypeLibFromMetaData メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
ms.openlocfilehash: eed8661f8885ca16492ab336a599b5290057843a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714602"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="9d806-102">IMetaDataConverter::GetTypeLibFromMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="9d806-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>

<span data-ttu-id="9d806-103">指定した `ITypeLib` ライブラリ名とモジュール名を持つタイプライブラリを表すインスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="9d806-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d806-104">構文</span><span class="sxs-lookup"><span data-stu-id="9d806-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,
    [in]  BSTR     strTlbName,
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d806-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9d806-105">Parameters</span></span>  

 `strModule`  
 <span data-ttu-id="9d806-106">からタイプライブラリのモジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="9d806-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="9d806-107">からタイプライブラリの名前。</span><span class="sxs-lookup"><span data-stu-id="9d806-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="9d806-108">入出力タイプライブラリを表すインスタンスのアドレスを受け取る場所へのポインター `ITypeLib` 。</span><span class="sxs-lookup"><span data-stu-id="9d806-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d806-109">要件</span><span class="sxs-lookup"><span data-stu-id="9d806-109">Requirements</span></span>  

 <span data-ttu-id="9d806-110">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d806-110">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d806-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="9d806-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9d806-112">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="9d806-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9d806-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d806-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d806-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d806-114">See also</span></span>

- [<span data-ttu-id="9d806-115">IMetaDataConverter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9d806-115">IMetaDataConverter Interface</span></span>](imetadataconverter-interface.md)
