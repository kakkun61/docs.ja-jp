---
title: SYSLIB0009 警告
description: コンパイル時の警告 SYSLIB0009 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 47b4f595a54800370da90f61d838c665df8b6091
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439977"
---
# <a name="syslib0009-the-authenticationmanager-authenticate-and-preauthenticate-methods-are-not-supported"></a><span data-ttu-id="f49f1-103">SYSLIB0009:AuthenticationManager 認証および PreAuthenticate メソッドはサポートされていません</span><span class="sxs-lookup"><span data-stu-id="f49f1-103">SYSLIB0009: The AuthenticationManager Authenticate and PreAuthenticate methods are not supported</span></span>

<span data-ttu-id="f49f1-104">.NET 5.0 以降、次の API は古いものとしてマークされています。</span><span class="sxs-lookup"><span data-stu-id="f49f1-104">The following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="f49f1-105">これらの API を使用すると、コンパイル時に警告 `SYSLIB0009` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f49f1-105">Use of these APIs generates warning `SYSLIB0009` at compile time.</span></span>

- <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>
- <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType>

## <a name="suppress-the-warning"></a><span data-ttu-id="f49f1-106">警告を非表示にする</span><span class="sxs-lookup"><span data-stu-id="f49f1-106">Suppress the warning</span></span>

<span data-ttu-id="f49f1-107">コードを変更できない場合、`#pragma` ディレクティブか `<NoWarn>` プロジェクト設定で警告を非表示にできます。</span><span class="sxs-lookup"><span data-stu-id="f49f1-107">If you cannot change your code, you can suppress the warning through a `#pragma` directive or a `<NoWarn>` project setting.</span></span> <span data-ttu-id="f49f1-108">例については、「[警告を表示しない](syslib-obsoletions.md#suppress-warnings)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f49f1-108">For examples, see [Suppress warnings](syslib-obsoletions.md#suppress-warnings).</span></span>
