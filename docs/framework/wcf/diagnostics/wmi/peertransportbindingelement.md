---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: ae6a3448896cb206bce8867daf7104c3e484ecc8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269016"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="93478-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="93478-102">PeerTransportBindingElement</span></span>

<span data-ttu-id="93478-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="93478-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93478-104">構文</span><span class="sxs-lookup"><span data-stu-id="93478-104">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="93478-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="93478-105">Methods</span></span>  

 <span data-ttu-id="93478-106">PeerTransportBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="93478-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="93478-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="93478-107">Properties</span></span>  

 <span data-ttu-id="93478-108">PeerTransportBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="93478-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="93478-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="93478-109">ListenIPAddress</span></span>  

 <span data-ttu-id="93478-110">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="93478-110">Data type: string</span></span>  
  
 <span data-ttu-id="93478-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="93478-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93478-112">ピア ノードがメッセージをリッスンする IP アドレスです。</span><span class="sxs-lookup"><span data-stu-id="93478-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="93478-113">Port</span><span class="sxs-lookup"><span data-stu-id="93478-113">Port</span></span>  

 <span data-ttu-id="93478-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="93478-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="93478-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="93478-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93478-116">このバインディングがピア チャネル メッセージを処理するネットワーク インターフェイス ポートです。</span><span class="sxs-lookup"><span data-stu-id="93478-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="93478-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="93478-117">Security</span></span>  

 <span data-ttu-id="93478-118">データ型 : PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="93478-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="93478-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="93478-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93478-120">ピア トランスポートのセキュリティ設定です。</span><span class="sxs-lookup"><span data-stu-id="93478-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93478-121">要件</span><span class="sxs-lookup"><span data-stu-id="93478-121">Requirements</span></span>  
  
|<span data-ttu-id="93478-122">MOF</span><span class="sxs-lookup"><span data-stu-id="93478-122">MOF</span></span>|<span data-ttu-id="93478-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="93478-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="93478-124">名前空間</span><span class="sxs-lookup"><span data-stu-id="93478-124">Namespace</span></span>|<span data-ttu-id="93478-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="93478-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93478-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="93478-126">See also</span></span>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
