# GIZO Orientation Setting

## Overview

Screen orientation refers to the orientation of the screen of device, which can be either portrait (vertical) or landscape (horizontal). Proper orientation of the device is essential for AI analysis and recoding video. A proper orientation of the device means landscape orientation (horizontal) with +y axis parallel to the the +y axis of the vehicle coordinates system. For more information regarding device and vehicle coordinates systems, see coordinates system page in the [appendix](broken-reference).

You can add the following block of code in the Application class, onCreate function, inside Gizo.initialize to set the orientation settings.

{% tabs %}
{% tab title="Swift" %}
<pre class="language-swift"><code class="lang-swift"><strong>let options: GizoAppOptions = GizoAppOptions()
</strong>options.orientationSetting.allowGravitySensor = true
</code></pre>
{% endtab %}
{% endtabs %}

The orientationSetting sets the orientation-related property, which is:

* <mark style="color:blue;">allowGravitySensor</mark>(true): Enabling the Gravity sensor.

<mark style="color:green;">**Gravity sensor**</mark>**:** It refers to gravitational part of the measured accelerometer forces excluding the effect of linear accelerations.

Here is the available option that can be set in orientationSetting in the Application class:

<table><thead><tr><th width="227">Options</th><th width="141.33333333333331">Default Value</th><th>Descriptions</th></tr></thead><tbody><tr><td><p>allowGravitySensor</p><p>(Boolean)</p></td><td>false</td><td>To activate the gravity sensor or not.</td></tr></tbody></table>
