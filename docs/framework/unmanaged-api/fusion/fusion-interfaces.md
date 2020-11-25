---
title: Fusion インターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
ms.openlocfilehash: 59e34a39bada1dcf5e66a0c5b92a7fcbfb41d884
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711690"
---
# <a name="fusion-interfaces"></a><span data-ttu-id="8d851-102">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d851-102">Fusion Interfaces</span></span>

<span data-ttu-id="8d851-103">このセクションでは、アプリケーションのリソースのプロパティにアクセスするために fusion API が使用するアンマネージインターフェイスについて説明し、アプリケーションのリソースの正しいバージョンを特定します。</span><span class="sxs-lookup"><span data-stu-id="8d851-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8d851-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8d851-104">In This Section</span></span>  

 [<span data-ttu-id="8d851-105">IAppIdAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d851-105">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)  
 <span data-ttu-id="8d851-106">アプリケーション id と参照のキーを生成して比較するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="8d851-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="8d851-107">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d851-107">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)  
 <span data-ttu-id="8d851-108">グローバルアセンブリキャッシュの表現を提供します。</span><span class="sxs-lookup"><span data-stu-id="8d851-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="8d851-109">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d851-109">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)  
 <span data-ttu-id="8d851-110">グローバルアセンブリキャッシュ内の1つのアセンブリを表します。</span><span class="sxs-lookup"><span data-stu-id="8d851-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="8d851-111">IAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d851-111">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)  
 <span data-ttu-id="8d851-112">オブジェクトの配列の列挙子を表し `IAssemblyName` ます。</span><span class="sxs-lookup"><span data-stu-id="8d851-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="8d851-113">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d851-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)  
 <span data-ttu-id="8d851-114">アセンブリの一意の id を記述および操作するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="8d851-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="8d851-115">IDefinitionAppId インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d851-115">IDefinitionAppId Interface</span></span>](idefinitionappid-interface.md)  
 <span data-ttu-id="8d851-116">現在のスコープ内のアプリケーションを定義するコードの一意の識別子を表します。</span><span class="sxs-lookup"><span data-stu-id="8d851-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="8d851-117">IDefinitionIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d851-117">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)  
 <span data-ttu-id="8d851-118">現在のスコープ内のアプリケーションを定義するコードの一意の署名を表します。</span><span class="sxs-lookup"><span data-stu-id="8d851-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="8d851-119">IEnumDefinitionIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d851-119">IEnumDefinitionIdentity Interface</span></span>](ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="8d851-120">オブジェクトのコレクションの列挙子として機能し `IDefinitionIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="8d851-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="8d851-121">IEnumIDENTITY_ATTRIBUTE インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d851-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)  
 <span data-ttu-id="8d851-122">現在のスコープ内のコードオブジェクトの属性の列挙子として機能します。</span><span class="sxs-lookup"><span data-stu-id="8d851-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="8d851-123">IEnumReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d851-123">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)  
 <span data-ttu-id="8d851-124">オブジェクトのコレクションの列挙子として機能し `IReferenceIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="8d851-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="8d851-125">IIdentityAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d851-125">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)  
 <span data-ttu-id="8d851-126">コードオブジェクトの id キーを管理します。</span><span class="sxs-lookup"><span data-stu-id="8d851-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="8d851-127">IInstallReferenceEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d851-127">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)  
 <span data-ttu-id="8d851-128">グローバルアセンブリキャッシュにインストールされている参照アセンブリの列挙子を表します。</span><span class="sxs-lookup"><span data-stu-id="8d851-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="8d851-129">IInstallReferenceItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d851-129">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)  
 <span data-ttu-id="8d851-130">グローバルアセンブリキャッシュにインストールされている項目を表します。</span><span class="sxs-lookup"><span data-stu-id="8d851-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="8d851-131">IReferenceAppId インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d851-131">IReferenceAppId Interface</span></span>](ireferenceappid-interface.md)  
 <span data-ttu-id="8d851-132">現在のスコープ内のアプリケーションの一意の識別子への参照を表します。</span><span class="sxs-lookup"><span data-stu-id="8d851-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="8d851-133">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8d851-133">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)  
 <span data-ttu-id="8d851-134">コードオブジェクトの一意の署名への参照を表します。</span><span class="sxs-lookup"><span data-stu-id="8d851-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8d851-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d851-135">Reference</span></span>  

 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="8d851-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d851-136">Related Sections</span></span>  

 [<span data-ttu-id="8d851-137">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="8d851-137">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)  
  
 [<span data-ttu-id="8d851-138">fusion 列挙体</span><span class="sxs-lookup"><span data-stu-id="8d851-138">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="8d851-139">Fusion 構造体</span><span class="sxs-lookup"><span data-stu-id="8d851-139">Fusion Structures</span></span>](fusion-structures.md)
