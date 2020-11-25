---
title: Next 関数 (アンマネージ API リファレンス)
description: 次の関数は、列挙体の次のプロパティを取得します。
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c2a7fae32e82caae40a95bfdad10fa78082988ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726787"
---
# <a name="next-function"></a><span data-ttu-id="91396-103">Next 関数</span><span class="sxs-lookup"><span data-stu-id="91396-103">Next function</span></span>

<span data-ttu-id="91396-104">[Beginenumeration](beginenumeration.md)への呼び出しで始まる列挙体の次のプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="91396-104">Retrieves the next property in an enumeration that begins with a call to [BeginEnumeration](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="91396-105">構文</span><span class="sxs-lookup"><span data-stu-id="91396-105">Syntax</span></span>

```cpp
HRESULT Next (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="91396-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="91396-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="91396-107">からこのパラメーターは使用されていません。</span><span class="sxs-lookup"><span data-stu-id="91396-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="91396-108">から [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="91396-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`\
<span data-ttu-id="91396-109">[in] 予約されています。</span><span class="sxs-lookup"><span data-stu-id="91396-109">[in] Reserved.</span></span> <span data-ttu-id="91396-110">このパラメーターには0を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91396-110">This parameter must be 0.</span></span>

`pstrName`\
<span data-ttu-id="91396-111">入出力 `BSTR` プロパティ名を格納している新しい。</span><span class="sxs-lookup"><span data-stu-id="91396-111">[out] A new `BSTR` that contains the property name.</span></span> <span data-ttu-id="91396-112">`null`名前が不要な場合は、このパラメーターをに設定できます。</span><span class="sxs-lookup"><span data-stu-id="91396-112">You can set this parameter to `null` if the name is not required.</span></span>

`pVal`\
<span data-ttu-id="91396-113">入出力 `VARIANT` プロパティの値を格納した。</span><span class="sxs-lookup"><span data-stu-id="91396-113">[out] A `VARIANT` filled with the value of the property.</span></span> <span data-ttu-id="91396-114">値が不要な場合は、このパラメーターをに設定でき `null` ます。</span><span class="sxs-lookup"><span data-stu-id="91396-114">You can set this parameter to `null` if the value is not required.</span></span> <span data-ttu-id="91396-115">関数がエラーコードを返す場合、に渡されたは `VARIANT` 変更されずに `pVal` 残ります。</span><span class="sxs-lookup"><span data-stu-id="91396-115">If the function returns an error code, the `VARIANT` passed to `pVal` is left unmodified.</span></span>

`pvtType`\
<span data-ttu-id="91396-116">入出力 `CIMTYPE` 変数 ( `LONG` プロパティの型が配置される) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="91396-116">[out] A pointer to a `CIMTYPE` variable (a `LONG` into which the type of the property is placed).</span></span> <span data-ttu-id="91396-117">このプロパティの値には、を指定できます `VT_NULL_VARIANT` 。この場合、プロパティの実際の型を決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91396-117">The value of this property can be a `VT_NULL_VARIANT`, in which case it is necessary to determine the actual type of the property.</span></span> <span data-ttu-id="91396-118">このパラメーターは、にすることもでき `null` ます。</span><span class="sxs-lookup"><span data-stu-id="91396-118">This parameter can also be `null`.</span></span>

`plFlavor`\
<span data-ttu-id="91396-119">[out] `null` 、またはプロパティの配信元に関する情報を受け取る値。</span><span class="sxs-lookup"><span data-stu-id="91396-119">[out] `null`, or a value that receives information on the origin of the property.</span></span> <span data-ttu-id="91396-120">使用可能な値については、[解説] セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="91396-120">See the [Remarks] section for possible values.</span></span>

## <a name="return-value"></a><span data-ttu-id="91396-121">戻り値</span><span class="sxs-lookup"><span data-stu-id="91396-121">Return value</span></span>

<span data-ttu-id="91396-122">この関数によって返される次の値は、 *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="91396-122">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="91396-123">定数</span><span class="sxs-lookup"><span data-stu-id="91396-123">Constant</span></span>  |<span data-ttu-id="91396-124">値</span><span class="sxs-lookup"><span data-stu-id="91396-124">Value</span></span>  |<span data-ttu-id="91396-125">説明</span><span class="sxs-lookup"><span data-stu-id="91396-125">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="91396-126">0x80041001</span><span class="sxs-lookup"><span data-stu-id="91396-126">0x80041001</span></span> | <span data-ttu-id="91396-127">一般的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="91396-127">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="91396-128">0x80041008</span><span class="sxs-lookup"><span data-stu-id="91396-128">0x80041008</span></span> | <span data-ttu-id="91396-129">パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="91396-129">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="91396-130">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="91396-130">0x8004101d</span></span> | <span data-ttu-id="91396-131">関数の呼び出しがありませんでした [`BeginEnumeration`](beginenumeration.md) 。</span><span class="sxs-lookup"><span data-stu-id="91396-131">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="91396-132">0x80041006</span><span class="sxs-lookup"><span data-stu-id="91396-132">0x80041006</span></span> | <span data-ttu-id="91396-133">新しい列挙を開始するために必要なメモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="91396-133">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="91396-134">0x80041015</span><span class="sxs-lookup"><span data-stu-id="91396-134">0x80041015</span></span> | <span data-ttu-id="91396-135">現在のプロセスと Windows の管理の間のリモートプロシージャコールが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="91396-135">The remote procedure call between the current process and Windows Management failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="91396-136">0</span><span class="sxs-lookup"><span data-stu-id="91396-136">0</span></span> | <span data-ttu-id="91396-137">関数の呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="91396-137">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="91396-138">0x40005</span><span class="sxs-lookup"><span data-stu-id="91396-138">0x40005</span></span> | <span data-ttu-id="91396-139">列挙体にはそれ以上のプロパティがありません。</span><span class="sxs-lookup"><span data-stu-id="91396-139">There are no more properties in the enumeration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="91396-140">注釈</span><span class="sxs-lookup"><span data-stu-id="91396-140">Remarks</span></span>

<span data-ttu-id="91396-141">この関数は、 [IWbemClassObject:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) メソッドの呼び出しをラップします。</span><span class="sxs-lookup"><span data-stu-id="91396-141">This function wraps a call to the [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) method.</span></span>

<span data-ttu-id="91396-142">このメソッドは、システムプロパティも返します。</span><span class="sxs-lookup"><span data-stu-id="91396-142">This method also returns system properties.</span></span>

<span data-ttu-id="91396-143">プロパティの基になる型がオブジェクトパス、日付または時刻、または別の特殊な型である場合、返される型には十分な情報が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="91396-143">If the underlying type of the property is an object path, a date or time, or another special type, then the returned type does not contain enough information.</span></span> <span data-ttu-id="91396-144">呼び出し元は、 `CIMTYPE` プロパティがオブジェクト参照、日付または時刻、または別の特殊な型であるかどうかを判断するために、指定されたプロパティのを調べる必要があります。</span><span class="sxs-lookup"><span data-stu-id="91396-144">The caller must examine the `CIMTYPE` for the specified property to determine if the property is an object reference, a date or time, or another special type.</span></span>

<span data-ttu-id="91396-145">`plFlavor`がでない場合 `null` 、この値は、次のように、 `LONG` プロパティの配信元に関する情報を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="91396-145">If `plFlavor` is not `null`, the `LONG` value receives information about the origin of the property, as follows:</span></span>

|<span data-ttu-id="91396-146">定数</span><span class="sxs-lookup"><span data-stu-id="91396-146">Constant</span></span>  |<span data-ttu-id="91396-147">値</span><span class="sxs-lookup"><span data-stu-id="91396-147">Value</span></span>  |<span data-ttu-id="91396-148">説明</span><span class="sxs-lookup"><span data-stu-id="91396-148">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="91396-149">0x40</span><span class="sxs-lookup"><span data-stu-id="91396-149">0x40</span></span> | <span data-ttu-id="91396-150">プロパティは、標準のシステムプロパティです。</span><span class="sxs-lookup"><span data-stu-id="91396-150">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="91396-151">0x20</span><span class="sxs-lookup"><span data-stu-id="91396-151">0x20</span></span> | <span data-ttu-id="91396-152">クラスの場合: プロパティは親クラスから継承されます。</span><span class="sxs-lookup"><span data-stu-id="91396-152">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="91396-153">インスタンスの場合: 親クラスから継承されたプロパティは、インスタンスによって変更されていません。</span><span class="sxs-lookup"><span data-stu-id="91396-153">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="91396-154">0</span><span class="sxs-lookup"><span data-stu-id="91396-154">0</span></span> | <span data-ttu-id="91396-155">クラスの場合: プロパティは派生クラスに属します。</span><span class="sxs-lookup"><span data-stu-id="91396-155">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="91396-156">インスタンスの場合: プロパティは、インスタンスによって変更されます。つまり、値が指定されたか、または修飾子が追加または変更されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="91396-156">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="requirements"></a><span data-ttu-id="91396-157">要件</span><span class="sxs-lookup"><span data-stu-id="91396-157">Requirements</span></span>

<span data-ttu-id="91396-158">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91396-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="91396-159">**ヘッダー:** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="91396-159">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="91396-160">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="91396-160">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="91396-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="91396-161">See also</span></span>

- [<span data-ttu-id="91396-162">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="91396-162">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
