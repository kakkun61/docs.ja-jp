---
title: CeeSectionAttr 列挙型
ms.date: 03/30/2017
api_name:
- CeeSectionAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionAttr
helpviewer_keywords:
- CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type:
- apiref
ms.openlocfilehash: 4b2fb80298f6eef331b5b7ae4a46222ce97ede6f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732737"
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="6b523-102">CeeSectionAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="6b523-102">CeeSectionAttr Enumeration</span></span>

<span data-ttu-id="6b523-103">[ICeeGen](iceegen-interface.md)インターフェイスで使用するセクションの属性を指定する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="6b523-103">Provides values that specify attributes of a section for use by the [ICeeGen](iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b523-104">構文</span><span class="sxs-lookup"><span data-stu-id="6b523-104">Syntax</span></span>  
  
```cpp  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="6b523-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="6b523-105">Members</span></span>  
  
|<span data-ttu-id="6b523-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="6b523-106">Member</span></span>|<span data-ttu-id="6b523-107">説明</span><span class="sxs-lookup"><span data-stu-id="6b523-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="6b523-108">Section には属性がありません。</span><span class="sxs-lookup"><span data-stu-id="6b523-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="6b523-109">セクションには、読み取りのみが可能な、更新されていない初期化済みのデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6b523-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="6b523-110">セクションには、読み取りまたは更新が可能な初期化済みのデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6b523-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="6b523-111">セクションには、読み取りと実行が許可されている実行可能コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6b523-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6b523-112">要件</span><span class="sxs-lookup"><span data-stu-id="6b523-112">Requirements</span></span>  

 <span data-ttu-id="6b523-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b523-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b523-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="6b523-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b523-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6b523-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6b523-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b523-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b523-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b523-117">See also</span></span>

- [<span data-ttu-id="6b523-118">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="6b523-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
