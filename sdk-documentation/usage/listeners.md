# Listeners

## Overview

Callback listeners provide a way to handle user interactions and system events in iOS applications. They allow developers to customize the behavior of their app based on the events that occur, making their application more interactive and responsive to user actions.

Callback listeners allow developers to register a listener object that will be notified when a specific event occurs. The listener object contains a set of callback methods that will be called by the system when the associated event occurs. These events include Analysis, IMU Sensors, GPS, Video, Battery, and Orientation.​

### <mark style="color:purple;">Load Model Listener</mark>

Loading the model allows the application to perform complex tasks that go beyond traditional programming capabilities. By incorporating machine learning models into iOS applications, developers can provide intelligent, data-driven features and functionalities to their users. When the model is loaded a listener is triggered to check the state of loading the model.

When the Gizo.app.loadModel method is called, this value parameter can be checked out:

| Value-parameters | Type              | Description                                                                                        |
| ---------------- | ----------------- | -------------------------------------------------------------------------------------------------- |
| status           | InterpreterStatus | To check different stats of loading, such as **LOADING**, **LOADED**, **FAILED**, **NOT\_LOADED**. |

​Add these lines of code in the Application class to load the model and receive the listener for different state of loading, such as **LOADING**, **LOADED**, **FAILED**, **NOT\_LOADED**.

```swift
func onLoadModel(status: LoadModelStatus) {
}
```

An observer is a design pattern that allows an object (the observer) to monitor changes or events in another object (the subject). In this case, it appears that the setLoadModelObserver method is used to set an observer function or callback for monitoring the status of a model loading process in the GIZO library.

The code snippet you provided shows an anonymous function being passed as the argument to setLoadModelObserver. The function takes a single parameter named status, which likely represents the current status of the model loading process.​

### <mark style="color:purple;">Session Status Listener</mark>

As previously stated, based on the settings we have applied, some files related to video, AI analysis, GPS, and IMU are saved.

When the Start Session gets activated, these value parameters can be checked out:

| Value-parameters | Type    | Description                                      |
| ---------------- | ------- | ------------------------------------------------ |
| inProgress       | Boolean | To check whether the sensor is recording or not. |
| previewAttached  | Boolean | To check whether the preview is attached or not. |

​It is possible to gain the parameters mentioned above with the method below in Preview:

```swift
func onSessionStatus(inProgress: Int, previewAttached: Int) {
}
```

The gizoAnalysis component represents a module or functionality within the application responsible for managing sessions and their associated status.

Inside the lambda expression, the code block that would be executed when a change in the session status occurs is not provided in the given snippet. However, within this code block, a logic can be defined to handle the updated session status. For example, the application could perform actions based on whether the recording is in progress (inProgress) or if a preview is currently attached (previewAttached). This could involve updating the user interface, triggering specific behaviors, or performing other operations based on the current session status.​

### <mark style="color:purple;">Session Status Listener</mark>

In our SDK, we require accurate and efficient detection and localization of objects in images and video streams and also accurate and efficient estimation of the depth or distance of objects in a scene and we gain these data with GizoAnalysisSetting.

When Analysis gets activated, these value parameters can be checked out:

| Value-Parameters    | Type     | Description                                                                                              |
| ------------------- | -------- | -------------------------------------------------------------------------------------------------------- |
| preview             | UIImage? | It outputs an image that includes object detection and road lines.                                       |
| ttc                 | Float?   | Time to collision.                                                                                       |
| ttcStatus           | Int      | It returns state **collision**, **tailgating**, and **None** based on the calculated formula in the TTC. |
| frontObjectDistance | String   | The distance to the front object.                                                                        |
| egoSpeed            | Float?   | The speed of the ego vehicle.                                                                            |
| gpsTime             | String   | The current time.                                                                                        |

​It is possible to gain the parameters mentioned above with the method below in Preview:

```swift
func onAnalysisResult(preview: UIImage?, ttc: Float?, ttcStatus: Int, frontObjectDistance: String, egoSpeed: Float?, gpsTime: String) {
}
```

