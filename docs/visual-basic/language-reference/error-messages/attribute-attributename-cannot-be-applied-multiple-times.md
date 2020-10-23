---
title: 属性 '<attributename>' を複数回適用することはできません。
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 27cbe6d0043179c4a5d52baae06bad805f9d1d3a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162662"
---
# <a name="bc30663-attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="ae619-102">BC30663:属性 '\<attributename>' を複数回適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ae619-102">BC30663: Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="ae619-103">属性は、1 回のみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="ae619-103">The attribute can only be applied once.</span></span> <span data-ttu-id="ae619-104">`AttributeUsage` 属性は、属性を複数回適用できるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="ae619-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>

 <span data-ttu-id="ae619-105">**エラー ID:** BC30663</span><span class="sxs-lookup"><span data-stu-id="ae619-105">**Error ID:** BC30663</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ae619-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="ae619-106">To correct this error</span></span>

1. <span data-ttu-id="ae619-107">属性が 1 回だけ適用されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ae619-107">Make sure the attribute is only applied once.</span></span>

2. <span data-ttu-id="ae619-108">開発したカスタム属性を使用する場合は、次の例のように、複数の属性の使用を許可するように `AttributeUsage` 属性を変更することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ae619-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>

```vb
<AttributeUsage(AllowMultiple := True)>
```

## <a name="see-also"></a><span data-ttu-id="ae619-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae619-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="ae619-110">カスタム属性の作成</span><span class="sxs-lookup"><span data-stu-id="ae619-110">Creating Custom Attributes</span></span>](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="ae619-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="ae619-111">AttributeUsage</span></span>](../../programming-guide/concepts/attributes/attributeusage.md)
