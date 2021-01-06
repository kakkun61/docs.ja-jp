---
title: Protobuf maps for dictionary-gRPC for WCF 開発者
description: Protobuf maps を使用して .NET で辞書型を表す方法について説明します。
ms.date: 12/15/2020
ms.openlocfilehash: d38270d4bc320cf1f758080c18843ed1d716b350
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938547"
---
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="e594c-103">Protobuf のディクショナリのマップ</span><span class="sxs-lookup"><span data-stu-id="e594c-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="e594c-104">メッセージ内の名前付きの値の任意のコレクションを表すことができることが重要です。</span><span class="sxs-lookup"><span data-stu-id="e594c-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="e594c-105">.NET では、通常、このアクティビティはディクショナリ型によって処理されます。</span><span class="sxs-lookup"><span data-stu-id="e594c-105">In .NET, this activity is commonly handled through dictionary types.</span></span> <span data-ttu-id="e594c-106"><xref:System.Collections.Generic.IDictionary%602>プロトコルバッファー (Protobuf) の .net 型に相当するものが `map<key_type, value_type>` 型です。</span><span class="sxs-lookup"><span data-stu-id="e594c-106">The equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type in Protocol Buffer (Protobuf) is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="e594c-107">このセクションでは、Protobuf で型を宣言する方法 `map` と、生成されたコードを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e594c-107">This section shows how to declare a `map` type in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="e594c-108">生成されたコードで `map` は、フィールドは、型の読み取り専用プロパティによって表され [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] ます。</span><span class="sxs-lookup"><span data-stu-id="e594c-108">In the generated code, `map` fields are represented by read-only properties of the [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] type.</span></span> <span data-ttu-id="e594c-109">この型は、を含む標準の .NET コレクションインターフェイスを実装し <xref:System.Collections.Generic.IDictionary%602> ます。</span><span class="sxs-lookup"><span data-stu-id="e594c-109">This type implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="e594c-110">マップフィールドは、メッセージ定義内で直接繰り返すことはできません。</span><span class="sxs-lookup"><span data-stu-id="e594c-110">Map fields can't be directly repeated in a message definition.</span></span> <span data-ttu-id="e594c-111">ただし、次の例のように、マップを含む入れ子になったメッセージを作成し、メッセージの種類でを使用することができ `repeated` ます。</span><span class="sxs-lookup"><span data-stu-id="e594c-111">But you can create a nested message that contains a map and use `repeated` on the message type, as in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="e594c-112">コードでの MapField プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="e594c-112">Using MapField properties in code</span></span>

<span data-ttu-id="e594c-113">`MapField`フィールドから生成されたプロパティ `map` は読み取り専用であり、になることはありません `null` 。</span><span class="sxs-lookup"><span data-stu-id="e594c-113">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="e594c-114">マッププロパティを設定するには、空のプロパティに対してメソッドを使用して、 `Add(IDictionary<TKey,TValue> values)` `MapField` 任意の .net ディクショナリから値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="e594c-114">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="e594c-115">参考資料</span><span class="sxs-lookup"><span data-stu-id="e594c-115">Further reading</span></span>

<span data-ttu-id="e594c-116">Protobuf の詳細については、公式の [Protobuf のドキュメント](https://developers.google.com/protocol-buffers/docs/overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e594c-116">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

[map-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/map-field-t-key-t-value-

>[!div class="step-by-step"]
><span data-ttu-id="e594c-117">[前へ](protobuf-enums.md)
>[次へ](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="e594c-117">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
