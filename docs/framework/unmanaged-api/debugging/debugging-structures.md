---
title: デバッグ構造体
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: bf84f8ddb1e86da3b9d0e4326584e61304640558
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676271"
---
# <a name="debugging-structures"></a><span data-ttu-id="b7144-102">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="b7144-102">Debugging Structures</span></span>

<span data-ttu-id="b7144-103">このセクションでは、デバッグ API が使用するアンマネージ構造体について説明します。</span><span class="sxs-lookup"><span data-stu-id="b7144-103">This section describes the unmanaged structures that the debugging API uses.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b7144-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b7144-104">In This Section</span></span>

 <span data-ttu-id="b7144-105">[CLRDATA_ADDRESS_RANGE 構造体](clrdata-address-range-structure.md) アドレス範囲を定義します。</span><span class="sxs-lookup"><span data-stu-id="b7144-105">[CLRDATA_ADDRESS_RANGE Structure](clrdata-address-range-structure.md) Defines an address range.</span></span>

 <span data-ttu-id="b7144-106">[CLRDATA_IL_ADDRESS_MAP 構造体](clrdata-il-address-map-structure.md) IL とアドレスのマッピングを定義します。</span><span class="sxs-lookup"><span data-stu-id="b7144-106">[CLRDATA_IL_ADDRESS_MAP Structure](clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>

 <span data-ttu-id="b7144-107">[CLR_DEBUGGING_VERSION 構造体](clr-debugging-version-structure.md) デバッグのために共通言語ランタイム (CLR) の製品バージョンを定義します。</span><span class="sxs-lookup"><span data-stu-id="b7144-107">[CLR_DEBUGGING_VERSION Structure](clr-debugging-version-structure.md) Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>

 <span data-ttu-id="b7144-108">[CodeChunkInfo 構造体](codechunkinfo-structure.md) メモリ内の1つのコードチャンクを表します。</span><span class="sxs-lookup"><span data-stu-id="b7144-108">[CodeChunkInfo Structure](codechunkinfo-structure.md) Represents a single chunk of code in memory.</span></span>

 <span data-ttu-id="b7144-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) スレッドのフレームで現在アクティブになっている関数に関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="b7144-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contains information about the functions that are currently active in a thread's frames.</span></span>

 <span data-ttu-id="b7144-110">[COR_ARRAY_LAYOUT 構造体](cor-array-layout-structure.md) メモリ内の配列オブジェクトのレイアウトに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="b7144-110">[COR_ARRAY_LAYOUT Structure](cor-array-layout-structure.md) Provides information about the layout of an array object in memory.</span></span>

 <span data-ttu-id="b7144-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Microsoft 中間言語 (MSIL) コードをネイティブコードにマップするために使用されるオフセットを格納します。</span><span class="sxs-lookup"><span data-stu-id="b7144-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>

 <span data-ttu-id="b7144-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) コード範囲のオフセット情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="b7144-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contains the offset information for a range of code.</span></span>

 <span data-ttu-id="b7144-113">[COR_FIELD 構造体](cor-field-structure.md) オブジェクトのフィールドに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="b7144-113">[COR_FIELD Structure](cor-field-structure.md) Provides information about a field in an object.</span></span>

 <span data-ttu-id="b7144-114">[COR_GC_REFERENCE 構造体](cor-gc-reference-structure.md) ガベージコレクトされるオブジェクトに関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="b7144-114">[COR_GC_REFERENCE Structure](cor-gc-reference-structure.md) Contains information about an object that is to be garbage-collected.</span></span>

 <span data-ttu-id="b7144-115">[COR_HEAPINFO 構造体](cor-heapinfo-structure.md) 列挙可能かどうかなど、ガベージコレクションヒープに関する一般的な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="b7144-115">[COR_HEAPINFO Structure](cor-heapinfo-structure.md) Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>

 <span data-ttu-id="b7144-116">[COR_HEAPOBJECT 構造体](cor-heapobject-structure.md) マネージヒープ上のオブジェクトに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="b7144-116">[COR_HEAPOBJECT Structure](cor-heapobject-structure.md) Provides information about an object on the managed heap.</span></span>

 <span data-ttu-id="b7144-117">[COR_IL_MAP](cor-il-map-structure.md) 関数の相対オフセットの変更を指定します。</span><span class="sxs-lookup"><span data-stu-id="b7144-117">[COR_IL_MAP](cor-il-map-structure.md) Specifies changes in the relative offset of a function.</span></span>

 <span data-ttu-id="b7144-118">[COR_SEGMENT 構造体](cor-segment-structure.md) マネージヒープのメモリ領域に関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="b7144-118">[COR_SEGMENT Structure](cor-segment-structure.md) Contains information about a region of memory in the managed heap.</span></span>

 <span data-ttu-id="b7144-119">[COR_TYPEID 構造体](cor-typeid-structure.md) 型識別子を格納します。</span><span class="sxs-lookup"><span data-stu-id="b7144-119">[COR_TYPEID Structure](cor-typeid-structure.md) Contains a type identifier.</span></span>

 <span data-ttu-id="b7144-120">[COR_TYPE_LAYOUT 構造体](cor-type-layout-structure.md) メモリ内のオブジェクトのレイアウトに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="b7144-120">[COR_TYPE_LAYOUT Structure](cor-type-layout-structure.md) Provides information about the layout of an object in memory.</span></span>

 <span data-ttu-id="b7144-121">[COR_VERSION](cor-version-structure.md) 共通言語ランタイムの標準の4部構成のバージョン番号を格納します。</span><span class="sxs-lookup"><span data-stu-id="b7144-121">[COR_VERSION](cor-version-structure.md) Stores the standard four-part version number of the common language runtime.</span></span>

 <span data-ttu-id="b7144-122">[CorDebugBlockingObject 構造体](cordebugblockingobject-structure.md) スレッドをブロックするオブジェクトと、スレッドがブロックされる理由を定義します。</span><span class="sxs-lookup"><span data-stu-id="b7144-122">[CorDebugBlockingObject Structure](cordebugblockingobject-structure.md) Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>

 <span data-ttu-id="b7144-123">[CorDebugEHClause 構造体](cordebugehclause-structure.md) 指定された中間言語 (IL) の例外処理 (EH) 句を表します。</span><span class="sxs-lookup"><span data-stu-id="b7144-123">[CorDebugEHClause Structure](cordebugehclause-structure.md) Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>

 <span data-ttu-id="b7144-124">[CorDebugExceptionObjectStackFrame 構造体](cordebugexceptionobjectstackframe-structure.md) 例外オブジェクトからのスタックフレーム情報を表します。</span><span class="sxs-lookup"><span data-stu-id="b7144-124">[CorDebugExceptionObjectStackFrame Structure](cordebugexceptionobjectstackframe-structure.md) Represents stack frame information from an exception object.</span></span>

 <span data-ttu-id="b7144-125">[Cordebugguidtotypemapping 構造体](cordebugguidtotypemapping-structure.md) Windows ランタイム GUID を対応する [テキスト](icordebugtype-interface.md) オブジェクトにマップします。</span><span class="sxs-lookup"><span data-stu-id="b7144-125">[CorDebugGuidToTypeMapping Structure](cordebugguidtotypemapping-structure.md) Maps a Windows Runtime GUID to its corresponding [ICorDebugType](icordebugtype-interface.md) object.</span></span>

 <span data-ttu-id="b7144-126">[DacpGetModuleAddress 構造体](dacpgetmoduleaddress-structure.md) モジュールアドレス要求のコンテナーを定義します。</span><span class="sxs-lookup"><span data-stu-id="b7144-126">[DacpGetModuleAddress Structure](dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

 <span data-ttu-id="b7144-127">[DacpMethodDescData 構造体](dacpmethoddescdata-structure.md) メソッドのランタイム情報のトランスポートバッファーを定義します。</span><span class="sxs-lookup"><span data-stu-id="b7144-127">[DacpMethodDescData Structure](dacpmethoddescdata-structure.md) Defines a transport buffer for a method's runtime information.</span></span>

 <span data-ttu-id="b7144-128">[Dacpmoduledata 構造体](dacpmoduledata-structure.md) モジュールのランタイム情報のトランスポートバッファーを定義します。</span><span class="sxs-lookup"><span data-stu-id="b7144-128">[DacpModuleData Structure](dacpmoduledata-structure.md) Defines a transport buffer for a module's runtime information.</span></span>

 <span data-ttu-id="b7144-129">[DacpReJitData 構造体](dacprejitdata-structure.md) プロファイラーによってインストルメント化された特定のメソッドに関する基本情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="b7144-129">[DacpReJitData Structure](dacprejitdata-structure.md) Defines the basic information about a given profiler-instrumented method.</span></span>

 <span data-ttu-id="b7144-130">[StackTrace_SimpleContext 構造体](stacktrace-simplecontext-structure.md) 完全な構造体の代わりに使用できる単純なコンテキストを提供 `CONTEXT` します。</span><span class="sxs-lookup"><span data-stu-id="b7144-130">[StackTrace_SimpleContext Structure](stacktrace-simplecontext-structure.md) Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="b7144-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7144-131">Related Sections</span></span>

 [<span data-ttu-id="b7144-132">デバッグ コクラス</span><span class="sxs-lookup"><span data-stu-id="b7144-132">Debugging Coclasses</span></span>](debugging-coclasses.md)

 [<span data-ttu-id="b7144-133">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7144-133">Debugging Interfaces</span></span>](debugging-interfaces.md)

 [<span data-ttu-id="b7144-134">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="b7144-134">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)

 [<span data-ttu-id="b7144-135">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="b7144-135">Debugging Enumerations</span></span>](debugging-enumerations.md)

 [<span data-ttu-id="b7144-136">デバッグ</span><span class="sxs-lookup"><span data-stu-id="b7144-136">Debugging</span></span>](index.md)
