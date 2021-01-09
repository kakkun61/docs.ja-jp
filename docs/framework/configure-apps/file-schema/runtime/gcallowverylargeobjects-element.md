---
title: gcAllowVeryLargeObjects 要素
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 1e54b0780ffb5bbe81ab1be2b376ff7a038ee05c
ms.sourcegitcommit: 0273f8845eb1ea8de64086bef2271b4f22182c91
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2021
ms.locfileid: "98058130"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="3f581-102">\<gcAllowVeryLargeObjects> 要素</span><span class="sxs-lookup"><span data-stu-id="3f581-102">\<gcAllowVeryLargeObjects> element</span></span>

<span data-ttu-id="3f581-103">64 ビット プラットフォームで、合計サイズが 2 GB (ギガバイト) を超える配列を有効にします。</span><span class="sxs-lookup"><span data-stu-id="3f581-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a><span data-ttu-id="3f581-104">構文</span><span class="sxs-lookup"><span data-stu-id="3f581-104">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects enabled="true|false" />  
```  
  
## <a name="attributes"></a><span data-ttu-id="3f581-105">属性</span><span class="sxs-lookup"><span data-stu-id="3f581-105">Attributes</span></span>
  
|<span data-ttu-id="3f581-106">属性</span><span class="sxs-lookup"><span data-stu-id="3f581-106">Attribute</span></span>|<span data-ttu-id="3f581-107">説明</span><span class="sxs-lookup"><span data-stu-id="3f581-107">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3f581-108">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="3f581-108">Required attribute.</span></span><br /><br /> <span data-ttu-id="3f581-109">64 ビット プラットフォームで、合計サイズが 2 GB (ギガバイト) を超える配列が有効であるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3f581-109">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="3f581-110">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="3f581-110">enabled attribute</span></span>  
  
|<span data-ttu-id="3f581-111">[値]</span><span class="sxs-lookup"><span data-stu-id="3f581-111">Value</span></span>|<span data-ttu-id="3f581-112">説明</span><span class="sxs-lookup"><span data-stu-id="3f581-112">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="3f581-113">合計サイズが 2 GB を超える配列は有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="3f581-113">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="3f581-114">これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="3f581-114">This is the default.</span></span>|  
|`true`|<span data-ttu-id="3f581-115">64 ビット プラットフォームで、合計サイズが 2 GB を超える配列が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="3f581-115">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="3f581-116">子要素</span><span class="sxs-lookup"><span data-stu-id="3f581-116">Child elements</span></span>  

<span data-ttu-id="3f581-117">なし。</span><span class="sxs-lookup"><span data-stu-id="3f581-117">None.</span></span>  
  
## <a name="parent-elements"></a><span data-ttu-id="3f581-118">親要素</span><span class="sxs-lookup"><span data-stu-id="3f581-118">Parent elements</span></span>
  
|<span data-ttu-id="3f581-119">要素</span><span class="sxs-lookup"><span data-stu-id="3f581-119">Element</span></span>|<span data-ttu-id="3f581-120">説明</span><span class="sxs-lookup"><span data-stu-id="3f581-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3f581-121">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="3f581-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3f581-122">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="3f581-122">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f581-123">解説</span><span class="sxs-lookup"><span data-stu-id="3f581-123">Remarks</span></span>  

 <span data-ttu-id="3f581-124">アプリケーション構成ファイルで次の要素を使用すると 2 GB を超えるサイズの配列が有効になりますが、オブジェクトのサイズや配列のサイズに対するその他の制限は変更されません。</span><span class="sxs-lookup"><span data-stu-id="3f581-124">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="3f581-125">配列の要素の最大数は <xref:System.UInt32.MaxValue?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="3f581-125">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="3f581-126">1つの次元の最大サイズは、バイト配列と1バイト構造の配列の場合は 2147483591 (0x7FFFFFC7)、他の型を含む配列の場合は 2146435071 (0X7FEFFFFF) です。</span><span class="sxs-lookup"><span data-stu-id="3f581-126">The maximum size in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for arrays containing other types.</span></span>  
  
- <span data-ttu-id="3f581-127">文字列およびその他の非配列オブジェクトの最大サイズは変更されません。</span><span class="sxs-lookup"><span data-stu-id="3f581-127">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="3f581-128">この機能を有効にする前に、すべての配列のサイズが 2 GB よりも小さいことを前提としたアンセーフ コードがアプリケーションに含まれていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f581-128">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="3f581-129">たとえば、配列をバッファーとして使用するアンセーフコードは、配列が 2 GB を超えることを想定して記述されている場合、バッファーオーバーランの影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3f581-129">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it's written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f581-130">例</span><span class="sxs-lookup"><span data-stu-id="3f581-130">Example</span></span>  

 <span data-ttu-id="3f581-131">アプリケーションでこの機能を有効にする方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="3f581-131">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="3f581-132">サポート対象 :</span><span class="sxs-lookup"><span data-stu-id="3f581-132">Supported in</span></span>

<span data-ttu-id="3f581-133">.NET Framework 4.5 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="3f581-133">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="3f581-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f581-134">See also</span></span>

- [<span data-ttu-id="3f581-135">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="3f581-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3f581-136">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="3f581-136">Configuration File Schema</span></span>](../index.md)
