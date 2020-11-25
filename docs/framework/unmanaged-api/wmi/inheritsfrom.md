---
title: InheritsFrom 関数 (アンマネージ API リファレンス)
description: InheritsFrom 関数は、クラスまたはインスタンスが特定の親クラスから派生しているかどうかを判断します。
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 3cfe3388dc808335e6d3daaf7ec949108e95f52e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726794"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="0abf9-103">InheritsFrom 関数</span><span class="sxs-lookup"><span data-stu-id="0abf9-103">InheritsFrom function</span></span>

<span data-ttu-id="0abf9-104">指定した親クラスから現在のクラスまたはインスタンスが派生しているかどうかが判定されます。</span><span class="sxs-lookup"><span data-stu-id="0abf9-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0abf9-105">構文</span><span class="sxs-lookup"><span data-stu-id="0abf9-105">Syntax</span></span>  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszAncestor
);
```  

## <a name="parameters"></a><span data-ttu-id="0abf9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0abf9-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="0abf9-107">からこのパラメーターは使用されていません。</span><span class="sxs-lookup"><span data-stu-id="0abf9-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="0abf9-108">から [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0abf9-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="0abf9-109">からクラスの名前。</span><span class="sxs-lookup"><span data-stu-id="0abf9-109">[in] The name of the class.</span></span> <span data-ttu-id="0abf9-110">`wszAncestor` は有効なを指している必要があり `LPCWSTR` ます。</span><span class="sxs-lookup"><span data-stu-id="0abf9-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="0abf9-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="0abf9-111">Return value</span></span>

<span data-ttu-id="0abf9-112">この関数によって返される次の値は、 *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="0abf9-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0abf9-113">定数</span><span class="sxs-lookup"><span data-stu-id="0abf9-113">Constant</span></span>  |<span data-ttu-id="0abf9-114">値</span><span class="sxs-lookup"><span data-stu-id="0abf9-114">Value</span></span>  |<span data-ttu-id="0abf9-115">説明</span><span class="sxs-lookup"><span data-stu-id="0abf9-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="0abf9-116">0</span><span class="sxs-lookup"><span data-stu-id="0abf9-116">0</span></span> | <span data-ttu-id="0abf9-117">現在のオブジェクトはを継承 `wszAncestor` します。</span><span class="sxs-lookup"><span data-stu-id="0abf9-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="0abf9-118">1</span><span class="sxs-lookup"><span data-stu-id="0abf9-118">1</span></span> | <span data-ttu-id="0abf9-119">現在のオブジェクトはを継承しません `wszAncestor` 。</span><span class="sxs-lookup"><span data-stu-id="0abf9-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0abf9-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0abf9-120">0x80041008</span></span> | <span data-ttu-id="0abf9-121">`wszAncestor` が `null`です。</span><span class="sxs-lookup"><span data-stu-id="0abf9-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="0abf9-122">注釈</span><span class="sxs-lookup"><span data-stu-id="0abf9-122">Remarks</span></span>

<span data-ttu-id="0abf9-123">この関数は、 [IWbemClassObject:: InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) メソッドの呼び出しをラップします。</span><span class="sxs-lookup"><span data-stu-id="0abf9-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0abf9-124">要件</span><span class="sxs-lookup"><span data-stu-id="0abf9-124">Requirements</span></span>  

 <span data-ttu-id="0abf9-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0abf9-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0abf9-126">**ヘッダー:** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="0abf9-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0abf9-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0abf9-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0abf9-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="0abf9-128">See also</span></span>

- [<span data-ttu-id="0abf9-129">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="0abf9-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
