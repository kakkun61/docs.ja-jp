---
title: IXCLRDataProcess インターフェイス
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 376ec2b840bc17c79ed1f27c17a8ddd22c37a0f4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245355"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="36860-102">IXCLRDataProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="36860-102">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="36860-103">プロセスに関する情報を照会するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="36860-103">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="36860-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="36860-104">Methods</span></span>

| <span data-ttu-id="36860-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="36860-105">Method</span></span>                                                                                                                                               | <span data-ttu-id="36860-106">説明</span><span class="sxs-lookup"><span data-stu-id="36860-106">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="36860-107">GetRuntimeNameByAddress</span><span class="sxs-lookup"><span data-stu-id="36860-107">GetRuntimeNameByAddress</span></span>](ixclrdataprocess-getruntimenamebyaddress-method.md)                     | <span data-ttu-id="36860-108">指定されたアドレスの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="36860-108">Gets a name for the given address.</span></span>                                                               |
| [<span data-ttu-id="36860-109">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="36860-109">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="36860-110">`AppDomain`プロセス内のを一意の id で取得します。</span><span class="sxs-lookup"><span data-stu-id="36860-110">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="36860-111">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="36860-111">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="36860-112">プロセスのモジュールを列挙するハンドルを提供します。</span><span class="sxs-lookup"><span data-stu-id="36860-112">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="36860-113">EnumModule</span><span class="sxs-lookup"><span data-stu-id="36860-113">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="36860-114">このプロセスのモジュールを列挙します。</span><span class="sxs-lookup"><span data-stu-id="36860-114">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="36860-115">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="36860-115">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="36860-116">モジュールの列挙中に使用される内部反復子によって使用されるリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="36860-116">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="36860-117">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="36860-117">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="36860-118">指定されたアドレスから開始するのメソッドインスタンスを列挙するハンドルを提供し `AppDomain` ます。</span><span class="sxs-lookup"><span data-stu-id="36860-118">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="36860-119">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="36860-119">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="36860-120">このプロセスのメソッドインスタンスを、アドレスオフセットを開始位置として列挙します。</span><span class="sxs-lookup"><span data-stu-id="36860-120">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="36860-121">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="36860-121">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="36860-122">インスタンスの列挙中に使用される内部反復子によって使用されるリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="36860-122">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="36860-123">解説</span><span class="sxs-lookup"><span data-stu-id="36860-123">Remarks</span></span>

<span data-ttu-id="36860-124">このインターフェイスはランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="36860-124">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="36860-125">ただし、これは、 `IUnknown` `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` 通常の com 機構を通じて取得できる GUID を使用してから派生する com インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="36860-125">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="36860-126">要件</span><span class="sxs-lookup"><span data-stu-id="36860-126">Requirements</span></span>

<span data-ttu-id="36860-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36860-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="36860-128">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="36860-128">**Header:** None</span></span>  
<span data-ttu-id="36860-129">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="36860-129">**Library:** None</span></span>  
<span data-ttu-id="36860-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="36860-130">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="36860-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="36860-131">See also</span></span>

- [<span data-ttu-id="36860-132">デバッグ</span><span class="sxs-lookup"><span data-stu-id="36860-132">Debugging</span></span>](index.md)
- [<span data-ttu-id="36860-133">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="36860-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
