---
title: 識別子が長すぎます。
ms.date: 07/20/2015
f1_keywords:
- bc30033
- vbc30033
helpviewer_keywords:
- BC30033
ms.assetid: 3d07f6d0-9a2f-49ca-94e8-1e354932e855
ms.openlocfilehash: eafcb2fdf706e12fa606a442ad577c88ed5a7427
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162857"
---
# <a name="bc30033-identifier-is-too-long"></a><span data-ttu-id="deade-102">BC30033:識別子が長すぎます。</span><span class="sxs-lookup"><span data-stu-id="deade-102">BC30033: Identifier is too long</span></span>

<span data-ttu-id="deade-103">すべてのプログラミング要素の名前または識別子は、1023 文字に制限されています。</span><span class="sxs-lookup"><span data-stu-id="deade-103">The name, or identifier, of every programming element is limited to 1023 characters.</span></span> <span data-ttu-id="deade-104">さらに、完全修飾名は 1023 文字を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="deade-104">In addition, a fully qualified name cannot exceed 1023 characters.</span></span> <span data-ttu-id="deade-105">つまり、識別子の文字列全体 (`<namespace>.<...>.<namespace>.<class>.<element>`) で、メンバーアクセス演算子 (`.`) 文字を含めて、1023 文字の長さを超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="deade-105">This means that the entire identifier string (`<namespace>.<...>.<namespace>.<class>.<element>`) cannot be more than 1023 characters long, including the member-access operator (`.`) characters.</span></span>

 <span data-ttu-id="deade-106">**エラー ID:** BC30033</span><span class="sxs-lookup"><span data-stu-id="deade-106">**Error ID:** BC30033</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="deade-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="deade-107">To correct this error</span></span>

- <span data-ttu-id="deade-108">識別子の長さを短くします。</span><span class="sxs-lookup"><span data-stu-id="deade-108">Reduce the length of the identifier.</span></span>

## <a name="see-also"></a><span data-ttu-id="deade-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="deade-109">See also</span></span>

- [<span data-ttu-id="deade-110">宣言された要素の名前</span><span class="sxs-lookup"><span data-stu-id="deade-110">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
