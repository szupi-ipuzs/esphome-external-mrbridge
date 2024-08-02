## mr_bridge
This is a simple Motor/Relay pulse bridge that drives specified GPIO outputs for a specified period of time.
Such implementation is actually used for controlling latching relays in Tuya switches. I also used it succesfully in Tuya valve.

### Usage:
1. Add this external component to your yaml

``` yaml
external_components:
  - source: github://szupi-ipuzs/esphome-external-components
    components: mr_bridge
```

2. Add a switch and specify 2 gpio outputs as `pin_forward` and `pin_reverse`. You also need to define `pulse_length` which specifies the time (in ms) during which the outputs should be driven high. The allowed range is 10ms - 10000ms (10 seconds).\
Additional optional `optimistic` parameter (True/False) specifies if the switch state should be changed immediately (True) or only after the pulse is finished (False). The default is True.

``` yaml
switch:
  - platform: mr_bridge
    id: test_mrbridge_switch
    name: "Test M/R bridge"
    pin_forward: GPIO16
    pin_reverse: GPIO17
    pulse_length: 1000ms
    optimistic: False
```
