# mqtt-wrapper

[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://www.webcomponents.org/element/hobbyquaker/mqtt-wrapper)

Polymer Element that wraps other Elements and links them to MQTT topics.


## Installation

`bower install hobbyquaker/mqtt-wrapper`


## Usage

### Attributes



### Examples

Wrapping a paper-toggle-button and linking it to [hue2mqtt.js](https://github.com/hobbyquaker/hue2mqtt.js) 
topics:
```html
<script src="bower_components/webcomponentsjs/webcomponents-lite.js"></script>

<link rel="import" href="bower_components/polymer/polymer.html">
<link rel="import" href="bower_components/paper-toggle-button/paper-toggle-button.html">
<link rel="import" href="bower_components/mqtt-connection/mqtt-connection.html">
<link rel="import" href="bower_components/mqtt-wrapper/mqtt-wrapper.html">

<mqtt-connection host="microserver" port="8080"></mqtt-connection>

<mqtt-wrapper
        sub='{"hue/status/lights/Hobbyraum/on":{"attribute":"checked","json":"val","type":"boolean"}}'
        pub='{"change":{"topic":"hue/set/lights/Hobbyraum/on","attribute":"checked"}}'>
        
    <paper-toggle-button></paper-toggle-button>
    
</mqtt-wrapper>
```

Inserts a topics value as innerHTML to the wrapped element:
```html
<mqtt-wrapper sub='{"var/status/Infobox":{"content":"html"}}'>
    <div></div>
</mqtt-wrapper>
```


## License

MIT (c) Sebastian Raff
