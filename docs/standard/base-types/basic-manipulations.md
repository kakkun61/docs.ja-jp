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
ms.openlocfilehash: 659f01cc1d7ae03e12e83329e4fd2446b7512475
ms.sourcegitcommit: ffd4d5e824db6c5f0c3521c0e802fd9e8f0edcbe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93342619"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="cb42e-103">方法: .NET の基本的な文字列操作を実行する</span><span class="sxs-lookup"><span data-stu-id="cb42e-103">How to: Perform Basic String Manipulations in .NET</span></span>

<span data-ttu-id="cb42e-104">次の例では、「[基本的な文字列操作](basic-string-operations.md)」のトピックで説明したいくつかの方法を使用して、実際のアプリケーションで見られる方法で文字列の操作を実行するクラスを構築します。</span><span class="sxs-lookup"><span data-stu-id="cb42e-104">The following example uses some of the methods discussed in the [Basic String Operations](basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="cb42e-105">`MailToData` クラスは、個人の名前とアドレスを個別のプロパティに格納し、`City`、`State`、`Zip` フィールドを組み合わせて、ユーザーに表示する1 つの文字列にする方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="cb42e-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="cb42e-106">さらに、そのクラスを使用すると、ユーザーは市区町村、都道府県、郵便番号の情報を 1 つの文字列として入力できます。</span><span class="sxs-lookup"><span data-stu-id="cb42e-106">Furthermore, the class allows the user to enter the city, state, and zip code information as a single string.</span></span> <span data-ttu-id="cb42e-107">アプリケーションにより、1 つの文字列が自動的に解析され、対応するプロパティに適切な情報が入力されます。</span><span class="sxs-lookup"><span data-stu-id="cb42e-107">The application automatically parses the single string and enters the proper information into the corresponding property.</span></span>

<span data-ttu-id="cb42e-108">わかりやすいように、この例ではコマンド ライン インターフェイスによるコンソール アプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="cb42e-108">For simplicity, this example uses a console application with a command-line interface.</span></span>

## <a name="example"></a><span data-ttu-id="cb42e-109">例</span><span class="sxs-lookup"><span data-stu-id="cb42e-109">Example</span></span>

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]

<span data-ttu-id="cb42e-110">上記のコードを実行すると、ユーザーは自分の名前とアドレスを入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="cb42e-110">When the preceding code is executed, the user is asked to enter their name and address.</span></span> <span data-ttu-id="cb42e-111">アプリケーションにより、適切なプロパティに情報が格納され、市区町村、都道府県、郵便番号の情報を表示する 1 つの文字列が作成されて、ユーザーに情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb42e-111">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and zip code information.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb42e-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb42e-112">See also</span></span>

- [<span data-ttu-id="cb42e-113">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="cb42e-113">Basic String Operations</span></span>](basic-string-operations.md)
