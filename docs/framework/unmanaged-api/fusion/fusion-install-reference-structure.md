---
title: FUSION_INSTALL_REFERENCE 構造体
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
ms.openlocfilehash: d5ff08e62b94d7f164b103ae0535bb62e4e60aea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688810"
---
# <a name="fusion_install_reference-structure"></a><span data-ttu-id="b2a91-102">FUSION_INSTALL_REFERENCE 構造体</span><span class="sxs-lookup"><span data-stu-id="b2a91-102">FUSION_INSTALL_REFERENCE Structure</span></span>

<span data-ttu-id="b2a91-103">アプリケーションがグローバルアセンブリキャッシュにインストールしたアセンブリに対して行う参照を表します。</span><span class="sxs-lookup"><span data-stu-id="b2a91-103">Represents a reference that an application makes to an assembly that the application has installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2a91-104">構文</span><span class="sxs-lookup"><span data-stu-id="b2a91-104">Syntax</span></span>  
  
```cpp  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="b2a91-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="b2a91-105">Members</span></span>  
  
|<span data-ttu-id="b2a91-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b2a91-106">Member</span></span>|<span data-ttu-id="b2a91-107">説明</span><span class="sxs-lookup"><span data-stu-id="b2a91-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="b2a91-108">構造体のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="b2a91-108">The size of the structure in bytes.</span></span>|  
|`dwFlags`|<span data-ttu-id="b2a91-109">将来の拡張のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="b2a91-109">Reserved for future extensibility.</span></span> <span data-ttu-id="b2a91-110">この値は 0 (ゼロ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2a91-110">This value must be 0 (zero).</span></span>|  
|`guidScheme`|<span data-ttu-id="b2a91-111">参照を追加するエンティティ。</span><span class="sxs-lookup"><span data-stu-id="b2a91-111">The entity that adds the reference.</span></span> <span data-ttu-id="b2a91-112">このフィールドには、次のいずれかの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b2a91-112">This field can have one of the following values:</span></span><br /><br /> <span data-ttu-id="b2a91-113">-FUSION_REFCOUNT_MSI_GUID: アセンブリは、Microsoft Windows インストーラーを使用してインストールされたアプリケーションによって参照されています。</span><span class="sxs-lookup"><span data-stu-id="b2a91-113">-   FUSION_REFCOUNT_MSI_GUID: The assembly is referenced by an application that was installed using the Microsoft Windows Installer.</span></span> <span data-ttu-id="b2a91-114">`szIdentifier`フィールドはに設定され、 `MSI` `szNonCanonicalData` フィールドはに設定され `Windows Installer` ます。</span><span class="sxs-lookup"><span data-stu-id="b2a91-114">The `szIdentifier` field is set to `MSI`, and the `szNonCanonicalData` field is set to `Windows Installer`.</span></span> <span data-ttu-id="b2a91-115">このスキームは、Windows サイドバイサイドアセンブリに使用されます。</span><span class="sxs-lookup"><span data-stu-id="b2a91-115">This scheme is used for Windows side-by-side assemblies.</span></span><br /><span data-ttu-id="b2a91-116">-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: アセンブリは、[ **プログラムの追加と削除** ] インターフェイスに表示されるアプリケーションによって参照されています。</span><span class="sxs-lookup"><span data-stu-id="b2a91-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: The assembly is referenced by an application that appears in the **Add/Remove Programs** interface.</span></span> <span data-ttu-id="b2a91-117">`szIdentifier`フィールドは、アプリケーションを [**プログラムの追加と削除**] インターフェイスに登録するトークンを提供します。</span><span class="sxs-lookup"><span data-stu-id="b2a91-117">The `szIdentifier` field provides the token that registers the application with the **Add/Remove Programs** interface.</span></span><br /><span data-ttu-id="b2a91-118">-FUSION_REFCOUNT_FILEPATH_GUID: アセンブリは、ファイルシステム内のファイルによって表されるアプリケーションによって参照されています。</span><span class="sxs-lookup"><span data-stu-id="b2a91-118">-   FUSION_REFCOUNT_FILEPATH_GUID: The assembly is referenced by an application that is represented by a file in the file system.</span></span> <span data-ttu-id="b2a91-119">`szIdentifier`フィールドには、このファイルへのパスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2a91-119">The `szIdentifier` field provides the path to this file.</span></span><br /><span data-ttu-id="b2a91-120">-FUSION_REFCOUNT_OPAQUE_STRING_GUID: アセンブリは、不透明な文字列によってのみ表されるアプリケーションによって参照されています。</span><span class="sxs-lookup"><span data-stu-id="b2a91-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: The assembly is referenced by an application that is represented only by an opaque string.</span></span> <span data-ttu-id="b2a91-121">フィールドは、 `szIdentifier` この不透明な文字列を提供します。</span><span class="sxs-lookup"><span data-stu-id="b2a91-121">The `szIdentifier` field provides this opaque string.</span></span> <span data-ttu-id="b2a91-122">グローバルアセンブリキャッシュは、この値を削除するときに、不透明な参照が存在するかどうかを確認しません。</span><span class="sxs-lookup"><span data-stu-id="b2a91-122">The global assembly cache does not check for the existence of opaque references when you remove this value.</span></span><br /><span data-ttu-id="b2a91-123">-FUSION_REFCOUNT_OSINSTALL_GUID: この値は予約されています。</span><span class="sxs-lookup"><span data-stu-id="b2a91-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: This value is reserved.</span></span>|  
|`szIdentifier`|<span data-ttu-id="b2a91-124">グローバルアセンブリキャッシュにアセンブリをインストールしたアプリケーションを識別する一意の文字列。</span><span class="sxs-lookup"><span data-stu-id="b2a91-124">A unique string that identifies the application that installed the assembly in the global assembly cache.</span></span> <span data-ttu-id="b2a91-125">値は、フィールドの値によって異なり `guidScheme` ます。</span><span class="sxs-lookup"><span data-stu-id="b2a91-125">Its value depends upon the value of the `guidScheme` field.</span></span>|  
|`szNonCanonicalData`|<span data-ttu-id="b2a91-126">参照を追加するエンティティによってのみ認識される文字列。</span><span class="sxs-lookup"><span data-stu-id="b2a91-126">A string that is understood only by the entity that adds the reference.</span></span> <span data-ttu-id="b2a91-127">グローバルアセンブリキャッシュはこの文字列を格納しますが、この文字列は使用しません。</span><span class="sxs-lookup"><span data-stu-id="b2a91-127">The global assembly cache stores this string, but does not use it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2a91-128">要件</span><span class="sxs-lookup"><span data-stu-id="b2a91-128">Requirements</span></span>  

 <span data-ttu-id="b2a91-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2a91-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2a91-130">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b2a91-130">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b2a91-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2a91-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a91-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2a91-132">See also</span></span>

- [<span data-ttu-id="b2a91-133">Fusion 構造体</span><span class="sxs-lookup"><span data-stu-id="b2a91-133">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="b2a91-134">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="b2a91-134">Global Assembly Cache</span></span>](../../app-domains/gac.md)
