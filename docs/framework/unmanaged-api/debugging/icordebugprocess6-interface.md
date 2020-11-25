---
title: ICorDebugProcess6 インターフェイス
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: ba70bab28eeddad6e3cf3c2b82b196a69ce68647
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732607"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="755a1-102">ICorDebugProcess6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="755a1-102">ICorDebugProcess6 Interface</span></span>

<span data-ttu-id="755a1-103">ICorDebugProcess インターフェイスを論理的に拡張し、ネイティブ例外デバッグ イベントにエンコードされたマネージド デバッグ イベントのデコードや仮想モジュール分割などの機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="755a1-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="755a1-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="755a1-104">Methods</span></span>  
  
|<span data-ttu-id="755a1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="755a1-105">Method</span></span>|<span data-ttu-id="755a1-106">説明</span><span class="sxs-lookup"><span data-stu-id="755a1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="755a1-107">DecodeEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="755a1-107">DecodeEvent Method</span></span>](icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="755a1-108">特別に作成されたネイティブ例外デバッグ イベントのペイロードにカプセル化されたマネージド デバッグ イベントをデコードします。</span><span class="sxs-lookup"><span data-stu-id="755a1-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="755a1-109">EnableVirtualModuleSplitting メソッド</span><span class="sxs-lookup"><span data-stu-id="755a1-109">EnableVirtualModuleSplitting Method</span></span>](icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="755a1-110">仮想モジュール分割を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="755a1-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="755a1-111">GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="755a1-111">GetCode Method</span></span>](icordebugprocess6-getcode-method.md)|<span data-ttu-id="755a1-112">特定のコード アドレスで、マネージド コードに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="755a1-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="755a1-113">GetExportStepInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="755a1-113">GetExportStepInfo Method</span></span>](icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="755a1-114">マネージド コードのステップ実行に役立つランタイム エクスポート関数の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="755a1-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="755a1-115">MarkDebuggerAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="755a1-115">MarkDebuggerAttached Method</span></span>](icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="755a1-116">.NET Framework クラス ライブラリの <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> メソッドが `true` を返すように、デバッグ対象の内部状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="755a1-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="755a1-117">ProcessStateChanged メソッド</span><span class="sxs-lookup"><span data-stu-id="755a1-117">ProcessStateChanged Method</span></span>](icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="755a1-118">プロセスが実行されていることを [ICorDebug](icordebug-interface.md) に通知します。</span><span class="sxs-lookup"><span data-stu-id="755a1-118">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="755a1-119">注釈</span><span class="sxs-lookup"><span data-stu-id="755a1-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="755a1-120">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="755a1-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="755a1-121">インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。</span><span class="sxs-lookup"><span data-stu-id="755a1-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="755a1-122">要件</span><span class="sxs-lookup"><span data-stu-id="755a1-122">Requirements</span></span>  

 <span data-ttu-id="755a1-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="755a1-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="755a1-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="755a1-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="755a1-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="755a1-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="755a1-126">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="755a1-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="755a1-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="755a1-127">See also</span></span>

- [<span data-ttu-id="755a1-128">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="755a1-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="755a1-129">デバッグ</span><span class="sxs-lookup"><span data-stu-id="755a1-129">Debugging</span></span>](index.md)
