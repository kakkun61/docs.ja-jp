---
title: 既定プロパティ '<propertyname1>' は、'<propertyname2>' の既定プロパティ '<classname>' と競合しているため、'Shadows' と宣言できません。
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 290971a3173c59f08fbd279b6fffe3bcb618cb72
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160608"
---
# <a name="bc40007-default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="884f9-102">BC40007:既定プロパティ '\<propertyname1>' は、'\<propertyname2>' の既定プロパティ '\<classname>' と競合しているため、'Shadows' と宣言できません。</span><span class="sxs-lookup"><span data-stu-id="884f9-102">BC40007: Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>

<span data-ttu-id="884f9-103">プロパティが、基底クラスで定義されたプロパティと同じ名前で宣言されています。</span><span class="sxs-lookup"><span data-stu-id="884f9-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="884f9-104">この場合、このクラスのプロパティは、基底クラス プロパティをシャドウする必要があります。</span><span class="sxs-lookup"><span data-stu-id="884f9-104">In this situation, the property in this class should shadow the base class property.</span></span>

 <span data-ttu-id="884f9-105">このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="884f9-105">This message is a warning.</span></span> <span data-ttu-id="884f9-106">`Shadows` は、既定で指定されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="884f9-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="884f9-107">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="884f9-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="884f9-108">**エラー ID:** BC40007</span><span class="sxs-lookup"><span data-stu-id="884f9-108">**Error ID:** BC40007</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="884f9-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="884f9-109">To correct this error</span></span>

- <span data-ttu-id="884f9-110">`Shadows` キーワードを宣言に追加するか、宣言されるプロパティの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="884f9-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>

## <a name="see-also"></a><span data-ttu-id="884f9-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="884f9-111">See also</span></span>

- [<span data-ttu-id="884f9-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="884f9-112">Shadows</span></span>](../modifiers/shadows.md)
- [<span data-ttu-id="884f9-113">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="884f9-113">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
