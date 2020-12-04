---
title: センサーから環境条件を読み取る
description: .NET IoT ライブラリを使用して termperature、気圧、湿度を読み取る方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/14/2020
ms.topic: tutorial
ms.prod: dotnet
ms.openlocfilehash: 1270e7629e9afc12b1d76d260d4b8b51428f1040
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96594151"
---
# <a name="read-environmental-conditions-from-a-sensor"></a><span data-ttu-id="23b5a-103">センサーから環境条件を読み取る</span><span class="sxs-lookup"><span data-stu-id="23b5a-103">Read environmental conditions from a sensor</span></span>

<span data-ttu-id="23b5a-104">IoT デバイスの最も一般的なシナリオの1つは、環境の状態の検出です。</span><span class="sxs-lookup"><span data-stu-id="23b5a-104">One of the most common scenarios for IoT devices is detection of environmental conditions.</span></span> <span data-ttu-id="23b5a-105">温度、湿度、気圧などを監視するために、さまざまなセンサーを利用できます。</span><span class="sxs-lookup"><span data-stu-id="23b5a-105">A variety of sensors are available to monitor temperature, humidity, barometric pressure, and more.</span></span>

<span data-ttu-id="23b5a-106">このトピックでは、.NET を使用してセンサーから環境の状態を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="23b5a-106">In this topic, you will use .NET to read environmental conditions from a sensor.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="23b5a-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="23b5a-107">Prerequisites</span></span>

- [!INCLUDE [prereq-rpi](../includes/prereq-rpi.md)]
- <span data-ttu-id="23b5a-108">[BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) <span class="docon docon-navigate-external x-hidden-focus"></span> 湿度/気圧/温度センサーのブレイクアウト</span><span class="sxs-lookup"><span data-stu-id="23b5a-108">[BME280](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout) <span class="docon docon-navigate-external x-hidden-focus"></span> humidity/barometric pressure/temperature sensor breakout</span></span>
- <span data-ttu-id="23b5a-109">ジャンパー ワイヤ</span><span class="sxs-lookup"><span data-stu-id="23b5a-109">Jumper wires</span></span>
- <span data-ttu-id="23b5a-110">ブレッドボード (省略可能)</span><span class="sxs-lookup"><span data-stu-id="23b5a-110">Breadboard (optional)</span></span>
- <span data-ttu-id="23b5a-111">Raspberry Pi GPIO ブレイクボードボード (オプション)</span><span class="sxs-lookup"><span data-stu-id="23b5a-111">Raspberry Pi GPIO breakout board (optional)</span></span>
- [!INCLUDE [tutorial-prereq-dotnet](../includes/tutorial-prereq-dotnet.md)]

> [!IMPORTANT]
> <span data-ttu-id="23b5a-112">BME280 テクニカルの製造元は多数あります。</span><span class="sxs-lookup"><span data-stu-id="23b5a-112">There are many manufacturers of BME280 breakouts.</span></span> <span data-ttu-id="23b5a-113">ほとんどの設計は類似しており、製造元は機能に違いがないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="23b5a-113">Most designs are similar, and the manufacturer shouldn't make any difference to the functionality.</span></span> <span data-ttu-id="23b5a-114">このチュートリアルでは、バリエーションの考慮を試みます。</span><span class="sxs-lookup"><span data-stu-id="23b5a-114">This tutorial attempts to account for variations.</span></span> <span data-ttu-id="23b5a-115">BME280 のブレイクアウトに Inter-Integrated サーキット (I2C) インターフェイスが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="23b5a-115">Ensure your BME280 breakout includes an Inter-Integrated Circuit (I2C) interface.</span></span>

[!INCLUDE [prepare-pi-i2c](../includes/prepare-pi-i2c.md)]

## <a name="prepare-the-hardware"></a><span data-ttu-id="23b5a-116">ハードウェアを準備する</span><span class="sxs-lookup"><span data-stu-id="23b5a-116">Prepare the hardware</span></span>

<span data-ttu-id="23b5a-117">ハードウェアコンポーネントを使用して、次の図に示すように回線を構築します。</span><span class="sxs-lookup"><span data-stu-id="23b5a-117">Use the hardware components to build the circuit as depicted in the following diagram:</span></span>

:::image type="content" source="../media/rpi-bmp280_i2c-thumb.png" alt-text="Raspberry Pi から BME280 ブレイクボードボードへの接続を示す Fritzing 図" lightbox="../media/rpi-bmp280_i2c.png":::

<span data-ttu-id="23b5a-119">Raspberry Pi から BME280 ブレイクアウトへの接続を次に示します。</span><span class="sxs-lookup"><span data-stu-id="23b5a-119">The following are the connections from the Raspberry Pi to the BME280 breakout:</span></span>

