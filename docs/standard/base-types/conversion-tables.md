---
title: .NET の型変換の表
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- widening conversions
- narrowing conversions
- type conversion, table
- converting types, narrowing conversions
- converting types, widening conversions
- base types, converting
- tables [.NET], type conversions
- data types [.NET], converting
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
ms.openlocfilehash: 27578d46a80b0372c6ddc2266a751cd0e6e9aa91
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889453"
---
# <a name="type-conversion-tables-in-net"></a><span data-ttu-id="f1267-102">.NET の型変換の表</span><span class="sxs-lookup"><span data-stu-id="f1267-102">Type Conversion Tables in .NET</span></span>
<span data-ttu-id="f1267-103">拡大変換は、1 つの型の値が、サイズが同じかそれ以上の別の型に変換されるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="f1267-103">Widening conversion occurs when a value of one type is converted to another type that is of equal or greater size.</span></span> <span data-ttu-id="f1267-104">縮小変換は、1 つの型の値が、サイズがより小さい別の型の値に変換されるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="f1267-104">A narrowing conversion occurs when a value of one type is converted to a value of another type that is of a smaller size.</span></span> <span data-ttu-id="f1267-105">このトピックの表は、両方の種類の変換の動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="f1267-105">The tables in this topic illustrate the behaviors exhibited by both types of conversions.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="f1267-106">拡大変換</span><span class="sxs-lookup"><span data-stu-id="f1267-106">Widening Conversions</span></span>  
 <span data-ttu-id="f1267-107">次の表は、情報を失うことなく実行できる拡大変換を示しています。</span><span class="sxs-lookup"><span data-stu-id="f1267-107">The following table describes the widening conversions that can be performed without the loss of information.</span></span>  
  
|<span data-ttu-id="f1267-108">[種類]</span><span class="sxs-lookup"><span data-stu-id="f1267-108">Type</span></span>|<span data-ttu-id="f1267-109">データ損失なしに次の型に変換可能</span><span class="sxs-lookup"><span data-stu-id="f1267-109">Can be converted without data loss to</span></span>|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<span data-ttu-id="f1267-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="f1267-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.SByte>|<span data-ttu-id="f1267-111"><xref:System.Int16>、<xref:System.Int32>、<xref:System.Int64>、<xref:System.Single>、<xref:System.Double>、<xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="f1267-111"><xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="f1267-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="f1267-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="f1267-113"><xref:System.UInt32>､<xref:System.Int32>、<xref:System.UInt64>、<xref:System.Int64>、<xref:System.Single>、<xref:System.Double>、<xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="f1267-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Char>|<span data-ttu-id="f1267-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="f1267-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="f1267-115"><xref:System.Int64>、 <xref:System.Double>、 <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="f1267-115"><xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="f1267-116"><xref:System.Int64>、<xref:System.UInt64>、<xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="f1267-116"><xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 <span data-ttu-id="f1267-117">一部の <xref:System.Single> または <xref:System.Double> への拡大変換では、精度が損なわれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f1267-117">Some widening conversions to <xref:System.Single> or <xref:System.Double> can cause a loss of precision.</span></span> <span data-ttu-id="f1267-118">次の表は、情報が失われる可能性のある拡大変換を示しています。</span><span class="sxs-lookup"><span data-stu-id="f1267-118">The following table describes the widening conversions that sometimes result in a loss of information.</span></span>  
  
