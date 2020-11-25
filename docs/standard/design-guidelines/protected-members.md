---
title: プロテクト メンバー
ms.date: 10/22/2008
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: a6f36ac4f994fdc3211cac619cc0b20f7b0335b1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730956"
---
# <a name="protected-members"></a><span data-ttu-id="83899-102">プロテクト メンバー</span><span class="sxs-lookup"><span data-stu-id="83899-102">Protected Members</span></span>

<span data-ttu-id="83899-103">保護されたメンバー自体が拡張機能を提供することはありませんが、より強力なサブクラス化によって、拡張性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="83899-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="83899-104">これらを使用すると、メインのパブリックインターフェイスを不必要に複雑にすることなく、高度なカスタマイズオプションを公開できます。</span><span class="sxs-lookup"><span data-stu-id="83899-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>

 <span data-ttu-id="83899-105">フレームワークデザイナーは、保護されたメンバーに注意する必要があります。これは、"protected" という名前のセキュリティが誤った意味を持つ可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="83899-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="83899-106">だれでも、封印されていないクラスをサブクラス化し、保護されたメンバーにアクセスできるので、パブリックメンバーに使用される同じ防御的なコーディング方法がすべてプロテクトメンバーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="83899-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>

 <span data-ttu-id="83899-107">高度なカスタマイズには、保護されたメンバーの使用を検討✔️。</span><span class="sxs-lookup"><span data-stu-id="83899-107">✔️ CONSIDER using protected members for advanced customization.</span></span>

 <span data-ttu-id="83899-108">✔️は、セキュリティ、ドキュメント、互換性分析のために、封印されていないクラスのプロテクトメンバーをパブリックとして扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="83899-108">✔️ DO treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>

 <span data-ttu-id="83899-109">だれでもクラスを継承し、保護されたメンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="83899-109">Anyone can inherit from a class and access the protected members.</span></span>

 <span data-ttu-id="83899-110">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="83899-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="83899-111">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="83899-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="83899-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="83899-112">See also</span></span>

- [<span data-ttu-id="83899-113">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="83899-113">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="83899-114">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="83899-114">Designing for Extensibility</span></span>](designing-for-extensibility.md)