- <span data-ttu-id="23b5a-120">3.3 v から VIN *または* 3v3 (赤で表示)</span><span class="sxs-lookup"><span data-stu-id="23b5a-120">3.3V to VIN *OR* 3V3 (shown in red)</span></span>
- <span data-ttu-id="23b5a-121">グランドから GND (黒)</span><span class="sxs-lookup"><span data-stu-id="23b5a-121">Ground to GND (black)</span></span>
- <span data-ttu-id="23b5a-122">SDA (GPIO 2) から SDI *または* SDA へ (ブルー)</span><span class="sxs-lookup"><span data-stu-id="23b5a-122">SDA (GPIO 2) to SDI *OR* SDA (blue)</span></span>
- <span data-ttu-id="23b5a-123">SCL (GPIO 3) から SCK *または* scl (オレンジ色)</span><span class="sxs-lookup"><span data-stu-id="23b5a-123">SCL (GPIO 3) to SCK *OR* SCL (orange)</span></span>

[!INCLUDE [tutorial-rpi-gpio](../includes/tutorial-rpi-gpio.md)]

[!INCLUDE [gpio-breakout](../includes/gpio-breakout.md)]

## <a name="create-the-app"></a><span data-ttu-id="23b5a-124">アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="23b5a-124">Create the app</span></span>

<span data-ttu-id="23b5a-125">お好みの開発環境で、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="23b5a-125">Complete the following steps in your preferred development environment:</span></span>

1. <span data-ttu-id="23b5a-126">[.NET CLI](../../core/tools/dotnet-new.md)または[Visual Studio](../../core/tutorials/with-visual-studio.md)を使用して、新しい .net コンソールアプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="23b5a-126">Create a new .NET Console App using either the [.NET CLI](../../core/tools/dotnet-new.md) or [Visual Studio](../../core/tutorials/with-visual-studio.md).</span></span> <span data-ttu-id="23b5a-127">*Sensortutorial* という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="23b5a-127">Name it *SensorTutorial*.</span></span>

    ```dotnetcli
    dotnet new console -o SensorTutorial
    ```

