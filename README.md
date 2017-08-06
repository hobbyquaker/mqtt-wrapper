# &lt;mqtt-wrapper&gt;

[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://www.webcomponents.org/element/hobbyquaker/mqtt-wrapper)
![alt text][shield-polymer] 
![alt text][shield-license]

Polymer Element that wraps other Elements and links them to MQTT topics. Needs a `mqtt-connection` element.


## Installation

`bower install hobbyquaker/mqtt-wrapper`


## Imports and mqtt-connection

```html
<script src="bower_components/webcomponentsjs/webcomponents-lite.js"></script>
<link rel="import" href="bower_components/polymer/polymer.html">

<link rel="import" href="bower_components/mqtt-connection/mqtt-connection.html">
<link rel="import" href="bower_components/mqtt-wrapper/mqtt-wrapper.html">

<mqtt-connection host="mqtt-broker" port="8080"></mqtt-connection>
```


## Usage Examples

Inserts the last received message on the MQTT topic `test/info` as innerHTML to the wrapped div:
```html
<mqtt-wrapper sub='[{"topic":"test/info","content":"html"}]'>
    <div></div>
</mqtt-wrapper>
```

Publish the payload `1` on the MQTT topic `test/button` when the wrapped paper-button is clicked:
```html
<mqtt-wrapper pub='[{"event":"click","topic":"test/button","payload":"1"}]'>
    <paper-button>Licht an</paper-button>
</mqtt-wrapper>
```

Wrapping a paper-toggle-button and linking it to [hue2mqtt.js](https://github.com/hobbyquaker/hue2mqtt.js) 
topics to switch a Hue lamp on and off:
```html
<mqtt-wrapper
        sub='[{"topic":"hue/status/lights/Hobbyraum/on","attribute":"checked","json":"val","type":"boolean"}]'
        pub='[{"event":"change","topic":"hue/set/lights/Hobbyraum/on","attribute":"checked"}]'>
        
    <paper-toggle-button></paper-toggle-button>
    
</mqtt-wrapper>
```

Wrapping a paper-slider and linking it to hue2mqtt.js topics to control a Hue lamps brightness. Slider will be disabled
when the lamp is off:
```html
<mqtt-wrapper
        sub='[{"topic":"hue/status/lights/Hobbyraum/bri","attribute":"value","json":"val","disable":"dragging"},{"topic":"hue/status/lights/Hobbyraum/on","attribute":"disabled","json":"val","type":"boolean","negate":true}]'
        pub='[{"event":"change","topic":"hue/set/lights/Hobbyraum/bri","attribute":"value"},{"event":"immediate-value-change","topic":"hue/set/lights/Hobbyraum/bri","attribute":"immediateValue"}]'>

    <paper-slider max="254"></paper-slider>

</mqtt-wrapper>
```

## License

MIT (c) Sebastian Raff

[shield-license]: https://img.shields.io/badge/license-MIT-blue.svg "License: MIT"
[shield-polymer]: https://img.shields.io/badge/polymer%20version-2.0-green.svg "Polymer Version: 2.0"
