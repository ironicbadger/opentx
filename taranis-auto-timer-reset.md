# Taranis Automatic Timer Reset

After watching a video from StingerSwarm on how to reset flight timers automatically, his method didn't quite work for me as it relied on RSSI - which doesn't reset on the XSR as it doesn't reset on the X4R-SB. Using VFAS < 16.7v (a fully charged 4S Lipo) as the conditional works just as well.

## Logical Switches

| Logical Switch | Function | V1   | V2       | AND switch |
|----------------|----------|------|----------|------------|
| L1             | a=x      | VFAS | `16.70V` |            |
| L2             | a=x      | VFAS | `16.80V` |            |
| L3             | a<x      | Tmr1 | `5:00`   |            |
| L4             | OR       | L1   | L2       |            |
| L5             | AND      | L3   | L4       | SF(up)     |

* SF is my ARM switch in this example, the switch must be 'armed' for L5 to activate.
