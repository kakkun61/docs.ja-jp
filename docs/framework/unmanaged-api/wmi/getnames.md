---
title: GetNames 関数 (アンマネージ API リファレンス)
description: GetNames 関数は、オブジェクトのプロパティの名前を取得します。
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fd889158e61b86f42d88bcf86eda7d816277e6ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687659"
---
# <a name="getnames-function"></a><span data-ttu-id="ff565-103">GetNames 関数</span><span class="sxs-lookup"><span data-stu-id="ff565-103">GetNames function</span></span>

<span data-ttu-id="ff565-104">オブジェクトのプロパティの名前の一部またはすべてが取得されます。</span><span class="sxs-lookup"><span data-stu-id="ff565-104">Retrieves either a subset or all of the names of the properties of an object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="ff565-105">構文</span><span class="sxs-lookup"><span data-stu-id="ff565-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNames (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
);
```  

## <a name="parameters"></a><span data-ttu-id="ff565-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff565-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="ff565-107">からこのパラメーターは使用されていません。</span><span class="sxs-lookup"><span data-stu-id="ff565-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="ff565-108">から [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ff565-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="ff565-109">から `LPCWSTR` フィルターの一部として動作する修飾子名を指定する、有効なへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ff565-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="ff565-110">詳細については、「[解説](#remarks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff565-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="ff565-111">このパラメーターは、`null` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="ff565-111">This parameter can be `null`.</span></span>

`lFlags`  
<span data-ttu-id="ff565-112">からビットフィールドの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="ff565-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="ff565-113">詳細については、「[解説](#remarks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff565-113">For more information, see the [Remarks](#remarks) section.</span></span>

<span data-ttu-id="ff565-114">`pQualifierValue` から `VARIANT` フィルター値に初期化された有効な構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ff565-114">`pQualifierValue` [in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="ff565-115">このパラメーターは、`null` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="ff565-115">This parameter can be `null`.</span></span>

`pstrNames`  
<span data-ttu-id="ff565-116">入出力 `SAFEARRAY` プロパティ名を格納している構造体。</span><span class="sxs-lookup"><span data-stu-id="ff565-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="ff565-117">エントリでは、このパラメーターは常にへのポインターである必要があり `null` ます。</span><span class="sxs-lookup"><span data-stu-id="ff565-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="ff565-118">詳細については、「 [解説](#remarks) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff565-118">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="ff565-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff565-119">Return value</span></span>

<span data-ttu-id="ff565-120">この関数によって返される次の値は、 *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="ff565-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ff565-121">定数</span><span class="sxs-lookup"><span data-stu-id="ff565-121">Constant</span></span>  |<span data-ttu-id="ff565-122">値</span><span class="sxs-lookup"><span data-stu-id="ff565-122">Value</span></span>  |<span data-ttu-id="ff565-123">説明</span><span class="sxs-lookup"><span data-stu-id="ff565-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="ff565-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="ff565-124">0x80041001</span></span> | <span data-ttu-id="ff565-125">一般的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ff565-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ff565-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ff565-126">0x80041008</span></span> | <span data-ttu-id="ff565-127">1つ以上のパラメーターが無効であるか、またはフラグとパラメーターの組み合わせが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="ff565-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ff565-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ff565-128">0x80041006</span></span> | <span data-ttu-id="ff565-129">メモリ不足のため、操作を完了できません。</span><span class="sxs-lookup"><span data-stu-id="ff565-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ff565-130">0</span><span class="sxs-lookup"><span data-stu-id="ff565-130">0</span></span> | <span data-ttu-id="ff565-131">関数の呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="ff565-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="ff565-132">注釈</span><span class="sxs-lookup"><span data-stu-id="ff565-132">Remarks</span></span>

<span data-ttu-id="ff565-133">この関数は、 [IWbemClassObject:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) メソッドの呼び出しをラップします。</span><span class="sxs-lookup"><span data-stu-id="ff565-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="ff565-134">返される名前付きのは、フラグとパラメーターの組み合わせによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="ff565-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="ff565-135">たとえば、関数は、すべてのプロパティの名前、またはキープロパティの名前のみを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="ff565-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="ff565-136">プライマリフィルターはパラメーターで指定され、 `lFlags` その他のパラメーターはそれに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="ff565-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="ff565-137">のフラグ値 `lFlags` はビットフィールドです。</span><span class="sxs-lookup"><span data-stu-id="ff565-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="ff565-138">引数として渡すことができるフラグは、 `lEnumFlags` *WbemCli* ヘッダーファイルで定義されているビットフィールドです。また、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="ff565-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="ff565-139">各グループのフラグは、他のグループのフラグと組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="ff565-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="ff565-140">ただし、同じグループのフラグは相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="ff565-140">However, flags from the same group are mutually exclusive.</span></span>

| <span data-ttu-id="ff565-141">グループ1フラグ</span><span class="sxs-lookup"><span data-stu-id="ff565-141">Group 1 flags</span></span> |<span data-ttu-id="ff565-142">値</span><span class="sxs-lookup"><span data-stu-id="ff565-142">Value</span></span>  |<span data-ttu-id="ff565-143">説明</span><span class="sxs-lookup"><span data-stu-id="ff565-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="ff565-144">0</span><span class="sxs-lookup"><span data-stu-id="ff565-144">0</span></span> | <span data-ttu-id="ff565-145">すべてのプロパティ名を返します。</span><span class="sxs-lookup"><span data-stu-id="ff565-145">Return all property names.</span></span> <span data-ttu-id="ff565-146">`strQualifierName` および `pQualifierVal` は使用されていません。</span><span class="sxs-lookup"><span data-stu-id="ff565-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="ff565-147">1</span><span class="sxs-lookup"><span data-stu-id="ff565-147">1</span></span> | <span data-ttu-id="ff565-148">パラメーターで指定された名前の修飾子を持つプロパティのみを返し `strQualifierName` ます。</span><span class="sxs-lookup"><span data-stu-id="ff565-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="ff565-149">このフラグを使用する場合は、を指定する必要があり `strQualifierName` ます。</span><span class="sxs-lookup"><span data-stu-id="ff565-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="ff565-150">2</span><span class="sxs-lookup"><span data-stu-id="ff565-150">2</span></span> |  <span data-ttu-id="ff565-151">パラメーターで指定された名前の修飾子を持たないプロパティだけを返し `strQualifierName` ます。</span><span class="sxs-lookup"><span data-stu-id="ff565-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="ff565-152">このフラグを使用する場合は、を指定する必要があり `strQualifierName` ます。</span><span class="sxs-lookup"><span data-stu-id="ff565-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="ff565-153">3</span><span class="sxs-lookup"><span data-stu-id="ff565-153">3</span></span> | <span data-ttu-id="ff565-154">パラメーターで指定された名前の修飾子を持ち、 `wszQualifierName` 構造体で指定された値と同じ値を持つプロパティのみを返し `pQualifierVal` ます。</span><span class="sxs-lookup"><span data-stu-id="ff565-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="ff565-155">このフラグを使用する場合は、との両方を指定する必要があり `wszQualifierName` `pQualifierValue` ます。</span><span class="sxs-lookup"><span data-stu-id="ff565-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="ff565-156">グループ2のフラグ</span><span class="sxs-lookup"><span data-stu-id="ff565-156">Group 2 flags</span></span> |<span data-ttu-id="ff565-157">値</span><span class="sxs-lookup"><span data-stu-id="ff565-157">Value</span></span>  |<span data-ttu-id="ff565-158">説明</span><span class="sxs-lookup"><span data-stu-id="ff565-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="ff565-159">0x4</span><span class="sxs-lookup"><span data-stu-id="ff565-159">0x4</span></span> | <span data-ttu-id="ff565-160">キーを定義するプロパティの名前のみを返します。</span><span class="sxs-lookup"><span data-stu-id="ff565-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="ff565-161">0x8</span><span class="sxs-lookup"><span data-stu-id="ff565-161">0x8</span></span> | <span data-ttu-id="ff565-162">オブジェクト参照であるプロパティ名だけを返します。</span><span class="sxs-lookup"><span data-stu-id="ff565-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="ff565-163">グループ3のフラグ</span><span class="sxs-lookup"><span data-stu-id="ff565-163">Group 3 flags</span></span> |<span data-ttu-id="ff565-164">値</span><span class="sxs-lookup"><span data-stu-id="ff565-164">Value</span></span>  |<span data-ttu-id="ff565-165">説明</span><span class="sxs-lookup"><span data-stu-id="ff565-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="ff565-166">0x10</span><span class="sxs-lookup"><span data-stu-id="ff565-166">0x10</span></span> | <span data-ttu-id="ff565-167">最派生クラスに属しているプロパティ名だけを返します。</span><span class="sxs-lookup"><span data-stu-id="ff565-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="ff565-168">親クラスからプロパティを除外します。</span><span class="sxs-lookup"><span data-stu-id="ff565-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="ff565-169">0x20</span><span class="sxs-lookup"><span data-stu-id="ff565-169">0x20</span></span> | <span data-ttu-id="ff565-170">親クラスに属するプロパティ名だけを返します。</span><span class="sxs-lookup"><span data-stu-id="ff565-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="ff565-171">0x30</span><span class="sxs-lookup"><span data-stu-id="ff565-171">0x30</span></span> | <span data-ttu-id="ff565-172">システムプロパティの名前のみを返します。</span><span class="sxs-lookup"><span data-stu-id="ff565-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="ff565-173">0x40</span><span class="sxs-lookup"><span data-stu-id="ff565-173">0x40</span></span> | <span data-ttu-id="ff565-174">システム以外のプロパティの名前のみを返します。</span><span class="sxs-lookup"><span data-stu-id="ff565-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="ff565-175">関数は、を返す場合は常に新しいを割り当て `SAFEARRAY` `WBEM_S_NO_ERROR` ます。この関数は常にを `pstrNames` 指すように設定されます。</span><span class="sxs-lookup"><span data-stu-id="ff565-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="ff565-176">指定したフィルターに一致するプロパティがない場合、返される配列には0個の要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ff565-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="ff565-177">関数が以外の値を返す場合 `WBM_S_NO_ERROR` 、新しい `SAFEARRAY` 構造体は返されません。</span><span class="sxs-lookup"><span data-stu-id="ff565-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="ff565-178">要件</span><span class="sxs-lookup"><span data-stu-id="ff565-178">Requirements</span></span>  

 <span data-ttu-id="ff565-179">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff565-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff565-180">**ヘッダー:** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="ff565-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ff565-181">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ff565-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff565-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff565-182">See also</span></span>

- [<span data-ttu-id="ff565-183">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ff565-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
