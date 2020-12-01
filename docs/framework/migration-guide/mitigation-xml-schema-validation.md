---
title: '軽減策: XML スキーマ検証'
description: .NET Framework 4.6 では、複合キーが使用され、1 つのキーが空の場合、XSD スキーマ検証によって一意制約の違反が検出されます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 0744a703c1e9dc35a8accc448d34f1a736e77e4d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253532"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="be590-103">軽減策:XML スキーマ検証</span><span class="sxs-lookup"><span data-stu-id="be590-103">Mitigation: XML Schema Validation</span></span>

<span data-ttu-id="be590-104">.NET Framework 4.6 では、複合キーが使用され、1 つのキーが空の場合、XSD スキーマ検証で一意制約の違反が検出されます。</span><span class="sxs-lookup"><span data-stu-id="be590-104">In the .NET Framework 4.6, XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="be590-105">影響</span><span class="sxs-lookup"><span data-stu-id="be590-105">Impact</span></span>  

 <span data-ttu-id="be590-106">この変更の影響は最小限のものになります。スキーマの仕様に基づき、複合キーが空のキーと共に使用されて `xsd:unique` の違反が発生した場合、スキーマの検証エラーの発生が予期されます。</span><span class="sxs-lookup"><span data-stu-id="be590-106">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="be590-107">軽減策</span><span class="sxs-lookup"><span data-stu-id="be590-107">Mitigation</span></span>  

 <span data-ttu-id="be590-108">複合キーに空の 1 つのキーがある場合にスキーマ検証エラーが検出されるようにするかどうかは、構成可能な機能です。</span><span class="sxs-lookup"><span data-stu-id="be590-108">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="be590-109">.NET Framework 4.6 以降を対象とするアプリでは、スキーマ検証エラーの検出が既定で有効になっていますが、この動作を無効にして、スキーマ検証エラーが検出されないようにすることも可能です。</span><span class="sxs-lookup"><span data-stu-id="be590-109">Starting with the apps that target the .NET Framework 4.6, detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="be590-110">.NET Framework 4.6 の下で実行されているものの、.NET Framework 4.5.2 以前のバージョンを対象とするアプリでは、既定ではスキーマ検証エラーが検出されませんが、この動作を有効にして、スキーマ検証エラーが検出されるようにすることも可能です。</span><span class="sxs-lookup"><span data-stu-id="be590-110">In apps that run under the .NET Framework 4.6 but target the .NET Framework 4.5.2 and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="be590-111">この動作は、<xref:System.AppContext> クラスを使用して `System.Xml.IgnoreEmptyKeySequences` スイッチの値を定義することにより構成できます。</span><span class="sxs-lookup"><span data-stu-id="be590-111">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="be590-112">スイッチの既定値が `false` (空のキー シーケンスが無視されない) であるため、.NET Framework 4.6 を対象とするアプリは、以下のコードを使用してスイッチの値を `true` に設定することにより、その動作を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="be590-112">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the .NET Framework 4.6 can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="be590-113">.NET Framework 4.5.2 以前のバージョンを対象とするアプリでは、スイッチの既定値が `true` (空のキー シーケンスが無視される) であるため、以下のコードを使用してスイッチの値を `false` に設定することにより、複合キーに空のキーがある場合にスキーマ検証エラーを生成させることが可能です。</span><span class="sxs-lookup"><span data-stu-id="be590-113">For apps that target the .NET Framework 4.5.2 and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="be590-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="be590-114">See also</span></span>

- [<span data-ttu-id="be590-115">アプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="be590-115">Application compatibility</span></span>](application-compatibility.md)
