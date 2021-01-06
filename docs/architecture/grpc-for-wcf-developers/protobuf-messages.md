---
title: Protobuf messages-WCF 開発者向け gRPC
description: Protobuf メッセージを IDL で定義し、C# で生成する方法について説明します。
ms.date: 12/15/2020
ms.openlocfilehash: c1f2a3071d45dcbe4b98d747f19fed508bad102f
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938105"
---
# <a name="protobuf-messages"></a><span data-ttu-id="332a6-103">Protobuf メッセージ</span><span class="sxs-lookup"><span data-stu-id="332a6-103">Protobuf messages</span></span>

<span data-ttu-id="332a6-104">このセクションでは、ファイルでプロトコルバッファー (Protobuf) メッセージを宣言する方法について説明し `.proto` ます。</span><span class="sxs-lookup"><span data-stu-id="332a6-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="332a6-105">ここでは、フィールドの数値と型の基本的な概念について説明し、コンパイラによって生成される C# コードを見ていき `protoc` ます。</span><span class="sxs-lookup"><span data-stu-id="332a6-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span>

<span data-ttu-id="332a6-106">この章の残りの部分では、Protobuf でさまざまな種類のデータがどのように表現されるかについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="332a6-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="332a6-107">メッセージの宣言</span><span class="sxs-lookup"><span data-stu-id="332a6-107">Declaring a message</span></span>

<span data-ttu-id="332a6-108">Windows Communication Foundation (WCF) では、 `Stock` 株式市場取引アプリケーションのクラスが次の例のように定義されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="332a6-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

<span data-ttu-id="332a6-109">Protobuf で同等のクラスを実装するには、ファイルでそれを宣言する必要があり `.proto` ます。</span><span class="sxs-lookup"><span data-stu-id="332a6-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="332a6-110">コンパイラは、 `protoc` ビルド処理の一部として .net クラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="332a6-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

<span data-ttu-id="332a6-111">最初の行は、使用されている構文のバージョンを宣言します。</span><span class="sxs-lookup"><span data-stu-id="332a6-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="332a6-112">言語のバージョン3は2016でリリースされました。</span><span class="sxs-lookup"><span data-stu-id="332a6-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="332a6-113">これは、gRPC サービスに推奨されるバージョンです。</span><span class="sxs-lookup"><span data-stu-id="332a6-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="332a6-114">行は、生成された `option csharp_namespace` C# 型に使用される名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="332a6-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="332a6-115">このオプションは、 `.proto` ファイルが他の言語用にコンパイルされるときには無視されます。</span><span class="sxs-lookup"><span data-stu-id="332a6-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="332a6-116">Protobuf ファイルには、多くの場合、複数の言語の言語固有のオプションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="332a6-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="332a6-117">メッセージ定義では、 `Stock` 4 つのフィールドを指定します。</span><span class="sxs-lookup"><span data-stu-id="332a6-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="332a6-118">各には、型、名前、およびフィールド番号があります。</span><span class="sxs-lookup"><span data-stu-id="332a6-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="332a6-119">フィールド番号</span><span class="sxs-lookup"><span data-stu-id="332a6-119">Field numbers</span></span>

<span data-ttu-id="332a6-120">フィールド番号は Protobuf の重要な部分です。</span><span class="sxs-lookup"><span data-stu-id="332a6-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="332a6-121">これらは、バイナリエンコードデータ内のフィールドを識別するために使用されます。つまり、サービスのバージョンごとに変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="332a6-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="332a6-122">長所は、下位互換性と上位互換性が可能であることです。</span><span class="sxs-lookup"><span data-stu-id="332a6-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="332a6-123">クライアントとサービスは、不明な値が処理される可能性がある限り、知られていないフィールド番号を無視します。</span><span class="sxs-lookup"><span data-stu-id="332a6-123">Clients and services will ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="332a6-124">バイナリ形式では、フィールド番号が型識別子と結合されます。</span><span class="sxs-lookup"><span data-stu-id="332a6-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="332a6-125">1 ~ 15 のフィールド番号は、その型で1バイトとしてエンコードできます。</span><span class="sxs-lookup"><span data-stu-id="332a6-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="332a6-126">16から2047の数値は2バイトになります。</span><span class="sxs-lookup"><span data-stu-id="332a6-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="332a6-127">何らかの理由でメッセージに2047を超えるフィールドが必要な場合は、より高い値にすることができます。</span><span class="sxs-lookup"><span data-stu-id="332a6-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="332a6-128">フィールド番号が 1 ~ 15 の1バイト識別子ではパフォーマンスが向上します。そのため、最も基本的で頻繁に使用されるフィールドで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="332a6-128">The single-byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="332a6-129">種類</span><span class="sxs-lookup"><span data-stu-id="332a6-129">Types</span></span>

<span data-ttu-id="332a6-130">型宣言は、Protobuf のネイティブスカラーデータ型を使用しています。詳細については、 [次のセクション](protobuf-data-types.md)で説明します。</span><span class="sxs-lookup"><span data-stu-id="332a6-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="332a6-131">この章の残りの部分では、Protobuf の組み込み型について説明し、一般的な .NET 型にどのように関連しているかを示します。</span><span class="sxs-lookup"><span data-stu-id="332a6-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="332a6-132">Protobuf は型をネイティブでサポートしていない `decimal` ため、 `double` 代わりにを使用します。</span><span class="sxs-lookup"><span data-stu-id="332a6-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="332a6-133">完全な10進数の有効桁数を必要とするアプリケーションについては、この章の次の部分にある10進数 [に関するセクション](protobuf-data-types.md#decimals) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="332a6-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="332a6-134">生成されたコード</span><span class="sxs-lookup"><span data-stu-id="332a6-134">The generated code</span></span>

<span data-ttu-id="332a6-135">アプリケーションをビルドすると、Protobuf はメッセージごとにクラスを作成し、ネイティブな型を C# 型にマップします。</span><span class="sxs-lookup"><span data-stu-id="332a6-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="332a6-136">生成された `Stock` 型のシグネチャは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="332a6-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="332a6-137">生成される実際のコードは、これよりもはるかに複雑です。</span><span class="sxs-lookup"><span data-stu-id="332a6-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="332a6-138">その理由は、各クラスには、それ自体をバイナリワイヤ形式にシリアル化および逆シリアル化するために必要なすべてのコードが含まれているからです。</span><span class="sxs-lookup"><span data-stu-id="332a6-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="332a6-139">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="332a6-139">Property names</span></span>

<span data-ttu-id="332a6-140">Protobuf コンパイラはプロパティ名に適用されることに注意して `PascalCase` ください。ただし、これらは `snake_case` ファイルに含まれてい `.proto` ます。</span><span class="sxs-lookup"><span data-stu-id="332a6-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="332a6-141">[Protobuf スタイルガイド](https://developers.google.com/protocol-buffers/docs/style)では、メッセージ定義でを使用して、 `snake_case` 他のプラットフォームのコード生成によって意図した規約のケースが生成されるようにすることを推奨しています。</span><span class="sxs-lookup"><span data-stu-id="332a6-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="332a6-142">[前へ](protocol-buffers.md)
>[次へ](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="332a6-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
