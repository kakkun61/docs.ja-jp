---
title: ローカライズ化の確認
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET], localization
- localizability [.NET]
- international applications [.NET], localizability
- globalization [.NET], localizability
- culture, localizability
- localization [.NET], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
ms.openlocfilehash: ecfba7b6b5908a16bb23860704a35035f58e3ed4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686021"
---
# <a name="localizability-review"></a><span data-ttu-id="7af7c-102">ローカライズ化の確認</span><span class="sxs-lookup"><span data-stu-id="7af7c-102">Localizability review</span></span>

<span data-ttu-id="7af7c-103">ローカライズ化の確認は、国際対応アプリケーション開発の中間段階です。</span><span class="sxs-lookup"><span data-stu-id="7af7c-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="7af7c-104">グローバル化されたアプリケーションがローカライズの準備ができていることを確認し、特別な処理が必要なコードやユーザー インターフェイスの側面を特定します。</span><span class="sxs-lookup"><span data-stu-id="7af7c-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="7af7c-105">この手順は、ローカライズ プロセスでアプリケーションに機能上の欠陥が持ち込まれないようにするためにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7af7c-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="7af7c-106">ローカライズ化の確認で生じた問題がすべて解決されたら、アプリケーションのローカライズの準備は完了です。</span><span class="sxs-lookup"><span data-stu-id="7af7c-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="7af7c-107">ローカライズ化の確認が徹底していれば、ローカライズ プロセス中にソース コードを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7af7c-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>

<span data-ttu-id="7af7c-108">ローカライズ化の確認は、次の 3 つの確認で構成されます。</span><span class="sxs-lookup"><span data-stu-id="7af7c-108">The localizability review consists of the following three checks:</span></span>

