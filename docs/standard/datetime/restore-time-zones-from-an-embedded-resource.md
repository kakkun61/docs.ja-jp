---
title: '方法: 埋め込みリソースからタイム ゾーンを復元する'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], deserializing
- time zones [.NET], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
ms.openlocfilehash: a1302f595a0907103bae2695e703e5af6da660a7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817667"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="0fc05-102">方法: 埋め込みリソースからタイム ゾーンを復元する</span><span class="sxs-lookup"><span data-stu-id="0fc05-102">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="0fc05-103">このトピックでは、リソースファイルに保存されているタイムゾーンを復元する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0fc05-103">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="0fc05-104">タイムゾーンの保存に関する情報および手順については、「 [方法: 埋め込みリソースにタイムゾーンを保存する](save-time-zones-to-an-embedded-resource.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fc05-104">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="0fc05-105">埋め込みリソースから TimeZoneInfo オブジェクトを逆シリアル化するには</span><span class="sxs-lookup"><span data-stu-id="0fc05-105">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="0fc05-106">取得するタイムゾーンがカスタムタイムゾーンでない場合は、メソッドを使用してインスタンス化し <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="0fc05-106">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="0fc05-107"><xref:System.Resources.ResourceManager>埋め込みリソースファイルの完全修飾名と、リソースファイルを含むアセンブリへの参照を渡すことによって、オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="0fc05-107">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="0fc05-108">埋め込みリソースファイルの完全修飾名を特定できない場合は、 [Ildasm.exe (IL 逆アセンブラー)](../../framework/tools/ildasm-exe-il-disassembler.md) を使用してアセンブリのマニフェストを確認します。</span><span class="sxs-lookup"><span data-stu-id="0fc05-108">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="0fc05-109">`.mresource`リソースを識別するエントリ。</span><span class="sxs-lookup"><span data-stu-id="0fc05-109">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="0fc05-110">この例では、リソースの完全修飾名は `SerializeTimeZoneData.SerializedTimeZones` です。</span><span class="sxs-lookup"><span data-stu-id="0fc05-110">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="0fc05-111">リソースファイルが、タイムゾーンのインスタンス化コードを含む同じアセンブリに埋め込まれている場合は、 `static` (Visual Basic) メソッドを呼び出すことによって、そのファイルへの参照を取得でき `Shared` <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="0fc05-111">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="0fc05-112">メソッドの呼び出しが失敗した場合 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 、またはカスタムタイムゾーンをインスタンス化する場合は、メソッドを呼び出して、シリアル化されたタイムゾーンを含む文字列を取得し <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="0fc05-112">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="0fc05-113">メソッドを呼び出してタイムゾーンデータを逆シリアル化し <xref:System.TimeZoneInfo.FromSerializedString%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="0fc05-113">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="0fc05-114">例</span><span class="sxs-lookup"><span data-stu-id="0fc05-114">Example</span></span>

<span data-ttu-id="0fc05-115">次の例では、 <xref:System.TimeZoneInfo> 埋め込み .NET XML リソースファイルに格納されているオブジェクトを逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="0fc05-115">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="0fc05-116">このコード <xref:System.TimeZoneInfo> は、アプリケーションに必要なオブジェクトが存在することを確認するための例外処理を示しています。</span><span class="sxs-lookup"><span data-stu-id="0fc05-116">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="0fc05-117">まず、 <xref:System.TimeZoneInfo> メソッドを使用してレジストリからオブジェクトを取得することによって、オブジェクトのインスタンス化を試み <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="0fc05-117">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="0fc05-118">タイムゾーンをインスタンス化できない場合、コードは埋め込みリソースファイルからタイムゾーンを取得します。</span><span class="sxs-lookup"><span data-stu-id="0fc05-118">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="0fc05-119">カスタムタイムゾーン (メソッドを使用してインスタンス化されたタイムゾーン) のデータはレジストリに格納されないため、コードはを <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 呼び出して、 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 南極のタイムゾーンをインスタンス化しません。</span><span class="sxs-lookup"><span data-stu-id="0fc05-119">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="0fc05-120">代わりに、埋め込みリソースファイルをすぐに検索して、メソッドを呼び出す前にタイムゾーンのデータを含む文字列を取得し <xref:System.TimeZoneInfo.FromSerializedString%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="0fc05-120">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="0fc05-121">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="0fc05-121">Compiling the code</span></span>

<span data-ttu-id="0fc05-122">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0fc05-122">This example requires:</span></span>

- <span data-ttu-id="0fc05-123">System.Windows.Forms.dll および System.Core.dll への参照をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="0fc05-123">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="0fc05-124">次の名前空間がインポートされます。</span><span class="sxs-lookup"><span data-stu-id="0fc05-124">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="0fc05-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="0fc05-125">See also</span></span>

- [<span data-ttu-id="0fc05-126">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="0fc05-126">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="0fc05-127">タイム ゾーンの概要</span><span class="sxs-lookup"><span data-stu-id="0fc05-127">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="0fc05-128">方法: 埋め込みリソースにタイムゾーンを保存する</span><span class="sxs-lookup"><span data-stu-id="0fc05-128">How to: Save time zones to an embedded resource</span></span>](save-time-zones-to-an-embedded-resource.md)
