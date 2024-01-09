# 🚀 Getting Started

Welcome to GIZO iOS SDK! This guide will help you get started with integrating and using the SDK in your iOS projects.

## Introduction

GIZO SDK is a powerful and versatile library that provides an efficient tool to increase traffic safety by analysis of driving performance. GIZO SDK allows collection of driving behavior, analysis of the data, and prevention of accidents or mitigation of crash severity by sending in-time warnings based on the analyzed data.&#x20;

## Prerequisites

Before using GIZO SDK, make sure you have installed the following prerequisites and set up in your development environment:

* Install the latest version of the Xcode
* Install Mapbox Navigation SDK and its dependencies for iOS and get an [access token](https://docs.mapbox.com/ios/maps/guides/install/).

### To use GIZO SDK library, follow these steps:

1. Open your iOS project in Xcode
2. Choose "File"->"Add Packages"，Add GizoSDK-iOS to the project

<figure><img src="../.gitbook/assets/截屏2023-12-20 下午7.06.45.png" alt=""><figcaption></figcaption></figure>

3. We need to implement settings for [Mapbox](https://docs.mapbox.com/ios/maps/guides/) because we use it in our library, therefore, MBXAccessToken are required to be added to "Target"->"Info":

<figure><img src="../.gitbook/assets/截屏2023-12-20 下午7.50.26.png" alt=""><figcaption></figcaption></figure>

## Using The SDK In Your iOS Application

### <mark style="color:purple;">Initialize The SDK</mark>

To initialize the iOS SDK, an instance of the Application class should be created and initialized using the "initialize" method:

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

<mark style="color:red;">**Note:**</mark> For using features of the SDK you need to add [Model](usage/gizo-analysis.md#step-2-adding-model) and required [App Options](usage/app-options/). In the following sections, we will elaborate on these topics.
