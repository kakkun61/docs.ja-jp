---
title: バイト配列を int に変換する方法 - C# プログラミング ガイド
description: バイト配列を int に変換する方法について説明します。コード例を参照し、使用可能なその他のリソースを確認してください。
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: f6fb6ad907ecd668d59ca95b19218c19d378d83e
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513251"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="f1bf3-103">バイト配列を int に変換する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f1bf3-103">How to convert a byte array to an int (C# Programming Guide)</span></span>

<span data-ttu-id="f1bf3-104">次の例では、<xref:System.BitConverter> クラスを使用して、バイト配列を [int](../../language-reference/builtin-types/integral-numeric-types.md) に変換する方法、またバイト配列に戻す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-104">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="f1bf3-105">たとえば、ネットワークからバイトを読み込んだ後、バイトから組み込みデータ型への変換が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-105">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="f1bf3-106">この例の [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) メソッド以外にも、バイト列を (バイト配列から) 他の組み込み型に変換する <xref:System.BitConverter> クラスのメソッドがあります。次の表にそれらのメソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-106">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>

|<span data-ttu-id="f1bf3-107">返される型</span><span class="sxs-lookup"><span data-stu-id="f1bf3-107">Type returned</span></span>|<span data-ttu-id="f1bf3-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="f1bf3-108">Method</span></span>|
|-------------------|------------|
|`bool`|<span data-ttu-id="f1bf3-109">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f1bf3-109">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|
|`char`|<span data-ttu-id="f1bf3-110">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f1bf3-110">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|
|`double`|<span data-ttu-id="f1bf3-111">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f1bf3-111">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|
|`short`|<span data-ttu-id="f1bf3-112">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f1bf3-112">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|
|`int`|<span data-ttu-id="f1bf3-113">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f1bf3-113">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|
|`long`|<span data-ttu-id="f1bf3-114">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f1bf3-114">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|
|`float`|<span data-ttu-id="f1bf3-115">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f1bf3-115">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|
|`ushort`|<span data-ttu-id="f1bf3-116">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f1bf3-116">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|
|`uint`|<span data-ttu-id="f1bf3-117">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f1bf3-117">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|
|`ulong`|<span data-ttu-id="f1bf3-118">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f1bf3-118">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|

## <a name="example"></a><span data-ttu-id="f1bf3-119">例</span><span class="sxs-lookup"><span data-stu-id="f1bf3-119">Example</span></span>

<span data-ttu-id="f1bf3-120">この例では、バイトの配列を初期化して、コンピューター アーキテクチャがリトル エンディアンである場合 (つまり、下位バイトから先に格納する場合) は、配列を反転します。次に、[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) メソッドを呼び出して、配列内の 4 バイトを `int` に変換します。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-120">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="f1bf3-121">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) の 2 番目の引数は、バイト配列の開始インデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-121">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="f1bf3-122">出力は、コンピューター アーキテクチャのエンディアンによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-122">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a><span data-ttu-id="f1bf3-123">例</span><span class="sxs-lookup"><span data-stu-id="f1bf3-123">Example</span></span>

<span data-ttu-id="f1bf3-124">この例では、<xref:System.BitConverter> クラスの <xref:System.BitConverter.GetBytes%28System.Int32%29> メソッドを呼び出して、`int` をバイト配列に変換します。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-124">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="f1bf3-125">出力は、コンピューター アーキテクチャのエンディアンによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f1bf3-125">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a><span data-ttu-id="f1bf3-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1bf3-126">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="f1bf3-127">型</span><span class="sxs-lookup"><span data-stu-id="f1bf3-127">Types</span></span>](./index.md)
