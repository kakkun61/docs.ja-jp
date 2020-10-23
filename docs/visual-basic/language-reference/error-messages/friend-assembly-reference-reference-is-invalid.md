---
title: フレンド アセンブリ参照 <reference> は無効です
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: a42dd99ffaa06dce4823ce5d022fac02ae99c6bd
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160712"
---
# <a name="bc31535-friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="54a2b-102">BC31535:フレンド アセンブリ参照 \<reference> は無効です</span><span class="sxs-lookup"><span data-stu-id="54a2b-102">BC31535: Friend assembly reference \<reference> is invalid</span></span>

<span data-ttu-id="54a2b-103">フレンド アセンブリ参照 \<reference> は無効です。</span><span class="sxs-lookup"><span data-stu-id="54a2b-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="54a2b-104">厳密な名前の署名つきアセンブリはその InternalsVisibleTo 宣言内で公開キーを指定しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="54a2b-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>

 <span data-ttu-id="54a2b-105"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性コンストラクターに渡されたアセンブリ名は、厳密な名前のアセンブリを識別しますが、`PublicKey` 属性を含みません。</span><span class="sxs-lookup"><span data-stu-id="54a2b-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>

 <span data-ttu-id="54a2b-106">**エラー ID:** BC31535</span><span class="sxs-lookup"><span data-stu-id="54a2b-106">**Error ID:** BC31535</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="54a2b-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="54a2b-107">To correct this error</span></span>

1. <span data-ttu-id="54a2b-108">厳密な名前のフレンド アセンブリの公開キーを調べます。</span><span class="sxs-lookup"><span data-stu-id="54a2b-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="54a2b-109">`PublicKey` 属性を使用して <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性コンストラクターに渡されるアセンブリ名の一部として、公開キーを含めます。</span><span class="sxs-lookup"><span data-stu-id="54a2b-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="54a2b-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="54a2b-110">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="54a2b-111">フレンド アセンブリ</span><span class="sxs-lookup"><span data-stu-id="54a2b-111">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
