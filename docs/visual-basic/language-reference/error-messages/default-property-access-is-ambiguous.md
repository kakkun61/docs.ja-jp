---
title: Default プロパティ アクセスは、インターフェイス '<defaultpropertyname>' の継承インターフェイス メンバー '<interfacename1>' とインターフェイス '<defaultpropertyname>' の '<interfacename2>' との間で不適切です。
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: b7c4c9c75de1b3777f34a70470b89f323a5699f9
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162064"
---
# <a name="bc30686-default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a><span data-ttu-id="edf44-102">BC30686:Default プロパティ アクセスは、インターフェイス '\<defaultpropertyname>' の継承インターフェイス メンバー '\<interfacename1>' とインターフェイス '\<defaultpropertyname>' の '\<interfacename2>' との間で不適切です。</span><span class="sxs-lookup"><span data-stu-id="edf44-102">BC30686: Default property access is ambiguous between the inherited interface members '\<defaultpropertyname>' of interface '\<interfacename1>' and '\<defaultpropertyname>' of interface '\<interfacename2>'</span></span>

<span data-ttu-id="edf44-103">インターフェイスは、それぞれが同じ名前の既定のプロパティを宣言する 2 つのインターフェイスから継承します。</span><span class="sxs-lookup"><span data-stu-id="edf44-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="edf44-104">コンパイラは、この既定のプロパティへのアクセスを修飾なしで解決することはできません。</span><span class="sxs-lookup"><span data-stu-id="edf44-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="edf44-105">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="edf44-105">The following example illustrates this.</span></span>

```vb
Public Interface Iface1
    Default Property prop(ByVal arg As Integer) As Integer
End Interface
Public Interface Iface2
    Default Property prop(ByVal arg As Integer) As Integer
End Interface
Public Interface Iface3
    Inherits Iface1, Iface2
End Interface
Public Class testClass
    Public Sub accessDefaultProperty()
        Dim testObj As Iface3
        Dim testInt As Integer = testObj(1)
    End Sub
End Class
```

<span data-ttu-id="edf44-106">`testObj(1)` を指定すると、コンパイラは、それを既定のプロパティに解決しようとします。</span><span class="sxs-lookup"><span data-stu-id="edf44-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="edf44-107">ただし、継承されたインターフェイスにより 2 つの既定のプロパティが考えられるため、コンパイラがこのエラーを通知します。</span><span class="sxs-lookup"><span data-stu-id="edf44-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>

<span data-ttu-id="edf44-108">**エラー ID:** BC30686</span><span class="sxs-lookup"><span data-stu-id="edf44-108">**Error ID:** BC30686</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="edf44-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="edf44-109">To correct this error</span></span>

- <span data-ttu-id="edf44-110">同じ名前のメンバーを継承しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="edf44-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="edf44-111">前の例では、`testObj` が、メンバーのいずれか (たとえば `Iface2`) を必要としない場合は、次のように宣言します。</span><span class="sxs-lookup"><span data-stu-id="edf44-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>

  ```vb
  Dim testObj As Iface1
  ```

  <span data-ttu-id="edf44-112">\- または -</span><span class="sxs-lookup"><span data-stu-id="edf44-112">\-or-</span></span>

- <span data-ttu-id="edf44-113">クラスに継承するインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="edf44-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="edf44-114">その後、異なる名前を持つ継承されたプロパティのそれぞれを実装できます。</span><span class="sxs-lookup"><span data-stu-id="edf44-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="edf44-115">ただし、実装するクラスの既定のプロパティにすることができるのは、そのうちの 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="edf44-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="edf44-116">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="edf44-116">The following example illustrates this.</span></span>

  ```vb
  Public Class useIface3
      Implements Iface3
      Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop
          ' Insert code to define Get and Set procedures for prop1.
      End Property
      Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop
          ' Insert code to define Get and Set procedures for prop2.
      End Property
  End Class
  ```

## <a name="see-also"></a><span data-ttu-id="edf44-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="edf44-117">See also</span></span>

- [<span data-ttu-id="edf44-118">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="edf44-118">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
