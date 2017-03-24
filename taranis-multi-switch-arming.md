# Taranis Multi-Switch Arming

**PLEASE TEST THIS WITH YOUR PROPS OFF**

How to setup multi switch arming for a Taranis running OpenTX 2.2. The purpose of dual switch arming is primarily safety. 

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Intro](#intro)
- [Logical Switches](#logical-switches)
- [Mixer](#mixer)

<!-- /TOC -->

## Intro

The settings below require first flicking switch SF to the 'armed' position and the holding a momentary switch (SH in this case) for 0.6 seconds before the TX transmits the 'armed' value on CH5 to your aircraft. You might need to change some values such as the actual switches in question to suit your needs, but this should be easy enough to figure out.

## Logical Switches

Setup Logical Switches first, then move onto your Mixer tab. L1-4 are used here, but can be *any* number so long as the relative numbers are kept the same.

Logical Switch | Function | V1          | V2       | AND switch | Duration
---------------|----------|-------------|----------|------------|---------
L1             | Edge     | SH(down)    | [0.6:<<] | SF(down)   | 0.1
L2             | a<x      | I-Thr `-99` |          |            |
L3             | AND      | L1          |          | L2         |
L4             | Stky     | L3          | SF(up)   |            |

## Mixer

Not all values listed, only those that require changing are. The logical switch here controls arming and must match L4 (or whatever yours is) above.

Channel | Mix Name (optional) | Source | Weight | Switch
--------|---------------------|--------|--------|-------------------------
CH5     | Arm                 | MAX    | 100    | L4
CH5 +=  | Arm                 | MAX    | -100   | !L4

* Note to add multiple lines to a single channel, press and hold enter on your Radio.
