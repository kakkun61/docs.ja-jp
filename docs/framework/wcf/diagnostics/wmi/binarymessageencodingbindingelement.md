---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: eb174d12731d7f1bc78f4d709cf043daf2346bd2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269796"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="b4c33-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="b4c33-102">BinaryMessageEncodingBindingElement</span></span>

<span data-ttu-id="b4c33-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="b4c33-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4c33-104">構文</span><span class="sxs-lookup"><span data-stu-id="b4c33-104">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b4c33-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b4c33-105">Methods</span></span>  

 <span data-ttu-id="b4c33-106">BinaryMessageEncodingBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="b4c33-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b4c33-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b4c33-107">Properties</span></span>  

 <span data-ttu-id="b4c33-108">BinaryMessageEncodingBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="b4c33-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="b4c33-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="b4c33-109">MaxReadPoolSize</span></span>  

 <span data-ttu-id="b4c33-110">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="b4c33-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="b4c33-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="b4c33-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4c33-112">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="b4c33-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="b4c33-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="b4c33-113">MaxSessionSize</span></span>  

 <span data-ttu-id="b4c33-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="b4c33-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="b4c33-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="b4c33-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4c33-116">エンコーディングに使用するバッファーのサイズ (バイト単位) を指定する値です。</span><span class="sxs-lookup"><span data-stu-id="b4c33-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="b4c33-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="b4c33-117">MaxWritePoolSize</span></span>  

 <span data-ttu-id="b4c33-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="b4c33-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="b4c33-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="b4c33-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4c33-120">新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="b4c33-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="b4c33-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="b4c33-121">ReaderQuotas</span></span>  

 <span data-ttu-id="b4c33-122">データ型 : XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="b4c33-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="b4c33-123">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="b4c33-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4c33-124">リーダのクォータ。</span><span class="sxs-lookup"><span data-stu-id="b4c33-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4c33-125">要件</span><span class="sxs-lookup"><span data-stu-id="b4c33-125">Requirements</span></span>  
  
|<span data-ttu-id="b4c33-126">MOF</span><span class="sxs-lookup"><span data-stu-id="b4c33-126">MOF</span></span>|<span data-ttu-id="b4c33-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="b4c33-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b4c33-128">名前空間</span><span class="sxs-lookup"><span data-stu-id="b4c33-128">Namespace</span></span>|<span data-ttu-id="b4c33-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="b4c33-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4c33-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4c33-130">See also</span></span>

- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
