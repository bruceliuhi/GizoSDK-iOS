---
coverY: 0
---

# ⚙ Usage

To use GIZO iOS SDK in your app, follow these steps:

* To start the SDK, we need to start the [GIZO Analysis](gizo-analysis.md). For this reason, we need a lifecycle like an activity or a fragment and implement the required modules in the Main Activity.
* The SDK requires certain[ permissions](permissions.md) in order to function properly. These permissions are necessary to enable the GPS, capture videos, Mapbox Navigation and save files in the download folder.
* The SDK provides several [APP options](app-options/) that can be configured at the app level to customize its behavior. These options can be set in the Application class of your iOS APP.
* Using a [listener](listeners.md), which is a mechanism that allows registering a listener object that will be notified when a specific event occurs. The listener object contains a set of callback methods that will be called by the system when the associated event occurs. These events include Analysis, IMU Sensors, GPS, Video, Battery, and Orientation events.