|<span data-ttu-id="f1267-119">[種類]</span><span class="sxs-lookup"><span data-stu-id="f1267-119">Type</span></span>|<span data-ttu-id="f1267-120">次の型に変換可能</span><span class="sxs-lookup"><span data-stu-id="f1267-120">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<span data-ttu-id="f1267-121"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="f1267-121"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="f1267-122"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="f1267-122"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="f1267-123"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="f1267-123"><xref:System.Single>, <xref:System.Double></span></span>|  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="f1267-124">縮小変換</span><span class="sxs-lookup"><span data-stu-id="f1267-124">Narrowing Conversions</span></span>  
 <span data-ttu-id="f1267-125"><xref:System.Single> または <xref:System.Double> への縮小変換では、情報が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f1267-125">A narrowing conversion to <xref:System.Single> or <xref:System.Double> can cause a loss of information.</span></span> <span data-ttu-id="f1267-126">ターゲット型がソースの大きさを正確に表現できない場合、結果の型は定数 `PositiveInfinity` または `NegativeInfinity` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f1267-126">If the target type cannot properly express the magnitude of the source, the resulting type is set to the constant `PositiveInfinity` or `NegativeInfinity`.</span></span> <span data-ttu-id="f1267-127">`PositiveInfinity` は、正の数を 0 で除算した結果であり、<xref:System.Single> または <xref:System.Double> の値が `MaxValue` フィールドの値を超える場合にも返されます。</span><span class="sxs-lookup"><span data-stu-id="f1267-127">`PositiveInfinity` results from dividing a positive number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> exceeds the value of the `MaxValue` field.</span></span> <span data-ttu-id="f1267-128">`NegativeInfinity` は、負の数を 0 で除算した結果であり、<xref:System.Single> または <xref:System.Double> の値が `MinValue` フィールドの値を下回る場合にも返されます。</span><span class="sxs-lookup"><span data-stu-id="f1267-128">`NegativeInfinity` results from dividing a negative number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> falls below the value of the `MinValue` field.</span></span> <span data-ttu-id="f1267-129"><xref:System.Double> から <xref:System.Single> への変換は、`PositiveInfinity` または `NegativeInfinity` になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f1267-129">A conversion from a <xref:System.Double> to a <xref:System.Single> might result in `PositiveInfinity` or `NegativeInfinity`.</span></span>  
  
 <span data-ttu-id="f1267-130">その他のデータ型についても、縮小変換によって情報が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f1267-130">A narrowing conversion can also result in a loss of information for other data types.</span></span> <span data-ttu-id="f1267-131">ただし、変換される型の値が、ターゲット型の `MaxValue` フィールドと `MinValue` フィールドで指定された範囲外にある場合は、<xref:System.OverflowException> がスローされます。また、ターゲット型の値がその `MaxValue` または `MinValue` を超えないことを確認するために、ランタイムによって変換がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="f1267-131">However, an <xref:System.OverflowException> is thrown if the value of a type that is being converted falls outside of the range specified by the target type's `MaxValue` and `MinValue` fields, and the conversion is checked by the runtime to ensure that the value of the target type does not exceed its `MaxValue` or `MinValue`.</span></span> <span data-ttu-id="f1267-132"><xref:System.Convert?displayProperty=nameWithType> クラスを使用して実行される変換は、常にこの方法でチェックされます。</span><span class="sxs-lookup"><span data-stu-id="f1267-132">Conversions that are performed with the <xref:System.Convert?displayProperty=nameWithType> class are always checked in this manner.</span></span>  
  
 <span data-ttu-id="f1267-133">次の表は、<xref:System.Convert?displayProperty=nameWithType> を使用して <xref:System.OverflowException> をスローする変換、または、変換される型の値が結果の型の定義済みの範囲外にあるかどうかのチェックを行うすべての変換を示しています。</span><span class="sxs-lookup"><span data-stu-id="f1267-133">The following table lists conversions that throw an <xref:System.OverflowException> using <xref:System.Convert?displayProperty=nameWithType> or any checked conversion if the value of the type being converted is outside the defined range of the resulting type.</span></span>  
  
|<span data-ttu-id="f1267-134">[種類]</span><span class="sxs-lookup"><span data-stu-id="f1267-134">Type</span></span>|<span data-ttu-id="f1267-135">次の型に変換可能</span><span class="sxs-lookup"><span data-stu-id="f1267-135">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<span data-ttu-id="f1267-136"><xref:System.Byte>、<xref:System.UInt16>、<xref:System.UInt32>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="f1267-136"><xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="f1267-137"><xref:System.Byte>、 <xref:System.SByte>、 <xref:System.UInt16></span><span class="sxs-lookup"><span data-stu-id="f1267-137"><xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="f1267-138"><xref:System.Byte>、 <xref:System.SByte>、 <xref:System.Int16></span><span class="sxs-lookup"><span data-stu-id="f1267-138"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="f1267-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span><span class="sxs-lookup"><span data-stu-id="f1267-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="f1267-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="f1267-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span></span>|  
|<xref:System.Int64>|<span data-ttu-id="f1267-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="f1267-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="f1267-142"><xref:System.Byte>､<xref:System.SByte>、<xref:System.Int16>、<xref:System.UInt16>、<xref:System.Int32>、<xref:System.UInt32>、<xref:System.Int64></span><span class="sxs-lookup"><span data-stu-id="f1267-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="f1267-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="f1267-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Single>|<span data-ttu-id="f1267-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="f1267-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Double>|<span data-ttu-id="f1267-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="f1267-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1267-146">参照</span><span class="sxs-lookup"><span data-stu-id="f1267-146">See also</span></span>

- <xref:System.Convert?displayProperty=nameWithType>
- [<span data-ttu-id="f1267-147">.NET での型変換</span><span class="sxs-lookup"><span data-stu-id="f1267-147">Type Conversion in .NET</span></span>](type-conversion.md)
