---
ms.openlocfilehash: 83644b9205d650da68c910095dd1d22a14940c44
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97366857"
---
### <a name="exclude-specific-symbols"></a><span data-ttu-id="65b14-101">特定のシンボルを除外する</span><span class="sxs-lookup"><span data-stu-id="65b14-101">Exclude specific symbols</span></span>

<span data-ttu-id="65b14-102">型やメソッドなど、特定のシンボルを分析から除外することができます。</span><span class="sxs-lookup"><span data-stu-id="65b14-102">You can exclude specific symbols, such as types and methods, from analysis.</span></span> <span data-ttu-id="65b14-103">たとえば、という名前の型内のどのコードでもルールを実行しないように指定するには、 `MyType` プロジェクトの *editorconfig* ファイルに次のキーと値のペアを追加します。</span><span class="sxs-lookup"><span data-stu-id="65b14-103">For example, to specify that the rule should not run on any code within types named `MyType`, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType
```

<span data-ttu-id="65b14-104">オプションの値で使用できるシンボル名の形式 (で区切られてい `|` ます):</span><span class="sxs-lookup"><span data-stu-id="65b14-104">Allowed symbol name formats in the option value (separated by `|`):</span></span>

- <span data-ttu-id="65b14-105">シンボル名のみ (包含する型または名前空間に関係なく、名前の付いたすべての記号が含まれます)。</span><span class="sxs-lookup"><span data-stu-id="65b14-105">Symbol name only (includes all symbols with the name, regardless of the containing type or namespace).</span></span>
- <span data-ttu-id="65b14-106">シンボルの [ドキュメント ID 形式](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)の完全修飾名。</span><span class="sxs-lookup"><span data-stu-id="65b14-106">Fully qualified names in the symbol's [documentation ID format](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings).</span></span> <span data-ttu-id="65b14-107">各シンボル名には、 `M:` メソッドの場合、型の場合は、 `T:` 名前空間の場合など、シンボルの種類のプレフィックスが必要です `N:` 。</span><span class="sxs-lookup"><span data-stu-id="65b14-107">Each symbol name requires a symbol-kind prefix, such as `M:` for methods, `T:` for types, and `N:` for namespaces.</span></span>
- <span data-ttu-id="65b14-108">`.ctor` コンストラクターの場合は、 `.cctor` 静的コンストラクターの場合は。</span><span class="sxs-lookup"><span data-stu-id="65b14-108">`.ctor` for constructors and `.cctor` for static constructors.</span></span>

<span data-ttu-id="65b14-109">例 :</span><span class="sxs-lookup"><span data-stu-id="65b14-109">Examples:</span></span>

| <span data-ttu-id="65b14-110">オプション値</span><span class="sxs-lookup"><span data-stu-id="65b14-110">Option Value</span></span> | <span data-ttu-id="65b14-111">まとめ</span><span class="sxs-lookup"><span data-stu-id="65b14-111">Summary</span></span> |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType` | <span data-ttu-id="65b14-112">という名前 `MyType` のすべての記号を検索します。</span><span class="sxs-lookup"><span data-stu-id="65b14-112">Matches all symbols named `MyType`.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType1|MyType2` | <span data-ttu-id="65b14-113">またはという名前のすべての記号と一致 `MyType1` `MyType2` します。</span><span class="sxs-lookup"><span data-stu-id="65b14-113">Matches all symbols named either `MyType1` or `MyType2`.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS.MyType.MyMethod(ParamType)` | <span data-ttu-id="65b14-114">`MyMethod`指定した完全修飾シグネチャと特定のメソッドを照合します。</span><span class="sxs-lookup"><span data-stu-id="65b14-114">Matches specific method `MyMethod` with the specified fully qualified signature.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS1.MyType1.MyMethod1(ParamType)|M:NS2.MyType2.MyMethod2(ParamType)` | <span data-ttu-id="65b14-115">特定のメソッド `MyMethod1` と、 `MyMethod2` それぞれの完全修飾署名を照合します。</span><span class="sxs-lookup"><span data-stu-id="65b14-115">Matches specific methods `MyMethod1` and `MyMethod2` with the respective fully qualified signatures.</span></span> |
