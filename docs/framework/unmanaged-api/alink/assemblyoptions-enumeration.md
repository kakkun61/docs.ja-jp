---
title: AssemblyOptions 列挙体
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
ms.openlocfilehash: 352e1acd1fdd8297754e18b2e8c6448ea723a557
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717032"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="8944c-102">AssemblyOptions 列挙体</span><span class="sxs-lookup"><span data-stu-id="8944c-102">AssemblyOptions Enumeration</span></span>

<span data-ttu-id="8944c-103">アセンブリオプションを列挙します。</span><span class="sxs-lookup"><span data-stu-id="8944c-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8944c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8944c-104">Syntax</span></span>  
  
```cpp  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a><span data-ttu-id="8944c-105">フィールド</span><span class="sxs-lookup"><span data-stu-id="8944c-105">Fields</span></span>  
  
|<span data-ttu-id="8944c-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="8944c-106">Field</span></span>|<span data-ttu-id="8944c-107">説明</span><span class="sxs-lookup"><span data-stu-id="8944c-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8944c-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="8944c-108">optAssemTitle</span></span>|<span data-ttu-id="8944c-109">String-アセンブリのタイトルを表します。</span><span class="sxs-lookup"><span data-stu-id="8944c-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="8944c-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="8944c-110">optAssemDescription</span></span>|<span data-ttu-id="8944c-111">String-アセンブリの説明が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8944c-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="8944c-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="8944c-112">optAssemConfig</span></span>|<span data-ttu-id="8944c-113">String-アセンブリ構成が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8944c-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="8944c-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="8944c-114">optAssemOS</span></span>|<span data-ttu-id="8944c-115">"DwOSPlatformId" としてエンコードされた文字列。</span><span class="sxs-lookup"><span data-stu-id="8944c-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="8944c-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="8944c-116">optAssemProcessor</span></span>|<span data-ttu-id="8944c-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="8944c-117">ULONG</span></span>|  
|<span data-ttu-id="8944c-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="8944c-118">optAssemLocale</span></span>|<span data-ttu-id="8944c-119">String-アセンブリロケールを格納します。</span><span class="sxs-lookup"><span data-stu-id="8944c-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="8944c-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="8944c-120">optAssemVersion</span></span>|<span data-ttu-id="8944c-121">"Major. Minor. Build. Revision" としてエンコードされた文字列。</span><span class="sxs-lookup"><span data-stu-id="8944c-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="8944c-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="8944c-122">optAssemCompany</span></span>|<span data-ttu-id="8944c-123">文字列-会社を含みます。</span><span class="sxs-lookup"><span data-stu-id="8944c-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="8944c-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="8944c-124">optAssemProduct</span></span>|<span data-ttu-id="8944c-125">文字列-製品名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8944c-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="8944c-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="8944c-126">optAssemProductVersion</span></span>|<span data-ttu-id="8944c-127">文字列 (InformationalVersion とも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="8944c-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="8944c-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="8944c-128">optAssemCopyright</span></span>|<span data-ttu-id="8944c-129">文字列-著作権情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8944c-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="8944c-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="8944c-130">optAssemTrademark</span></span>|<span data-ttu-id="8944c-131">String-商標情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8944c-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="8944c-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="8944c-132">optAssemKeyFile</span></span>|<span data-ttu-id="8944c-133">文字列 (ファイル名)。</span><span class="sxs-lookup"><span data-stu-id="8944c-133">String (file name).</span></span>|  
|<span data-ttu-id="8944c-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="8944c-134">optAssemKeyName</span></span>|<span data-ttu-id="8944c-135">文字列 (キー名)。</span><span class="sxs-lookup"><span data-stu-id="8944c-135">String (The key name).</span></span>|  
|<span data-ttu-id="8944c-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="8944c-136">optAssemAlgID</span></span>|<span data-ttu-id="8944c-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="8944c-137">ULONG</span></span>|  
|<span data-ttu-id="8944c-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="8944c-138">optAssemFlags</span></span>|<span data-ttu-id="8944c-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="8944c-139">ULONG</span></span>|  
|<span data-ttu-id="8944c-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="8944c-140">optAssemHalfSign</span></span>|<span data-ttu-id="8944c-141">Bool (DelaySign とも呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="8944c-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="8944c-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="8944c-142">optAssemFileVersion</span></span>|<span data-ttu-id="8944c-143">"Major. Minor. Build. Revision" としてエンコードされた文字列。 ProductVersion と同じです。</span><span class="sxs-lookup"><span data-stu-id="8944c-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="8944c-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="8944c-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="8944c-145">"Major. Minor. Build. Revision" としてエンコードされた文字列。</span><span class="sxs-lookup"><span data-stu-id="8944c-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="8944c-146">optlastassemoopt</span><span class="sxs-lookup"><span data-stu-id="8944c-146">optLastAssemOption</span></span>|<span data-ttu-id="8944c-147">要素数のカウンター。</span><span class="sxs-lookup"><span data-stu-id="8944c-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8944c-148">要件</span><span class="sxs-lookup"><span data-stu-id="8944c-148">Requirements</span></span>  

 <span data-ttu-id="8944c-149">**ヘッダー:** alink</span><span class="sxs-lookup"><span data-stu-id="8944c-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="8944c-150">**ライブラリ**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="8944c-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8944c-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="8944c-151">See also</span></span>

- [<span data-ttu-id="8944c-152">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="8944c-152">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
