---
title: アクセスするインスタンスがインターフェイス型であるため、遅延バインドされたオーバーロードの解決は '<procedurename>' に適用されません。
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: 090ec6f3bbf56350fda2ab15c974b0bc6b15e3d3
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162519"
---
# <a name="bc30933-latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="c8107-102">BC30933:アクセスするインスタンスがインターフェイス型であるため、遅延バインドされたオーバーロードの解決は '\<procedurename>' に適用されません。</span><span class="sxs-lookup"><span data-stu-id="c8107-102">BC30933: Latebound overload resolution cannot be applied to '\<procedurename>' because the accessing instance is an interface type</span></span>

<span data-ttu-id="c8107-103">コンパイラでは、オーバーロードされたプロパティまたはプロシージャへの参照を解決しようとしますが、引数の型が `Object` であり、参照元のオブジェクトがインターフェイスのデータ型を持つため、参照が失敗します。</span><span class="sxs-lookup"><span data-stu-id="c8107-103">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="c8107-104">`Object` 引数は、コンパイラに参照を遅延バインドとして強制的に解決させます。</span><span class="sxs-lookup"><span data-stu-id="c8107-104">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>

<span data-ttu-id="c8107-105">このような状況では、コンパイラは、基になるインターフェイスを使用するのではなく、実装するクラスを使用してオーバーロードを解決します。</span><span class="sxs-lookup"><span data-stu-id="c8107-105">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="c8107-106">クラスで、オーバーロードされたいずれかのバージョンの名前が変更された場合、コンパイラは、そのバージョンの名前が異なるため、それをオーバーロードされているものと見なしません。</span><span class="sxs-lookup"><span data-stu-id="c8107-106">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="c8107-107">これにより、名前が変更されたバージョンが参照を解決するための正しい選択である可能性がある場合に、コンパイラがそれを無視します。</span><span class="sxs-lookup"><span data-stu-id="c8107-107">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>

<span data-ttu-id="c8107-108">**エラー ID:** BC30933</span><span class="sxs-lookup"><span data-stu-id="c8107-108">**Error ID:** BC30933</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c8107-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c8107-109">To correct this error</span></span>

- <span data-ttu-id="c8107-110">`CType` を使用して、`Object` からの引数を、呼び出すオーバーロードのシグネチャで指定された型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="c8107-110">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>

  <span data-ttu-id="c8107-111">参照元のオブジェクトを、基になるインターフェイスにキャストすることは役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="c8107-111">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="c8107-112">このエラーを回避するには、引数をキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8107-112">You must cast the argument to avoid this error.</span></span>

## <a name="example"></a><span data-ttu-id="c8107-113">例</span><span class="sxs-lookup"><span data-stu-id="c8107-113">Example</span></span>

<span data-ttu-id="c8107-114">次の例では、コンパイル時にこのエラーを発生させるオーバーロードされた `Sub` プロシージャの呼び出しを示しています。</span><span class="sxs-lookup"><span data-stu-id="c8107-114">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>

```vb
Module m1
    Interface i1
        Sub s1(ByVal p1 As Integer)
        Sub s1(ByVal p1 As Double)
    End Interface
    Class c1
        Implements i1
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1
        End Sub
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1
        End Sub
    End Class
    Sub Main()
        Dim refer As i1 = New c1
        Dim o1 As Object = 3.1415
        ' The following reference is INVALID and causes a compiler error.
        refer.s1(o1)
    End Sub
End Module
```

<span data-ttu-id="c8107-115">前の例で、コンパイラが記述どおりに `s1` の呼び出しを許可した場合、インターフェイス `i1` ではなく `c1` クラスを使用して解決が行われます。</span><span class="sxs-lookup"><span data-stu-id="c8107-115">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="c8107-116">これは、`i1` によって定義されているとおりに、正しい選択であっても、`c1` でその名前が異なるため、コンパイラが `s2` を考慮しないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="c8107-116">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>

<span data-ttu-id="c8107-117">このエラーを修正するには、呼び出しを次のいずれかのコード行に変更します。</span><span class="sxs-lookup"><span data-stu-id="c8107-117">You can correct the error by changing the call to either of the following lines of code:</span></span>

```vb
refer.s1(CType(o1, Integer))
refer.s1(CType(o1, Double))
```

<span data-ttu-id="c8107-118">前の各コード行では、`Object` 変数 `o1` をオーバーロードに定義されているいずれかのパラメーター型に明示的にキャストしています。</span><span class="sxs-lookup"><span data-stu-id="c8107-118">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8107-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8107-119">See also</span></span>

- [<span data-ttu-id="c8107-120">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="c8107-120">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="c8107-121">オーバーロードの解決</span><span class="sxs-lookup"><span data-stu-id="c8107-121">Overload Resolution</span></span>](../../programming-guide/language-features/procedures/overload-resolution.md)
- [<span data-ttu-id="c8107-122">CType 関数</span><span class="sxs-lookup"><span data-stu-id="c8107-122">CType Function</span></span>](../functions/ctype-function.md)
