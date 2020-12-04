---
title: .NET IoT ライブラリを使用して IoT デバイス用のアプリを開発する
description: .NET を使用して IoT デバイスとシナリオ用のアプリケーションを作成する方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: overview
ms.prod: dotnet
ms.openlocfilehash: c3d05ec5b05780f91404c3c27e91bcd602b0faeb
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "96594030"
---
# <a name="develop-apps-for-iot-devices-with-the-net-iot-libraries"></a><span data-ttu-id="e9d85-103">.NET IoT ライブラリを使用して IoT デバイス用のアプリを開発する</span><span class="sxs-lookup"><span data-stu-id="e9d85-103">Develop apps for IoT devices with the .NET IoT Libraries</span></span>

<span data-ttu-id="e9d85-104">.NET は、さまざまなプラットフォームとアーキテクチャで動作します。</span><span class="sxs-lookup"><span data-stu-id="e9d85-104">.NET runs on a variety of platforms and architectures.</span></span> <span data-ttu-id="e9d85-105">Raspberry Pi や Hummingboard など、一般的なモノのインターネット (IoT) ボードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e9d85-105">Common Internet of things (IoT) boards, such as Raspberry Pi and Hummingboard, are supported.</span></span> <span data-ttu-id="e9d85-106">IoT アプリは通常、センサー、アナログ-デジタルコンバーター、および LCD デバイスといった特殊なハードウェアと対話します。</span><span class="sxs-lookup"><span data-stu-id="e9d85-106">IoT apps typically interact with specialized hardware, such as sensors, analog-to-digital converters, and LCD devices.</span></span> <span data-ttu-id="e9d85-107">.NET IoT ライブラリを使用すると、これらのシナリオを実現できます。</span><span class="sxs-lookup"><span data-stu-id="e9d85-107">The .NET IoT Libraries enable these scenarios.</span></span>

## <a name="video-overview"></a><span data-ttu-id="e9d85-108">ビデオの概要</span><span class="sxs-lookup"><span data-stu-id="e9d85-108">Video overview</span></span>

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/IoT-101/Intro-to-IOT-with-NET-Core-1-of-9/player]

## <a name="libraries"></a><span data-ttu-id="e9d85-109">ライブラリ</span><span class="sxs-lookup"><span data-stu-id="e9d85-109">Libraries</span></span>

<span data-ttu-id="e9d85-110">.NET IoT ライブラリは、次の2つの NuGet パッケージで構成されています。</span><span class="sxs-lookup"><span data-stu-id="e9d85-110">The .NET IoT Libraries are composed of two NuGet packages:</span></span>

