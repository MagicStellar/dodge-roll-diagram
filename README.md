# Dodge Roll System

A compact overview of an 8-way dodge roll system in Unreal Engine using C++ and Mover.

```mermaid
flowchart TD
    input["Dodge input"] --> check{"Can dodge?"}
    check -->|No| ignore["Ignore request"]
    check -->|Yes| direction["Lock direction • Forward if idle"]
    direction --> move["Queue Mover dodge"]
    move --> animation["Play matching 8-way montage"]
    animation --> finish["Duration ends → Clear dodge state"]

    data[("Dodge Data Asset")]
    data -.->|"Distance + duration"| move
    data -.->|"Directional montages"| animation
    data -.->|"Duration"| finish
```

**Can dodge?** checks that the character is grounded, is not already dodging, and has a valid setup.

The configurable Dodge Data Asset supplies dodge distance, duration, and the montage for each of the eight directions.
