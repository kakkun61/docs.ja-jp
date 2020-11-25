---
title: CreateDebuggingInterfaceFromVersion 関数
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
ms.openlocfilehash: b68fbc713374642c9f55d49ee51a88c5785cf4b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727875"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="8be2e-102">CreateDebuggingInterfaceFromVersion 関数</span><span class="sxs-lookup"><span data-stu-id="8be2e-102">CreateDebuggingInterfaceFromVersion Function</span></span>

<span data-ttu-id="8be2e-103">指定されたバージョン情報に基づいて [ICorDebug](../debugging/icordebug-interface.md) オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8be2e-103">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="8be2e-104">この関数は、.NET Framework 4 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="8be2e-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="8be2e-105">代わりに、共通言語ランタイム (CLR) 2.0 のインターフェイスを取得するには、 [ICLRRuntimeInfo:: GetInterface](iclrruntimeinfo-getinterface-method.md) メソッドを使用して、クラス識別子 CLSID_CLRDebuggingLegacy とインターフェイス識別子 IID_ICorDebug を指定します。</span><span class="sxs-lookup"><span data-stu-id="8be2e-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="8be2e-106">CLR 4 以降のインターフェイスを取得するには、 [Clrcreateinstance](clrcreateinstance-function.md) 関数を呼び出し、クラス識別子 CLSID_CLRDebugging とインターフェイス識別子 IID_ICLRDebugging を指定します。</span><span class="sxs-lookup"><span data-stu-id="8be2e-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8be2e-107">構文</span><span class="sxs-lookup"><span data-stu-id="8be2e-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8be2e-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8be2e-108">Parameters</span></span>  

 `iDebuggerVersion`  
 <span data-ttu-id="8be2e-109">から `ICorDebug` デバッガーによって想定されているのバージョン。</span><span class="sxs-lookup"><span data-stu-id="8be2e-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="8be2e-110">有効な値については、 [Cordebuginterfaceversion](../debugging/cordebuginterfaceversion-enumeration.md) 列挙体を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8be2e-110">See the [CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="8be2e-111">からデバッグ対象のアプリケーションまたはプロセスに関連付けられている共通言語ランタイムのバージョン。</span><span class="sxs-lookup"><span data-stu-id="8be2e-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="8be2e-112">この値を取得する方法については、「 [Getversionfromprocess](getversionfromprocess-function.md) 」または「 [Getversionfromprocess](getrequestedruntimeversion-function.md) メソッド」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8be2e-112">See the [GetVersionFromProcess](getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="8be2e-113">入出力オブジェクトへのポインターを受け取る位置 `ICorDebug` 。</span><span class="sxs-lookup"><span data-stu-id="8be2e-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8be2e-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="8be2e-114">Return Value</span></span>  

 <span data-ttu-id="8be2e-115">このメソッドは、次の値に加えて、Winerror.h ファイルで定義されている標準 COM エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="8be2e-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="8be2e-116">リターン コード</span><span class="sxs-lookup"><span data-stu-id="8be2e-116">Return code</span></span>|<span data-ttu-id="8be2e-117">説明</span><span class="sxs-lookup"><span data-stu-id="8be2e-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="8be2e-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="8be2e-118">S_OK</span></span>|<span data-ttu-id="8be2e-119">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="8be2e-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="8be2e-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8be2e-120">E_INVALIDARG</span></span>|<span data-ttu-id="8be2e-121">`szDebuggeeVersion` または `ppCordb` が null であるか、またはバージョン文字列が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="8be2e-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8be2e-122">注釈</span><span class="sxs-lookup"><span data-stu-id="8be2e-122">Remarks</span></span>  

 <span data-ttu-id="8be2e-123">パラメーターは、 `szDebuggeeVersion` 対応するバージョンの MSCorDbi.dll にマップされます。</span><span class="sxs-lookup"><span data-stu-id="8be2e-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8be2e-124">要件</span><span class="sxs-lookup"><span data-stu-id="8be2e-124">Requirements</span></span>  

 <span data-ttu-id="8be2e-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8be2e-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8be2e-126">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8be2e-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8be2e-127">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8be2e-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8be2e-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8be2e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8be2e-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="8be2e-129">See also</span></span>

- [<span data-ttu-id="8be2e-130">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="8be2e-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
