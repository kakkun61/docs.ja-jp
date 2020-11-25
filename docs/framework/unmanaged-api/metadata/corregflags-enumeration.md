---
title: CorRegFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorRegFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegFlags
helpviewer_keywords:
- CorRegFlags enumeration [.NET Framework metadata]
ms.assetid: 8d3080ee-39fe-4c57-8950-51323632d045
topic_type:
- apiref
ms.openlocfilehash: 5ea588194720394ad9f361fbba702f3fcdcbe110
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706100"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="75821-102">CorRegFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="75821-102">CorRegFlags Enumeration</span></span>

<span data-ttu-id="75821-103">モジュールまたは複合イメージをインストールするときに登録に使用されるフラグ値を提供します。</span><span class="sxs-lookup"><span data-stu-id="75821-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75821-104">構文</span><span class="sxs-lookup"><span data-stu-id="75821-104">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="75821-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="75821-105">Members</span></span>  
  
|<span data-ttu-id="75821-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="75821-106">Member</span></span>|<span data-ttu-id="75821-107">説明</span><span class="sxs-lookup"><span data-stu-id="75821-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="75821-108">転送先にファイルをコピーしないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="75821-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="75821-109">モジュールまたは複合が構成であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="75821-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="75821-110">モジュールまたは複合にクラス参照があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="75821-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75821-111">要件</span><span class="sxs-lookup"><span data-stu-id="75821-111">Requirements</span></span>  

 <span data-ttu-id="75821-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75821-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75821-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="75821-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75821-114">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="75821-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="75821-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75821-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75821-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="75821-116">See also</span></span>

- [<span data-ttu-id="75821-117">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="75821-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