The gizoAnalysis property is responsible for analysis of video frames using AI and generating TTC and warning flags (ttcStatus).

The lambda expression assigned to the onAnalysisResult property takes several parameters: preview, ttc, ttcStatus, frontObjectDistance, egoSpeed, and gpsTime. These parameters represent the outputs of the AI analysis pipeline.

Within this code block, a logic can be developed to further process the results of the analysis. This can be showing the analysis result, changing the interface, saving the result for later, or taking actions based on the outcome.

​Additionally, it is possible to write a customized formula and calculate TTC in Preview.

```swift
func ttcCalculator(frontObjectDistance: String, egoSpeed: Float?, ttc: Float?) {
}
```

**Note:** The purpose of this method is to calculate the Time To Collision (TTC) using the provided frontObjectDistance and egoSpeed values. The calculated TTC is then returned as the result of the function call and can be used in the previous tab of the code.​

Moreover, there is the possibility to calculate a customized ttcStatus based on frontObjectDistance, egoSpeed, and TTC in Preview.

```swift
func ttcStatusCalculator(ttc: Float?, egoSpeed: Float?, ttcStatus: Int) {
}
```

**Note:** The exact implementation of the ttcStatusCalculator function is not provided in the given snippet, but it is expected to perform the necessary calculations to determine the TTC status based on the input parameters. Therefore, the ttcStatus variable be modified within the function to obtain a customized TTC status.

By calling the function, a customized ttcStatus is calculated and can be used in the onAnalysisResult method mentioned above.​

### <mark style="color:purple;">GPS Listener</mark>

As mentioned earlier, this documentation provides instructions on enabling GPS, accessing location, speed, direction of movement (heading), and speed limit.

When GPS gets activated, these values are returned:

| Value-parameters | Type                    | Description                                                                                                                                                                                                 |
| ---------------- | ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| location         | CLLocationCoordinate2D? | A data class representing a geographic location. A location consists of a latitude, longitude, timestamp, accuracy, and other information such as bearing, altitude, and speed. For more details, see the . |
| isGpsOn          | Boolean?                | To check whether the GPS is on or not.                                                                                                                                                                      |
| speedLimitKph    | Int?                    | speed limit in kilometer per hour.                                                                                                                                                                          |
| speedKph         | Int                     | speed in kilometer per hour.                                                                                                                                                                                |

​​It is possible to gain the parameters mentioned above with the method below in Preview:

```swift
func onLocationChange(location: CLLocationCoordinate2D?, isGpsOn: Bool?) {
}
```

The gizoAnalysis object is a component responsible for analyzing and processing location data. By assigning a lambda expression to the onLocationChange method, the application can respond to changes in the location of device.

The lambda expression takes two parameters: location and isGpsOn.

Location is the updated GPS info, explained in the table above. isGpsOn is a Boolean parameter that indicates whether the GPS functionality is currently enabled on the device.

Within this code block, a logic can be defined to handle the updated location. For example, the application could update the user interface to display the new location information, trigger specific processes or calculations based on the new location, or save the location data for future use.​

```swift
func onSpeedChange(speedLimitKph: Int?, speedKph: Int) {
}
```

The gizoAnalysis object is a component responsible for analyzing and processing speed-related data. By assigning a lambda expression to the onSpeedChange method, the application can respond to changes in the device's speed.

The lambda expression takes two parameters: speedLimitKph and speedKph.

speedLimitKph represents the speed limit in kilometers per hour (kph) corresponding to the current state of the device.

speedKph represents the current speed of the device or vehicle in kph.

Within the lambda expression, it is feasible to add a customized block of code upon a change in speed. For example, the application could compare the current speed with the speed limit and trigger alerts or warnings if the speed exceeds the limit. The user interface could also be updated to display the updated speed information, providing real-time feedback to the user. Additionally, further calculations or analysis based on the speed data could be performed within this code block.​

### <mark style="color:purple;">IMU Listener</mark>

As previously mentioned, the IMU setting in GIZO SDK allows developers to utilize the motion sensors of the device's IMU. The IMU typically consists of the **accelerometer**, **gyroscope**, and **magnetometer. Gravity** and **linear acceleration** are also estimated by fusing the IMU data.

