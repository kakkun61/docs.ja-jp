---
title: コピー コンストラクターを記述する方法 - C# プログラミング ガイド
description: クラスのインスタンスを受け取り、入力の値を使用して新しいインスタンスを返すコピー コンストラクターを C# で記述する方法について説明します。
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: dfc702bfe183b3712b20c64f9e82d2d3c3edd6d5
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512373"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="ab51e-103">コピー コンストラクターを記述する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="ab51e-103">How to write a copy constructor (C# Programming Guide)</span></span>

<span data-ttu-id="ab51e-104">C# では、オブジェクトのコピー コンストラクターが提供されていませんが、独自に作成することができます。</span><span class="sxs-lookup"><span data-stu-id="ab51e-104">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab51e-105">例</span><span class="sxs-lookup"><span data-stu-id="ab51e-105">Example</span></span>  

 <span data-ttu-id="ab51e-106">次の例の `Person`[クラス](../../language-reference/keywords/class.md)では、`Person` のインスタンスを引数として受け取るコピー コンストラクターが定義されています。</span><span class="sxs-lookup"><span data-stu-id="ab51e-106">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="ab51e-107">引数のプロパティの値は、`Person`の新しいインスタンスのプロパティに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="ab51e-107">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="ab51e-108">このコードには、コピーするインスタンスの `Name` プロパティと `Age` プロパティをクラスのインスタンス コンストラクターに渡す代替のコピー コンストラクターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ab51e-108">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="ab51e-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab51e-109">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="ab51e-110">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="ab51e-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ab51e-111">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="ab51e-111">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="ab51e-112">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="ab51e-112">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="ab51e-113">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="ab51e-113">Finalizers</span></span>](./destructors.md)
