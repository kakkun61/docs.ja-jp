---
title: SpawnDerivedClass 関数 (アンマネージ API リファレンス)
description: SpawnDerivedClass 関数は、オブジェクトから派生する新しいオブジェクトを作成します。
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 8020dd851b6773e6c76c53892c4b2bc21e4261bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716513"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="9f781-103">SpawnDerivedClass 関数</span><span class="sxs-lookup"><span data-stu-id="9f781-103">SpawnDerivedClass function</span></span>

<span data-ttu-id="9f781-104">指定したオブジェクトから新たに派生するクラス オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9f781-104">Creates a newly derived class object from a specified object.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9f781-105">構文</span><span class="sxs-lookup"><span data-stu-id="9f781-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass);
```  

## <a name="parameters"></a><span data-ttu-id="9f781-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f781-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="9f781-107">からこのパラメーターは使用されていません。</span><span class="sxs-lookup"><span data-stu-id="9f781-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="9f781-108">から [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9f781-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="9f781-109">[in] 予約されています。</span><span class="sxs-lookup"><span data-stu-id="9f781-109">[in] Reserved.</span></span> <span data-ttu-id="9f781-110">このパラメーターには0を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f781-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="9f781-111">入出力新しいクラス定義オブジェクトへのポインターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="9f781-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="9f781-112">エラーが発生した場合、新しいオブジェクトは返されず、 `ppNewClass` 未変更のままになります。</span><span class="sxs-lookup"><span data-stu-id="9f781-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="9f781-113">値をにすることはできません `null` 。</span><span class="sxs-lookup"><span data-stu-id="9f781-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="9f781-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="9f781-114">Return value</span></span>

<span data-ttu-id="9f781-115">この関数によって返される次の値は、 *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="9f781-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9f781-116">定数</span><span class="sxs-lookup"><span data-stu-id="9f781-116">Constant</span></span>  |<span data-ttu-id="9f781-117">値</span><span class="sxs-lookup"><span data-stu-id="9f781-117">Value</span></span>  |<span data-ttu-id="9f781-118">説明</span><span class="sxs-lookup"><span data-stu-id="9f781-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="9f781-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="9f781-119">0x80041001</span></span> | <span data-ttu-id="9f781-120">一般的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9f781-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="9f781-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="9f781-121">0x80041016</span></span> | <span data-ttu-id="9f781-122">インスタンスからのクラスの生成などの無効な操作が要求されました。</span><span class="sxs-lookup"><span data-stu-id="9f781-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="9f781-123">ソースクラスが完全に定義されていないか、Windows Management に登録されていないため、新しい派生クラスは許可されません。</span><span class="sxs-lookup"><span data-stu-id="9f781-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="9f781-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="9f781-124">0x80041006</span></span> | <span data-ttu-id="9f781-125">メモリ不足のため、操作を完了できません。</span><span class="sxs-lookup"><span data-stu-id="9f781-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9f781-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9f781-126">0x80041008</span></span> | <span data-ttu-id="9f781-127">`ppNewClass` が `null`です。</span><span class="sxs-lookup"><span data-stu-id="9f781-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="9f781-128">0</span><span class="sxs-lookup"><span data-stu-id="9f781-128">0</span></span> | <span data-ttu-id="9f781-129">関数の呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="9f781-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="9f781-130">注釈</span><span class="sxs-lookup"><span data-stu-id="9f781-130">Remarks</span></span>

<span data-ttu-id="9f781-131">この関数は、 [IWbemClassObject:: SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) メソッドの呼び出しをラップします。</span><span class="sxs-lookup"><span data-stu-id="9f781-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="9f781-132">`ptr` は、生成されたオブジェクトの親クラスになるクラス定義である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f781-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="9f781-133">返されたオブジェクトは、現在のオブジェクトのサブクラスになります。</span><span class="sxs-lookup"><span data-stu-id="9f781-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="9f781-134">で返された新しいオブジェクトは、 `ppNewClass` 自動的に現在のオブジェクトのサブクラスになります。</span><span class="sxs-lookup"><span data-stu-id="9f781-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="9f781-135">この動作をオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9f781-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="9f781-136">サブクラス (派生クラス) を作成する方法は他にもありません。</span><span class="sxs-lookup"><span data-stu-id="9f781-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="9f781-137">要件</span><span class="sxs-lookup"><span data-stu-id="9f781-137">Requirements</span></span>  

 <span data-ttu-id="9f781-138">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f781-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f781-139">**ヘッダー:** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="9f781-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9f781-140">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9f781-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f781-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f781-141">See also</span></span>

- [<span data-ttu-id="9f781-142">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="9f781-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
