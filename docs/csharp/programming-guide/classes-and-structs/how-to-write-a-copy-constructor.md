---
title: コピー コンストラクターを記述する方法 - C# プログラミング ガイド
description: クラスのインスタンスを受け取り、入力の値を使用して新しいインスタンスを返すコピー コンストラクターを C# で記述する方法について説明します。
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 85899d2de05312be921199387cc1155fa8e9d2f1
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2020
ms.locfileid: "95098984"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="c0671-103">コピー コンストラクターを記述する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c0671-103">How to write a copy constructor (C# Programming Guide)</span></span>

<span data-ttu-id="c0671-104">C# では、オブジェクトのコピー コンストラクターが提供されていませんが、独自に作成することができます。</span><span class="sxs-lookup"><span data-stu-id="c0671-104">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0671-105">例</span><span class="sxs-lookup"><span data-stu-id="c0671-105">Example</span></span>  

 <span data-ttu-id="c0671-106">次の例の `Person`[クラス](../../language-reference/keywords/class.md)では、`Person` のインスタンスを引数として受け取るコピー コンストラクターが定義されています。</span><span class="sxs-lookup"><span data-stu-id="c0671-106">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="c0671-107">引数のプロパティの値は、`Person`の新しいインスタンスのプロパティに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="c0671-107">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="c0671-108">このコードには、コピーするインスタンスの `Name` プロパティと `Age` プロパティをクラスのインスタンス コンストラクターに渡す代替のコピー コンストラクターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c0671-108">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="c0671-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0671-109">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="c0671-110">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c0671-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c0671-111">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="c0671-111">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="c0671-112">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="c0671-112">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="c0671-113">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="c0671-113">Finalizers</span></span>](./destructors.md)
