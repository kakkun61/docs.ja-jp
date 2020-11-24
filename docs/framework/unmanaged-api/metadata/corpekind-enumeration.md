---
title: CorPEKind 列挙型
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
ms.openlocfilehash: 001be0c5e8897bacf76d2a044fb9400768473052
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673528"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="d6137-102">CorPEKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="d6137-102">CorPEKind Enumeration</span></span>

<span data-ttu-id="d6137-103">[IMetaDataImport2:: GetPEKind](imetadataimport2-getpekind-method.md)の呼び出しから返される、ポータブル実行可能 (PE) ファイルを記述する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="d6137-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6137-104">構文</span><span class="sxs-lookup"><span data-stu-id="d6137-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="d6137-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="d6137-105">Members</span></span>  
  
|<span data-ttu-id="d6137-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="d6137-106">Member</span></span>|<span data-ttu-id="d6137-107">説明</span><span class="sxs-lookup"><span data-stu-id="d6137-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="d6137-108">これが PE ファイルではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="d6137-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="d6137-109">この PE ファイルにマネージコードのみが含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="d6137-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="d6137-110">この PE ファイルが Win32 呼び出しを行うことを示します。</span><span class="sxs-lookup"><span data-stu-id="d6137-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="d6137-111">この PE ファイルが64ビットプラットフォームで実行されることを示します。</span><span class="sxs-lookup"><span data-stu-id="d6137-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="d6137-112">この PE ファイルがネイティブコードであることを示します。</span><span class="sxs-lookup"><span data-stu-id="d6137-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="d6137-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="d6137-113">pe32BitPreferred</span></span>|<span data-ttu-id="d6137-114">この PE ファイルがプラットフォームに依存せず、32ビット環境で読み込まれることを示すことを示します。</span><span class="sxs-lookup"><span data-stu-id="d6137-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6137-115">注釈</span><span class="sxs-lookup"><span data-stu-id="d6137-115">Remarks</span></span>  

 <span data-ttu-id="d6137-116">これらの値は、ビットごとの組み合わせで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d6137-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6137-117">要件</span><span class="sxs-lookup"><span data-stu-id="d6137-117">Requirements</span></span>  

 <span data-ttu-id="d6137-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6137-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6137-119">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="d6137-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d6137-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6137-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6137-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6137-121">See also</span></span>

- [<span data-ttu-id="d6137-122">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="d6137-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
