# H-Bridge Driver for 3.3V PWM Input (HI/LO)

This project is a discrete transistor-based H-bridge driver designed to drive loads such as a bi-directional LED string (NOT motors, you *need* to use protection diodes in that case!) using two 3.3V logic-level PWM inputs.

![PCB Layout](images/pcb-layout.png)
![PCB Layout](images/pcb-rendering.png)

## Overview

The circuit takes two complementary (non-overlapping) PWM inputs: `HI_IN` and `LO_IN`, each at 3.3V logic level. These signals are level-shifted and drive a discrete H-bridge output stage composed of NPN and PNP BJTs. The output connects to a load (e.g., LED strip) in a push-pull fashion.

## Inputs

- `HI_IN`: 3.3V logic PWM input (controls left-side NPN-PNP transistors)
- `LO_IN`: 3.3V logic PWM input (controls right-side NPN-PNP transistors)

⚠️ **Important:**  
`HI_IN` and `LO_IN` **must be phase-shifted**, even though the NPN-PNP-pair makes sure shoot-through is impossible. If both are high simultaneously, the output is off.

## Supply

- `+5V`: Power rail for the H-bridge (used to drive the load)
- `GND`: Common ground

## Outputs

- `O1`, `O2`: Differential outputs to the load

## Notes

- Input resistors and capacitors are used for filtering and protection.
- BJTs are used in complementary pairs (NPN/PNP) for each half-bridge.
- I have not yet tested how much current this schematic can tolerate (depending on transistors and thermal limits).
- Load: connected between `O1` and `O2` (e.g., antiparallel LEDs)

## License

Attribution-NonCommercial-ShareAlike 4.0 International

See LICENSE for details, or: https://creativecommons.org/licenses/by-nc-sa/4.0/
