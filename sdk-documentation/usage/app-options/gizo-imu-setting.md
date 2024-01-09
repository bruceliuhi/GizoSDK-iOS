---
coverY: 0
---

# GIZO IMU Setting

## GIZO IMU Setting

### Overview <a href="#overview" id="overview"></a>

The IMU setting in GIZO SDK allows developers to utilize the motion sensors of the device IMU. The IMU typically consists of the **accelerometer**, **gyroscope**, and **magnetometer**. **Linear** and **gravity** are estimated through the fusion of IMU data.

GizoImuSetting can be used to customize the behavior of an app by adjusting its reading and saving parameters.

For this reason, add the following block of code in the Application class, onCreate function, inside Gizo.initialize to set the GizoImuSetting.

{% tabs %}
{% tab title="Swift" %}
```swift
let options: GizoAppOptions = GizoAppOptions()
options.imuSetting.allowAccelerationSensor = true
options.imuSetting.allowMagneticSensor = true
options.imuSetting.allowGyroscopeSensor = true
options.imuSetting.saveCsvFile = true
options.imuSetting.fileLocation = FileLocationPath.Cache
options.imuSetting.saveDataTimerPeriod = 10
```
{% endtab %}
{% endtabs %}

The GizoImuSetting sets the IMU-related properties, such as

* allowAccelerationSensor(true): Enabling the raw, linear, gravity sensors.
* allowMagneticSensor(true): Enabling the Magnetic Field/Magnetometer.
* allowGyroscopeSensor(true): Enabling the Gyroscope sensor.
* saveCsvFile(true): Indicating that the IMU data should be saved to a CSV file.
* fileLocation(FileLocationPath.CACHE): Specifying the file location path for storing the IMU data CSV file (in this case, set to the cache directory).
* saveDataTimerPeriod(10L): Setting the period of the IMU data timer to 10 milliseconds.

This code suggests that the GizoAppOptions class specifies various configuration options for the GIZO application, including IMU-related settings. The specific implementation and usage of GizoAppOptions would depend on the details of the GIZO application.​

* **Accelerometer sensor:** It is a sensor commonly found in mobile devices that measures acceleration forces acting on the device in three dimensions: along the x-axis (horizontal), y-axis (vertical), and z-axis (perpendicular to the device's screen). It detects changes in velocity and movement, allowing the device to respond to various types of motion.
* **Magnetic sensor:** It is a sensor that measures the strength and direction of the magnetic field in its vicinity. It is typically used to detect the presence of a magnetic field and determine its orientation. It is commonly used to determine the orientation of a phone based on the magnetic field of the Earth.
* **Gyroscope sensor:** It is part of the device's sensor array and is used to measure the angular velocity or rotational motion of the device. The gyroscope provides information about the angular velocity or rotational motion of the device.

​Here are the available options that can be set in imuSetting in the Application class:

| Options                          | Default Value          | Description                                                                                     |
| -------------------------------- | ---------------------- | ----------------------------------------------------------------------------------------------- |
| allowAccelerationSensor(Boolean) | false                  | To activate the raw acceleration, linear acceleration, and gravity acceleration sensors or not. |
| allowGyroscopeSensor(Boolean)    | false                  | To activate the gyroscope sensor or not.                                                        |
| allowMagneticSensor(Boolean)     | false                  | To activate the magnetic field or not.                                                          |
| allowGravitySensor(Boolean)      | false                  | To activate the gravity sensor or not.                                                          |
| saveCsvFile(Boolean)             | false                  | To save CSV file or not.                                                                        |
| fileLocation(FileLocationPath)   | FileLocationPath.CACHE | To save the IMU file, in the **CACHE** or **DOWNLOAD**.                                         |
| saveDataTimerPeriod(Long)        | 10L                    | The period of time that an IMU data row is saved in a CSV file.                                 |

​