- [<span data-ttu-id="7af7c-109">グローバリゼーションの推奨事項は実装されているか</span><span class="sxs-lookup"><span data-stu-id="7af7c-109">Are the globalization recommendations implemented?</span></span>](#global)

- [<span data-ttu-id="7af7c-110">カルチャに依存した機能は正しく処理されているか</span><span class="sxs-lookup"><span data-stu-id="7af7c-110">Are culture-sensitive features handled correctly?</span></span>](#culture)

- [<span data-ttu-id="7af7c-111">各種言語データでアプリケーションはテストされているか</span><span class="sxs-lookup"><span data-stu-id="7af7c-111">Have you tested your application with international data?</span></span>](#test)

<a name="global"></a>

## <a name="implement-globalization-recommendations"></a><span data-ttu-id="7af7c-112">グローバリゼーションの推奨事項を実装する</span><span class="sxs-lookup"><span data-stu-id="7af7c-112">Implement globalization recommendations</span></span>

<span data-ttu-id="7af7c-113">ローカライズを考慮してアプリケーションの設計と開発を行い、[グローバリゼーション](globalization.md)に関する記事で説明されている推奨事項に従っている場合、ローカライズ化の確認は品質保証の点でほぼ合格です。</span><span class="sxs-lookup"><span data-stu-id="7af7c-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="7af7c-114">それ以外の場合は、この段階で[グローバリゼーション](globalization.md)の推奨事項を確認して実装し、ローカライズを妨げるソース コードのエラーを修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7af7c-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](globalization.md) and fix the errors in source code that prevent localization.</span></span>

<a name="culture"></a>

## <a name="handle-culture-sensitive-features"></a><span data-ttu-id="7af7c-115">カルチャに依存した機能を処理する</span><span class="sxs-lookup"><span data-stu-id="7af7c-115">Handle culture-sensitive features</span></span>

<span data-ttu-id="7af7c-116">.NET では、カルチャによって大きく異なるさまざまな領域のプログラムによるサポートは提供されていません。</span><span class="sxs-lookup"><span data-stu-id="7af7c-116">.NET does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="7af7c-117">ほとんどの場合、次のような機能領域を処理するカスタム コードを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7af7c-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>

- <span data-ttu-id="7af7c-118">アドレス</span><span class="sxs-lookup"><span data-stu-id="7af7c-118">Addresses</span></span>

- <span data-ttu-id="7af7c-119">電話番号</span><span class="sxs-lookup"><span data-stu-id="7af7c-119">Telephone numbers</span></span>

- <span data-ttu-id="7af7c-120">用紙サイズ</span><span class="sxs-lookup"><span data-stu-id="7af7c-120">Paper sizes</span></span>

- <span data-ttu-id="7af7c-121">長さ、重量、面積、体積、および温度に使用される測定単位</span><span class="sxs-lookup"><span data-stu-id="7af7c-121">Units of measure used for lengths, weights, area, volume, and temperatures</span></span>

   <span data-ttu-id="7af7c-122">.NET には測定単位の変換のサポートが組み込まれていませんが、次の例に示すように、<xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> プロパティを使用して特定の国または地域でメートル法が使用されているかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="7af7c-122">Although .NET does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>

## <a name="test-your-application"></a><span data-ttu-id="7af7c-123">アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="7af7c-123">Test your application</span></span>

<span data-ttu-id="7af7c-124">アプリケーションをローカライズする前に、各言語版のオペレーティング システム上で各種言語データを使用してアプリケーションをテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7af7c-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="7af7c-125">この時点では、ほとんどのユーザー インターフェイスはローカライズされていませんが、次のような問題を検出できます。</span><span class="sxs-lookup"><span data-stu-id="7af7c-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>

- <span data-ttu-id="7af7c-126">シリアル化されたデータが、オペレーティング システムのバージョン間で正しく逆シリアル化されない場合。</span><span class="sxs-lookup"><span data-stu-id="7af7c-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>

- <span data-ttu-id="7af7c-127">現在のカルチャの規則を反映していない数値データ。</span><span class="sxs-lookup"><span data-stu-id="7af7c-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="7af7c-128">たとえば、不適切なグループ区切り記号、小数点区切り記号、または通貨記号で数値が表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="7af7c-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>

- <span data-ttu-id="7af7c-129">現在のカルチャの規則を反映していない日時データ。</span><span class="sxs-lookup"><span data-stu-id="7af7c-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="7af7c-130">たとえば、月と日を表す数値が不適切な順序で表示される場合、日付の区切りが正しくない場合、タイム ゾーン情報が正しくない場合があります。</span><span class="sxs-lookup"><span data-stu-id="7af7c-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>

- <span data-ttu-id="7af7c-131">アプリケーションの既定のカルチャを指定していないために見つからないリソース。</span><span class="sxs-lookup"><span data-stu-id="7af7c-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>

- <span data-ttu-id="7af7c-132">特定のカルチャでは通常とは異なる順序で表示される文字列。</span><span class="sxs-lookup"><span data-stu-id="7af7c-132">Strings that are displayed in an unusual order for the specific culture.</span></span>

- <span data-ttu-id="7af7c-133">予期しない結果が返される文字列の比較または等価比較。</span><span class="sxs-lookup"><span data-stu-id="7af7c-133">String comparisons or comparisons for equality that return unexpected results.</span></span>

<span data-ttu-id="7af7c-134">アプリケーションの開発時にグローバリゼーションの推奨事項に従い、カルチャに依存した機能を正しく処理し、テスト中に発生したローカライズの問題を特定して対処した場合は、次の手順である[ローカライズ](localization.md)に進むことができます。</span><span class="sxs-lookup"><span data-stu-id="7af7c-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](localization.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7af7c-135">参照</span><span class="sxs-lookup"><span data-stu-id="7af7c-135">See also</span></span>

- [<span data-ttu-id="7af7c-136">グローバライズとローカライズ</span><span class="sxs-lookup"><span data-stu-id="7af7c-136">Globalization and Localization</span></span>](index.md)
- [<span data-ttu-id="7af7c-137">ローカリゼーション</span><span class="sxs-lookup"><span data-stu-id="7af7c-137">Localization</span></span>](localization.md)
- [<span data-ttu-id="7af7c-138">グローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="7af7c-138">Globalization</span></span>](globalization.md)
- [<span data-ttu-id="7af7c-139">デスクトップ アプリケーションのリソース</span><span class="sxs-lookup"><span data-stu-id="7af7c-139">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
