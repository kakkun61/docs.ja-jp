---
title: CorFileMapping 列挙体
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: 63e27a62e176a92b03c10b59a55d9da3192918f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726117"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="0891a-102">CorFileMapping 列挙体</span><span class="sxs-lookup"><span data-stu-id="0891a-102">CorFileMapping Enumeration</span></span>

<span data-ttu-id="0891a-103">[IMetaDataInfo:: GetFileMapping](imetadatainfo-getfilemapping-method.md)メソッドの呼び出しから返されるファイルマッピングの種類を記述する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="0891a-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0891a-104">構文</span><span class="sxs-lookup"><span data-stu-id="0891a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="0891a-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="0891a-105">Members</span></span>  
  
|<span data-ttu-id="0891a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="0891a-106">Member</span></span>|<span data-ttu-id="0891a-107">説明</span><span class="sxs-lookup"><span data-stu-id="0891a-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="0891a-108">ファイルはデータファイルとしてマップされます。</span><span class="sxs-lookup"><span data-stu-id="0891a-108">The file is mapped as a data file.</span></span> <span data-ttu-id="0891a-109">つまり、フラグは `SEC_IMAGE` Microsoft Win32 関数に渡されませんでした `CreateFileMapping` 。</span><span class="sxs-lookup"><span data-stu-id="0891a-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="0891a-110">`LoadLibrary`関数または関数をフラグと共に使用することで、ファイルは実行用にマップされ `CreateFileMapping` `SEC_IMAGE` ます。</span><span class="sxs-lookup"><span data-stu-id="0891a-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0891a-111">要件</span><span class="sxs-lookup"><span data-stu-id="0891a-111">Requirements</span></span>  

 <span data-ttu-id="0891a-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0891a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0891a-113">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="0891a-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0891a-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0891a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0891a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0891a-115">See also</span></span>

- [<span data-ttu-id="0891a-116">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="0891a-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="0891a-117">GetFileMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="0891a-117">GetFileMapping Method</span></span>](imetadatainfo-getfilemapping-method.md)
