---
title: BeginEnumeration 関数 (アンマネージ API リファレンス)
description: BeginEnumeration 関数は、列挙子を列挙体の先頭にリセットします。
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6057526ddbe2efed65f8569e829c35524829e43e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708219"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="4e90c-103">BeginEnumeration 関数</span><span class="sxs-lookup"><span data-stu-id="4e90c-103">BeginEnumeration function</span></span>

<span data-ttu-id="4e90c-104">列挙子を列挙体の先頭にリセットします。</span><span class="sxs-lookup"><span data-stu-id="4e90c-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="4e90c-105">構文</span><span class="sxs-lookup"><span data-stu-id="4e90c-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a><span data-ttu-id="4e90c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4e90c-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="4e90c-107">からこのパラメーターは使用されていません。</span><span class="sxs-lookup"><span data-stu-id="4e90c-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="4e90c-108">から [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4e90c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="4e90c-109">から列挙に含まれるプロパティを制御する、「 [解説](#remarks) 」で説明されているフラグまたは値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="4e90c-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="4e90c-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="4e90c-110">Return value</span></span>

<span data-ttu-id="4e90c-111">この関数によって返される次の値は、 *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="4e90c-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4e90c-112">定数</span><span class="sxs-lookup"><span data-stu-id="4e90c-112">Constant</span></span>  |<span data-ttu-id="4e90c-113">値</span><span class="sxs-lookup"><span data-stu-id="4e90c-113">Value</span></span>  |<span data-ttu-id="4e90c-114">説明</span><span class="sxs-lookup"><span data-stu-id="4e90c-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4e90c-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4e90c-115">0x80041008</span></span> | <span data-ttu-id="4e90c-116">のフラグの組み合わせ `lEnumFlags` が無効であるか、無効な引数が指定されました。</span><span class="sxs-lookup"><span data-stu-id="4e90c-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="4e90c-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="4e90c-117">0x8004101d</span></span> | <span data-ttu-id="4e90c-118">への2回目の呼び出しは、の `BeginEnumeration` 間の呼び出しなしで行われました [`EndEnumeration`](endenumeration.md) 。</span><span class="sxs-lookup"><span data-stu-id="4e90c-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4e90c-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4e90c-119">0x80041006</span></span> | <span data-ttu-id="4e90c-120">新しい列挙を開始するために必要なメモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="4e90c-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4e90c-121">0</span><span class="sxs-lookup"><span data-stu-id="4e90c-121">0</span></span> | <span data-ttu-id="4e90c-122">関数の呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="4e90c-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4e90c-123">注釈</span><span class="sxs-lookup"><span data-stu-id="4e90c-123">Remarks</span></span>

<span data-ttu-id="4e90c-124">この関数は、 [IWbemClassObject:: BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) メソッドの呼び出しをラップします。</span><span class="sxs-lookup"><span data-stu-id="4e90c-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="4e90c-125">引数として渡すことができるフラグは、 `lEnumFlags` *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="4e90c-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="4e90c-126">各グループのフラグは、他のグループのフラグと組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="4e90c-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="4e90c-127">ただし、同じグループのフラグは相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="4e90c-127">However, flags from the same group are mutually exclusive.</span></span>

<span data-ttu-id="4e90c-128">**グループ 1**</span><span class="sxs-lookup"><span data-stu-id="4e90c-128">**Group 1**</span></span>

|<span data-ttu-id="4e90c-129">定数</span><span class="sxs-lookup"><span data-stu-id="4e90c-129">Constant</span></span>  |<span data-ttu-id="4e90c-130">値</span><span class="sxs-lookup"><span data-stu-id="4e90c-130">Value</span></span>  |<span data-ttu-id="4e90c-131">説明</span><span class="sxs-lookup"><span data-stu-id="4e90c-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="4e90c-132">0x4</span><span class="sxs-lookup"><span data-stu-id="4e90c-132">0x4</span></span> | <span data-ttu-id="4e90c-133">キーのみを構成するプロパティを含めます。</span><span class="sxs-lookup"><span data-stu-id="4e90c-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="4e90c-134">0x8</span><span class="sxs-lookup"><span data-stu-id="4e90c-134">0x8</span></span> | <span data-ttu-id="4e90c-135">オブジェクト参照のみのプロパティを含めます。</span><span class="sxs-lookup"><span data-stu-id="4e90c-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="4e90c-136">**グループ 2**</span><span class="sxs-lookup"><span data-stu-id="4e90c-136">**Group 2**</span></span>

<span data-ttu-id="4e90c-137">定数</span><span class="sxs-lookup"><span data-stu-id="4e90c-137">Constant</span></span>  |<span data-ttu-id="4e90c-138">値</span><span class="sxs-lookup"><span data-stu-id="4e90c-138">Value</span></span>  |<span data-ttu-id="4e90c-139">説明</span><span class="sxs-lookup"><span data-stu-id="4e90c-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="4e90c-140">0x30</span><span class="sxs-lookup"><span data-stu-id="4e90c-140">0x30</span></span> | <span data-ttu-id="4e90c-141">列挙体をシステムプロパティのみに制限します。</span><span class="sxs-lookup"><span data-stu-id="4e90c-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="4e90c-142">0x40</span><span class="sxs-lookup"><span data-stu-id="4e90c-142">0x40</span></span> | <span data-ttu-id="4e90c-143">ローカルプロパティと伝達されたプロパティを含めますが、列挙からシステムプロパティを除外します。</span><span class="sxs-lookup"><span data-stu-id="4e90c-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="4e90c-144">クラスの場合:</span><span class="sxs-lookup"><span data-stu-id="4e90c-144">For classes:</span></span>

<span data-ttu-id="4e90c-145">定数</span><span class="sxs-lookup"><span data-stu-id="4e90c-145">Constant</span></span>  |<span data-ttu-id="4e90c-146">値</span><span class="sxs-lookup"><span data-stu-id="4e90c-146">Value</span></span>  |<span data-ttu-id="4e90c-147">説明</span><span class="sxs-lookup"><span data-stu-id="4e90c-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="4e90c-148">0x100</span><span class="sxs-lookup"><span data-stu-id="4e90c-148">0x100</span></span> | <span data-ttu-id="4e90c-149">列挙型をクラス定義でオーバーライドされたプロパティに限定します。</span><span class="sxs-lookup"><span data-stu-id="4e90c-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="4e90c-150">0x100</span><span class="sxs-lookup"><span data-stu-id="4e90c-150">0x100</span></span> | <span data-ttu-id="4e90c-151">列挙体を、現在のクラス定義でオーバーライドされたプロパティと、クラスで定義されている新しいプロパティに限定します。</span><span class="sxs-lookup"><span data-stu-id="4e90c-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="4e90c-152">0x300</span><span class="sxs-lookup"><span data-stu-id="4e90c-152">0x300</span></span> | <span data-ttu-id="4e90c-153">`lEnumFlags` `WBEM_FLAG_CLASS_OVERRIDES_ONLY` または `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` が設定されているかどうかを確認するために、値に対して適用するマスク (フラグではなく)。</span><span class="sxs-lookup"><span data-stu-id="4e90c-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="4e90c-154">0x10</span><span class="sxs-lookup"><span data-stu-id="4e90c-154">0x10</span></span> | <span data-ttu-id="4e90c-155">列挙体は、クラス自体で定義または変更されたプロパティに限定します。</span><span class="sxs-lookup"><span data-stu-id="4e90c-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="4e90c-156">0x20</span><span class="sxs-lookup"><span data-stu-id="4e90c-156">0x20</span></span> | <span data-ttu-id="4e90c-157">列挙型を基底クラスから継承されたプロパティに限定します。</span><span class="sxs-lookup"><span data-stu-id="4e90c-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="4e90c-158">インスタンスの場合:</span><span class="sxs-lookup"><span data-stu-id="4e90c-158">For instances:</span></span>

<span data-ttu-id="4e90c-159">定数</span><span class="sxs-lookup"><span data-stu-id="4e90c-159">Constant</span></span>  |<span data-ttu-id="4e90c-160">値</span><span class="sxs-lookup"><span data-stu-id="4e90c-160">Value</span></span>  |<span data-ttu-id="4e90c-161">説明</span><span class="sxs-lookup"><span data-stu-id="4e90c-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="4e90c-162">0x10</span><span class="sxs-lookup"><span data-stu-id="4e90c-162">0x10</span></span> | <span data-ttu-id="4e90c-163">列挙体は、クラス自体で定義または変更されたプロパティに限定します。</span><span class="sxs-lookup"><span data-stu-id="4e90c-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="4e90c-164">0x20</span><span class="sxs-lookup"><span data-stu-id="4e90c-164">0x20</span></span> | <span data-ttu-id="4e90c-165">列挙型を基底クラスから継承されたプロパティに限定します。</span><span class="sxs-lookup"><span data-stu-id="4e90c-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="4e90c-166">要件</span><span class="sxs-lookup"><span data-stu-id="4e90c-166">Requirements</span></span>  

 <span data-ttu-id="4e90c-167">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e90c-167">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e90c-168">**ヘッダー:** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="4e90c-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4e90c-169">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4e90c-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e90c-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e90c-170">See also</span></span>

- [<span data-ttu-id="4e90c-171">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="4e90c-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
