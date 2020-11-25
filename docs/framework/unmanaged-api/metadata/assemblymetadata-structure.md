---
title: ASSEMBLYMETADATA 構造体
ms.date: 03/30/2017
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
ms.openlocfilehash: 8071c3f43775975de37e3255582b6fc8f13f7de3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732789"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="1fde3-102">ASSEMBLYMETADATA 構造体</span><span class="sxs-lookup"><span data-stu-id="1fde3-102">ASSEMBLYMETADATA Structure</span></span>

<span data-ttu-id="1fde3-103">バージョン、ロケール、プロセッサ、オペレーティングシステムのサポートレベルなど、参照されるアセンブリに関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="1fde3-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fde3-104">構文</span><span class="sxs-lookup"><span data-stu-id="1fde3-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a><span data-ttu-id="1fde3-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="1fde3-105">Members</span></span>  
  
|<span data-ttu-id="1fde3-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1fde3-106">Member</span></span>|<span data-ttu-id="1fde3-107">説明</span><span class="sxs-lookup"><span data-stu-id="1fde3-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="1fde3-108">参照アセンブリのメジャーバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="1fde3-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="1fde3-109">この値を0にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1fde3-109">This value cannot be zero.</span></span> <span data-ttu-id="1fde3-110">のすべてのビットが設定されている場合は、 `usMajorVersion` メジャーバージョンが指定されていません。</span><span class="sxs-lookup"><span data-stu-id="1fde3-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="1fde3-111">参照アセンブリのマイナーバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="1fde3-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="1fde3-112">この値を0にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1fde3-112">This value cannot be zero.</span></span> <span data-ttu-id="1fde3-113">のすべてのビットが設定されている場合は、 `usMinorVersion` マイナーバージョンが指定されていません。</span><span class="sxs-lookup"><span data-stu-id="1fde3-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="1fde3-114">参照アセンブリのビルド番号。</span><span class="sxs-lookup"><span data-stu-id="1fde3-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="1fde3-115">この値を0にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1fde3-115">This value cannot be zero.</span></span> <span data-ttu-id="1fde3-116">のすべてのビットが設定されている場合は、 `usBuildNumber` ビルド番号が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="1fde3-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="1fde3-117">参照アセンブリのリビジョン番号。</span><span class="sxs-lookup"><span data-stu-id="1fde3-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="1fde3-118">この値を0にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1fde3-118">This value cannot be zero.</span></span> <span data-ttu-id="1fde3-119">のすべてのビットが設定されている場合は、 `usRevisionNumber` リビジョン番号が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="1fde3-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="1fde3-120">RFC1766 仕様に準拠しているロケール名のリスト。セミコロンで区切られ、参照アセンブリによってサポートされるロケールを指定します。</span><span class="sxs-lookup"><span data-stu-id="1fde3-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="1fde3-121">Null 値は、ロケールに依存しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="1fde3-121">A null value indicates locale independence.</span></span> <span data-ttu-id="1fde3-122">**注:**  .NET Framework バージョン1.0 では、複数のロケールを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="1fde3-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="1fde3-123">のワイド文字のサイズ `szLocale` 。</span><span class="sxs-lookup"><span data-stu-id="1fde3-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="1fde3-124">参照アセンブリでサポートされているプロセッサの種類について、Winnt.h で定義されている識別子の配列。</span><span class="sxs-lookup"><span data-stu-id="1fde3-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="1fde3-125">NULL 値は、プロセッサに依存しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="1fde3-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="1fde3-126">`rdwProcessor` 配列の長さ。</span><span class="sxs-lookup"><span data-stu-id="1fde3-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="1fde3-127">参照アセンブリによってサポートされているオペレーティングシステムを指定する [Osinfo](osinfo-structure.md) インスタンスの配列。</span><span class="sxs-lookup"><span data-stu-id="1fde3-127">An array of [OSINFO](osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="1fde3-128">NULL 値は、オペレーティングシステムに依存しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="1fde3-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="1fde3-129">`rOS` 配列の長さ。</span><span class="sxs-lookup"><span data-stu-id="1fde3-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1fde3-130">要件</span><span class="sxs-lookup"><span data-stu-id="1fde3-130">Requirements</span></span>  

 <span data-ttu-id="1fde3-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fde3-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fde3-132">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="1fde3-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1fde3-133">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="1fde3-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1fde3-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fde3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fde3-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="1fde3-135">See also</span></span>

- [<span data-ttu-id="1fde3-136">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="1fde3-136">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="1fde3-137">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1fde3-137">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="1fde3-138">OSINFO 構造体</span><span class="sxs-lookup"><span data-stu-id="1fde3-138">OSINFO Structure</span></span>](osinfo-structure.md)
