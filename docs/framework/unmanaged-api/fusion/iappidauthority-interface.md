---
title: IAppIdAuthority インターフェイス
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
ms.openlocfilehash: a344f2ab5d9a7aa92018c47ee7a162cd1721aeb5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732113"
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="61247-102">IAppIdAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="61247-102">IAppIdAuthority Interface</span></span>

<span data-ttu-id="61247-103">アプリケーション id と参照のキーを生成して比較するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="61247-103">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="61247-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="61247-104">Methods</span></span>  
  
|<span data-ttu-id="61247-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="61247-105">Method</span></span>|<span data-ttu-id="61247-106">説明</span><span class="sxs-lookup"><span data-stu-id="61247-106">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="61247-107">指定した2つの [IDefinitionAppId](idefinitionappid-interface.md) インスタンスが等しいかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="61247-107">Gets a value that indicates whether the two specified [IDefinitionAppId](idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="61247-108">フラグ値 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION を渡して、それぞれのバージョン情報を無視することができます。</span><span class="sxs-lookup"><span data-stu-id="61247-108">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="61247-109">指定した2つの [IReferenceAppId](ireferenceappid-interface.md) インスタンスが等しいかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="61247-109">Gets a value that indicates whether the two specified [IReferenceAppId](ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="61247-110">フラグ値 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION を渡して、それぞれのバージョン情報を無視することができます。</span><span class="sxs-lookup"><span data-stu-id="61247-110">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="61247-111">指定した2つの文字列定義が等しいかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="61247-111">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="61247-112">フラグ値 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION を渡して、それぞれのバージョン情報を無視することができます。</span><span class="sxs-lookup"><span data-stu-id="61247-112">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="61247-113">指定した2つの文字列参照が等しいかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="61247-113">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="61247-114">フラグ値 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION を渡して、それぞれのバージョン情報を無視することができます。</span><span class="sxs-lookup"><span data-stu-id="61247-114">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="61247-115">現在のスコープ内のアセンブリを表す、新しく生成されたインスタンスへのインターフェイスポインターを取得し `IDefinitionAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="61247-115">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="61247-116">現在のスコープ内のアセンブリを表す、新しく作成されたへのインターフェイスポインターを取得し `IReferenceAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="61247-116">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="61247-117">指定した `IDefinitionAppId` フラグ値を使用して、指定したの文字列バージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="61247-117">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="61247-118">指定した `IDefinitionAppId` とが同じアセンブリを表しているかどうかを示す値を取得し `IReferenceAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="61247-118">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="61247-119">指定した定義文字列と参照文字列が同じアセンブリを表しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="61247-119">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="61247-120">指定したインスタンスを表す文字列キーを取得し `IDefinitionAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="61247-120">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="61247-121">指定したインスタンスを表す文字列キーを取得し `IReferenceAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="61247-121">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="61247-122">指定したインスタンスのハッシュキーを取得し `IDefinitionAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="61247-122">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="61247-123">指定したインスタンスのハッシュキーを取得し `IReferenceAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="61247-123">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="61247-124">指定した `IReferenceAppId` フラグ値を使用して、指定したの文字列バージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="61247-124">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="61247-125">`IDefinitionAppId`指定した文字列キーによって参照されるアセンブリを表すインスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="61247-125">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="61247-126">`IReferenceAppId`指定した文字列キーによって参照されるアセンブリを表すインスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="61247-126">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61247-127">要件</span><span class="sxs-lookup"><span data-stu-id="61247-127">Requirements</span></span>  

 <span data-ttu-id="61247-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61247-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61247-129">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="61247-129">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="61247-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61247-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61247-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="61247-131">See also</span></span>

- [<span data-ttu-id="61247-132">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="61247-132">Fusion Interfaces</span></span>](fusion-interfaces.md)
