---
coverY: 0
---

# GIZO GPS Setting

## GIZO GPS Setting

### Overview <a href="#overview" id="overview"></a>

The GPS settings in GIZO SDK allow developers to incorporate GPS functionality into their iOS applications. This documentation provides instructions on enabling GPS, accessing location, speed, direction of movement (heading), and speed limit.

GizoGpsSetting can be used to customize the behavior an app by adjusting its reading and saving parameters.

For this reason, add the following block of code in the Application class, onCreate function, inside Gizo.initialize to set the GizoGpsSetting.

**Note:** We need to get [MAPBOX\_PUBLIC\_KEY](https://docs.mapbox.com/android/maps/guides/install/#configure-credentials) from Mapbox.

{% tabs %}
{% tab title="Swift" %}
```swift
let options: GizoAppOptions = GizoAppOptions()
options.gpsSetting.allowGps = true
options.gpsSetting.mapBoxKey = "MAPBOX_PUBLIC_KEY"
options.gpsSetting.interval = 1000
options.gpsSetting.maxWaitTime = 1000
options.gpsSetting.withForegroundService = false
options.gpsSetting.saveCsvFile = true
options.gpsSetting.fileLocation = FileLocationPath.Cache
options.gpsSetting.saveDataTimerPeriod = 10
```
{% endtab %}
{% endtabs %}

The GizoGpsSetting sets the GPS-related properties such as

* allowGps(true): Enabling GPS.
* mapBoxKey("MAPBOX\_PUBLIC\_KEY"): Providing the [Mapbox API key](https://docs.mapbox.com/android/maps/guides/install/#configure-credentials) for accessing Mapbox services.
* interval(1000L): Default interval between location updates which updates to 1000 milliseconds (1 second) here.
* maxWaitTime(1000L): Sets the maximum wait time in milliseconds for location updates. Locations are determined at intervals but delivered in batch based on wait time. Batching is not supported by all engines.
* withForegroundService(true): If you set withForegroundService to true, you should only invoke this method when the app is in the foreground. withForegroundService - Boolean, if set to false, foreground service will not be started, no notifications will be rendered, and no location updates will be available while the app is in the background.
* saveCsvFile(true): Indicating that the GPS data should be saved to a CSV file.
* fileLocation(FileLocationPath.CACHE): Specifying the file location path for storing the GPS data CSV file (in this case, set to the cache directory).
* saveDataTimerPeriod(10L): Setting the period of saving GPS data to 10 milliseconds.

This code suggests that the GizoAppOptions class provides a way to specify various configuration options for the GIZO application, including GPS-related settings. The specific implementation and usage of GizoAppOptions would depend on the details of the GIZO application itself.

​Here are the available options that can be set in gpsSetting in the Application class:

<table data-header-hidden><thead><tr><th width="207.33333333333331"></th><th></th><th></th></tr></thead><tbody><tr><td>Options</td><td>Default Value</td><td>Description</td></tr><tr><td>allowGps(Boolean)</td><td>false</td><td>To allow access to GPS setting.</td></tr><tr><td>mapBoxKey(String)</td><td>_____</td><td>The key was obtained from Mapbox.</td></tr><tr><td>interval(Long)</td><td>1000L</td><td>Default interval between location updates.</td></tr><tr><td>maxWaitTime(Long)</td><td>1000L</td><td>Sets the maximum wait time in milliseconds for location updates. Locations are determined at intervals but delivered in batch based on wait time. Batching is not supported by all engines.</td></tr><tr><td>withForegroundService(Boolean)</td><td>true</td><td>If set to true, foreground service will be started, notifications will be rendered, and location updates will be available while the app is in the background.</td></tr><tr><td>saveCsvFile(Boolean)</td><td>false</td><td>To save CSV file or not.</td></tr><tr><td>fileLocation(FileLocationPath)</td><td>FileLocationPath.CACHE</td><td>To save GPS file, in the <strong>CACHE</strong> or <strong>DOWNLOAD</strong>.</td></tr><tr><td>saveDataTimerPeriod(Long)</td><td>10L</td><td>The period of time that a GPS data row is saved in CSV file.</td></tr></tbody></table>
