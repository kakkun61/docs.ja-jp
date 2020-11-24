---
title: Fusion グローバル静的関数
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
ms.openlocfilehash: 691fd50e05cadd3f82196fc6ba5df9bb84a66faa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688745"
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="6f3b7-102">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-102">Fusion Global Static Functions</span></span>

<span data-ttu-id="6f3b7-103">このセクションでは、fusion API が使用するアンマネージグローバル静的関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-103">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f3b7-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6f3b7-104">In This Section</span></span>  

 [<span data-ttu-id="6f3b7-105">ClearDownloadCache 関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-105">ClearDownloadCache Function</span></span>](cleardownloadcache-function.md)  
 <span data-ttu-id="6f3b7-106">ダウンロードされたアセンブリのグローバルアセンブリキャッシュを消去します。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-106">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="6f3b7-107">CompareAssemblyIdentity 関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-107">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)  
 <span data-ttu-id="6f3b7-108">2つのアセンブリ id を比較して、それらが等しいかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-108">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="6f3b7-109">CreateApplicationContext 関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-109">CreateApplicationContext Function</span></span>](createapplicationcontext-function.md)  
 <span data-ttu-id="6f3b7-110">内部でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-110">Internal only.</span></span> <span data-ttu-id="6f3b7-111">(この関数は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません)。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-111">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="6f3b7-112">CreateAssemblyCache 関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-112">CreateAssemblyCache Function</span></span>](createassemblycache-function.md)  
 <span data-ttu-id="6f3b7-113">グローバルアセンブリキャッシュを表す新しい [Iassemblycache](iassemblycache-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-113">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="6f3b7-114">CreateAssemblyEnum 関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-114">CreateAssemblyEnum Function</span></span>](createassemblyenum-function.md)  
 <span data-ttu-id="6f3b7-115">指定したアセンブリ内に存在するオブジェクトのリストを表す [Iassemblyenum](iassemblyenum-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-115">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="6f3b7-116">CreateAssemblyNameObject 関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-116">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)  
 <span data-ttu-id="6f3b7-117">指定した名前のアセンブリの一意の id を表す [IAssemblyName](iassemblyname-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-117">Gets a pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="6f3b7-118">CreateHistoryReader 関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-118">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)  
 <span data-ttu-id="6f3b7-119">指定されたファイルの履歴リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-119">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="6f3b7-120">CreateInstallReferenceEnum 関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-120">CreateInstallReferenceEnum Function</span></span>](createinstallreferenceenum-function.md)  
 <span data-ttu-id="6f3b7-121">指定したアセンブリへのアプリケーションの参照のリストを表す [Iinstallreferenceenum](iinstallreferenceenum-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-121">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="6f3b7-122">GetAppIdAuthority 関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-122">GetAppIdAuthority Function</span></span>](getappidauthority-function.md)  
 <span data-ttu-id="6f3b7-123">アプリケーション id と参照のキーを管理する [Iappidauthority](iappidauthority-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-123">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="6f3b7-124">GetAssemblyIdentityFromFile 関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-124">GetAssemblyIdentityFromFile Function</span></span>](getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="6f3b7-125">指定した `IUnknown` `IID` ファイルパスのアセンブリ内で、指定したを持つオブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-125">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="6f3b7-126">GetCachePath 関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-126">GetCachePath Function</span></span>](getcachepath-function.md)  
 <span data-ttu-id="6f3b7-127">指定したフラグを使用して、キャッシュされたアセンブリへのパスを取得します。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-127">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="6f3b7-128">GetHistoryFileDirectory 関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-128">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)  
 <span data-ttu-id="6f3b7-129">アプリケーション履歴ディレクトリのパスを取得します。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-129">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="6f3b7-130">GetIdentityAuthority 関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-130">GetIdentityAuthority Function</span></span>](getidentityauthority-function.md)  
 <span data-ttu-id="6f3b7-131">コードオブジェクトのキーを管理する [Iidentity authority](iidentityauthority-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-131">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="6f3b7-132">IsFrameworkAssembly 関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-132">IsFrameworkAssembly Function</span></span>](isframeworkassembly-function.md)  
 <span data-ttu-id="6f3b7-133">指定したアセンブリが管理されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-133">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="6f3b7-134">NukeDownloadedCache 関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-134">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)  
 <span data-ttu-id="6f3b7-135">共通言語ランタイムのダウンロードキャッシュを削除します。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-135">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="6f3b7-136">PreBindAssemblyEx 関数</span><span class="sxs-lookup"><span data-stu-id="6f3b7-136">PreBindAssemblyEx Function</span></span>](prebindassemblyex-function.md)  
 <span data-ttu-id="6f3b7-137">アセンブリのポリシー後の表示名を取得します。</span><span class="sxs-lookup"><span data-stu-id="6f3b7-137">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6f3b7-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f3b7-138">Related Sections</span></span>  

 [<span data-ttu-id="6f3b7-139">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6f3b7-139">Fusion Interfaces</span></span>](fusion-interfaces.md)  
  
 [<span data-ttu-id="6f3b7-140">fusion 列挙体</span><span class="sxs-lookup"><span data-stu-id="6f3b7-140">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="6f3b7-141">Fusion 構造体</span><span class="sxs-lookup"><span data-stu-id="6f3b7-141">Fusion Structures</span></span>](fusion-structures.md)  
  
 [<span data-ttu-id="6f3b7-142">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="6f3b7-142">Global Assembly Cache</span></span>](../../app-domains/gac.md)
