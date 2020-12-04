---
ms.openlocfilehash: 60e326af0d956ceb63b32e5d3ec2436fe09a7005
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "96594019"
---
<span data-ttu-id="1c14b-101">[SFTP クライアントを使用して](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md)、開発用コンピューターの発行場所から Raspberry Pi 上の新しいフォルダーにファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="1c14b-101">[Using an SFTP client](https://www.raspberrypi.org/documentation/remote-access/ssh/sftp.md), copy the files from the publish location on the development computer to a new folder on the Raspberry Pi.</span></span>

<span data-ttu-id="1c14b-102">たとえば、コマンドを使用し `scp` て開発用コンピューターから Raspberry Pi にファイルをコピーするには、コマンドプロンプトを開き、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1c14b-102">For example, to use the `scp` command to copy files from the development computer to your Raspberry Pi, open a command prompt and execute the following:</span></span>

```console
scp -r /publish-location/* pi@raspberrypi:/home/pi/deployment-location/
```

<span data-ttu-id="1c14b-103">この場合、</span><span class="sxs-lookup"><span data-stu-id="1c14b-103">Where:</span></span>

- <span data-ttu-id="1c14b-104">`-r`オプションは、 `scp` ファイルを再帰的にコピーするように指示します。</span><span class="sxs-lookup"><span data-stu-id="1c14b-104">The `-r` option instructs `scp` to copy files recursively.</span></span>
- <span data-ttu-id="1c14b-105">*また* は、前の手順で発行したフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="1c14b-105">*/publish-location/* is the folder you published to in the previous step.</span></span>
- <span data-ttu-id="1c14b-106">`pi@raspberypi` は、という形式のユーザー名とホスト名です `<username>@<hostname>` 。</span><span class="sxs-lookup"><span data-stu-id="1c14b-106">`pi@raspberypi` is the user and host names in the format `<username>@<hostname>`.</span></span>
- <span data-ttu-id="1c14b-107">*/home/pi/deployment-location/* は、Raspberry pi 上の新しいフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="1c14b-107">*/home/pi/deployment-location/* is the new folder on the Raspberry Pi.</span></span>

> [!TIP]
> <span data-ttu-id="1c14b-108">最新バージョンの Windows には、インストール済みのが含まれている OpenSSH があり `scp` ます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-108">Recent versions of Windows have OpenSSH, which includes `scp`, pre-installed.</span></span>
