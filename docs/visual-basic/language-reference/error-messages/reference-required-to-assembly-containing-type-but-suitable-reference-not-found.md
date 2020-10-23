---
title: 参照には型 '<assemblyidentity>' を含むアセンブリ '<typename>' が必要ですが、プロジェクト '<projectname1>' と '<projectname2>' があいまいであるため、適切な参照が見つかりませんでした。
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: ca574bfe926b7b9df272e296190b36f8635263db
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162311"
---
# <a name="bc30969-reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a><span data-ttu-id="eac8b-102">BC30969:参照には型 '\<assemblyidentity>' を含むアセンブリ '\<typename>' が必要ですが、プロジェクト '\<projectname1>' と '\<projectname2>' があいまいであるため、適切な参照が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="eac8b-102">BC30969: Reference required to assembly '\<assemblyidentity>' containing type '\<typename>', but a suitable reference could not be found due to ambiguity between projects '\<projectname1>' and '\<projectname2>'</span></span>

<span data-ttu-id="eac8b-103">プロジェクト外で定義されているクラス、構造体、インターフェイス、列挙型、デリゲートなどの型が式で使用されています。</span><span class="sxs-lookup"><span data-stu-id="eac8b-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="eac8b-104">しかし、その型を定義する複数のアセンブリへのプロジェクト参照があります。</span><span class="sxs-lookup"><span data-stu-id="eac8b-104">However, you have project references to more than one assembly defining that type.</span></span>

 <span data-ttu-id="eac8b-105">問題のプロジェクトは、同じ名前のアセンブリを複数作成します。</span><span class="sxs-lookup"><span data-stu-id="eac8b-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="eac8b-106">このため、コンパイラは、アクセスしている型にどちらのアセンブリを使用すればよいかを判断できません。</span><span class="sxs-lookup"><span data-stu-id="eac8b-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>

 <span data-ttu-id="eac8b-107">別のアセンブリで定義されている型にアクセスするには、そのアセンブリへの参照を Visual Basic コンパイラが保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eac8b-107">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="eac8b-108">これは、プロジェクト間の循環参照にならない、単一であいまいさのない参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="eac8b-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>

 <span data-ttu-id="eac8b-109">**エラー ID:** BC30969</span><span class="sxs-lookup"><span data-stu-id="eac8b-109">**Error ID:** BC30969</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="eac8b-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="eac8b-110">To correct this error</span></span>

1. <span data-ttu-id="eac8b-111">どのプロジェクトが、プロジェクトからの参照に最適なアセンブリを作成しているか特定します。</span><span class="sxs-lookup"><span data-stu-id="eac8b-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="eac8b-112">この判断には、ファイル アクセスの容易さや更新の頻度などの基準を使用できます。</span><span class="sxs-lookup"><span data-stu-id="eac8b-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>

2. <span data-ttu-id="eac8b-113">プロジェクトのプロパティに、使用する型が定義されているアセンブリを含むファイルへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="eac8b-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>

## <a name="see-also"></a><span data-ttu-id="eac8b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="eac8b-114">See also</span></span>

- [<span data-ttu-id="eac8b-115">プロジェクト内の参照の管理</span><span class="sxs-lookup"><span data-stu-id="eac8b-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="eac8b-116">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="eac8b-116">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="eac8b-117">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="eac8b-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="eac8b-118">壊れた参照のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="eac8b-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
