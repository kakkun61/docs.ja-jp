---
title: CorFileFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorFileFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileFlags
helpviewer_keywords:
- CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type:
- apiref
ms.openlocfilehash: 70d789f417700734b546cac6ff527ed5aa84fcf9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688628"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="e6761-102">CorFileFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="e6761-102">CorFileFlags Enumeration</span></span>

<span data-ttu-id="e6761-103">[IMetaDataAssemblyEmit::D efineFile](imetadataassemblyemit-definefile-method.md)への呼び出しで定義されているファイルの種類を記述する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="e6761-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6761-104">構文</span><span class="sxs-lookup"><span data-stu-id="e6761-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="e6761-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="e6761-105">Members</span></span>  
  
|<span data-ttu-id="e6761-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e6761-106">Member</span></span>|<span data-ttu-id="e6761-107">説明</span><span class="sxs-lookup"><span data-stu-id="e6761-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="e6761-108">は、ファイルがリソースファイルではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="e6761-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="e6761-109">ファイル (場合によってはリソースファイル) にメタデータが含まれていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="e6761-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6761-110">要件</span><span class="sxs-lookup"><span data-stu-id="e6761-110">Requirements</span></span>  

 <span data-ttu-id="e6761-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6761-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6761-112">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="e6761-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e6761-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6761-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6761-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6761-114">See also</span></span>

- [<span data-ttu-id="e6761-115">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="e6761-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
