---
layout: default
sidebar: yes
permalink: /docs/studio/Widgets/
---

Most widgets are backed by a PV. Some widgets (e.g. layouting widgets) are typically not connected to a PV, other widgets (e.g. charts) can be backed by more than one PV.

### Color Decorations
When a widget is backed by a PV, it will be decorated according to its runtime state. The specific colors of these decorations can vary since the default colors can be overriden (or disabled) by the display author.

<table class="inline">
    <tr>
        <th>State</th>
        <th>Decoration</th>
    </tr>
    <tr>
        <td>Connected</td>
        <td>No decorations</td>
    </tr>
    <tr>
        <td style="white-space: nowrap;">Connected, but no value (yet)</td>
        <td>Dashed pink border around the widget</td>
    </tr>
    <tr>
        <td>Disconnected</td>
        <td>
            Solid pink border around the widget and the label 'Disconnected' in the top left corner (space-permitting)
        </td>
    </tr>
    <tr>
        <td>Expired</td>
        <td>
            Blinking solid pink border around the widget 
        </td>
    </tr>
    <tr>
        <td>Minor Alarm</td>
        <td>Solid orange border around the widget</td>
    </tr>
    <tr>
        <td>Major Alarm</td>
        <td>Solid red border around the widget</td>
    </tr>
</table>

Note that the color-information for alarms is currently not as rich as it could be. Yamcs parameters support five different levels of alarms, as well as a range of special monitoring values. This information is transformed using the following mapping:

<table class="inline nostretch">
    <tr>
        <th>Yamcs Server</th>
        <th style="text-align: center;" width="200">Yamcs Studio</th>
    </tr>
    <tr>
        <td>
            WATCH<br>
            WATCH_LOW<br>
            WATCH_HIGH
        </td>
        <td rowspan="3" style="text-align: center;">
            MINOR
        </td>
    </tr>
    <tr>
        <td>
            WARNING<br>
            WARNING_LOW<br>
            WARNING_HIGH
        </td>
    </tr>
    <tr>
        <td>
            DISTRESS<br>
            DISTRESS_LOW<br>
            DISTRESS_HIGH
        </td>
    </tr>
    <tr>
        <td>
            CRITICAL<br>
            CRITICAL_LOW<br>
            CRITICAL_HIGH
        </td>
        <td rowspan="2" style="text-align: center;">
            MAJOR
        </td>
    </tr>
    <tr>
        <td>
            SEVERE<br>
            SEVERE_LOW<br>
            SEVERE_HIGH
        </td>
    </tr>
</table>

The original Yamcs alarm state can however still be viewed by right clicking and opening **PV Info**.

### Library
We limit ourselves to liting the default widgets. Their runtime behaviour should be fairly straightforward. Their various properties are detailed in [Widget Properties](/docs/studio/Widget_Properties/), when we address the OPI Editor.

#### Graphics

<table class="inline image-overview">
    <tr>
        <td width="33%"><img src="/assets/studio/icons/widgets/arc.png">Arc</td>
        <td width="33%"><img src="/assets/studio/icons/widgets/rectangle2.png">Rectangle</td>
        <td width="33%"><img src="/assets/studio/icons/widgets/label.png">Label</td>
    </tr>
    <tr>
        <td><img src="/assets/studio/icons/widgets/polyline.gif">Polyline</td>
        <td><img src="/assets/studio/icons/widgets/roundedRectangle.png">Rounded Rectangle</td>
        <td><img src="/assets/studio/icons/widgets/image.gif">Image</td>
    </tr>
    <tr>
        <td><img src="/assets/studio/icons/widgets/polygon.png">Polygon</td>
        <td><img src="/assets/studio/icons/widgets/ellipse2.png">Ellipse</td>
        <td></td>
    </tr>
</table>

#### Monitors

<table class="inline image-overview">
    <tr>
        <td width="33%"><img src="/assets/studio/icons/widgets/LED.png">LED</td>
        <td width="33%"><img src="/assets/studio/icons/widgets/ProgressBar.gif">Progress Bar</td>
        <td width="33%"><img src="/assets/studio/icons/widgets/XYGraph.gif">XY Graph</td>
    </tr>
    <tr>
        <td><img src="/assets/studio/icons/widgets/imageBooleanindicator.gif">Image Boolean Indicator</td>
        <td><img src="/assets/studio/icons/widgets/gauge2.png">Gauge</td>
        <td><img src="/assets/studio/icons/widgets/intensityGraph.png">Intensity Graph</td>
    </tr>
    <tr>
        <td><img src="/assets/studio/icons/widgets/textUpdate.png">Text Update</td>
        <td><img src="/assets/studio/icons/widgets/thermo.gif">Thermometer</td>
        <td><img src="/assets/studio/icons/widgets/ByteMonitor.png">Byte Monitor</td>
    </tr>
    <tr>
        <td><img src="/assets/studio/icons/widgets/XMeter.png">Meter</td>
        <td><img src="/assets/studio/icons/widgets/tank.png">Tank</td>
        <td></td>
    </tr>
</table>

#### Controls

<table class="inline image-overview">
    <tr>
        <td width="33%"><img src="/assets/studio/icons/widgets/actionbutton.gif">Action Button</td>
        <td width="33%"><img src="/assets/studio/icons/widgets/knob.gif">Knob</td>
        <td width="33%"><img src="/assets/studio/icons/widgets/imageButton.gif">Image Boolean Button</td>
    </tr>
    <tr>
        <td><img src="/assets/studio/icons/widgets/menubutton.gif">Menu Button</td>
        <td><img src="/assets/studio/icons/widgets/scrollbar.png">Scrollbar</td>
        <td><img src="/assets/studio/icons/widgets/checkboxenabledon.gif">Check Box</td>
    </tr>
    <tr>
        <td><img src="/assets/studio/icons/widgets/textinput.png">Text Input</td>
        <td><img src="/assets/studio/icons/widgets/thumbwheel.gif">Thumb Wheel</td>
        <td><img src="/assets/studio/icons/widgets/radiobutton.gif">Radio Box</td>
    </tr>
    <tr>
        <td><img src="/assets/studio/icons/widgets/Spinner.gif">Spinner</td>
        <td><img src="/assets/studio/icons/widgets/BoolSwitch.gif">Boolean Switch</td>
        <td><img src="/assets/studio/icons/widgets/ChoiceButton.png">Choice Button</td>
    </tr>
    <tr>
        <td><img src="/assets/studio/icons/widgets/scaled_slider.gif">Scaled Slider</td>
        <td><img src="/assets/studio/icons/widgets/BoolButton.gif">Boolean Button</td>
        <td><img src="/assets/studio/icons/widgets/combo.gif">Combo</td>
    </tr>
</table>

#### Others

<table class="inline image-overview">
    <tr>
        <td width="33%"><img src="/assets/studio/icons/widgets/table.gif">Table</td>
        <td width="33%"><img src="/assets/studio/icons/widgets/groupContainer.png">Grouping Container</td>
        <td width="33%"><img src="/assets/studio/icons/widgets/SashContainer.png">Sash Container</td>
    </tr>
    <tr>
        <td><img src="/assets/studio/icons/widgets/web_browser.png">Web Browser</td>
        <td><img src="/assets/studio/icons/widgets/linkingcontainer.png">Linking Container</td>
        <td><img src="/assets/studio/icons/widgets/grid.gif">Grid Layout</td>
    </tr>
    <tr>
        <td><img src="/assets/studio/icons/widgets/array.gif">Array</td>
        <td><img src="/assets/studio/icons/widgets/tab.png">Tabbed Container</td>
        <td></td>
    </tr>
</table>
