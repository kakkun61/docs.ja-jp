---
title: CorOpenFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
ms.openlocfilehash: e676547d20dc9535241150d24b65e1fbaf9e89ab
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725106"
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="10730-102">CorOpenFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="10730-102">CorOpenFlags Enumeration</span></span>

<span data-ttu-id="10730-103">マニフェスト ファイルを開くときにメタデータの動作を制御するフラグ値を含めます。</span><span class="sxs-lookup"><span data-stu-id="10730-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10730-104">構文</span><span class="sxs-lookup"><span data-stu-id="10730-104">Syntax</span></span>  
  
```cpp  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="10730-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="10730-105">Members</span></span>  
  
|<span data-ttu-id="10730-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="10730-106">Member</span></span>|<span data-ttu-id="10730-107">説明</span><span class="sxs-lookup"><span data-stu-id="10730-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="10730-108">ファイルが読み取り専用で開かれることを示します。</span><span class="sxs-lookup"><span data-stu-id="10730-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="10730-109">ファイルが書き込み用に開かれることを示します。</span><span class="sxs-lookup"><span data-stu-id="10730-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="10730-110">.winmd ファイルを開くときに `ofWrite` フラグを使用する場合は、`ofNoTransform` フラグも渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="10730-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="10730-111">読み取りおよび書き込み用のマスク。</span><span class="sxs-lookup"><span data-stu-id="10730-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="10730-112">ファイルがメモリ内に読み込まれることを示します。</span><span class="sxs-lookup"><span data-stu-id="10730-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="10730-113">メタデータは自身のコピーを保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="10730-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="10730-114">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="10730-114">Obsolete.</span></span> <span data-ttu-id="10730-115">このフラグは無視されます。</span><span class="sxs-lookup"><span data-stu-id="10730-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="10730-116">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="10730-116">Obsolete.</span></span> <span data-ttu-id="10730-117">このフラグは無視されます。</span><span class="sxs-lookup"><span data-stu-id="10730-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="10730-118">は、ファイルを読み取り用に開く必要があること、および IMetaDataEmit に対するの呼び出しを行うことができないことを示し `QueryInterface` ます。 [IMetaDataEmit](imetadataemit-interface.md)</span><span class="sxs-lookup"><span data-stu-id="10730-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="10730-119">[CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc)への呼び出しを使用してメモリが割り当てられ、メタデータによって解放されることを示します。</span><span class="sxs-lookup"><span data-stu-id="10730-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="10730-120">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="10730-120">Obsolete.</span></span> <span data-ttu-id="10730-121">このフラグは無視されます。</span><span class="sxs-lookup"><span data-stu-id="10730-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="10730-122">.winmd ファイルの自動変換を無効にする必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="10730-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="10730-123">つまり、Windows Runtime タイプから .NET Framework タイプへの投射は無効になります。</span><span class="sxs-lookup"><span data-stu-id="10730-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="10730-124">詳細については、「 [Windows ランタイムと CLR-.net と Windows ランタイム](/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10730-124">For more information, see [Windows Runtime and the CLR - Underneath the Hood with .NET and the Windows Runtime](/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).</span></span>|  
|`ofReserved1`|<span data-ttu-id="10730-125">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="10730-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="10730-126">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="10730-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="10730-127">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="10730-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10730-128">要件</span><span class="sxs-lookup"><span data-stu-id="10730-128">Requirements</span></span>  

 <span data-ttu-id="10730-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10730-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10730-130">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="10730-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="10730-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10730-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10730-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="10730-132">See also</span></span>

- [<span data-ttu-id="10730-133">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="10730-133">Metadata Enumerations</span></span>](metadata-enumerations.md)
