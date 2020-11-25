---
title: ICorDebugModule::GetToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type:
- apiref
ms.openlocfilehash: 6ffc74247a4ecafcc3744923c0def99220b5ca6f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709883"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="84f02-102">ICorDebugModule::GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="84f02-102">ICorDebugModule::GetToken Method</span></span>

<span data-ttu-id="84f02-103">このモジュールのテーブルエントリのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="84f02-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84f02-104">構文</span><span class="sxs-lookup"><span data-stu-id="84f02-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84f02-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="84f02-105">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="84f02-106">入出力 `mdModule` モジュールのメタデータを参照するトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="84f02-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84f02-107">注釈</span><span class="sxs-lookup"><span data-stu-id="84f02-107">Remarks</span></span>  

 <span data-ttu-id="84f02-108">トークンは、 [IMetaDataImport](../metadata/imetadataimport-interface.md)、 [IMetaDataImport2](../metadata/imetadataimport2-interface.md)、および [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) メタデータインポートインターフェイスに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="84f02-108">The token can be passed to the [IMetaDataImport](../metadata/imetadataimport-interface.md), [IMetaDataImport2](../metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84f02-109">要件</span><span class="sxs-lookup"><span data-stu-id="84f02-109">Requirements</span></span>  

 <span data-ttu-id="84f02-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84f02-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84f02-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84f02-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84f02-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84f02-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84f02-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84f02-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84f02-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="84f02-114">See also</span></span>

- [<span data-ttu-id="84f02-115">Metadata</span><span class="sxs-lookup"><span data-stu-id="84f02-115">Metadata</span></span>](../metadata/index.md)
