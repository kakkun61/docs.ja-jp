---
title: DOM における名前空間のサポート
ms.date: 03/30/2017
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
ms.openlocfilehash: b3214d77b069b672e8772ec78db51c9d8ee1bf50
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714407"
---
# <a name="namespace-support-in-the-dom"></a><span data-ttu-id="baf20-102">DOM における名前空間のサポート</span><span class="sxs-lookup"><span data-stu-id="baf20-102">Namespace Support in the DOM</span></span>

<span data-ttu-id="baf20-103">XML ドキュメント オブジェクト モデル (DOM) は名前空間に完全に対応しています。</span><span class="sxs-lookup"><span data-stu-id="baf20-103">The XML Document Object Model (DOM) is completely namespace-aware.</span></span> <span data-ttu-id="baf20-104">名前空間に対応している XML ドキュメントだけがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="baf20-104">Only namespace-aware XML documents are supported.</span></span> <span data-ttu-id="baf20-105">W3C (World Wide Web Consortium) の仕様によれば、DOM Level 1 を実装する DOM アプリケーションは名前空間に対応していなくてもかまいませんが、DOM Level 2 の機能は名前空間に対応しています。</span><span class="sxs-lookup"><span data-stu-id="baf20-105">The World Wide Web Consortium (W3C) specifies that DOM applications that implement Level 1 can be non-namespace-aware, and DOM Level 2 features are namespace-aware.</span></span> <span data-ttu-id="baf20-106">ただし、メソッドが DOM 勧告の Level 1 または Level 2 のどちらに準拠しているかに関係なく、XML DOM のすべての機能は名前空間に対応しています。</span><span class="sxs-lookup"><span data-stu-id="baf20-106">However, all features in the XML DOM are namespace-aware, regardless if the method is from the Level 1 or Level 2 DOM Recommendation.</span></span>  
  
 <span data-ttu-id="baf20-107">たとえば、名前空間に対応していない環境では、DOM Level 1 勧告の規定に従って `setAttribute("A:b", "123")` を呼び出しても、プレフィックス `A` とローカル名 `b` を持つ属性は設定されません。</span><span class="sxs-lookup"><span data-stu-id="baf20-107">For example, in a non-namespace-aware setting, calling `setAttribute("A:b", "123")`, as specified in the DOM Level 1 Recommendation, does not result in an attribute with a prefix of `A` and a local name of `b`.</span></span> <span data-ttu-id="baf20-108">この結果は、`A:b` という値の属性になります。</span><span class="sxs-lookup"><span data-stu-id="baf20-108">It would result in an attribute with the value `A:b`.</span></span>  
  
 <span data-ttu-id="baf20-109">名前空間に対応している環境では、DOM Level 2 の `setAttribute("A:b", "123")` を呼び出すと、属性のプレフィックスが `A` になり、ローカル名が `b` になります。</span><span class="sxs-lookup"><span data-stu-id="baf20-109">In a namespace-aware environment, the call to the DOM Level 2 `setAttribute("A:b", "123")` results in an attribute with a prefix of `A` and a local name of `b`.</span></span> <span data-ttu-id="baf20-110">これが Microsoft .NET Framework DOM の動作です。</span><span class="sxs-lookup"><span data-stu-id="baf20-110">This is how the Microsoft .NET Framework DOM works.</span></span>  
  
 <span data-ttu-id="baf20-111">したがって、名前パラメーターを受け取るすべてのメソッドは、名前を修飾するプレフィックスも受け取ります。</span><span class="sxs-lookup"><span data-stu-id="baf20-111">Therefore, for all methods that take a name parameter, these methods also take a prefix to qualify the name.</span></span> <span data-ttu-id="baf20-112">DOM Level 1 の **setAttribute** メソッドの `A:b` のような名前パラメーターは、次のように解析されます。</span><span class="sxs-lookup"><span data-stu-id="baf20-112">The name parameter, such as the `A:b` in the **setAttribute** DOM Level 1 method, is parsed as follows:</span></span>  
  
- <span data-ttu-id="baf20-113">コロン (:) が含まれない場合は、ローカル名が `name` パラメーターに設定され、プレフィックスと名前空間 URI は空の文字列になります。</span><span class="sxs-lookup"><span data-stu-id="baf20-113">If there are no colon (:) characters, then the local name is set to the `name` parameter, and the prefix and NamespaceURI are empty strings.</span></span>  
  
- <span data-ttu-id="baf20-114">コロンが見つかると、最初のコロンの位置に基づいて名前が 2 つの部分に分割されます。</span><span class="sxs-lookup"><span data-stu-id="baf20-114">If a colon is found, then the name is split into two parts based on the position of the first colon character.</span></span> <span data-ttu-id="baf20-115">プレフィックスはコロンより前の文字列に設定され、ローカル名はコロンより後の文字列に設定されます。</span><span class="sxs-lookup"><span data-stu-id="baf20-115">The prefix is set to the string found before the colon, and local name is set to the string found after the colon.</span></span> <span data-ttu-id="baf20-116">名前空間 URI の値をとらないメソッドでは、名前空間 URI は解決されず、空の文字列のままになります。</span><span class="sxs-lookup"><span data-stu-id="baf20-116">For methods that do not take a NamespaceURI value, the NamespaceURI is not resolved and remains set to empty string.</span></span> <span data-ttu-id="baf20-117">それ以外の場合は、メソッドに渡された文字列が名前空間 URI として設定されます。</span><span class="sxs-lookup"><span data-stu-id="baf20-117">Otherwise, the NamespaceURI is set to the string passed to the method.</span></span> <span data-ttu-id="baf20-118">プレフィックスが定義されていない場合、**Save** メソッド、**InnerXml** プロパティ、**OuterXml** プロパティは失敗します。</span><span class="sxs-lookup"><span data-stu-id="baf20-118">If the prefix is undefined, then the **Save** method and **InnerXml** and **OuterXml** properties fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf20-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="baf20-119">See also</span></span>

- [<span data-ttu-id="baf20-120">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="baf20-120">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
