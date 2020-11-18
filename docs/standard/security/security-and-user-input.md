---
title: セキュリティとユーザー入力
description: コードでは、ユーザーが入力したデータをパラメーターとして他のコードに渡すことがあり、これはセキュリティに影響を与える可能性があります。 範囲チェックを実行して、問題のある入力を拒否することができます。
ms.date: 07/15/2020
helpviewer_keywords:
- security [.NET], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: e476db90dd1fd579f4ecfe3f2088cc76c955b9c0
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824058"
---
# <a name="security-and-user-input"></a><span data-ttu-id="700cc-104">セキュリティとユーザー入力</span><span class="sxs-lookup"><span data-stu-id="700cc-104">Security and User Input</span></span>

<span data-ttu-id="700cc-105">ユーザー データにはあらゆる種類の入力 (Web 要求または URL からのデータや、Microsoft Windows Forms アプリケーションのコントロールへの入力など) がありますが、これはコードに悪影響を及ぼすことがあります。このようなデータはパラメーターとして直接使用され、他のコードを呼び出す場合が多いためです。</span><span class="sxs-lookup"><span data-stu-id="700cc-105">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="700cc-106">この状況は、悪意のあるコードが不明なパラメーターを使用してコードを呼び出すことと似ており、同じ予防策をとる必要があります。</span><span class="sxs-lookup"><span data-stu-id="700cc-106">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="700cc-107">実際には、ユーザー入力の安全性を保つ方が困難です。潜在的に信頼されていないデータの存在をトレースするスタック フレームがないためです。</span><span class="sxs-lookup"><span data-stu-id="700cc-107">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>

<span data-ttu-id="700cc-108">これらは最も微小で見つけにくいセキュリティ バグです。セキュリティとは無関係に見えるコードに存在すことができ、他のコードに悪いデータを送り出すゲートウェイだからです。</span><span class="sxs-lookup"><span data-stu-id="700cc-108">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="700cc-109">このようなバグを探し出すには、あらゆる種類の入力データを追跡し、可能性のある値の範囲を想像し、そのデータを扱うコードがすべてのケースを処理できるかどうかを検討します。</span><span class="sxs-lookup"><span data-stu-id="700cc-109">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="700cc-110">これらのバグは、範囲チェックを使用して、コードで処理できない入力を拒否することで修正できます。</span><span class="sxs-lookup"><span data-stu-id="700cc-110">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>

<span data-ttu-id="700cc-111">ユーザー データに関連する重要な注意事項を次に示します。</span><span class="sxs-lookup"><span data-stu-id="700cc-111">Some important considerations involving user data include the following:</span></span>

- <span data-ttu-id="700cc-112">サーバー応答内のすべてのユーザー データは、クライアント上でサーバーのサイトのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="700cc-112">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="700cc-113">Web サーバーがユーザーデータを取得し、返された Web ページに挿入する場合、たとえば、タグを含め、 **\<script>** サーバーからのように実行します。</span><span class="sxs-lookup"><span data-stu-id="700cc-113">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>

- <span data-ttu-id="700cc-114">クライアントはすべての URL を要求できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="700cc-114">Remember that the client can request any URL.</span></span>

- <span data-ttu-id="700cc-115">巧妙なパスまたは無効なパスに注意してください。</span><span class="sxs-lookup"><span data-stu-id="700cc-115">Consider tricky or invalid paths:</span></span>

  - <span data-ttu-id="700cc-116">..\、極端に長いパス。</span><span class="sxs-lookup"><span data-stu-id="700cc-116">..\ , extremely long paths.</span></span>

  - <span data-ttu-id="700cc-117">ワイルドカード文字 (\*) の使用。</span><span class="sxs-lookup"><span data-stu-id="700cc-117">Use of wild card characters (\*).</span></span>

  - <span data-ttu-id="700cc-118">トークンの展開 (%token%)。</span><span class="sxs-lookup"><span data-stu-id="700cc-118">Token expansion (%token%).</span></span>

  - <span data-ttu-id="700cc-119">特別な意味を持つ変わった形式のパス。</span><span class="sxs-lookup"><span data-stu-id="700cc-119">Strange forms of paths with special meaning.</span></span>

  - <span data-ttu-id="700cc-120">代替ファイル システム ストリーム名、`filename::$DATA` など。</span><span class="sxs-lookup"><span data-stu-id="700cc-120">Alternate file system stream names such as `filename::$DATA`.</span></span>

  - <span data-ttu-id="700cc-121">ファイル名の短縮バージョン、`longfilename`に対して `longfi~1` など。</span><span class="sxs-lookup"><span data-stu-id="700cc-121">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>

- <span data-ttu-id="700cc-122">Eval(userdata) は何でも実行できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="700cc-122">Remember that Eval(userdata) can do anything.</span></span>

- <span data-ttu-id="700cc-123">ユーザー データを含む名前の遅延バインディングを警戒してください。</span><span class="sxs-lookup"><span data-stu-id="700cc-123">Be wary of late binding to a name that includes some user data.</span></span>

- <span data-ttu-id="700cc-124">Web データを扱う場合は、許容されるさまざまな形式のエスケープを検討してください。</span><span class="sxs-lookup"><span data-stu-id="700cc-124">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>

  - <span data-ttu-id="700cc-125">16 進数エスケープ (%nn)。</span><span class="sxs-lookup"><span data-stu-id="700cc-125">Hexadecimal escapes (%nn).</span></span>

  - <span data-ttu-id="700cc-126">Unicode エスケープ (%nnn)。</span><span class="sxs-lookup"><span data-stu-id="700cc-126">Unicode escapes (%nnn).</span></span>

  - <span data-ttu-id="700cc-127">オーバーロング UTF-8 エスケープ (%nn%nn)。</span><span class="sxs-lookup"><span data-stu-id="700cc-127">Overlong UTF-8 escapes (%nn%nn).</span></span>

  - <span data-ttu-id="700cc-128">ダブル エスケープ (%nn が %mmnn になります。%mm は '%' のエスケープです)。</span><span class="sxs-lookup"><span data-stu-id="700cc-128">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>

- <span data-ttu-id="700cc-129">標準形式が複数あるユーザー名に注意してください。</span><span class="sxs-lookup"><span data-stu-id="700cc-129">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="700cc-130">たとえば、よく使用するのは MYDOMAIN\\*username* 形式または *username*@mydomain.example.com 形式です。</span><span class="sxs-lookup"><span data-stu-id="700cc-130">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>

## <a name="see-also"></a><span data-ttu-id="700cc-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="700cc-131">See also</span></span>

- [<span data-ttu-id="700cc-132">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="700cc-132">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
- [<span data-ttu-id="700cc-133">ASP.NET Core のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="700cc-133">ASP.NET Core Security</span></span>](/aspnet/core/security/)
