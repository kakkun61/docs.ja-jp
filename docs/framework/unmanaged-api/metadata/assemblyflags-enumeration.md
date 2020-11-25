---
title: AssemblyFlags 列挙体
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
ms.openlocfilehash: 561b4d68a574a2859286fb5f2e2d950518a9d29d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732781"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="b258e-102">AssemblyFlags 列挙体</span><span class="sxs-lookup"><span data-stu-id="b258e-102">AssemblyFlags Enumeration</span></span>

<span data-ttu-id="b258e-103">アセンブリのランタイム機能を記述する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="b258e-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b258e-104">構文</span><span class="sxs-lookup"><span data-stu-id="b258e-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="b258e-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="b258e-105">Members</span></span>  
  
|<span data-ttu-id="b258e-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b258e-106">Member</span></span>|<span data-ttu-id="b258e-107">説明</span><span class="sxs-lookup"><span data-stu-id="b258e-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="b258e-108">エクスポートされた型定義が、アセンブリを構成するファイル内で暗黙的に指定されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b258e-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="b258e-109">.NET Framework バージョン1.0 および1.1 では、この値は常に設定されると想定されます。</span><span class="sxs-lookup"><span data-stu-id="b258e-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="b258e-110">アセンブリを構成するファイル内でリソース定義が暗黙的であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b258e-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="b258e-111">.NET Framework 1.0 および1.1 では、この値は常に設定されると想定されます。</span><span class="sxs-lookup"><span data-stu-id="b258e-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="b258e-112">アセンブリが同じアプリケーションドメインで実行されている場合、その他のバージョンでは実行できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="b258e-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="b258e-113">同じプロセスで実行されている場合、アセンブリを他のバージョンと一緒に実行できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="b258e-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="b258e-114">アセンブリが同じコンピューター上で実行されている場合、その他のバージョンでは実行できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="b258e-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b258e-115">注釈</span><span class="sxs-lookup"><span data-stu-id="b258e-115">Remarks</span></span>  

 <span data-ttu-id="b258e-116">0x0010 と0x0070 の間の値は、参照アセンブリのサイドバイサイドの互換性機能を記述するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b258e-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="b258e-117">これらの値のいずれも設定されていない場合、アセンブリはサイドバイサイドで互換性があると見なされます。</span><span class="sxs-lookup"><span data-stu-id="b258e-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b258e-118">要件</span><span class="sxs-lookup"><span data-stu-id="b258e-118">Requirements</span></span>  

 <span data-ttu-id="b258e-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b258e-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b258e-120">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b258e-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="b258e-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b258e-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b258e-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b258e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b258e-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="b258e-123">See also</span></span>

- [<span data-ttu-id="b258e-124">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="b258e-124">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="b258e-125">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b258e-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
