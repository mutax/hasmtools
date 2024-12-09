# hasmtools

A small tool to help me working with the Finite State Machine Sensor for Home Assistant by
generating a png and converting the definition between JSON and YAML.

See https://github.com/edalquist/ha_state_machine for the Sensor.

# Features

* write your definition in YAML instead of JSON
* convert from YAML to JSON and back
* generate an image of the state machine using graphviz

# Examples

## YAML input file

```yaml
initial:
  a: state2
  b: state3
state2:
  a: initial
  b: state3
state3:
  a: initial
  b: state2
```
Note that in yaml the first state is the default/initial state.

## Converted to JSON

```
 $ hasmtool example.yaml example.json
```

```json
{
    "state": {
        "status": "initial"
    },
    "transitions": {
        "initial": {
            "a": "state2",
            "b": "state3"
        },
        "state2": {
            "a": "initial",
            "b": "state3"
        },
        "state3": {
            "a": "initial",
            "b": "state2"
        }
    }
}
```

## Finally converted to PNG

```
 $ hasmtool example.json example.png
```

![FSM example](example.png)



# Status

Working MVP.

# Why Did I Do This?

It started with the desire to have a visualization of the FSM, then I realised I like yaml more than json for it, so one thing led to another...
