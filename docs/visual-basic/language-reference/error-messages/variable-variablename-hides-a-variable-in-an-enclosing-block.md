---
title: 変数 '<variablename>' は、囲まれたブロック内の変数を非表示にします。
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 408acaafd5e266266b5191313611b94b72a5c270
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161349"
---
# <a name="bc30616-variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="1cc23-102">BC30616:変数 '\<variablename>' は、囲まれたブロック内の変数を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="1cc23-102">BC30616: Variable '\<variablename>' hides a variable in an enclosing block</span></span>

<span data-ttu-id="1cc23-103">ブロックで囲まれた変数の名前が、別のローカル変数と同じ名前です。</span><span class="sxs-lookup"><span data-stu-id="1cc23-103">A variable enclosed in a block has the same name as another local variable.</span></span>

 <span data-ttu-id="1cc23-104">**エラー ID:** BC30616</span><span class="sxs-lookup"><span data-stu-id="1cc23-104">**Error ID:** BC30616</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1cc23-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="1cc23-105">To correct this error</span></span>

- <span data-ttu-id="1cc23-106">囲まれたブロック内の変数の名前を、他のローカル変数と同じにならないように変更します。</span><span class="sxs-lookup"><span data-stu-id="1cc23-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="1cc23-107">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1cc23-107">For example:</span></span>

    ```vb
    Dim a, b, x As Integer
    If a = b Then
       Dim y As Integer = 20 ' Uniquely named block variable.
    End If
    ```

- <span data-ttu-id="1cc23-108">このエラーの一般的な原因は、イベント ハンドラー内で `Catch e As Exception` を使用することです。</span><span class="sxs-lookup"><span data-stu-id="1cc23-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="1cc23-109">この場合は、`e` ではなく、`Catch` ブロック変数に `ex` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="1cc23-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>

- <span data-ttu-id="1cc23-110">このエラーのもう 1 つの一般的な原因は、別の `Catch` ブロック内の `Try` ブロック内で宣言されたローカル変数へのアクセスを試みることです。</span><span class="sxs-lookup"><span data-stu-id="1cc23-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="1cc23-111">これを修正するには、`Try...Catch...Finally` 構造体の外側で変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="1cc23-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="1cc23-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1cc23-112">See also</span></span>

- [<span data-ttu-id="1cc23-113">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="1cc23-113">Try...Catch...Finally Statement</span></span>](../statements/try-catch-finally-statement.md)
- [<span data-ttu-id="1cc23-114">変数宣言</span><span class="sxs-lookup"><span data-stu-id="1cc23-114">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
