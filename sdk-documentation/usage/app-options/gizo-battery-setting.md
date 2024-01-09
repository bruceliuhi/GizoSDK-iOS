---
coverY: 0
---

# GIZO Battery Setting

## Overview

Battery settings on the GIZO SDK refer to the configuration and management options related to the battery level of device. These settings allow monitoring and controlling the battery usage of their mobile devices.

GizoBatterySetting is used to customize several behaviors and functionalities of the SDK,  including specifying the minimum percentage of battery level above which analysis or video recording can be implemented as well as the interval at which the battery level is checked.

To have access to battery setting options, you need to add the following block of code in the Application class, onCreate function, inside Gizo.initialize.

{% tabs %}
{% tab title="Swift" %}
```swift
let options: GizoAppOptions = GizoAppOptions()
options.batterySetting.checkBattery = true
options.batterySetting.lowBatteryLimit = 25
options.batterySetting.lowBatteryStop = 15
options.batterySetting.interval = 5000
```
{% endtab %}
{% endtabs %}

The GizoBatterySetting sets the battery-related properties such as checkBattery (enabling battery monitoring), lowBatteryLimit (the threshold below which the battery is considered low), lowBatteryStop (the threshold at which certain operations should be stopped), and interval (the interval at which the battery level is checked).

This code suggests that the GizoAppOptions class specifies various configuration options for the GIZO application, including battery-related settings. The specific implementation and usage of GizoAppOptions would depend on the details of the GIZO application itself.



Here are the available options that can be set in batterySetting in the Application class:

<table><thead><tr><th width="252">Options</th><th width="167.33333333333331">Default Value</th><th>Description</th></tr></thead><tbody><tr><td>checkBattery(Boolean)</td><td>false</td><td>To allow to check the battery status or not.</td></tr><tr><td>lowBatteryLimit(Float)</td><td>25f</td><td>The minimum percentage of battery charge above which AI analysis can be performed.</td></tr><tr><td>lowBatteryStop(Float)</td><td>15f</td><td>The minimum percentage of battery charge above which video can be recorded.</td></tr><tr><td>interval(Long)</td><td>5000L</td><td>An interval of time for getting battery status in 1 second.</td></tr></tbody></table>
