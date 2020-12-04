---
title: ドキュメントルール (コード分析)
description: コード分析ルールのドキュメントルールの詳細
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- warnings, documentation
author: mavasani
ms.author: mavasani
ms.openlocfilehash: 29d1734eec29bd00d456b4b00c48c2e8ef223441
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2020
ms.locfileid: "96591280"
---
# <a name="documentation-rules"></a><span data-ttu-id="13e18-103">ドキュメント規則</span><span class="sxs-lookup"><span data-stu-id="13e18-103">Documentation rules</span></span>

<span data-ttu-id="13e18-104">ドキュメントルールでは、外部から参照可能な Api に [XML ドキュメントコメント](../../../csharp/codedoc.md) を適切に使用することで、適切にドキュメント化されたライブラリの作成をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="13e18-104">Documentation rules support writing well-documented libraries through the correct use of [XML documentation comments](../../../csharp/codedoc.md) for externally visible APIs.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="13e18-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="13e18-105">In this section</span></span>

| <span data-ttu-id="13e18-106">ルール</span><span class="sxs-lookup"><span data-stu-id="13e18-106">Rule</span></span> | <span data-ttu-id="13e18-107">説明</span><span class="sxs-lookup"><span data-stu-id="13e18-107">Description</span></span> |
| - | - |
| [<span data-ttu-id="13e18-108">CA1200:プレフィックスで cref タグを使用しません</span><span class="sxs-lookup"><span data-stu-id="13e18-108">CA1200: Avoid using cref tags with a prefix</span></span>](ca1200.md) | <span data-ttu-id="13e18-109">XML ドキュメントタグの [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) 属性は、"コード参照" を意味します。</span><span class="sxs-lookup"><span data-stu-id="13e18-109">The [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) attribute in an XML documentation tag means "code reference".</span></span> <span data-ttu-id="13e18-110">タグの内部テキストが、型、メソッド、プロパティなど、コード要素であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="13e18-110">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="13e18-111">プレフィックスでタグを使用するのは避けて `cref` ください。これにより、コンパイラが参照を検証できなくなります。</span><span class="sxs-lookup"><span data-stu-id="13e18-111">Avoid using `cref` tags with prefixes, because it prevents the compiler from verifying references.</span></span> <span data-ttu-id="13e18-112">また、Visual Studio 統合開発環境 (IDE: integrated development environment) が、リファクタリング中にこれらのシンボル参照を検索および更新できないようにします。</span><span class="sxs-lookup"><span data-stu-id="13e18-112">It also prevents the Visual Studio integrated development environment (IDE) from finding and updating these symbol references during refactorings.</span></span> |
