---
title: CoInitializeEE 関数
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
ms.openlocfilehash: 707e182e62f4a7b7b813e6b288c6825b0d3d2eab
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731752"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="87aaa-102">CoInitializeEE 関数</span><span class="sxs-lookup"><span data-stu-id="87aaa-102">CoInitializeEE Function</span></span>

<span data-ttu-id="87aaa-103">共通言語ランタイムの実行エンジンが確実にプロセスに読み込まれるようにします。</span><span class="sxs-lookup"><span data-stu-id="87aaa-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="87aaa-104">この関数は .NET Framework 4 では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="87aaa-104">This function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="87aaa-105">代わりに [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="87aaa-105">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87aaa-106">構文</span><span class="sxs-lookup"><span data-stu-id="87aaa-106">Syntax</span></span>  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87aaa-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="87aaa-107">Parameters</span></span>  

 `fFlags`  
 <span data-ttu-id="87aaa-108">から [Coinitiee](../metadata/coinitiee-enumeration.md) 列挙定数の1つ。</span><span class="sxs-lookup"><span data-stu-id="87aaa-108">[in] One of the [COINITIEE](../metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87aaa-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="87aaa-109">Return Value</span></span>  

 <span data-ttu-id="87aaa-110">このメソッドは、Winerror.h で定義されている標準 COM エラーコードと、次の表の値を返します。</span><span class="sxs-lookup"><span data-stu-id="87aaa-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="87aaa-111">リターン コード</span><span class="sxs-lookup"><span data-stu-id="87aaa-111">Return code</span></span>|<span data-ttu-id="87aaa-112">説明</span><span class="sxs-lookup"><span data-stu-id="87aaa-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="87aaa-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="87aaa-113">S_OK</span></span>|<span data-ttu-id="87aaa-114">実行エンジンが正常に読み込まれました。</span><span class="sxs-lookup"><span data-stu-id="87aaa-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="87aaa-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="87aaa-115">S_FALSE</span></span>|<span data-ttu-id="87aaa-116">実行エンジンは既に読み込まれています。</span><span class="sxs-lookup"><span data-stu-id="87aaa-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="87aaa-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="87aaa-117">E_FAIL</span></span>|<span data-ttu-id="87aaa-118">実行エンジンを読み込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="87aaa-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87aaa-119">注釈</span><span class="sxs-lookup"><span data-stu-id="87aaa-119">Remarks</span></span>  

 <span data-ttu-id="87aaa-120">このメソッドは、まだ読み込まれていない場合、実行エンジンを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="87aaa-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87aaa-121">要件</span><span class="sxs-lookup"><span data-stu-id="87aaa-121">Requirements</span></span>  

 <span data-ttu-id="87aaa-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87aaa-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87aaa-123">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="87aaa-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="87aaa-124">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="87aaa-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="87aaa-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87aaa-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87aaa-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="87aaa-126">See also</span></span>

- [<span data-ttu-id="87aaa-127">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="87aaa-127">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
