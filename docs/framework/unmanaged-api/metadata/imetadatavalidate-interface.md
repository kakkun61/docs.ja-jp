---
title: IMetaDataValidate インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataValidate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate
helpviewer_keywords:
- IMetaDataValidate interface [.NET Framework metadata]
ms.assetid: db98608a-e85c-4f50-9d7b-5f57a426ddb6
topic_type:
- apiref
ms.openlocfilehash: 518ee65bc684f643bf4f608223c0fa40ea3f0dd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685540"
---
# <a name="imetadatavalidate-interface"></a><span data-ttu-id="f156b-102">IMetaDataValidate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f156b-102">IMetaDataValidate Interface</span></span>

<span data-ttu-id="f156b-103">メタデータ署名を検証するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f156b-103">Provides methods to validate metadata signatures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f156b-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="f156b-104">Methods</span></span>  
  
|<span data-ttu-id="f156b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f156b-105">Method</span></span>|<span data-ttu-id="f156b-106">説明</span><span class="sxs-lookup"><span data-stu-id="f156b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f156b-107">ValidateMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="f156b-107">ValidateMetaData Method</span></span>](imetadatavalidate-validatemetadata-method.md)|<span data-ttu-id="f156b-108">現在のメタデータ スコープ内にあるオブジェクトのメタデータ署名を検証します。</span><span class="sxs-lookup"><span data-stu-id="f156b-108">Validates the metadata signatures of the objects in the current metadata scope.</span></span>|  
|[<span data-ttu-id="f156b-109">ValidatorInit メソッド</span><span class="sxs-lookup"><span data-stu-id="f156b-109">ValidatorInit Method</span></span>](imetadatavalidate-validatorinit-method.md)|<span data-ttu-id="f156b-110">現在のメタデータ スコープ内にあるモジュールの種類を指定するフラグを設定し、指定されたコールバック メソッドを検証エラー用に登録します。</span><span class="sxs-lookup"><span data-stu-id="f156b-110">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f156b-111">要件</span><span class="sxs-lookup"><span data-stu-id="f156b-111">Requirements</span></span>  

 <span data-ttu-id="f156b-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f156b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f156b-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="f156b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f156b-114">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f156b-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f156b-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f156b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f156b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f156b-116">See also</span></span>

- [<span data-ttu-id="f156b-117">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f156b-117">Metadata Interfaces</span></span>](metadata-interfaces.md)
