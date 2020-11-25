---
title: IMetaDataValidate::ValidatorInit メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataValidate.ValidatorInit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type:
- apiref
ms.openlocfilehash: e2f54e11906cd4ba1440e220530f2ca5b9de769f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708557"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="6e457-102">IMetaDataValidate::ValidatorInit メソッド</span><span class="sxs-lookup"><span data-stu-id="6e457-102">IMetaDataValidate::ValidatorInit Method</span></span>

<span data-ttu-id="6e457-103">現在のメタデータ スコープ内にあるモジュールの種類を指定するフラグを設定し、指定されたコールバック メソッドを検証エラー用に登録します。</span><span class="sxs-lookup"><span data-stu-id="6e457-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e457-104">構文</span><span class="sxs-lookup"><span data-stu-id="6e457-104">Syntax</span></span>  
  
```cpp  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e457-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e457-105">Parameters</span></span>  

 `dwModule`  
 <span data-ttu-id="6e457-106">から現在のメタデータスコープ内のモジュールの型を指定する [Corvalidatormoduletype](corvalidatormoduletype-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="6e457-106">[in] A value of the [CorValidatorModuleType](corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="6e457-107">から検証エラーの関数コールバックとして機能する [IUnknown](/cpp/atl/iunknown) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6e457-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e457-108">要件</span><span class="sxs-lookup"><span data-stu-id="6e457-108">Requirements</span></span>  

 <span data-ttu-id="6e457-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e457-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e457-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="6e457-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e457-111">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="6e457-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6e457-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e457-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e457-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e457-113">See also</span></span>

- [<span data-ttu-id="6e457-114">IMetaDataValidate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e457-114">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)
