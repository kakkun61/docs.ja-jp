---
title: 変数 '<variablename>' は、値が割り当てられる前に参照によって使用されています。
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 6db8626701267f2051b289b267e7b2d9da51c283
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162220"
---
# <a name="bc42104-variable-variablename-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="c75b6-102">BC42104:変数 '\<variablename>' は、値が割り当てられる前に参照によって使用されています。</span><span class="sxs-lookup"><span data-stu-id="c75b6-102">BC42104: Variable '\<variablename>' is used before it has been assigned a value</span></span>

<span data-ttu-id="c75b6-103">変数 '\<variablename>' は、値が割り当てられる前に使用されています。</span><span class="sxs-lookup"><span data-stu-id="c75b6-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="c75b6-104">結果として、実行時に null 参照の例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c75b6-104">A null reference exception could result at run time.</span></span>

 <span data-ttu-id="c75b6-105">アプリケーションには、値が割り当てられる前に変数を読み取るコードを通る可能性があるパスが少なくとも 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="c75b6-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>

 <span data-ttu-id="c75b6-106">変数に値が割り当てられていない場合、変数はそのデータ型の既定値を保持します。</span><span class="sxs-lookup"><span data-stu-id="c75b6-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="c75b6-107">参照データ型の場合、その既定値は [Nothing](../nothing.md)です。</span><span class="sxs-lookup"><span data-stu-id="c75b6-107">For a reference data type, that default value is [Nothing](../nothing.md).</span></span> <span data-ttu-id="c75b6-108">値が `Nothing` である参照変数を読み取ると、状況によって <xref:System.NullReferenceException> が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c75b6-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>

 <span data-ttu-id="c75b6-109">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="c75b6-109">By default, this message is a warning.</span></span> <span data-ttu-id="c75b6-110">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c75b6-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="c75b6-111">**エラー ID:** BC42104</span><span class="sxs-lookup"><span data-stu-id="c75b6-111">**Error ID:** BC42104</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c75b6-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c75b6-112">To correct this error</span></span>

- <span data-ttu-id="c75b6-113">制御フロー ロジックをチェックして、変数を読み取るステートメントに制御が渡される前に、変数に有効な値が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c75b6-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>

- <span data-ttu-id="c75b6-114">変数が常に有効な値を持つようにする 1 つの方法は、その宣言の一部として変数を初期化することです。</span><span class="sxs-lookup"><span data-stu-id="c75b6-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="c75b6-115">[Dim ステートメント](../statements/dim-statement.md)の "初期化" に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c75b6-115">See "Initialization" in [Dim Statement](../statements/dim-statement.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c75b6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="c75b6-116">See also</span></span>

- [<span data-ttu-id="c75b6-117">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="c75b6-117">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="c75b6-118">変数宣言</span><span class="sxs-lookup"><span data-stu-id="c75b6-118">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="c75b6-119">変数のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c75b6-119">Troubleshooting Variables</span></span>](../../programming-guide/language-features/variables/troubleshooting-variables.md)
