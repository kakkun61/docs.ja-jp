---
title: OSINFO 構造体
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
ms.openlocfilehash: 49e29cc0367d5162dffcd641b163fd7b9a56ffd0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672891"
---
# <a name="osinfo-structure"></a><span data-ttu-id="93ba8-102">OSINFO 構造体</span><span class="sxs-lookup"><span data-stu-id="93ba8-102">OSINFO Structure</span></span>

<span data-ttu-id="93ba8-103">アセンブリまたはモジュールのオペレーティングシステムの詳細が含まれています。</span><span class="sxs-lookup"><span data-stu-id="93ba8-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93ba8-104">構文</span><span class="sxs-lookup"><span data-stu-id="93ba8-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="93ba8-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="93ba8-105">Members</span></span>  
  
|<span data-ttu-id="93ba8-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="93ba8-106">Member</span></span>|<span data-ttu-id="93ba8-107">説明</span><span class="sxs-lookup"><span data-stu-id="93ba8-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="93ba8-108">Microsoft Windows プラットフォーム関数によって定義された識別子の値の1つ `GetVersionEx` 。</span><span class="sxs-lookup"><span data-stu-id="93ba8-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="93ba8-109">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="93ba8-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="93ba8-110">-VER_PLATFORM_WIN32s、または0x0000。 Microsoft Windows 3.1 を指定します。</span><span class="sxs-lookup"><span data-stu-id="93ba8-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="93ba8-111">-VER_PLATFORM_WIN32_WINDOWS、または0x0001 を指定して、Windows 95、Windows 98、またはそれらから派生したオペレーティングシステムを指定します。</span><span class="sxs-lookup"><span data-stu-id="93ba8-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="93ba8-112">-VER_PLATFORM_WIN32_NT、または0x0002 を指定して、Windows NT またはそれからのオペレーティングシステムを指定します。</span><span class="sxs-lookup"><span data-stu-id="93ba8-112">-   VER_PLATFORM_WIN32_NT, or 0x0002, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="93ba8-113">オペレーティングシステムのメジャーバージョン。任意のバージョンを示す NULL 値。</span><span class="sxs-lookup"><span data-stu-id="93ba8-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="93ba8-114">オペレーティングシステムのマイナーバージョン。任意のバージョンを示す NULL 値。</span><span class="sxs-lookup"><span data-stu-id="93ba8-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93ba8-115">注釈</span><span class="sxs-lookup"><span data-stu-id="93ba8-115">Remarks</span></span>  

 <span data-ttu-id="93ba8-116">`OSINFO` は `OSVERSIONINFOEX` 、Microsoft Windows プラットフォーム関数の呼び出しで使用される構造に基づいてい `GetVersionEx` ます。</span><span class="sxs-lookup"><span data-stu-id="93ba8-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="93ba8-117">この構造体は、そのオペレーティングシステムのサポートを示すために ASSEMBLYMETADATA 構造体によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="93ba8-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93ba8-118">要件</span><span class="sxs-lookup"><span data-stu-id="93ba8-118">Requirements</span></span>  

 <span data-ttu-id="93ba8-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93ba8-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93ba8-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="93ba8-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="93ba8-121">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="93ba8-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="93ba8-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93ba8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93ba8-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="93ba8-123">See also</span></span>

- [<span data-ttu-id="93ba8-124">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="93ba8-124">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="93ba8-125">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93ba8-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
