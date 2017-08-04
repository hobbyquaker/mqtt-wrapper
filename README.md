# mqtt-wrapper

Polymer Element that wraps other Elements and links them to MQTT topics.


## Installation

`bower install hobbyquaker/mqtt-wrapper`


## Usage

Example wrapping a paper-toggle-button and linking it to hue2mqtt.js topics
```
<mqtt-wrapper
    sub='{"hue/status/lights/Hobbyraum/on":{"attribute":"checked","json":"val","type":"boolean"}}'
    pub='{"change":{"topic":"hue/set/lights/Hobbyraum/on","attribute":"checked"}}'>
    
    <paper-toggle-button></paper-toggle-button>
    
</mqtt-wrapper>
```


## License

MIT (c) Sebastian Raff
