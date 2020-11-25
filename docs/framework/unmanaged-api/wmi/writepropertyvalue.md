---
title: WritePropertyValue 関数 (アンマネージ API リファレンス)
description: WritePropertyValue 関数は、バイトをプロパティに書き込みます。
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e225516b06c477dc1a24cf721bc3e1ade9076b75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729409"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="212bd-103">WritePropertyValue 関数</span><span class="sxs-lookup"><span data-stu-id="212bd-103">WritePropertyValue function</span></span>

<span data-ttu-id="212bd-104">指定したバイト数が、プロパティ ハンドルによって識別されるプロパティに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="212bd-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="212bd-105">構文</span><span class="sxs-lookup"><span data-stu-id="212bd-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a><span data-ttu-id="212bd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="212bd-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="212bd-107">からこのパラメーターは使用されていません。</span><span class="sxs-lookup"><span data-stu-id="212bd-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="212bd-108">から [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="212bd-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="212bd-109">からこのプロパティを識別するハンドルを格納している整数。</span><span class="sxs-lookup"><span data-stu-id="212bd-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="212bd-110">ハンドルは、 [Getpropertyhandle](getpropertyhandle.md) 関数を呼び出すことによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="212bd-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>

`lNumBytes`  
<span data-ttu-id="212bd-111">からプロパティに書き込むバイト数。</span><span class="sxs-lookup"><span data-stu-id="212bd-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="212bd-112">詳細については、「 [解説](#remarks) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="212bd-112">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="212bd-113">`pHandle` 入出力データを格納しているバイト配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="212bd-113">`pHandle` [out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="212bd-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="212bd-114">Return value</span></span>

<span data-ttu-id="212bd-115">この関数によって返される次の値は、 *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="212bd-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="212bd-116">定数</span><span class="sxs-lookup"><span data-stu-id="212bd-116">Constant</span></span>  |<span data-ttu-id="212bd-117">値</span><span class="sxs-lookup"><span data-stu-id="212bd-117">Value</span></span>  |<span data-ttu-id="212bd-118">説明</span><span class="sxs-lookup"><span data-stu-id="212bd-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="212bd-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="212bd-119">0x80041008</span></span> | <span data-ttu-id="212bd-120">パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="212bd-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="212bd-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="212bd-121">0x80041005</span></span> | <span data-ttu-id="212bd-122">型の不一致が発生しました。</span><span class="sxs-lookup"><span data-stu-id="212bd-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="212bd-123">0</span><span class="sxs-lookup"><span data-stu-id="212bd-123">0</span></span> | <span data-ttu-id="212bd-124">関数の呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="212bd-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="212bd-125">注釈</span><span class="sxs-lookup"><span data-stu-id="212bd-125">Remarks</span></span>

<span data-ttu-id="212bd-126">この関数は、 [IWbemClassObject:: WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) メソッドの呼び出しをラップします。</span><span class="sxs-lookup"><span data-stu-id="212bd-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="212bd-127">この関数を使用すると、文字列とその他すべての非 `DWORD` データまたは非データを設定 `QWORD` できます。</span><span class="sxs-lookup"><span data-stu-id="212bd-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="212bd-128">文字列以外のプロパティ値の場合、は、 `lNumBytes` 指定されたプロパティ型の正しいデータサイズである必要があります。</span><span class="sxs-lookup"><span data-stu-id="212bd-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="212bd-129">文字列プロパティ値の場合、は `lNumBytes` 指定された文字列の長さ (バイト単位) である必要があり、文字列自体はバイト単位の長さで、その後に null 終端文字が続く必要があります。</span><span class="sxs-lookup"><span data-stu-id="212bd-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="212bd-130">要件</span><span class="sxs-lookup"><span data-stu-id="212bd-130">Requirements</span></span>  

<span data-ttu-id="212bd-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="212bd-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="212bd-132">**ヘッダー:** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="212bd-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="212bd-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="212bd-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="212bd-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="212bd-134">See also</span></span>

- [<span data-ttu-id="212bd-135">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="212bd-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
