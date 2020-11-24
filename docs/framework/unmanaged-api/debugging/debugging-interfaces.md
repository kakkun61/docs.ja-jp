---
title: デバッグのインターフェイス
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: a3dd81ceaab2ba467d4c8ca091c1c2219040a273
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676297"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="f56fb-102">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f56fb-102">Debugging Interfaces</span></span>

<span data-ttu-id="f56fb-103">ここでは、共通言語ランタイム (CLR: Common Language Runtime) で実行するプログラムのデバッグを処理するアンマネージ インターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f56fb-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f56fb-104">In This Section</span></span>  

 <span data-ttu-id="f56fb-105">[ICLRDataEnumMemoryRegions インターフェイス](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span></span>\
 <span data-ttu-id="f56fb-106">呼び出し元が指定したメモリ範囲を列挙するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="f56fb-107">[ICLRDataEnumMemoryRegionsCallback インターフェイス](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)</span></span>\
 <span data-ttu-id="f56fb-108">メモリの指定された領域を列挙した結果の `EnumMemoryRegions` をデバッガーにレポートするコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="f56fb-109">[ICLRDataTarget インターフェイス](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)</span></span>\
 <span data-ttu-id="f56fb-110">対象の CLR プロセスと対話するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="f56fb-111">[ICLRDataTarget2 インターフェイス](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-112">データ アクセス サービス層で使用して対象プロセスの仮想メモリ領域を操作する、`ICLRDataTarget` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="f56fb-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="f56fb-113">[ICLRDataTarget3 インターフェイス](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="f56fb-114">例外情報へのアクセスを提供する [ICLRDataTarget2](iclrdatatarget2-interface.md) のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="f56fb-114">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="f56fb-115">[ICLRDebugging インターフェイス](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-115">[ICLRDebugging Interface](iclrdebugging-interface.md)</span></span>\
 <span data-ttu-id="f56fb-116">デバッグ用にモジュールの読み込みとアンロードを処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="f56fb-117">[ICLRDebuggingLibraryProvider インターフェイス](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-117">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)</span></span>\
 <span data-ttu-id="f56fb-118">には、提供 [ライブラリのメソッド](iclrdebugginglibraryprovider-providelibrary-method.md) メソッドが含まれています。このメソッドは、共通言語ランタイムのバージョン固有のデバッグライブラリをオンデマンドで検索して読み込むことができるようにする、ライブラリプロバイダーのコールバックインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-118">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="f56fb-119">[ICLRMetadataLocator インターフェイス](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="f56fb-120">データ アクセス サービス層で使用して、対象プロセス内のアセンブリのメタデータを見つけるためのインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="f56fb-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="f56fb-121">[ICorDebug インターフェイス](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-121">[ICorDebug Interface](icordebug-interface.md)</span></span>\
 <span data-ttu-id="f56fb-122">開発者が CLR 環境でアプリケーションをデバッグできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="f56fb-123">[の Appdomain インターフェイス](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)</span></span>\
 <span data-ttu-id="f56fb-124">アプリケーション ドメインをデバッグするためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-124">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="f56fb-125">[ICorDebugAppDomain2 インターフェイス](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-126">配列、ポインター、関数ポインター、および ByRef 型を使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="f56fb-127">これは、`ICorDebugAppDomain` インターフェイスの機能を拡張するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="f56fb-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="f56fb-128">[ICorDebugAppDomain3 インターフェイス](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)</span></span>\
 <span data-ttu-id="f56fb-129">アプリケーションドメインの Windows ランタイム型を操作するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-129">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="f56fb-130">このインターフェイスは、`ICorDebugAppDomain` インターフェイスと `ICorDebugAppDomain2` インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="f56fb-131">[ICorDebugAppDomain4 インターフェイス](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)</span></span>\
 <span data-ttu-id="f56fb-132">コードを論理的に拡張して、COM 呼び出し可能ラッパーからマネージオブジェクトを [取得します](icordebugappdomain-interface.md) 。</span><span class="sxs-lookup"><span data-stu-id="f56fb-132">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="f56fb-133">[ICorDebugAppDomainEnum インターフェイス](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-134">列挙体の次の位置から、指定した数の `ICorDebugAppDomain` の値を返すメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="f56fb-135">[ICorDebugArrayValue インターフェイス](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-135">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)</span></span>\
 <span data-ttu-id="f56fb-136">1 次元または多次元の配列を表す `ICorDebugHeapValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="f56fb-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="f56fb-137">[のアセンブリインターフェイス](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-137">[ICorDebugAssembly Interface](icordebugassembly-interface.md)</span></span>\
 <span data-ttu-id="f56fb-138">アセンブリを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-138">Represents an assembly.</span></span>  
  
 <span data-ttu-id="f56fb-139">[ICorDebugAssembly2 インターフェイス](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-139">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-140">アセンブリを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-140">Represents an assembly.</span></span> <span data-ttu-id="f56fb-141">これは、`ICorDebugAssembly` インターフェイスの機能を拡張するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="f56fb-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="f56fb-142">[ICorDebugAssembly3 インターフェイス](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)</span></span>\
 <span data-ttu-id="f56fb-143">は、この [アセンブリ](icordebugassembly-interface.md) インターフェイスを論理的に拡張して、コンテナーアセンブリとそれに含まれるアセンブリのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-143">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="f56fb-144">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="f56fb-144">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f56fb-145">[いいね。インターフェイス](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-145">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-146">`ICorDebugEnum` メソッドを実装し、`ICorDebugAssembly` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="f56fb-147">[ICorDebugBlockingObjectEnum インターフェイス](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-148">[CorDebugBlockingObject](cordebugblockingobject-structure.md)構造体のリストの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-148">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="f56fb-149">[の値のインターフェイス](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-149">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)</span></span>\
 <span data-ttu-id="f56fb-150">ボックス化された値クラスのオブジェクトを表す `ICorDebugHeapValue` のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="f56fb-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="f56fb-151">[ICorDebugBreakpoint インターフェイス](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-151">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="f56fb-152">関数のブレークポイント、または値のウォッチ ポイントを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="f56fb-153">[いいね Pointenum インターフェイス](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-153">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-154">`ICorDebugEnum` メソッドを実装し、`ICorDebugBreakpoint` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="f56fb-155">[というチェーンインターフェイス](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-155">[ICorDebugChain Interface](icordebugchain-interface.md)</span></span>\
 <span data-ttu-id="f56fb-156">物理呼び出し履歴または論理呼び出し履歴のセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="f56fb-157">[ICorDebugChainEnum インターフェイス](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-157">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-158">`ICorDebugEnum` メソッドを実装し、`ICorDebugChain` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="f56fb-159">[のクラスインターフェイス](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-159">[ICorDebugClass Interface](icordebugclass-interface.md)</span></span>\
 <span data-ttu-id="f56fb-160">基本型または複合型 (つまり、ユーザー定義) のいずれかの型を表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="f56fb-161">型がジェネリックの場合、`ICorDebugClass` はインスタンス化されないジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="f56fb-162">[ICorDebugClass2 インターフェイス](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-163">ジェネリック、または <xref:System.Type> 型のメソッド パラメーターを持つクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="f56fb-164">このインターフェイスは、`ICorDebugClass` の機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-164">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="f56fb-165">[のコードインターフェイス](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-165">[ICorDebugCode Interface](icordebugcode-interface1.md)</span></span>\
 <span data-ttu-id="f56fb-166">Microsoft Intermediate Language (MSIL) コードまたはネイティブ コードのセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="f56fb-167">[ICorDebugCode2 インターフェイス](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-167">[ICorDebugCode2 Interface](icordebugcode2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-168">`ICorDebugCode` の機能を拡張するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="f56fb-169">[ICorDebugCode3 インターフェイス](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)</span></span>\
 <span data-ttu-id="f56fb-170">[コード](icordebugcode-interface1.md)と[ICorDebugCode2](icordebugcode2-interface.md)を拡張して、マネージ戻り値に関する情報を提供するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-170">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="f56fb-171">[ICorDebugCode4 インターフェイス](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)</span></span>\
 <span data-ttu-id="f56fb-172">デバッガーが関数のローカル変数と引数を列挙できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="f56fb-173">[のコードの列挙型インターフェイス](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-173">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-174">`ICorDebugEnum` メソッドを実装し、`ICorDebugCode` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="f56fb-175">[「いいね! 値インターフェイス」](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="f56fb-176">キャッシュされたインターフェイス オブジェクトを取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="f56fb-177">[テキストコンテキストインターフェイス](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-177">[ICorDebugContext Interface](icordebugcontext-interface.md)</span></span>\
 <span data-ttu-id="f56fb-178">コンテキストのオブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-178">Represents a context object.</span></span> <span data-ttu-id="f56fb-179">このインターフェイスはまだ実装されていません。</span><span class="sxs-lookup"><span data-stu-id="f56fb-179">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="f56fb-180">[のコントロールインターフェイス](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-180">[ICorDebugController Interface](icordebugcontroller-interface.md)</span></span>\
 <span data-ttu-id="f56fb-181">コードの実行コンテキストを制御できる <xref:System.Diagnostics.Process> または <xref:System.AppDomain> のスコープを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="f56fb-182">[の場合は、このインターフェイス](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-182">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)</span></span>\
 <span data-ttu-id="f56fb-183">特定のターゲット プロセスにアクセスするためのコールバック インターフェイスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f56fb-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="f56fb-184">[ICorDebugDataTarget2 インターフェイス](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-185">によって、"の" を論理的に [拡張します](icordebugdatatarget-interface.md) 。</span><span class="sxs-lookup"><span data-stu-id="f56fb-185">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="f56fb-186">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="f56fb-186">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f56fb-187">[ICorDebugDataTarget3 インターフェイス](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="f56fb-188">提供され [たモジュール](icordebugdatatarget-interface.md) に関する情報を提供するために、によって、参照インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-188">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="f56fb-189">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="f56fb-189">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f56fb-190">[のイベントインターフェイス](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)</span></span>\
 <span data-ttu-id="f56fb-191">すべての `ICorDebug` デバッグ イベントを派生させる基本インターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="f56fb-192">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="f56fb-192">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f56fb-193">[ICorDebugEditAndContinueErrorInfo インターフェイス](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)</span></span>\
 <span data-ttu-id="f56fb-194">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="f56fb-194">Obsolete.</span></span> <span data-ttu-id="f56fb-195">このインターフェイスは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f56fb-195">Do not use this interface.</span></span>  
  
 <span data-ttu-id="f56fb-196">[ICorDebugEditAndContinueSnapshot インターフェイス](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)</span></span>\
 <span data-ttu-id="f56fb-197">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="f56fb-197">Obsolete.</span></span> <span data-ttu-id="f56fb-198">このインターフェイスは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f56fb-198">Do not use this interface.</span></span>  
  
 <span data-ttu-id="f56fb-199">[ICorDebugEnum インターフェイス](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-199">[ICorDebugEnum Interface](icordebugenum-interface1.md)</span></span>\
 <span data-ttu-id="f56fb-200">デバッグ中の列挙子の抽象基底インターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="f56fb-201">[いいね Infoenum インターフェイス](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-201">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-202">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="f56fb-202">Obsolete.</span></span> <span data-ttu-id="f56fb-203">このインターフェイスは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f56fb-203">Do not use this interface.</span></span>  
  
 <span data-ttu-id="f56fb-204">[の場合は、インターフェイス](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-204">[ICorDebugEval Interface](icordebugeval-interface.md)</span></span>\
 <span data-ttu-id="f56fb-205">デバッガーが、デバッグ中のコードのコンテキスト内でコードを実行できるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="f56fb-206">[ICorDebugEval2 インターフェイス](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-206">[ICorDebugEval2 Interface](icordebugeval2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-207">ジェネリック型をサポートできるように `ICorDebugEval` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="f56fb-208">[は、の例外のイベントインターフェイス](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-208">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)</span></span>\
 <span data-ttu-id="f56fb-209">は、例外イベントをサポートするために、の [イベント](icordebugdebugevent-interface.md) インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-209">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="f56fb-210">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="f56fb-210">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f56fb-211">[いい Exceptionobjectcallstackenum インターフェイス](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-212">例外オブジェクトに埋め込まれているコール スタックの情報の列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="f56fb-213">[の値インターフェイス](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="f56fb-214">によっ [て、](icordebugobjectvalue-interface.md) のマネージ例外オブジェクトからスタックトレース情報を提供するように、の機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-214">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="f56fb-215">[テキストフレームインターフェイス](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-215">[ICorDebugFrame Interface](icordebugframe-interface.md)</span></span>\
 <span data-ttu-id="f56fb-216">現在のスタックのフレームを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-216">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="f56fb-217">[の場合は、インターフェイスの列挙体](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-217">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-218">`ICorDebugEnum` メソッドを実装し、`ICorDebugFrame` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="f56fb-219">[の関数インターフェイス](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-219">[ICorDebugFunction Interface](icordebugfunction-interface1.md)</span></span>\
 <span data-ttu-id="f56fb-220">マネージド関数またはマネージド メソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-220">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="f56fb-221">[ICorDebugFunction2 インターフェイス](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-222">`ICorDebugFunction` を論理的に拡張して、"マイ コードのみ" ステップ実行によるデバッグをサポートします。</span><span class="sxs-lookup"><span data-stu-id="f56fb-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="f56fb-223">[ICorDebugFunction3 インターフェイス](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)</span></span>\
 <span data-ttu-id="f56fb-224">により、再 Jit 要求からコードへのアクセスを提供するために、の [関数](icordebugfunction-interface1.md) インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-224">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="f56fb-225">[いいね! ブレークポイントインターフェイス](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="f56fb-226">関数内のブレークポイントをサポートするように `ICorDebugBreakpoint` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="f56fb-227">["いいね!" インターフェイスの列挙](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-228">ガベージ コレクトされるオブジェクトの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="f56fb-229">[の値インターフェイス](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-229">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)</span></span>\
 <span data-ttu-id="f56fb-230">すべての値に適用する `ICorDebugValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="f56fb-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="f56fb-231">このインターフェイスは、値に対して Get メソッドと Set メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-231">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="f56fb-232">[は、"いいね" インターフェイス](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-233">GUID およびその対応する `ICorDebugType` オブジェクトをマップするオブジェクトの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="f56fb-234">[の値インターフェイス](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-234">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)</span></span>\
 <span data-ttu-id="f56fb-235">デバッガーが作成したガベージ コレクションのハンドルへの参照値を表す `ICorDebugReferenceValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="f56fb-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="f56fb-236">[このインターフェイスは、このインターフェイスによって](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-237">マネージド ヒープのオブジェクトの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="f56fb-238">[ICorDebugHeapSegmentEnum インターフェイス](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-239">マネージド ヒープのメモリ領域の列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="f56fb-240">["いいね!" インターフェイス](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-240">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)</span></span>\
 <span data-ttu-id="f56fb-241">CLR ガベージ コレクターによって収集されたオブジェクトを表す `ICorDebugValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="f56fb-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="f56fb-242">[ICorDebugHeapValue2 インターフェイス](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)</span></span>\
 <span data-ttu-id="f56fb-243">ランタイム ハンドルのサポートを提供する `ICorDebugHeapValue` の拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="f56fb-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="f56fb-244">[ICorDebugHeapValue3 インターフェイス](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)</span></span>\
 <span data-ttu-id="f56fb-245">オブジェクトのモニター ロック プロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-245">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="f56fb-246">[のコードインターフェイス](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)</span></span>\
 <span data-ttu-id="f56fb-247">中間言語 (IL) コードのセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="f56fb-248">[ICorDebugILCode2 インターフェイス](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-249">では、この [コード](icordebugilcode-interface.md) インターフェイスを論理的に拡張して、関数のローカル変数シグネチャのトークンを返すメソッドを提供し、プロファイラーのインストルメント化された中間言語 (il) オフセットを元のメソッドの il オフセットにマップします。</span><span class="sxs-lookup"><span data-stu-id="f56fb-249">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="f56fb-250">[いいね! のインターフェイス](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)</span></span>\
 <span data-ttu-id="f56fb-251">MSIL コードのスタック フレームを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-251">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="f56fb-252">[ICorDebugILFrame2 インターフェイス](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-253">`ICorDebugILFrame` の論理拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="f56fb-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="f56fb-254">[ICorDebugILFrame3 インターフェイス](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)</span></span>\
 <span data-ttu-id="f56fb-255">関数の戻り値をカプセル化するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="f56fb-256">[ICorDebugILFrame4 インターフェイス](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)</span></span>\
 <span data-ttu-id="f56fb-257">ローカル変数にアクセスできるようにするメソッドおよび中間言語 (IL) コードのスタック フレームのコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="f56fb-258">パラメーターは、プロファイラーの ReJIT インストルメンテーションに追加される変数およびコードへデバッガーがアクセスできるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="f56fb-259">[のコードインターフェイス](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="f56fb-260">インスタンス フィールドのデバッグ シンボル情報を表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="f56fb-261">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="f56fb-261">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f56fb-262">[のテキストフレームインターフェイス](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-262">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)</span></span>\
 <span data-ttu-id="f56fb-263">デバッガーのフレーム種類を識別します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-263">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="f56fb-264">[ICorDebugInternalFrame2 インターフェイス](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-265">スタックアドレスや、 [テキストフレーム](icordebugframe-interface.md) オブジェクトに対する位置など、内部フレームに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="f56fb-266">[ICorDebugLoadedModule インターフェイス](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)</span></span>\
 <span data-ttu-id="f56fb-267">読み込まれたモジュールについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-267">Provides information about a loaded module.</span></span> <span data-ttu-id="f56fb-268">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="f56fb-268">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f56fb-269">[の Managedmanagedcallback インターフェイス](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="f56fb-270">デバッガーのコールバックを処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-270">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="f56fb-271">[ICorDebugManagedCallback2 インターフェイス](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-272">デバッガーの例外処理およびマネージド デバッグ アシスタント (MDA: Managed Debugging Assistants) をサポートするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="f56fb-273">`ICorDebugManagedCallback2` は、`ICorDebugManagedCallback` の論理拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="f56fb-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="f56fb-274">[ICorDebugManagedCallback3 インターフェイス](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)</span></span>\
 <span data-ttu-id="f56fb-275">有効なカスタムのデバッガー通知が発生したことを示すコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="f56fb-276">[は、のインターフェイス](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-276">[ICorDebugMDA Interface](icordebugmda-interface.md)</span></span>\
 <span data-ttu-id="f56fb-277">マネージド デバッグ アシスタント (MDA) メッセージを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="f56fb-278">[のの Memorybuffer インターフェイス](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)</span></span>\
 <span data-ttu-id="f56fb-279">メモリ内のバッファーを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="f56fb-280">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="f56fb-280">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f56fb-281">[ICorDebugMergedAssemblyRecord インターフェイス](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-281">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)</span></span>\
 <span data-ttu-id="f56fb-282">マージされたアセンブリに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="f56fb-283">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="f56fb-283">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f56fb-284">[ICorDebugMetaDataLocator インターフェイス](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="f56fb-285">デバッガーにメタデータ情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-285">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="f56fb-286">[のモジュールインターフェイス](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-286">[ICorDebugModule Interface](icordebugmodule-interface.md)</span></span>\
 <span data-ttu-id="f56fb-287">実行可能ファイルまたはダイナミック リンク ライブラリ (DLL: Dynamic-Link Library) のいずれかの CLR モジュールを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="f56fb-288">[ICorDebugModule2 インターフェイス](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-289">`ICorDebugModule` の論理的な拡張機能として動作します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="f56fb-290">[ICorDebugModule3 インターフェイス](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)</span></span>\
 <span data-ttu-id="f56fb-291">動的モジュールのシンボル リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="f56fb-292">[のモジュールのブレークポイントインターフェイス](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="f56fb-293">特定のモジュールにアクセスできるように `ICorDebugBreakpoint` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="f56fb-294">[いい Moduledebugevent インターフェイス](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-294">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)</span></span>\
 <span data-ttu-id="f56fb-295">モジュールレベルのイベントをサポートするように、のモジュールレベル [のイベントを](icordebugdebugevent-interface.md) 拡張します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-295">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="f56fb-296">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="f56fb-296">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f56fb-297">[のモジュール列挙型インターフェイス](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-297">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-298">`ICorDebugEnum` メソッドを実装し、`ICorDebugModule` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="f56fb-299">[ICorDebugMutableDataTarget インターフェイス](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)</span></span>\
 <span data-ttu-id="f56fb-300">変更可能なデータターゲットをサポートするために、の機能を拡張[します。](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-300">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="f56fb-301">[テキストフレームインターフェイス](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-301">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)</span></span>\
 <span data-ttu-id="f56fb-302">ネイティブ フレームで使用される `ICorDebugFrame` の特化された実装。</span><span class="sxs-lookup"><span data-stu-id="f56fb-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="f56fb-303">[ICorDebugNativeFrame2 インターフェイス](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-304">子と親のフレームの関係をテストするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="f56fb-305">[このインターフェイス](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-305">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-306">`ICorDebugEnum` メソッドを実装し、オブジェクトの配列を相対仮想アドレス (RVA: Relative Virtual Address) で列挙します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="f56fb-307">[の値インターフェイス](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-307">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="f56fb-308">オブジェクトが含まれた値を表す `ICorDebugValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="f56fb-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="f56fb-309">[ICorDebugObjectValue2 インターフェイス](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-309">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-310">継承およびオーバーライドをサポートするように `ICorDebugObjectValue` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="f56fb-311">[のプロセスインターフェイス](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-311">[ICorDebugProcess Interface](icordebugprocess-interface.md)</span></span>\
 <span data-ttu-id="f56fb-312">マネージド コードを実行しているプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-312">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="f56fb-313">[ICorDebugProcess2 インターフェイス](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-313">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)</span></span>\
 <span data-ttu-id="f56fb-314">`ICorDebugProcess` の論理拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="f56fb-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="f56fb-315">[ICorDebugProcess3 インターフェイス](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)</span></span>\
 <span data-ttu-id="f56fb-316">カスタムのデバッガー通知を制御します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-316">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="f56fb-317">[ICorDebugProcess4 インターフェイス](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)</span></span>\
 <span data-ttu-id="f56fb-318">アウトプロセス実行制御のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-318">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="f56fb-319">[ICorDebugProcess5 インターフェイス](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)</span></span>\
 <span data-ttu-id="f56fb-320">[は、](icordebugprocess-interface.md)マネージヒープへのアクセスをサポートし、マネージオブジェクトのガベージコレクションに関する情報を提供し、デバッガーがアプリケーションのローカルのネイティブイメージキャッシュからイメージを読み込むかどうかを判断するために、コードを拡張します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-320">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="f56fb-321">[ICorDebugProcess6 インターフェイス](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)</span></span>\
 <span data-ttu-id="f56fb-322">コードを論理的に [拡張して、ネイティブ](icordebugprocess-interface.md) の例外デバッグイベントと仮想モジュール分割でエンコードされたマネージデバッグイベントをデコードするなどの機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="f56fb-322">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="f56fb-323">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="f56fb-323">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f56fb-324">[ICorDebugProcess7 インターフェイス](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)</span></span>\
 <span data-ttu-id="f56fb-325">ターゲット プロセスでメモリ内のメタデータ更新を処理するようにデバッガーを構成するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-325">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="f56fb-326">[ICorDebugProcess8 インターフェイス](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)</span></span>\
 <span data-ttu-id="f56fb-327">ICorDebugManagedCallback2 [process](icordebugprocess-interface.md)インターフェイスを論理的に拡張して、特定の種類の[ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)例外コールバックを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="f56fb-327">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="f56fb-328">[の型の Processenum インターフェイス](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-328">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-329">`ICorDebugEnum` メソッドを実装し、`ICorDebugProcess` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-329">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="f56fb-330">[の値インターフェイス](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-330">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)</span></span>\
 <span data-ttu-id="f56fb-331">参照型をサポートする `ICorDebugValue` のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="f56fb-331">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="f56fb-332">[いいです。](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)</span></span>\
 <span data-ttu-id="f56fb-333">現在コードを実行しているマシン上で使用できるレジスタ セットを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-333">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="f56fb-334">[ICorDebugRegisterSet2 インターフェイス](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-335">64 を超えるレジスタを持つハードウェア プラットフォーム用に `ICorDebugRegisterSet` の機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-335">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="f56fb-336">[のリモートインターフェイス](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-336">[ICorDebugRemote Interface](icordebugremote-interface.md)</span></span>\
 <span data-ttu-id="f56fb-337">リモート ターゲット プロセスに対してマネージド デバッガーを起動または接続する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-337">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="f56fb-338">[の Remotetarget インターフェイス](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-338">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)</span></span>\
 <span data-ttu-id="f56fb-339">開発者が CLR 環境で Silverlight ベース アプリケーションをデバッグできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-339">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="f56fb-340">[ICorDebugRuntimeUnwindableFrame インターフェイス](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)</span></span>\
 <span data-ttu-id="f56fb-341">共通言語ランタイム (CLR: Common Language Runtime) でフレームをアンワインドする必要のあるアンマネージ メソッドに対してサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-341">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="f56fb-342">[は、このインターフェイス](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)</span></span>\
 <span data-ttu-id="f56fb-343">スレッドのスタック上のマネージド メソッド (フレーム) を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-343">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="f56fb-344">[の場合は、コードインターフェイス](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="f56fb-345">静的フィールドのデバッグ シンボル情報を表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-345">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="f56fb-346">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="f56fb-346">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f56fb-347">[ICorDebugStepper インターフェイス](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-347">[ICorDebugStepper Interface](icordebugstepper-interface.md)</span></span>\
 <span data-ttu-id="f56fb-348">デバッガーが実行するコード実行内のステップを表します。コマンドの発行から完了までの間は識別子として機能します。これを使用するとステップをキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="f56fb-348">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="f56fb-349">[ICorDebugStepper2 インターフェイス](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-349">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)</span></span>\
 <span data-ttu-id="f56fb-350">マイ コードのみ (JMC: Just My Code) デバッグのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-350">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="f56fb-351">[というインターフェイス](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-351">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-352">`ICorDebugEnum` メソッドを実装し、`ICorDebugStepper` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-352">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="f56fb-353">[いいねインターフェイス](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-353">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)</span></span>\
 <span data-ttu-id="f56fb-354">文字列値に適用する `ICorDebugHeapValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="f56fb-354">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="f56fb-355">[は、プロバイダーインターフェイス](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)</span></span>\
 <span data-ttu-id="f56fb-356">デバッグ シンボル情報を取得するために使用できるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-356">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="f56fb-357">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="f56fb-357">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f56fb-358">[ICorDebugSymbolProvider2 インターフェイス](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-359">追加のデバッグシンボル情報を取得するために、この [プロバイダー](icordebugsymbolprovider-interface.md) インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-359">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="f56fb-360">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="f56fb-360">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f56fb-361">[のスレッドインターフェイス](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-361">[ICorDebugThread Interface](icordebugthread-interface.md)</span></span>\
 <span data-ttu-id="f56fb-362">プロセス内のスレッドを表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-362">Represents a thread in a process.</span></span> <span data-ttu-id="f56fb-363">`ICorDebugThread` インスタンスの有効期間は、それが表しているスレッドの有効期間と同じです。</span><span class="sxs-lookup"><span data-stu-id="f56fb-363">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="f56fb-364">[ICorDebugThread2 インターフェイス](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-364">[ICorDebugThread2 Interface](icordebugthread2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-365">`ICorDebugThread` の論理的な拡張機能として動作します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-365">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="f56fb-366">[ICorDebugThread3 インターフェイス](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)</span></span>\
 <span data-ttu-id="f56fb-367">とそれに対応するインターフェイス [へのエントリ](icordebugstackwalk-interface.md) ポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-367">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="f56fb-368">[ICorDebugThread4 インターフェイス](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)</span></span>\
 <span data-ttu-id="f56fb-369">スレッドのブロック情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-369">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="f56fb-370">[いい Threadenum インターフェイス](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-370">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)</span></span>\
 <span data-ttu-id="f56fb-371">`ICorDebugEnum` メソッドを実装し、`ICorDebugThread` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-371">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="f56fb-372">[の型のインターフェイス](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-372">[ICorDebugType Interface](icordebugtype-interface.md)</span></span>\
 <span data-ttu-id="f56fb-373">基本型または複合型 (つまり、ユーザー定義) のいずれかの型を表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-373">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="f56fb-374">型がジェネリックの場合、`ICorDebugType` はインスタンス化されたジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-374">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="f56fb-375">[ICorDebugType2 インターフェイス](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-376">によって、テキスト型または複合型 (ユーザー定義型) の型識別子を取得するため [に、を拡張します](icordebugtype-interface.md) 。</span><span class="sxs-lookup"><span data-stu-id="f56fb-376">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="f56fb-377">[の型のインターフェイス](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-377">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-378">`ICorDebugEnum` メソッドを実装し、`ICorDebugType` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-378">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="f56fb-379">[ICorDebugUnmanagedCallback インターフェイス](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="f56fb-380">CLR に直接関連していないネイティブ イベントについて通知します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-380">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="f56fb-381">[ICorDebugValue](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-381">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="f56fb-382">デバッグ中のプロセス内の読み取り値または書き込み値を表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-382">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="f56fb-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="f56fb-384">`ICorDebugValue` をサポートできるように `ICorDebugType` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-384">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="f56fb-385">[ICorDebugValue3 インターフェイス](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)</span></span>\
 <span data-ttu-id="f56fb-386">"ICorDebugValue" インターフェイスと "ICorDebugValue2" インターフェイスを拡張して、2 GB を超える配列のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-386">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="f56fb-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="f56fb-388">特定の値にアクセスできるように `ICorDebugBreakpoint` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-388">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="f56fb-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-390">`ICorDebugEnum` メソッドを実装し、`ICorDebugValue` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-390">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="f56fb-391">[ページホームインターフェイス](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)</span></span>\
 <span data-ttu-id="f56fb-392">関数のローカル変数または引数を表します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-392">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="f56fb-393">[の型の変数の列挙型インターフェイス](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-394">関数のローカル変数および引数に列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-394">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="f56fb-395">[ICorDebugVariableSymbol インターフェイス](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)</span></span>\
 <span data-ttu-id="f56fb-396">変数のデバッグ シンボル情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-396">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="f56fb-397">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="f56fb-397">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f56fb-398">[ICorDebugVirtualUnwinder インターフェイス](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)</span></span>\
 <span data-ttu-id="f56fb-399">スタック アンワインドを支援するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-399">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="f56fb-400">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="f56fb-400">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="f56fb-401">[ICorPublish インターフェイス](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-401">[ICorPublish Interface](icorpublish-interface.md)</span></span>\
 <span data-ttu-id="f56fb-402">発行プロセスの汎用インターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-402">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="f56fb-403">[ICorPublishAppDomain インターフェイス](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)</span></span>\
 <span data-ttu-id="f56fb-404">アプリケーション ドメインの情報を表し、提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-404">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="f56fb-405">[ICorPublishAppDomainEnum インターフェイス](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-406">現在プロセス内に存在する `ICorPublishAppDomain` オブジェクトのコレクションを走査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-406">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="f56fb-407">[ICorPublishEnum インターフェイス](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-408">発行する列挙子の抽象ベースとして機能します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-408">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="f56fb-409">[ICorPublishProcess インターフェイス](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)</span></span>\
 <span data-ttu-id="f56fb-410">プロセスの情報にアクセスするメソッドを適用します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-410">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="f56fb-411">[ICorPublishProcessEnum インターフェイス](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)</span></span>\
 <span data-ttu-id="f56fb-412">`ICorPublishProcess` オブジェクトのコレクションを走査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-412">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="f56fb-413">[ISOSDacInterface インターフェイス](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)</span></span>\
 <span data-ttu-id="f56fb-414">からデータにアクセスするためのヘルパーメソッドを提供 `SOS` します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-414">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="f56fb-415">[IXCLRDataMethodDefinition インターフェイス](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-415">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)</span></span>\
 <span data-ttu-id="f56fb-416">メソッド定義に関する情報を照会するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-416">Provides methods for querying information about a method definition.</span></span>

 <span data-ttu-id="f56fb-417">[IXCLRDataMethodInstance インターフェイス](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)</span></span>\
 <span data-ttu-id="f56fb-418">メソッドインスタンスに関する情報を照会するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-418">Provides methods for querying information about a method instance.</span></span>

 <span data-ttu-id="f56fb-419">[IXCLRDataModule インターフェイス](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)</span></span>\
 <span data-ttu-id="f56fb-420">読み込まれたモジュールに関する情報を照会するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-420">Provides methods for querying information about a loaded module.</span></span>

 <span data-ttu-id="f56fb-421">[IXCLRDataProcess インターフェイス](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)</span></span>\
 <span data-ttu-id="f56fb-422">プロセスに関する情報を照会するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f56fb-422">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="f56fb-423">関連項目</span><span class="sxs-lookup"><span data-stu-id="f56fb-423">Related Sections</span></span>  

 <span data-ttu-id="f56fb-424">[デバッグコクラス](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-424">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="f56fb-425">[デバッググローバル静的関数](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-425">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="f56fb-426">[列挙型のデバッグ](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-426">[Debugging Enumerations](debugging-enumerations.md)</span></span>\
 <span data-ttu-id="f56fb-427">[デバッグ構造体](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="f56fb-427">[Debugging Structures](debugging-structures.md)</span></span>\
