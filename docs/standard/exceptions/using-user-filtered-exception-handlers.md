---
title: ユーザー フィルター例外ハンドラーの使用
ms.date: 03/30/2017
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
ms.openlocfilehash: 4b85c2be0ed61af38eac1b65fb70f0ef1ea4405e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669043"
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="0c9ae-102">ユーザー フィルター例外ハンドラーの使用</span><span class="sxs-lookup"><span data-stu-id="0c9ae-102">Using User-Filtered Exception Handlers</span></span>

<span data-ttu-id="0c9ae-103">現在 Visual Basic では、ユーザー フィルター例外をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0c9ae-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="0c9ae-104">ユーザー フィルター例外ハンドラーは、ユーザーが例外に対して定義した要件に基づいて、例外をキャッチして処理します。</span><span class="sxs-lookup"><span data-stu-id="0c9ae-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="0c9ae-105">これらのハンドラーでは、**Catch** ステートメントを **When** キーワードと一緒に使用します。</span><span class="sxs-lookup"><span data-stu-id="0c9ae-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="0c9ae-106">この手法は、特定の例外オブジェクトが複数のエラーに対応する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="0c9ae-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="0c9ae-107">その場合、オブジェクトには通常、エラーに関連付けられた特定のエラー コードが格納されているプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="0c9ae-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="0c9ae-108">エラー コード プロパティを式で使用すると、その **Catch** 句で処理する特定のエラーだけを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="0c9ae-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="0c9ae-109">**Catch/When** ステートメントを使用した Visual Basic コードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0c9ae-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 <span data-ttu-id="0c9ae-110">ユーザー フィルター句の式が制限されることはありません。</span><span class="sxs-lookup"><span data-stu-id="0c9ae-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="0c9ae-111">ユーザー フィルター式の実行中に例外が発生した場合、その例外は破棄され、フィルター式は false と評価されたものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="0c9ae-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="0c9ae-112">その場合、共通言語ランタイムは、現在の例外に対応するハンドラーの検索を継続します。</span><span class="sxs-lookup"><span data-stu-id="0c9ae-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="0c9ae-113">特定の例外とユーザー フィルター句の組み合わせ</span><span class="sxs-lookup"><span data-stu-id="0c9ae-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  

 <span data-ttu-id="0c9ae-114">catch ステートメントには、特定の例外とユーザー フィルター句の両方を記述できます。</span><span class="sxs-lookup"><span data-stu-id="0c9ae-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="0c9ae-115">ランタイムは、最初に特定の例外をテストします。</span><span class="sxs-lookup"><span data-stu-id="0c9ae-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="0c9ae-116">特定の例外がテストを通過すると、ランタイムはユーザー フィルターを実行します。</span><span class="sxs-lookup"><span data-stu-id="0c9ae-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="0c9ae-117">汎用フィルターには、クラス フィルターで宣言されている変数への参照を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="0c9ae-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="0c9ae-118">なお、2 つのフィルター句の順序をが逆にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="0c9ae-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="0c9ae-119">次に示すのは、`ClassLoadException` という例外が指定された **Catch** ステートメントと、**When** キーワードを使用したユーザー フィルター句がある Visual Basic コードの例です。</span><span class="sxs-lookup"><span data-stu-id="0c9ae-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="0c9ae-120">参照</span><span class="sxs-lookup"><span data-stu-id="0c9ae-120">See also</span></span>

- [<span data-ttu-id="0c9ae-121">例外</span><span class="sxs-lookup"><span data-stu-id="0c9ae-121">Exceptions</span></span>](index.md)
