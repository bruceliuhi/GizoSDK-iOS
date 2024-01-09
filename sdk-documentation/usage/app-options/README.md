# App Options

## Overview

The SDK provides several options that can be configured at the app level to customize its behavior.&#x20;

This section provides developers with the necessary tools to customize the behavior and functionality of the SDK according to their needs. By proper setting of these options, they can seamlessly integrate the features of the SDK with their applications and deliver personalized user experience.

In this documentation, we will walk you through the various settings available and explain how each setting influences the behavior of the SDK. You will find detailed descriptions and usage examples to better understand the functions and their parameters.

Please refer to the following sections for detailed information on each setting, including usage examples.&#x20;

Let's dive in and discover the functions that will empower you to make the most of our iOS library!



## Setting App Options

To set app options for the iOS SDK, you will need to create a new instance of the Application class in your app module and set the desired options:

{% tabs %}
{% tab title="Swift" %}
```swift
let options: GizoAppOptions = GizoAppOptions()
options.analysisSetting.modelName = "ArtiSense3.mlmodelc"
options.analysisSetting.allowAnalysis = true
options.analysisSetting.saveTtcCsvFile = true
options.analysisSetting.saveMatrixFile = true
options.gpsSetting.allowGps = true
options.gpsSetting.saveCsvFile = true
options.imuSetting.allowMagneticSensor = true
options.imuSetting.allowMagneticSensor = true
options.imuSetting.allowMagneticSensor = true
options.imuSetting.saveCsvFile = true
options.batterySetting.checkBattery = true
options.orientationSetting.allowGravitySensor = true
options.videoSetting.allowRecording = true
Gizo.initialize(delegate: self, options: options)
```
{% endtab %}
{% endtabs %}

In the example above, we initialize the SDK instance, then we will create a new instance of the GizoAppOptions class and set the desired options.



## Available Options

&#x20;Here are the available options that can be set in the Application class:

<table><thead><tr><th width="233.33333333333331">Option</th><th width="143">Default Value</th><th>Description</th></tr></thead><tbody><tr><td>debug(Boolean)</td><td>true</td><td>Set to enable debugging log feature.</td></tr><tr><td>folderName(String)</td><td>"Gizo"</td><td>Set to save files in a download folder with this name.</td></tr><tr><td><p>analysisSetting</p><p>(<a href="broken-reference">GizoAnalysisSetting</a>)</p></td><td>null</td><td>Set to activate analyzing model and main export of the SDK.</td></tr><tr><td><p>imuSetting</p><p>(<a href="broken-reference">GizoImuSetting</a>)</p></td><td>null</td><td>Set to activate motion sensors such as AccelerationSensor, GyroscopeSensor, MagneticSensor, and GravitySensor and get callbacks.</td></tr><tr><td><p>gpsSetting</p><p>(<a href="broken-reference">GizoGpsSetting</a>)</p></td><td>null</td><td>Set to provide location information.</td></tr><tr><td><p>videoSetting</p><p>(<a href="broken-reference">GizoVideoSetting</a>)</p></td><td>null</td><td>Set to change the video information.</td></tr><tr><td><p>batterySetting</p><p>(<a href="broken-reference">GizoBatterySetting</a>)</p></td><td>null</td><td>Set the required actions based on the battery level.</td></tr><tr><td><p>orientationSetting</p><p>(<a href="broken-reference">GizoOrientationSetting</a>)</p></td><td>null</td><td>Set to activate the gravity sensor.</td></tr></tbody></table>



* <mark style="color:green;">**GizoAnalysisSetting**</mark> allows developers to gain data based on the frame captured from the camera and get object detection and depth estimation.
* <mark style="color:green;">**GizoImuSetting**</mark> allows developers to utilize the sensors that make up the device's IMU. An IMU typically consists of the **accelerometer**, **gyroscope,** and **magnetometer**. **Gravity** and **linear acceleration** are estimated from the IMU data.
* <mark style="color:green;">**GizoGpsSetting**</mark> provides instructions on enabling GPS, accessing location, speed, the direction of movement (heading), and speed limit.
* <mark style="color:green;">**GizoVideoSetting**</mark> refers to the configuring and utilizing video-related features and components within an iOS application. Video settings include settings, such as capturing video from the device’s camera, or streaming video content.
* <mark style="color:green;">**GizoBatterySetting**</mark> refers to the configuration and management options related to the battery level of device. These settings allow developers and/or users to monitor and control the battery usage of their mobile devices.
* <mark style="color:green;">**GizoOrientationSetting**</mark> refers to checking the orientation of the device, which should be in a proper position, i.e. landscape with +y axis in the direction of vehicle +y axis.

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
