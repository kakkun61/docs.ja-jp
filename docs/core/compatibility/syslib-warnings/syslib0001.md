---
title: SYSLIB0001 警告
description: コンパイル時の警告 SYSLIB0001 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 6c4b6a2f41e9dc044ef76bb5a53a4a54a44bca5a
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596380"
---
# <a name="syslib0001-the-utf-7-encoding-is-insecure"></a><span data-ttu-id="2bc11-103">SYSLIB0001: UTF-7 エンコードは安全ではない</span><span class="sxs-lookup"><span data-stu-id="2bc11-103">SYSLIB0001: The UTF-7 encoding is insecure</span></span>

<span data-ttu-id="2bc11-104">UTF-7 エンコードがアプリケーション間で広く使用されることはなくなりました。多くの仕様では、現在インターチェンジでの[使用が禁止されています](https://security.stackexchange.com/a/68609/3573)。</span><span class="sxs-lookup"><span data-stu-id="2bc11-104">The UTF-7 encoding is no longer in wide use among applications, and many specs now [forbid its use](https://security.stackexchange.com/a/68609/3573) in interchange.</span></span> <span data-ttu-id="2bc11-105">また、UTF-7 でエンコードされたデータの使用を予測していないアプリケーションでは、[攻撃ベクトルとして使用される](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7)こともあります。</span><span class="sxs-lookup"><span data-stu-id="2bc11-105">It's also occasionally [used as an attack vector](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) in applications that don't anticipate encountering UTF-7-encoded data.</span></span> <span data-ttu-id="2bc11-106">Microsoft では、<xref:System.Text.UTF7Encoding?displayProperty=nameWithType> の使用に対して警告が行われます。エラー検出が提供されないためです。</span><span class="sxs-lookup"><span data-stu-id="2bc11-106">Microsoft warns against use of <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> because it doesn't provide error detection.</span></span>

<span data-ttu-id="2bc11-107">そのため、.NET 5.0 以降、次の API は古いものとしてマークさていれます。</span><span class="sxs-lookup"><span data-stu-id="2bc11-107">Consequently, the following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="2bc11-108">これらの API を使用すると、コンパイル時に警告 `SYSLIB0001` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2bc11-108">Use of these APIs generates warning `SYSLIB0001` at compile time.</span></span>

- <span data-ttu-id="2bc11-109"><xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> プロパティ</span><span class="sxs-lookup"><span data-stu-id="2bc11-109"><xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property</span></span>
- <span data-ttu-id="2bc11-110"><xref:System.Text.UTF7Encoding.%23ctor%2A> コンストラクター</span><span class="sxs-lookup"><span data-stu-id="2bc11-110"><xref:System.Text.UTF7Encoding.%23ctor%2A> constructors</span></span>

## <a name="workarounds"></a><span data-ttu-id="2bc11-111">回避策</span><span class="sxs-lookup"><span data-stu-id="2bc11-111">Workarounds</span></span>

- <span data-ttu-id="2bc11-112">独自のプロトコルまたはファイル形式内で <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> または <xref:System.Text.UTF7Encoding> を使用している場合:</span><span class="sxs-lookup"><span data-stu-id="2bc11-112">If you're using <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding> within your own protocol or file format:</span></span>

  <span data-ttu-id="2bc11-113"><xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> または <xref:System.Text.UTF8Encoding> の使用に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="2bc11-113">Switch to using <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> or <xref:System.Text.UTF8Encoding>.</span></span> <span data-ttu-id="2bc11-114">UTF-8 は業界標準であり、各言語、オペレーティング システム、およびランタイム間で広くサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2bc11-114">UTF-8 is an industry standard and is widely supported across languages, operating systems, and runtimes.</span></span> <span data-ttu-id="2bc11-115">UTF-8 を使用すると、将来のコードの保守が容易になり、エコシステムの他の部分との相互運用性が高まります。</span><span class="sxs-lookup"><span data-stu-id="2bc11-115">Using UTF-8 eases future maintenance of your code and makes it more interoperable with the rest of the ecosystem.</span></span>

- <span data-ttu-id="2bc11-116"><xref:System.Text.Encoding> インスタンスを <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> と比較している場合:</span><span class="sxs-lookup"><span data-stu-id="2bc11-116">If you're comparing an <xref:System.Text.Encoding> instance against <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span></span>

  <span data-ttu-id="2bc11-117">代わりに、既知の UTF-7 コード ページ (`65000`) に対してチェックを実行することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="2bc11-117">Instead, consider performing a check against the well-known UTF-7 code page, which is `65000`.</span></span> <span data-ttu-id="2bc11-118">コード ページと比較することによって、警告を回避し、一部のエッジ ケースを処理することもできます。たとえば、他のユーザーが `new UTF7Encoding()` を呼び出した場合や、型をサブクラス化した場合などです。</span><span class="sxs-lookup"><span data-stu-id="2bc11-118">By comparing against the code page, you avoid the warning and also handle some edge cases, such as if somebody called `new UTF7Encoding()` or subclassed the type.</span></span>

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="2bc11-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bc11-119">See also</span></span>

- [<span data-ttu-id="2bc11-120">UTF-7 コード パスが古い形式に</span><span class="sxs-lookup"><span data-stu-id="2bc11-120">UTF-7 code paths are obsolete</span></span>](../core-libraries/5.0/utf-7-code-paths-obsolete.md)
