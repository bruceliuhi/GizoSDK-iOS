---
coverY: 0
---

# Permissions

## Overview

Permissions refer to the security mechanisms that control an application access to specific resources or features of the device. These permissions are declared in the "Target"->"Info" and are essential for ensuring user privacy and security.

It is important to note that, dangerous permissions are requested at runtime, even if they are declared. This means that the user can grant or deny the permission when the application is running, and the iOS APP side must handle the permission flow accordingly.

Managing permissions properly is crucial for maintaining user trust and ensuring that applications access only the necessary resources. iOS SDK provides tools and APIs to handle permissions effectively and securely within your application.

## <mark style="color:purple;">Permissions Settings</mark>

The following permissions are required by the iOS SDK:

| PERMISSIONS                         | WHERE TO USE         |
| ----------------------------------- | -------------------- |
| NSLocationUsageDescription          | In GPS setting       |
| NSLocationWhenInUseUsageDescription | In GPS setting       |
| NSLocationAlwaysUsageDescription    | In GPS setting       |
| NSMotionUsageDescription            | In IMU setting       |
| NSCameraUsageDescription            | In capturing videos. |

## <mark style="color:purple;">Helper</mark> <mark style="color:purple;">Permission</mark>

In iOS, permissions are obtained from users to ensure app security and protect user privacy. When an iOS app requests certain permissions, it is asking for permission to access specific features or data on the device.

In GIZO SDK, we have provided a possibility for the developer to provide a list of permissions required to be received from the user according to the settings they have made for the SDK.

## What Does Helper Permission Do?

According to the settings made by the developer for **GIZO SDK**, it returns a list of required permissions

* If access to AnalysisSettings is granted, we will also have access to the camera.
* If we have access to GPS settings, permissions of NSLocationUsageDescription, NSLocationWhenInUseUsageDescription, NSLocationAlwaysUsageDescription will be provided.&#x20;
* If we have access to IMU settings, permissions of NSMotionUsageDescription will be provided.&#x20;

## Required Permissions&#x20;

The following permissions are required by the SDK:

#### <mark style="color:blue;">NSLocationUsageDescription</mark>

A message that tells the user why the app is requesting access to the user’s location information.

#### <mark style="color:blue;">NSLocationWhenInUseUsageDescription</mark>&#x20;

A message that tells the user why the app is requesting access to the user’s location information while the app is running in the foreground.

#### <mark style="color:blue;">NSLocationAlwaysAndWhenInUseUsageDescription</mark>

A message that tells the user why the app is requesting access to the user’s location information at all times.

#### <mark style="color:blue;">NSMotionUsageDescription</mark>

A message that tells the user why the app is requesting access to the device’s motion data.

#### <mark style="color:blue;">NSMotionUsageDescription</mark>

A message that tells the user why the app is requesting access to the device’s motion data.

#### <mark style="color:blue;">NSCameraUsageDescription</mark>

A message that tells the user why the app is requesting access to the device’s camera.

Those permissions can be found in "Info" tab's "Custom iOS Target Properties"

&#x20;

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

