---
ms.openlocfilehash: dfa8235fcfd868b80d3a610bddb492899519e289
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009055"
---
### <a name="xml-parsing-changes"></a><span data-ttu-id="f7a10-101">XML 解析の変更</span><span class="sxs-lookup"><span data-stu-id="f7a10-101">XML parsing changes</span></span>

| <span data-ttu-id="f7a10-102">名前</span><span class="sxs-lookup"><span data-stu-id="f7a10-102">Name</span></span>    | <span data-ttu-id="f7a10-103">値</span><span class="sxs-lookup"><span data-stu-id="f7a10-103">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="f7a10-104">スコープ</span><span class="sxs-lookup"><span data-stu-id="f7a10-104">Scope</span></span>   | <span data-ttu-id="f7a10-105">マイナー</span><span class="sxs-lookup"><span data-stu-id="f7a10-105">Minor</span></span>   |
| <span data-ttu-id="f7a10-106">バージョン</span><span class="sxs-lookup"><span data-stu-id="f7a10-106">Version</span></span> | <span data-ttu-id="f7a10-107">4.5.2</span><span class="sxs-lookup"><span data-stu-id="f7a10-107">4.5.2</span></span>   |
| <span data-ttu-id="f7a10-108">種類</span><span class="sxs-lookup"><span data-stu-id="f7a10-108">Type</span></span>    | <span data-ttu-id="f7a10-109">ランタイム</span><span class="sxs-lookup"><span data-stu-id="f7a10-109">Runtime</span></span> |

#### <a name="details"></a><span data-ttu-id="f7a10-110">詳細</span><span class="sxs-lookup"><span data-stu-id="f7a10-110">Details</span></span>

<span data-ttu-id="f7a10-111">セキュリティ上の理由から、次の変更が XML 解析 API に導入されました。</span><span class="sxs-lookup"><span data-stu-id="f7a10-111">For security reasons, the following changes were introduced into XML parsing APIS:</span></span>

- <span data-ttu-id="f7a10-112"><xref:System.Xml.XmlReaderSettings> が初期化されるときに、<xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=nameWithType> は 1,000 万に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f7a10-112"><xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=nameWithType> is set to 10 million when <xref:System.Xml.XmlReaderSettings> is initialized.</span></span>
- <span data-ttu-id="f7a10-113">既定では、<xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=nameWithType> は `null` に設定されています。</span><span class="sxs-lookup"><span data-stu-id="f7a10-113"><xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=nameWithType> is set to `null` by default.</span></span>

> [!NOTE]
> <span data-ttu-id="f7a10-114"><xref:System.Xml.XmlReaderSettings> はすべての XML パーサーによって使用されるため、この変更は <xref:System.Xml.XmlReader> のケースでは役に立ちますが、他のシナリオにも影響します。</span><span class="sxs-lookup"><span data-stu-id="f7a10-114"><xref:System.Xml.XmlReaderSettings> is used by all XML parsers, so while this change helps the <xref:System.Xml.XmlReader> case, it also affects other scenarios.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f7a10-115">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="f7a10-115">Suggestion</span></span>

<span data-ttu-id="f7a10-116">以前の動作に戻すには、レジストリで値を設定します。</span><span class="sxs-lookup"><span data-stu-id="f7a10-116">To revert to the previous behavior, you can set a value in the registry.</span></span> <span data-ttu-id="f7a10-117">`EnableLegacyXmlSettings` という名前のダブルワード値を `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\XML` レジストリ キーに追加し、その値を `1` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f7a10-117">Add a DWORD value named `EnableLegacyXmlSettings` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\XML` registry key, and set its value to `1`.</span></span> <span data-ttu-id="f7a10-118">代わりに、HKEY_CURRENT_USER ハイブでレジストリ値を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="f7a10-118">You can also add the registry value in the HKEY_CURRENT_USER hive instead.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f7a10-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="f7a10-119">Affected APIs</span></span>

- <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName>
- <xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=fullName>

<span data-ttu-id="f7a10-120">また、直接的または間接的に <xref:System.Xml.XmlResolver> に依存するすべての XML API が影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="f7a10-120">In addition, any XML API that depends on <xref:System.Xml.XmlResolver>, either directly or indirectly, is affected.</span></span>

<!--

#### Affected APIs

- `P:System.Xml.XmlReaderSettings.MaxCharactersFromEntities`
- `P:System.Xml.XmlReaderSettings.XmlResolver`

-->
