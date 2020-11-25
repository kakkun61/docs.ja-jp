---
title: IAssemblyName インターフェイス
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
ms.openlocfilehash: f6feed9f59715f9a2801cd3a2a99a087957d4377
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715070"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="851de-102">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="851de-102">IAssemblyName Interface</span></span>

<span data-ttu-id="851de-103">アセンブリの一意の id を記述および操作するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="851de-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="851de-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="851de-104">Methods</span></span>  
  
|<span data-ttu-id="851de-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="851de-105">Method</span></span>|<span data-ttu-id="851de-106">説明</span><span class="sxs-lookup"><span data-stu-id="851de-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="851de-107">Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="851de-107">Clone Method</span></span>](iassemblyname-clone-method.md)|<span data-ttu-id="851de-108">このオブジェクトの簡易コピーを作成し `IAssemblyName` ます。</span><span class="sxs-lookup"><span data-stu-id="851de-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="851de-109">Finalize メソッド</span><span class="sxs-lookup"><span data-stu-id="851de-109">Finalize Method</span></span>](iassemblyname-finalize-method.md)|<span data-ttu-id="851de-110">このオブジェクトが、 `IAssemblyName` デストラクターが呼び出される前にリソースを解放し、その他のクリーンアップ操作を実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="851de-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="851de-111">GetDisplayName メソッド</span><span class="sxs-lookup"><span data-stu-id="851de-111">GetDisplayName Method</span></span>](iassemblyname-getdisplayname-method.md)|<span data-ttu-id="851de-112">このオブジェクトによって参照されるアセンブリの、人間が判読できる名前を取得し `IAssemblyName` ます。</span><span class="sxs-lookup"><span data-stu-id="851de-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="851de-113">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="851de-113">GetName Method</span></span>](iassemblyname-getname-method.md)|<span data-ttu-id="851de-114">このオブジェクトによって参照されるアセンブリの単純な、暗号化されていない名前を取得し `IAssemblyName` ます。</span><span class="sxs-lookup"><span data-stu-id="851de-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="851de-115">GetProperty メソッド</span><span class="sxs-lookup"><span data-stu-id="851de-115">GetProperty Method</span></span>](iassemblyname-getproperty-method.md)|<span data-ttu-id="851de-116">指定したによって参照されるプロパティへのポインターを取得し `PropertyId` ます。</span><span class="sxs-lookup"><span data-stu-id="851de-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="851de-117">GetVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="851de-117">GetVersion Method</span></span>](iassemblyname-getversion-method.md)|<span data-ttu-id="851de-118">このオブジェクトによって参照されるアセンブリのバージョン情報を取得し `IAssemblyName` ます。</span><span class="sxs-lookup"><span data-stu-id="851de-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="851de-119">IsEqual メソッド</span><span class="sxs-lookup"><span data-stu-id="851de-119">IsEqual Method</span></span>](iassemblyname-isequal-method.md)|<span data-ttu-id="851de-120">指定した `IAssemblyName` `IAssemblyName` 比較フラグに基づいて、指定したオブジェクトがこのと等しいかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="851de-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="851de-121">SetProperty メソッド</span><span class="sxs-lookup"><span data-stu-id="851de-121">SetProperty Method</span></span>](iassemblyname-setproperty-method.md)|<span data-ttu-id="851de-122">指定したによって参照されるプロパティの値を設定 `PropertyId` します。</span><span class="sxs-lookup"><span data-stu-id="851de-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="851de-123">要件</span><span class="sxs-lookup"><span data-stu-id="851de-123">Requirements</span></span>  

 <span data-ttu-id="851de-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="851de-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="851de-125">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="851de-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="851de-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="851de-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="851de-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="851de-127">See also</span></span>

- [<span data-ttu-id="851de-128">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="851de-128">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="851de-129">IAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="851de-129">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
