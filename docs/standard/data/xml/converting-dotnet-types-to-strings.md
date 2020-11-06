---
title: .NET 型から文字列への変換
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: ca35af17a402dc901c02edf94099af1377e1160f
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687628"
---
# <a name="convert-net-types-to-strings"></a><span data-ttu-id="9f416-102">.NET 型を文字列に変換する</span><span class="sxs-lookup"><span data-stu-id="9f416-102">Convert .NET types to strings</span></span>

<span data-ttu-id="9f416-103">.NET 型を文字列に変換する場合は、 **ToString** メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9f416-103">If you want to convert a .NET type to a string, use the **ToString** method.</span></span> <span data-ttu-id="9f416-104">**ToString** メソッドは、渡された型の文字列表現を返します。</span><span class="sxs-lookup"><span data-stu-id="9f416-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="9f416-105">XML スキーマ (XSD) 仕様に対応する形式で文字列を返す .NET 型を、次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="9f416-105">The following table lists the .NET types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="9f416-106">.NET の種類</span><span class="sxs-lookup"><span data-stu-id="9f416-106">.NET type</span></span>|<span data-ttu-id="9f416-107">返される文字列型</span><span class="sxs-lookup"><span data-stu-id="9f416-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="9f416-108">ブール型</span><span class="sxs-lookup"><span data-stu-id="9f416-108">Boolean</span></span>|<span data-ttu-id="9f416-109">"true"、"false"</span><span class="sxs-lookup"><span data-stu-id="9f416-109">"true", "false"</span></span>|  
|<span data-ttu-id="9f416-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="9f416-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="9f416-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="9f416-111">"INF"</span></span>|  
|<span data-ttu-id="9f416-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="9f416-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="9f416-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="9f416-113">"-INF"</span></span>|  
|<span data-ttu-id="9f416-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="9f416-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="9f416-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="9f416-115">"INF"</span></span>|  
|<span data-ttu-id="9f416-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="9f416-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="9f416-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="9f416-117">"-INF"</span></span>|  
|<span data-ttu-id="9f416-118">DateTime</span><span class="sxs-lookup"><span data-stu-id="9f416-118">DateTime</span></span>|<span data-ttu-id="9f416-119">形式は、yyyy-MM-ddTHH:mm:sszzzzzz およびそのサブセットです。</span><span class="sxs-lookup"><span data-stu-id="9f416-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="9f416-120">Timespan</span><span class="sxs-lookup"><span data-stu-id="9f416-120">Timespan</span></span>|<span data-ttu-id="9f416-121">PnYnMnTnHnMnS の形式。たとえば、`P2Y10M15DT10H30M20S` は 2 年 10 か月 15 日 10 時間 30 分 20 秒の期間です。</span><span class="sxs-lookup"><span data-stu-id="9f416-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f416-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f416-122">See also</span></span>

- [<span data-ttu-id="9f416-123">XML データ型の変換</span><span class="sxs-lookup"><span data-stu-id="9f416-123">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="9f416-124">文字列から .NET データ型への変換</span><span class="sxs-lookup"><span data-stu-id="9f416-124">Converting Strings to .NET Data Types</span></span>](converting-strings-to-dotnet-data-types.md)