- <span data-ttu-id="e9d85-111">[System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="e9d85-111">[System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio/) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="e9d85-112">[Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/) <span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="e9d85-112">[Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings/) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>

### <a name="systemdevicegpio"></a><span data-ttu-id="e9d85-113">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="e9d85-113">System.Device.Gpio</span></span>

<span data-ttu-id="e9d85-114">`System.Device.Gpio` では、デバイスを制御するために低レベルのハードウェア pin と対話するためのさまざまなプロトコルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e9d85-114">`System.Device.Gpio` supports a variety of protocols for interacting with low-level hardware pins to control devices.</span></span> <span data-ttu-id="e9d85-115">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e9d85-115">These include:</span></span>

- <span data-ttu-id="e9d85-116">汎用入出力 (GPIO)</span><span class="sxs-lookup"><span data-stu-id="e9d85-116">General-purpose I/O (GPIO)</span></span>
- <span data-ttu-id="e9d85-117">Inter-Integrated 回線 (I2C)</span><span class="sxs-lookup"><span data-stu-id="e9d85-117">Inter-Integrated Circuit (I2C)</span></span>
- <span data-ttu-id="e9d85-118">シリアル周辺機器インターフェイス (SPI)</span><span class="sxs-lookup"><span data-stu-id="e9d85-118">Serial Peripheral Interface (SPI)</span></span>
- <span data-ttu-id="e9d85-119">パルス幅の変調 (PWM)</span><span class="sxs-lookup"><span data-stu-id="e9d85-119">Pulse Width Modulation (PWM)</span></span>
- <span data-ttu-id="e9d85-120">シリアル ポート</span><span class="sxs-lookup"><span data-stu-id="e9d85-120">Serial port</span></span>

### <a name="iotdevicebindings"></a><span data-ttu-id="e9d85-121">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="e9d85-121">Iot.Device.Bindings</span></span>

<span data-ttu-id="e9d85-122">`Iot.Device.Bindings`パッケージ:</span><span class="sxs-lookup"><span data-stu-id="e9d85-122">The `Iot.Device.Bindings` package:</span></span>

* <span data-ttu-id="e9d85-123">System.string [device bindings](https://github.com/dotnet/iot/blob/master/src/devices/README.md)を <span class="docon docon-navigate-external x-hidden-focus"></span> ラップすることによってアプリ開発を効率化するためのデバイスのバインドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e9d85-123">Contains [device bindings](https://github.com/dotnet/iot/blob/master/src/devices/README.md) <span class="docon docon-navigate-external x-hidden-focus"></span> to streamline app development by wrapping System.Device.Gpio.</span></span>
* <span data-ttu-id="e9d85-124">コミュニティでサポートされており、追加のバインドが継続的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="e9d85-124">Is community-supported, and additional bindings are added continually.</span></span>

<span data-ttu-id="e9d85-125">一般的に使用されるデバイスのバインドは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e9d85-125">Commonly used device bindings include:</span></span>

- <span data-ttu-id="e9d85-126">[文字 lcd-lcd 文字ディスプレイ](https://github.com/dotnet/iot/tree/master/src/devices/CharacterLcd)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="e9d85-126">[CharacterLcd - LCD character display](https://github.com/dotnet/iot/tree/master/src/devices/CharacterLcd) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="e9d85-127">[SN74HC595-8 ビットシフトレジスタ](https://github.com/dotnet/iot/tree/master/src/devices/Sn74hc595)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="e9d85-127">[SN74HC595 - 8-bit shift register](https://github.com/dotnet/iot/tree/master/src/devices/Sn74hc595) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="e9d85-128">[BrickPi3](https://github.com/dotnet/iot/tree/master/src/devices/BrickPi3)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="e9d85-128">[BrickPi3](https://github.com/dotnet/iot/tree/master/src/devices/BrickPi3) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="e9d85-129">[Max7219-LED マトリックスドライバー](https://github.com/dotnet/iot/tree/master/src/devices/Max7219)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="e9d85-129">[Max7219 - LED Matrix driver](https://github.com/dotnet/iot/tree/master/src/devices/Max7219) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
- <span data-ttu-id="e9d85-130">[RGBLedMatrix-RGB LED マトリックス](https://github.com/dotnet/iot/tree/master/src/devices/RGBLedMatrix)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="e9d85-130">[RGBLedMatrix - RGB LED Matrix](https://github.com/dotnet/iot/tree/master/src/devices/RGBLedMatrix) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="e9d85-131">サポートされるオペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="e9d85-131">Supported operating systems</span></span>

<span data-ttu-id="e9d85-132">`System.Device.Gpio` は、ARM/ARM64 と Windows 10 IoT Core をサポートするほとんどのバージョンの Linux でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e9d85-132">`System.Device.Gpio` is supported on most versions of Linux that support ARM/ARM64 and Windows 10 IoT Core.</span></span>

> [!TIP]
> <span data-ttu-id="e9d85-133">Raspberry Pi では、 [Raspberry PI OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) <span class="docon docon-navigate-external x-hidden-focus"></span> (旧称 Raspbian) を使用することをお勧めします。  </span><span class="sxs-lookup"><span data-stu-id="e9d85-133">For Raspberry Pi, [Raspberry Pi OS](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)  <span class="docon docon-navigate-external x-hidden-focus"></span> (formerly Raspbian) is recommended.</span></span>

## <a name="supported-hardware-platforms"></a><span data-ttu-id="e9d85-134">サポートされているハードウェアプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="e9d85-134">Supported hardware platforms</span></span>

<span data-ttu-id="e9d85-135">`System.Device.Gpio` は、ほとんどのシングルボードプラットフォームと互換性があります。</span><span class="sxs-lookup"><span data-stu-id="e9d85-135">`System.Device.Gpio` is compatible with most single-board platforms.</span></span> <span data-ttu-id="e9d85-136">推奨されるプラットフォームは Raspberry Pi (2 以上) と Hummingboard です。</span><span class="sxs-lookup"><span data-stu-id="e9d85-136">Recommended platforms are Raspberry Pi (2 and greater) and Hummingboard.</span></span> <span data-ttu-id="e9d85-137">互換性があるとわかっているその他のプラットフォームは、BeagleBoard と OID ID です。</span><span class="sxs-lookup"><span data-stu-id="e9d85-137">Other platforms known to be compatible are BeagleBoard and ODROID.</span></span>

<span data-ttu-id="e9d85-138">PC プラットフォームは、USB から SPI/I2C ブリッジを使用することによってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e9d85-138">PC platforms are supported via the use of a USB to SPI/I2C bridge.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9d85-139">.NET は、Raspberry Pi 2 より前の Raspberry Pi 0 および Raspberry Pi デバイスを含む、ARMv6 アーキテクチャデバイスではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e9d85-139">.NET is not supported on ARMv6 architecture devices, including Raspberry Pi Zero and Raspberry Pi devices prior to Raspberry Pi 2.</span></span>

## <a name="resources"></a><span data-ttu-id="e9d85-140">リソース</span><span class="sxs-lookup"><span data-stu-id="e9d85-140">Resources</span></span>

- <span data-ttu-id="e9d85-141">[Github の .Net IoT ライブラリ](https://github.com/dotnet/iot)<span class="docon docon-navigate-external x-hidden-focus"></span></span><span class="sxs-lookup"><span data-stu-id="e9d85-141">[.NET IoT Libraries on Github](https://github.com/dotnet/iot) <span class="docon docon-navigate-external x-hidden-focus"></span></span></span>
