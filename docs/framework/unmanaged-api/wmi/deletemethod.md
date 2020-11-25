---
title: DeleteMethod 関数 (アンマネージ API リファレンス)
description: DeleteMethod 関数は、指定されたメソッドを CIM クラス定義から削除します。
ms.date: 11/06/2017
api_name:
- DeleteMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- DeleteMethod
helpviewer_keywords:
- DeleteMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 8ca58ed3510360b20577890055e4284869d1bf94
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708102"
---
# <a name="deletemethod-function"></a><span data-ttu-id="0b883-103">DeleteMethod 関数</span><span class="sxs-lookup"><span data-stu-id="0b883-103">DeleteMethod function</span></span>

<span data-ttu-id="0b883-104">指定したメソッドを CIM クラス定義から削除します。</span><span class="sxs-lookup"><span data-stu-id="0b883-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0b883-105">構文</span><span class="sxs-lookup"><span data-stu-id="0b883-105">Syntax</span></span>  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="0b883-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0b883-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="0b883-107">からこのパラメーターは使用されていません。</span><span class="sxs-lookup"><span data-stu-id="0b883-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="0b883-108">から [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0b883-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="0b883-109">からクラステーブルから削除するメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="0b883-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="0b883-110">`wszName` は、有効なへのポインターである必要があり `LPCWSTR` ます。</span><span class="sxs-lookup"><span data-stu-id="0b883-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="0b883-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="0b883-111">Return value</span></span>

<span data-ttu-id="0b883-112">この関数によって返される次の値は、 *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="0b883-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0b883-113">定数</span><span class="sxs-lookup"><span data-stu-id="0b883-113">Constant</span></span>  |<span data-ttu-id="0b883-114">値</span><span class="sxs-lookup"><span data-stu-id="0b883-114">Value</span></span>  |<span data-ttu-id="0b883-115">説明</span><span class="sxs-lookup"><span data-stu-id="0b883-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="0b883-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="0b883-116">0x80041002</span></span> | <span data-ttu-id="0b883-117">指定されたメソッドは存在しません。</span><span class="sxs-lookup"><span data-stu-id="0b883-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="0b883-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="0b883-118">0x80041006</span></span> | <span data-ttu-id="0b883-119">操作を完了させるための十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="0b883-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="0b883-120">0</span><span class="sxs-lookup"><span data-stu-id="0b883-120">0</span></span> | <span data-ttu-id="0b883-121">関数の呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="0b883-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="0b883-122">注釈</span><span class="sxs-lookup"><span data-stu-id="0b883-122">Remarks</span></span>

<span data-ttu-id="0b883-123">この関数は、 [IWbemClassObject::D eletemethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) メソッドの呼び出しをラップします。</span><span class="sxs-lookup"><span data-stu-id="0b883-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="0b883-124">CIM インスタンスを指す [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ポインターでは、メソッドの削除はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="0b883-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="0b883-125">要件</span><span class="sxs-lookup"><span data-stu-id="0b883-125">Requirements</span></span>  

 <span data-ttu-id="0b883-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b883-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b883-127">**ヘッダー:** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="0b883-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0b883-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0b883-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b883-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b883-129">See also</span></span>

- [<span data-ttu-id="0b883-130">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="0b883-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
