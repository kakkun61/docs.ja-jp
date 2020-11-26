---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: b4d8503543c93d0112fc39e4b2dba5434bc56472
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237405"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="92248-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="92248-102">MtomMessageEncodingBindingElement</span></span>

<span data-ttu-id="92248-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="92248-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92248-104">構文</span><span class="sxs-lookup"><span data-stu-id="92248-104">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="92248-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="92248-105">Methods</span></span>  

 <span data-ttu-id="92248-106">MtomMessageEncodingBindingElement クラスで定義されているメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="92248-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="92248-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="92248-107">Properties</span></span>  

 <span data-ttu-id="92248-108">MtomMessageEncodingBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="92248-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="92248-109">エンコード</span><span class="sxs-lookup"><span data-stu-id="92248-109">Encoding</span></span>  

 <span data-ttu-id="92248-110">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="92248-110">Data type: string</span></span>  
  
 <span data-ttu-id="92248-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="92248-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="92248-112">バインディングでメッセージの送信に使用される文字セット エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="92248-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="92248-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="92248-113">MaxReadPoolSize</span></span>  

 <span data-ttu-id="92248-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="92248-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="92248-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="92248-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="92248-116">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="92248-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="92248-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="92248-117">MaxWritePoolSize</span></span>  

 <span data-ttu-id="92248-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="92248-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="92248-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="92248-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="92248-120">新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="92248-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="92248-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="92248-121">ReaderQuotas</span></span>  

 <span data-ttu-id="92248-122">データ型 : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="92248-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="92248-123">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="92248-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="92248-124">リーダのクォータ。</span><span class="sxs-lookup"><span data-stu-id="92248-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92248-125">要件</span><span class="sxs-lookup"><span data-stu-id="92248-125">Requirements</span></span>  
  
|<span data-ttu-id="92248-126">MOF</span><span class="sxs-lookup"><span data-stu-id="92248-126">MOF</span></span>|<span data-ttu-id="92248-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="92248-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="92248-128">名前空間</span><span class="sxs-lookup"><span data-stu-id="92248-128">Namespace</span></span>|<span data-ttu-id="92248-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="92248-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92248-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="92248-130">See also</span></span>

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
