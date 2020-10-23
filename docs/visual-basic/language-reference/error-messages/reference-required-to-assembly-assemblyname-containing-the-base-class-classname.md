---
title: 基本クラス '<assemblyname>' を含むアセンブリ '<classname>' への参照が必要です。参照をプロジェクトに追加してください。
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: d2fb3498219dfe3318ec418ede250de818874ba9
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162337"
---
# <a name="bc30007-reference-required-to-assembly-assemblyname-containing-the-base-class-classname"></a><span data-ttu-id="e3af9-102">BC30007:基本クラス '\<assemblyname>' を含むアセンブリ '\<classname>' への参照が必要です。参照をプロジェクトに追加してください。</span><span class="sxs-lookup"><span data-stu-id="e3af9-102">BC30007: Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'</span></span>

<span data-ttu-id="e3af9-103">基底クラス '\<classname>' を含むアセンブリ '\<assemblyname>' への参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="e3af9-103">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'.</span></span> <span data-ttu-id="e3af9-104">プロジェクトに参照を追加してください。</span><span class="sxs-lookup"><span data-stu-id="e3af9-104">Add one to your project.</span></span>

 <span data-ttu-id="e3af9-105">プロジェクト内で直接参照されないダイナミック リンク ライブラリ (DLL) またはアセンブリでクラスが定義されています。</span><span class="sxs-lookup"><span data-stu-id="e3af9-105">The class is defined in a dynamic-link library (DLL) or assembly that is not directly referenced in your project.</span></span> <span data-ttu-id="e3af9-106">Visual Basic コンパイラでは、クラスが複数の DLL またはアセンブリで定義されている場合に備えて、あいまいさを避けるための参照が必要になります。</span><span class="sxs-lookup"><span data-stu-id="e3af9-106">The Visual Basic compiler requires a reference to avoid ambiguity in case the class is defined in more than one DLL or assembly.</span></span>

 <span data-ttu-id="e3af9-107">**エラー ID:** BC30007</span><span class="sxs-lookup"><span data-stu-id="e3af9-107">**Error ID:** BC30007</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e3af9-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="e3af9-108">To correct this error</span></span>

- <span data-ttu-id="e3af9-109">参照されない DLL またはアセンブリの名前をプロジェクト参照に含めます。</span><span class="sxs-lookup"><span data-stu-id="e3af9-109">Include the name of the unreferenced DLL or assembly in your project references.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3af9-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3af9-110">See also</span></span>

- [<span data-ttu-id="e3af9-111">プロジェクト内の参照の管理</span><span class="sxs-lookup"><span data-stu-id="e3af9-111">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="e3af9-112">壊れた参照のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e3af9-112">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
