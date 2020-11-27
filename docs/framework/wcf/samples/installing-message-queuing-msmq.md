---
title: メッセージ キュー (MSMQ) のインストール
description: 1回限りのセットアップ手順の一部として、WFC サンプルで使用するメッセージキュー4.0 とメッセージキュー3.0 をインストールする方法について説明します。
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: bf33a5cd899bf2d7ef4947c51ac1723c8eb80c29
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281873"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="45b1f-103">メッセージ キュー (MSMQ) のインストール</span><span class="sxs-lookup"><span data-stu-id="45b1f-103">Installing Message Queuing (MSMQ)</span></span>

<span data-ttu-id="45b1f-104">メッセージ キュー 4.0 およびメッセージ キュー 3.0 をインストールする方法を次の手順に示します。</span><span class="sxs-lookup"><span data-stu-id="45b1f-104">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45b1f-105">Windows XP および Windows Server 2003 では、メッセージキュー4.0 は使用できません。</span><span class="sxs-lookup"><span data-stu-id="45b1f-105">Message Queuing 4.0 is not available in Windows XP and Windows Server 2003.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="45b1f-106">Windows Server 2008 または Windows Server 2008 R2 にメッセージ キュー 4.0 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="45b1f-106">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="45b1f-107">サーバーマネージャーで、[ **機能**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45b1f-107">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="45b1f-108">右側のウィンドウの [機能の **概要**] で、[ **機能の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45b1f-108">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="45b1f-109">結果のウィンドウで、[ **メッセージキュー**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="45b1f-109">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="45b1f-110">[ **メッセージキューサービス**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="45b1f-110">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="45b1f-111">[ **ディレクトリサービスの統合** ] (ドメインに参加しているコンピューターの場合) をクリックし、[ **HTTP サポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45b1f-111">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="45b1f-112">[ **次へ**] をクリックし、[ **インストール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45b1f-112">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="45b1f-113">Windows 7 または Windows Vista にメッセージ キュー 4.0 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="45b1f-113">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="45b1f-114">**[コントロール パネル]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="45b1f-114">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="45b1f-115">[ **プログラム** ] をクリックし、[ **プログラムと機能**] で [ **Windows の機能の有効化または無効化**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45b1f-115">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="45b1f-116">[Microsoft Message Queue (MSMQ) Server]、[Microsoft Message Queue (MSMQ) Server Core] の順に展開して、インストールする次のメッセージ キュー機能のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="45b1f-116">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="45b1f-117">[MSMQ Active Directory Domain Services Integration] (ドメインに参加するコンピューターの場合)</span><span class="sxs-lookup"><span data-stu-id="45b1f-117">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="45b1f-118">[MSMQ HTTP サポート]</span><span class="sxs-lookup"><span data-stu-id="45b1f-118">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="45b1f-119">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45b1f-119">Click **OK**.</span></span>  
  
5. <span data-ttu-id="45b1f-120">コンピューターの再起動を求めるメッセージが表示されたら、[ **OK** ] をクリックしてインストールを完了します。</span><span class="sxs-lookup"><span data-stu-id="45b1f-120">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="45b1f-121">Windows XP および Windows Server 2003 にメッセージ キュー 3.0 をインストールするには</span><span class="sxs-lookup"><span data-stu-id="45b1f-121">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="45b1f-122">**[コントロール パネル]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="45b1f-122">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="45b1f-123">[ **プログラムの追加と削除** ] をクリックし、[ **Windows コンポーネントの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45b1f-123">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="45b1f-124">[メッセージキュー] を選択し、[ **詳細**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45b1f-124">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="45b1f-125">Windows Server 2003 を実行している場合は、[アプリケーションサーバー] を選択してメッセージキューにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="45b1f-125">If you are running Windows Server 2003, select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="45b1f-126">詳細ページで、[MSMQ HTTP サポート] オプションが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="45b1f-126">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="45b1f-127">[ **OK** ] をクリックして詳細ページを終了し、[ **次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="45b1f-127">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="45b1f-128">インストールを完了します。</span><span class="sxs-lookup"><span data-stu-id="45b1f-128">Complete the installation.</span></span>  
  
6. <span data-ttu-id="45b1f-129">コンピューターの再起動を求めるメッセージが表示されたら、[ **OK** ] をクリックしてインストールを完了します。</span><span class="sxs-lookup"><span data-stu-id="45b1f-129">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45b1f-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="45b1f-130">See also</span></span>

- [<span data-ttu-id="45b1f-131">セットアップ手順</span><span class="sxs-lookup"><span data-stu-id="45b1f-131">Set-Up Instructions</span></span>](set-up-instructions.md)
