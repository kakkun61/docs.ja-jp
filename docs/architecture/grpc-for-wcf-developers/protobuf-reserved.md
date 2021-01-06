---
title: Protobuf の予約済みフィールド-WCF 開発者向け gRPC
description: バージョン間の互換性のために予約されているフィールドについて説明します。
ms.date: 12/15/2020
ms.openlocfilehash: d82043d619c5b3b81091ae4ea381e4778c1cf6ba
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938521"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="954be-103">Protobuf 予約フィールド</span><span class="sxs-lookup"><span data-stu-id="954be-103">Protobuf reserved fields</span></span>

<span data-ttu-id="954be-104">プロトコルバッファー (Protobuf) での下位互換性の保証は、常に同じデータ項目を表すフィールド番号に依存します。</span><span class="sxs-lookup"><span data-stu-id="954be-104">The backward-compatibility guarantees in Protocol Buffer (Protobuf) rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="954be-105">新しいバージョンのサービスでメッセージからフィールドが削除された場合、そのフィールド番号は再利用しないでください。</span><span class="sxs-lookup"><span data-stu-id="954be-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="954be-106">キーワードを使用して、この動作を強制でき `reserved` ます。</span><span class="sxs-lookup"><span data-stu-id="954be-106">You can enforce this behavior by using the `reserved` keyword.</span></span>

<span data-ttu-id="954be-107">前に `displayName` 定義したメッセージからフィールドとフィールドを削除した場合は `marketId` `Stock` 、次の例のようにフィールド番号を予約する必要があります。</span><span class="sxs-lookup"><span data-stu-id="954be-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="954be-108">キーワードは、 `reserved` 今後追加される可能性のあるフィールドのプレースホルダーとして使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="954be-108">You can also use the `reserved` keyword as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="954be-109">キーワードを使用して、連続するフィールド番号を範囲として表すことができ `to` ます。</span><span class="sxs-lookup"><span data-stu-id="954be-109">You can express contiguous field numbers as a range by using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="954be-110">[前へ](protobuf-repeated.md)
>[次へ](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="954be-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
