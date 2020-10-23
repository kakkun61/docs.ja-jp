---
title: シリアル化に関する破壊的変更
description: .NET Core と .NET 5.0 以降のシリアル化カテゴリにおける破壊的変更を一覧で示します。
ms.date: 07/30/2020
ms.openlocfilehash: bb6bd650afeba426edc6e102076f05f97f8e0598
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050471"
---
# <a name="serialization-breaking-changes"></a><span data-ttu-id="bc46f-103">シリアル化に関する破壊的変更</span><span class="sxs-lookup"><span data-stu-id="bc46f-103">Serialization breaking changes</span></span>

<span data-ttu-id="bc46f-104">このページでは、次の破壊的変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="bc46f-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="bc46f-105">互換性に影響する変更点</span><span class="sxs-lookup"><span data-stu-id="bc46f-105">Breaking change</span></span> | <span data-ttu-id="bc46f-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="bc46f-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="bc46f-107">キーと値のペアのシリアル化および逆シリアル化時、PropertyNamingPolicy、PropertyNameCaseInsensitive、Encoder オプションが許可される</span><span class="sxs-lookup"><span data-stu-id="bc46f-107">PropertyNamingPolicy, PropertyNameCaseInsensitive, and Encoder options are honored when serializing and deserializing key-value pairs</span></span>](#propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs) | <span data-ttu-id="bc46f-108">5.0</span><span class="sxs-lookup"><span data-stu-id="bc46f-108">5.0</span></span> |
| [<span data-ttu-id="bc46f-109">非パブリック、パラメーターなしのコンストラクターが逆シリアル化に使用されない</span><span class="sxs-lookup"><span data-stu-id="bc46f-109">Non-public, parameterless constructors not used for deserialization</span></span>](#non-public-parameterless-constructors-not-used-for-deserialization) | <span data-ttu-id="bc46f-110">5.0</span><span class="sxs-lookup"><span data-stu-id="bc46f-110">5.0</span></span> |
| [<span data-ttu-id="bc46f-111">型パラメーターが null の場合に JsonSerializer.Serialize によって ArgumentNullException がスローされる</span><span class="sxs-lookup"><span data-stu-id="bc46f-111">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="bc46f-112">5.0</span><span class="sxs-lookup"><span data-stu-id="bc46f-112">5.0</span></span> |
| [<span data-ttu-id="bc46f-113">JsonSerializer.Deserialize によって 1 文字の文字列が求められる</span><span class="sxs-lookup"><span data-stu-id="bc46f-113">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="bc46f-114">5.0</span><span class="sxs-lookup"><span data-stu-id="bc46f-114">5.0</span></span> |
| [<span data-ttu-id="bc46f-115">BinaryFormatter.Deserialize によって SerializationException の例外の一部が再ラップされる</span><span class="sxs-lookup"><span data-stu-id="bc46f-115">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="bc46f-116">5.0</span><span class="sxs-lookup"><span data-stu-id="bc46f-116">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="bc46f-117">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="bc46f-117">.NET 5.0</span></span>

[!INCLUDE [options-honored-when-serializing-key-value-pairs](../../../includes/core-changes/serialization/5.0/options-honored-when-serializing-key-value-pairs.md)]

***

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

***

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

***

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