1. [!INCLUDE [tutorial-add-packages](../includes/tutorial-add-packages.md)]
1. <span data-ttu-id="23b5a-128">*Program.cs* の内容を次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="23b5a-128">Replace the contents of *Program.cs* with the following code:</span></span>

    :::code language="csharp" source="~/iot-samples/tutorials/SensorTutorial/Program.cs" :::

    <span data-ttu-id="23b5a-129">上記のコードにより、次のことが行われます。</span><span class="sxs-lookup"><span data-stu-id="23b5a-129">In the preceding code:</span></span>

    - <span data-ttu-id="23b5a-130">`i2cSettings` は、の新しいインスタンスに設定され `I2cConnectionSettings` ます。</span><span class="sxs-lookup"><span data-stu-id="23b5a-130">`i2cSettings` is set to a new instance of `I2cConnectionSettings`.</span></span> <span data-ttu-id="23b5a-131">コンストラクターは、パラメーターを1に設定し、 `busId` `deviceAddress` パラメーターをに設定し `Bme280.DefaultI2cAddress` ます。</span><span class="sxs-lookup"><span data-stu-id="23b5a-131">The constructor sets the `busId` parameter to 1 and the `deviceAddress` parameter to `Bme280.DefaultI2cAddress`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="23b5a-132">一部の BME280 のブレイクアウト製造元は、セカンダリアドレス値を使用します。</span><span class="sxs-lookup"><span data-stu-id="23b5a-132">Some BME280 breakout manufacturers use the secondary address value.</span></span> <span data-ttu-id="23b5a-133">これらのデバイスについては、を使用 `Bme280.SecondaryI2cAddress` します。</span><span class="sxs-lookup"><span data-stu-id="23b5a-133">For those devices, use `Bme280.SecondaryI2cAddress`.</span></span>

    - <span data-ttu-id="23b5a-134">[Using 宣言](../../csharp/whats-new/csharp-8.md#using-declarations)は、を `I2cDevice` 呼び出してを渡すことによって、のインスタンスを作成し `I2cDevice.Create` `i2cSettings` ます。</span><span class="sxs-lookup"><span data-stu-id="23b5a-134">A [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations) creates an instance of `I2cDevice` by calling `I2cDevice.Create` and passing in `i2cSettings`.</span></span> <span data-ttu-id="23b5a-135">これ `I2cDevice` は、I2C バスを表します。</span><span class="sxs-lookup"><span data-stu-id="23b5a-135">This `I2cDevice` represents the I2C bus.</span></span> <span data-ttu-id="23b5a-136">この `using` 宣言により、オブジェクトが破棄され、ハードウェアリソースが正常に解放されます。</span><span class="sxs-lookup"><span data-stu-id="23b5a-136">The `using` declaration ensures the object is disposed and hardware resources are released properly.</span></span>
    - <span data-ttu-id="23b5a-137">別 `using` の宣言によって、センサーを表すのインスタンスが作成さ `Bme280` れます。</span><span class="sxs-lookup"><span data-stu-id="23b5a-137">Another `using` declaration creates an instance of `Bme280` to represent the sensor.</span></span> <span data-ttu-id="23b5a-138">は、 `I2cDevice` コンストラクターで渡されます。</span><span class="sxs-lookup"><span data-stu-id="23b5a-138">The `I2cDevice` is passed in the constructor.</span></span>
    - <span data-ttu-id="23b5a-139">チップの現在 (既定) の設定で測定を行うために必要な時間は、を呼び出すことによって取得され `GetMeasurementDuration` ます。</span><span class="sxs-lookup"><span data-stu-id="23b5a-139">The time required for the chip to take measurements with the chip's current (default) settings is retrieved by calling `GetMeasurementDuration`.</span></span>
    - <span data-ttu-id="23b5a-140">`while`ループは無期限に実行されます。</span><span class="sxs-lookup"><span data-stu-id="23b5a-140">A `while` loop runs indefinitely.</span></span> <span data-ttu-id="23b5a-141">各イテレーション:</span><span class="sxs-lookup"><span data-stu-id="23b5a-141">Each iteration:</span></span>
        1. <span data-ttu-id="23b5a-142">コンソールをクリアします。</span><span class="sxs-lookup"><span data-stu-id="23b5a-142">Clears the console.</span></span>
        1. <span data-ttu-id="23b5a-143">電源モードをに設定し `Bmx280PowerMode.Forced` ます。</span><span class="sxs-lookup"><span data-stu-id="23b5a-143">Sets the power mode to `Bmx280PowerMode.Forced`.</span></span> <span data-ttu-id="23b5a-144">これにより、チップが1つの測定を実行し、結果を格納して、スリープ状態になります。</span><span class="sxs-lookup"><span data-stu-id="23b5a-144">This forces the chip to perform one measurement, store the results, and then sleep.</span></span>
        1. <span data-ttu-id="23b5a-145">温度、気圧、湿度、および高度の値を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="23b5a-145">Reads the values for temperature, pressure, humidity, and altitude.</span></span>

            > [!NOTE]
            > <span data-ttu-id="23b5a-146">高度はデバイスのバインドによって計算されます。</span><span class="sxs-lookup"><span data-stu-id="23b5a-146">Altitude is calculated by the device binding.</span></span> <span data-ttu-id="23b5a-147">のこのオーバーロード `TryReadAltitude` は、平均海面レベルの圧力を使用して推定を生成します。</span><span class="sxs-lookup"><span data-stu-id="23b5a-147">This overload of `TryReadAltitude` uses mean sea level pressure to generate an estimate.</span></span>

        1. <span data-ttu-id="23b5a-148">現在の環境条件をコンソールに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="23b5a-148">Writes the current environmental conditions to the console.</span></span>
        1. <span data-ttu-id="23b5a-149">1000ミリ秒スリープします。</span><span class="sxs-lookup"><span data-stu-id="23b5a-149">Sleeps 1000 ms.</span></span>

1. [!INCLUDE [tutorial-build](../includes/tutorial-build.md)]
1. [!INCLUDE [tutorial-deploy](../includes/tutorial-deploy.md)]
1. <span data-ttu-id="23b5a-150">配置ディレクトリに切り替え、実行可能ファイルを実行して、Raspberry Pi でアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="23b5a-150">Run the app on the Raspberry Pi by switching to the deployment directory and running the executable.</span></span>

    ```bash
    ./SensorTutorial
    ```

    <span data-ttu-id="23b5a-151">コンソールでセンサーの出力を確認します。</span><span class="sxs-lookup"><span data-stu-id="23b5a-151">Observe the sensor output in the console.</span></span>

1. <span data-ttu-id="23b5a-152"><kbd>Ctrl + C</kbd>キーを押してプログラムを終了します。</span><span class="sxs-lookup"><span data-stu-id="23b5a-152">Terminate the program by pressing <kbd>Ctrl+C</kbd>.</span></span>

<span data-ttu-id="23b5a-153">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="23b5a-153">Congratulations!</span></span> <span data-ttu-id="23b5a-154">I2C を使用して、気温/湿度/気圧センサーから値を読み取りました。</span><span class="sxs-lookup"><span data-stu-id="23b5a-154">You've used I2C to read values from a temperature/humidity/barometric pressure sensor!</span></span>

## <a name="get-the-source-code"></a><span data-ttu-id="23b5a-155">ソース コードを入手する</span><span class="sxs-lookup"><span data-stu-id="23b5a-155">Get the source code</span></span>

<span data-ttu-id="23b5a-156">このチュートリアルのソースは、 [GitHub で入手でき](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span> ます。</span><span class="sxs-lookup"><span data-stu-id="23b5a-156">The source for this tutorial is [available on GitHub](https://github.com/MicrosoftDocs/dotnet-iot-assets/tree/master/tutorials/SensorTutorial) <span class="docon docon-navigate-external x-hidden-focus"></span>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="23b5a-157">次の手順</span><span class="sxs-lookup"><span data-stu-id="23b5a-157">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="23b5a-158">LCD にテキストを表示する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="23b5a-158">Learn how to display text on an LCD</span></span>](../tutorials/lcd-display.md)
