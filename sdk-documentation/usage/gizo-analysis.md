---
coverY: 0
---

# GIZO Analysis

## Overview

In this SDK, using artificial intelligence, driving behavior is analyzed to reduce the risk of accidents and other driving hazards, resulting in a smarter and safer driving experience.

When using GIZO Analysis, the following steps must be taken:

### <mark style="color:blue;">Step 1: Setting</mark> <a href="#step1" id="step1"></a>

In the first step, it is required to configure the functionality of the SDK through [GIZO Analysis Setting](app-options/gizo-analysis-setting.md).

### <mark style="color:blue;">Step 2: Adding Model</mark>

In this SDK, developers are provided with the necessary functions to detect and localize objects in video streams in an accurate and efficient way.

Object detection and depth estimation are crucial technologies in apps that can perceive their surroundings. By leveraging these capabilities, developers can enable their apps to identify objects within images or video streams and estimate the relative distances between the ego vehicle and the objects in the scene.

\
**Object detection** plays a vital role in various iOS applications<mark style="color:red;">,</mark> enabling tasks such as object tracking and augmented reality.

**Depth estimation** enables iOS applications to measure the distance to the objects in the scene. This capability is valuable for tasks such as depth-based segmentation, virtual reality, or 3D reconstruction.&#x20;

To take advantage of AI analysis, the model should be added to the assets of the app module.

Download the model from this link:&#x20;

[https://artificient-ai.s3.eu-central-1.amazonaws.com/artisense\_det\_da\_ll.data](https://artificient-ai.s3.eu-central-1.amazonaws.com/artisense\_det\_da\_ll.data)

### <mark style="color:blue;">Step 3: Loading Model</mark>

Loading a model allows the application to perform complex tasks that go beyond the capabilities of traditional programs. By incorporating neural networks into iOS applications, developers can provide intelligent, data-driven features and functionalities to their users.

Add the following block of code in the Application class to load the model and receive the [listener](listeners.md) for different states of loading, but the state of **LOADED** is essential for using GIZO Analysis completely.

```swift
override func viewDidLoad() {
    super.viewDidLoad()
    Gizo.app.loadModel()
}
```

<mark style="color:red;">**Note:**</mark> After these steps are done, a series of callbacks are triggered, so the corresponding output can be obtained.

### <mark style="color:purple;">Start GIZO Analysis</mark>

To start using the SDK, we need to start GIZO Analysis. For this reason, we need a lifecycle.

```swift
Gizo.app.gizoAnalysis.start(lifecycleOwner: self) {
    print("done")
}
```

**onDone is called when starting GIZO Analysis is completed.**

### <mark style="color:purple;">Stop GIZO Analysis</mark>

Upon termination of the analysis, the stop method must be called to halt all the processes which are related to the GIZO Analysis. These processes include video, GPS, and IMU recording as well as AI analysis and driving assistance functions.

```swift
Gizo.app.gizoAnalysis.stop()
```

### <mark style="color:purple;">Start Saving Session</mark>

Based on the settings we have applied, some files related to video, analysis, GPS, and IMU are saved.

Saving files in <mark style="color:red;">iOS Studio</mark> has benefits such as persistence, offline accessibility, advanced analysis, sharing, backup, and tracking. It enhances the functionality, usability, and reliability of the app by ensuring the availability and integrity of important data.

To start saving files using GIZO SDK, use the following code, and receive the [listener](listeners.md) for session progress.

```swift
Gizo.app.gizoAnalysis.startSavingSession() 
```

### <mark style="color:purple;">Stop Saving Session</mark>

While saving files is an essential aspect of many applications, it is important to consider the performance, battery, storage, security, and network implications associated with file-saving operations. By optimizing and managing file-saving processes, you can ensure a smooth user experience while efficiently utilizing system resources.

To stop saving files using GIZO SDK, use the following code:

```swift
Gizo.app.gizoAnalysis.stopSavingSession()
```

### <mark style="color:purple;">Attach Preview To Camera</mark>

Preview is a custom view that displays the camera feed for CameraX’s Preview. This class manages the preview of Surface lifecycle.

So, to display the camera, a <mark style="color:red;">previewView</mark> should be attached as well.

```swift
Gizo.app.gizoAnalysis.attachPreview(previewView)
```