When IMU gets activated, these value parameters are returned:

| Value-parameters        | Type         | Description                                                                                           |
| ----------------------- | ------------ | ----------------------------------------------------------------------------------------------------- |
| linearSensorEvent       | SensorEvent? | includes information such as Linear Acceleration values, Timestamps and Accuracy, or precision.       |
| accelerationSensorEvent | SensorEvent? | includes information such as Acceleration values, Timestamps and Accuracy, or precision.              |
| uncalibratedSensorEvent | SensorEvent? | includes information such as Uncalibrated Acceleration values, Timestamps and Accuracy, or precision. |
| gyroscopeSensorEvent    | SensorEvent? | includes information such as Angular velocity values, timestamps and Accuracy, or precision.          |
| gravitySensorEvent      | SensorEvent? | includes information such as Gravity values, timestamps and Accuracy, or precision.                   |
| magneticSensorEvent     | SensorEvent? | includes information such as Magnetic field values, timestamps and Accuracy, or precision.            |

​The above data can be obtained by using the commands described in the following:

```swift
func onLinearAccelerationSensor(accLinX: String?, accLinY: String?, accLinZ: String?) {
}
```

The gizoAnalysis object is a component responsible for analyzing and processing data from the linear acceleration sensor. Assigning a lambda expression to the onLinearAccelerationSensor method allows the application to respond to events triggered by the linear acceleration sensor.

The lambda expression uses linearSensorEvent as the input, which comes from the linear acceleration sensor. This event data typically includes information about the acceleration of the device along its X, Y, and Z axes.

Within this code block, a logic can be defined to handle the received acceleration data. For example, the application could analyze the acceleration values to detect specific motion patterns, such as shaking or sudden movements. The user interface could be updated to provide real-time feedback based on the acceleration values, such as displaying animations or triggering sound effects. Additionally, the acceleration data could be used to trigger specific behaviors or calculations within the application.​

```swift
func onAccelerationSensor(accX: String?, accY: String?, accZ: String?) {
}
```

This code suggests that the Gizo namespace contains an object gizoAnalysis which has a method onAccelerationSensor. This method is being assigned a lambda expression or callback function.

The lambda expression takes one parameter accelerationSensorEvent, which represents an event or data related to the acceleration sensor.​

```swift
func onAccelerationUncalibratedSensor(accUncX: String?, accUncY: String?, accUncZ: String?) {
}
```

This code suggests that the Gizo namespace contains an object gizoAnalysis which has a method onAccelerationUncalibratedSensor. This method is being assigned a lambda expression or callback function.

The lambda expression takes one parameter uncalibratedSensorEvent, which represents an event or data related to the uncalibrated acceleration sensor. The uncalibrated sensor data includes both raw and calibrated acceleration values.​

```swift
func onGyroscopeSensor(gyrX: String?, gyrY: String?, gyrZ: String?) {
}
```

The gizoAnalysis object is a component responsible for analyzing and processing data from the gyroscope sensor. By assigning a lambda expression to the onGyroscopeSensor method, the application can respond to events triggered by the gyroscope sensor.

The lambda expression takes a single parameter gyroscopeSensorEvent, which represents the event data received from the gyroscope sensor. This event data typically includes information about the rotational movement of the device along the X, Y, and Z axes of the device.

Within this code block, an algorithm may be defined to handle the received gyroscope data. For example, the application could analyze the gyroscope data to detect specific types of rotation or gestures, such as tilting, shaking, or rotating the device. The user interface could be updated to reflect the device's orientation or movement, such as adjusting the display based on the device's tilt or triggering animations based on rotation. Additionally, the gyroscope data could be used to trigger specific behaviors or calculations within the application.​

```swift
func onGravitySensor(graX: String?, graY: String?, graZ: String?) {
}
```

The gizoAnalysis method is responsible for analyzing and processing data from various sensors, including the gravity sensor.

