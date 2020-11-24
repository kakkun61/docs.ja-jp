---
title: IDefinitionAppId インターフェイス
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
ms.openlocfilehash: 1e6c42d8e74d2d3e7925c657c67832f662416e64
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673866"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="01aa8-102">IDefinitionAppId インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01aa8-102">IDefinitionAppId Interface</span></span>

<span data-ttu-id="01aa8-103">現在のスコープ内のアプリケーションを定義するコードの一意の識別子を表します。</span><span class="sxs-lookup"><span data-stu-id="01aa8-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01aa8-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="01aa8-104">Methods</span></span>  
  
|<span data-ttu-id="01aa8-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="01aa8-105">Method</span></span>|<span data-ttu-id="01aa8-106">説明</span><span class="sxs-lookup"><span data-stu-id="01aa8-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="01aa8-107">このオブジェクトのコードを表す書式設定された文字列を取得し `IDefinitionAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="01aa8-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="01aa8-108">このオブジェクトのコード `IDefinitionAppId` を、指定した書式設定された文字列値に設定します。</span><span class="sxs-lookup"><span data-stu-id="01aa8-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="01aa8-109">現在のアプリケーションパス内のアセンブリを格納する [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) オブジェクトへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="01aa8-109">Gets an interface pointer to an [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="01aa8-110">現在のスコープ内のアセンブリのアプリケーションパスを、指定した [IDefinitionIdentity](idefinitionidentity-interface.md) オブジェクトによって参照される値に設定します。</span><span class="sxs-lookup"><span data-stu-id="01aa8-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="01aa8-111">このオブジェクトに対するサブスクリプションのトークン識別子の文字列形式へのポインターを取得し `IDefinitionAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="01aa8-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="01aa8-112">このオブジェクトに対するサブスクリプションのトークン識別子 `IDefinitionAppId` を、指定された文字列値に設定します。</span><span class="sxs-lookup"><span data-stu-id="01aa8-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01aa8-113">要件</span><span class="sxs-lookup"><span data-stu-id="01aa8-113">Requirements</span></span>  

 <span data-ttu-id="01aa8-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01aa8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01aa8-115">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="01aa8-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="01aa8-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01aa8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01aa8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="01aa8-117">See also</span></span>

- [<span data-ttu-id="01aa8-118">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01aa8-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
