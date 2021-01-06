---
title: 列挙型対応の新しいメソッドを作成する方法 - C# プログラミング ガイド
description: 拡張メソッドを使用して C# で列挙型に機能を追加する方法について説明します。 この例では、成績と呼ばれる列挙型に対して合格という拡張メソッドを示しています。
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 88afff854b8136bde837db8effb0e0eb512e1099
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513095"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="47b6e-104">列挙型対応の新しいメソッドを作成する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="47b6e-104">How to create a new method for an enumeration (C# Programming Guide)</span></span>

<span data-ttu-id="47b6e-105">拡張メソッドを使用して、特定の列挙型に固有の機能を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="47b6e-105">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47b6e-106">例</span><span class="sxs-lookup"><span data-stu-id="47b6e-106">Example</span></span>  

 <span data-ttu-id="47b6e-107">次の例では、`Grades` 列挙型は学生が授業で受け取る成績評価を表わしています。</span><span class="sxs-lookup"><span data-stu-id="47b6e-107">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="47b6e-108">`Passing` という名前の拡張機能メソッドが `Grades` 型に追加されていて、この型の各インスタンスが合格点を表しているかどうかを自ら "認識" できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="47b6e-108">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="47b6e-109">`Extensions` クラスには動的に更新される静的変数も含まれていて、拡張メソッドの戻り値はその変数の現在の値を反映していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="47b6e-109">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="47b6e-110">背後では、拡張メソッドが自分が定義されている静的クラスに直接呼び出されることを、この例は示しています。</span><span class="sxs-lookup"><span data-stu-id="47b6e-110">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b6e-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="47b6e-111">See also</span></span>

- [<span data-ttu-id="47b6e-112">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="47b6e-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="47b6e-113">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="47b6e-113">Extension Methods</span></span>](./extension-methods.md)