The lambda expression assigned to the onGravitySensor method takes a single parameter gravitySensorEvent, which represents the event data received from the gravity sensor.

Within this code block, a logic can be defined to handle the received gravity sensor data. For example, the application could analyze the gravity data to determine the orientation of device. This could be used to detect tilts or changes in orientation, allowing the application to respond accordingly. The gravity sensor data could also be used to update the user interface, trigger specific behaviors, or perform calculations based on the orientation of device.​

```swift
func onMagneticSensor(magX: String?, magY: String?, magZ: String?) {
}
```

This code suggests that the Gizo namespace contains a gizoAnalysis object which has a method onMagneticSensor. This method is assigned a lambda expression or callback function.

The lambda expression takes one parameter, magneticSensorEvent, which represents an event or data related to the magnetic sensor. The magnetic sensor data typically includes information about the magnetic field strength and direction of the Earth.​

### <mark style="color:purple;">Video Listener</mark>

In mobile devices, the "video settings" typically refer to the configurable options and parameters that allow users to customize various aspects of video recording. These settings may vary depending on the specific device, operating system, and camera capabilities.

When the video gets activated, this value parameter can be checked out:

| Value-parameter | Type             | Description                                       |
| --------------- | ---------------- | ------------------------------------------------- |
| event           | VideoRecordEvent | Used to report video recording events and status. |

​The above data can be obtained by using the commands described in the following:

```swift
func onRecordingEvent(status: VideoRecordStatus) {
}
```

The gizoAnalysis component represents a module or functionality within the application that is responsible for managing recording-related operations.

The lambda expression assigned to the onRecordingEvent method takes a single parameter, event, which represents the recording event that has occurred.

Within this code block, a logic can be defined to handle different recording events and perform specific actions based on the event type. For example, the application could respond to events such as recording start and stop. This could involve updating the user interface, notifying the user, performing additional processing or analysis on the recorded data, or triggering other related operations.​

### <mark style="color:purple;">Battery Listener</mark>

Battery settings in the GIZO SDK library refer to the configuration and management options related to the battery state of the device. These settings allow monitoring and controlling the battery usage of their mobile devices.

When the battery monitoring is initialized, this value parameter is returned:

| Value-parameter | Type          | Description                                                                              |
| --------------- | ------------- | ---------------------------------------------------------------------------------------- |
| status          | BatteryStatus | To check what is the battery status: LOW\_BATTERY\_STOP, LOW-BATTERY\_WARNING, or NORMAL |

​This parameter can be obtained using the code below in Preview:

```swift
func onBatteryStatusChange(status: BatteryStatus) {
}
```

The gizoAnalysis method is responsible for analyzing and processing various aspects of the application, including monitoring the battery status.

The lambda expression assigned to the onBatteryStatusChange method takes a single parameter status, which represents the updated battery status.

Inside the lambda expression, a set of instructions can be defined when a change in the battery status occurs. For example, the application could perform actions based on the current battery level, such as adjusting power consumption, displaying a low battery warning, or triggering specific behaviors when the battery reaches a certain threshold.​

### <mark style="color:purple;">Orientation Listener</mark>

Screen orientation refers to the orientation of the device's screen, which can be either portrait (vertical) or landscape (horizontal).

when the mobile device is in landscape orientation with +y axis of the device parallel to the +y axis of the coordinates system of vehicle, this value parameter is returned:

| Value-parameters | Type    | Description                                                     |
| ---------------- | ------- | --------------------------------------------------------------- |
| isAlign          | Boolean | Whether the mobile device is in a landscape orientation or not. |

​This parameter can be obtained using the code below in Preview:

```swift
func onGravityAlignmentChange(isAlign: Bool) {
}
```

In GIZO SDK, if the mobile device is in landscape orientation with +y axis of the device parallel to the +y axis of the coordinates system, the listener calls back true. (isAlign would be true)When a mobile device is in landscape orientation, the user interface and content on the screen should be adjusted accordingly to make optimal use of the wider space. This orientation is commonly used for activities that benefit from a wider viewing area, such as watching videos, playing games, or viewing wide documents or images.
