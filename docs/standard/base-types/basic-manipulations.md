---
title: .NET の基本的な文字列操作
description: 多くの文字列メソッドを呼び出す例を確認します。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: cc04f0c874b732668b4813f8325bd7060927f22a
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889128"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="85c28-103">方法: .NET の基本的な文字列操作を実行する</span><span class="sxs-lookup"><span data-stu-id="85c28-103">How to: Perform Basic String Manipulations in .NET</span></span>

<span data-ttu-id="85c28-104">次の例では、「[基本的な文字列操作](basic-string-operations.md)」のトピックで説明したいくつかの方法を使用して、実際のアプリケーションで見られる方法で文字列の操作を実行するクラスを構築します。</span><span class="sxs-lookup"><span data-stu-id="85c28-104">The following example uses some of the methods discussed in the [Basic String Operations](basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="85c28-105">`MailToData` クラスは、個人の名前とアドレスを個別のプロパティに格納し、`City`、`State`、`Zip` フィールドを組み合わせて、ユーザーに表示する1 つの文字列にする方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="85c28-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="85c28-106">さらに、このクラスを使用して、ユーザーが市区町村、都道府県、および郵便番号情報を 1 つの文字列として入力することができます。アプリケーションは自動的に 1 つの文字列を解析し、対応するプロパティに適切な情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="85c28-106">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
<span data-ttu-id="85c28-107">わかりやすいように、この例ではコマンド ライン インターフェイスによるコンソール アプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="85c28-107">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85c28-108">例</span><span class="sxs-lookup"><span data-stu-id="85c28-108">Example</span></span>  

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
<span data-ttu-id="85c28-109">上記のコードを実行すると、ユーザーは自分の名前とアドレスを入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="85c28-109">When the preceding code is executed, the user is asked to enter their name and address.</span></span> <span data-ttu-id="85c28-110">アプリケーションは、適切なプロパティに情報を格納し、市区町村、都道府県、および郵便番号情報を表示する 1 つの文字列を作成して、ユーザーに情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="85c28-110">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c28-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="85c28-111">See also</span></span>

- [<span data-ttu-id="85c28-112">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="85c28-112">Basic String Operations</span></span>](basic-string-operations.md)
