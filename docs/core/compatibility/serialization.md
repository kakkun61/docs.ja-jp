---
title: シリアル化に関する破壊的変更
description: .NET Core と .NET 5.0 以降のシリアル化カテゴリにおける破壊的変更を一覧で示します。
ms.date: 07/30/2020
ms.openlocfilehash: 67608c8e7a9745c060b7eb179fe5a956ede9f80f
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332882"
---
# <a name="serialization-breaking-changes"></a><span data-ttu-id="74e8b-103">シリアル化に関する破壊的変更</span><span class="sxs-lookup"><span data-stu-id="74e8b-103">Serialization breaking changes</span></span>

<span data-ttu-id="74e8b-104">このページでは、次の破壊的変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="74e8b-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="74e8b-105">互換性に影響する変更点</span><span class="sxs-lookup"><span data-stu-id="74e8b-105">Breaking change</span></span> | <span data-ttu-id="74e8b-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="74e8b-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="74e8b-107">ASP.NET Core アプリで、引用符で囲まれた数値を逆シリアル化できる</span><span class="sxs-lookup"><span data-stu-id="74e8b-107">ASP.NET Core apps allow deserializing quoted numbers</span></span>](#aspnet-core-apps-allow-deserializing-quoted-numbers) | <span data-ttu-id="74e8b-108">5.0</span><span class="sxs-lookup"><span data-stu-id="74e8b-108">5.0</span></span> |
| [<span data-ttu-id="74e8b-109">キーと値のペアのシリアル化および逆シリアル化時、PropertyNamingPolicy、PropertyNameCaseInsensitive、Encoder オプションが許可される</span><span class="sxs-lookup"><span data-stu-id="74e8b-109">PropertyNamingPolicy, PropertyNameCaseInsensitive, and Encoder options are honored when serializing and deserializing key-value pairs</span></span>](#propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs) | <span data-ttu-id="74e8b-110">5.0</span><span class="sxs-lookup"><span data-stu-id="74e8b-110">5.0</span></span> |
| [<span data-ttu-id="74e8b-111">非パブリック、パラメーターなしのコンストラクターが逆シリアル化に使用されない</span><span class="sxs-lookup"><span data-stu-id="74e8b-111">Non-public, parameterless constructors not used for deserialization</span></span>](#non-public-parameterless-constructors-not-used-for-deserialization) | <span data-ttu-id="74e8b-112">5.0</span><span class="sxs-lookup"><span data-stu-id="74e8b-112">5.0</span></span> |
| [<span data-ttu-id="74e8b-113">型パラメーターが null の場合に JsonSerializer.Serialize によって ArgumentNullException がスローされる</span><span class="sxs-lookup"><span data-stu-id="74e8b-113">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="74e8b-114">5.0</span><span class="sxs-lookup"><span data-stu-id="74e8b-114">5.0</span></span> |
| [<span data-ttu-id="74e8b-115">JsonSerializer.Deserialize によって 1 文字の文字列が求められる</span><span class="sxs-lookup"><span data-stu-id="74e8b-115">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="74e8b-116">5.0</span><span class="sxs-lookup"><span data-stu-id="74e8b-116">5.0</span></span> |
| [<span data-ttu-id="74e8b-117">BinaryFormatter.Deserialize によって SerializationException の例外の一部が再ラップされる</span><span class="sxs-lookup"><span data-stu-id="74e8b-117">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="74e8b-118">5.0</span><span class="sxs-lookup"><span data-stu-id="74e8b-118">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="74e8b-119">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="74e8b-119">.NET 5.0</span></span>

[!INCLUDE [jsonserializer-allows-reading-numbers-as-strings](../../../includes/core-changes/serialization/5.0/jsonserializer-allows-reading-numbers-as-strings.md)]

***

[!INCLUDE [options-honored-when-serializing-key-value-pairs](../../../includes/core-changes/serialization/5.0/options-honored-when-serializing-key-value-pairs.md)]

<span data-ttu-id="74e8b-120">\*\*_</span><span class="sxs-lookup"><span data-stu-id="74e8b-120">\*\*_</span></span>

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

_*_

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

_*_

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

_*_

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

<span data-ttu-id="74e8b-121">_\*\*</span><span class="sxs-lookup"><span data-stu-id="74e8b-121">_\*\*</span></span>
