# CW Paddle Input

To use a CW paddle with your radio, you need to pick how the paddle connects to it. There are two options, and which one is right for you depends on whether you're willing to open up the radio.

If you're not sure which radio model you have, follow the [radio identification guide](identify-your-radio.md) first.

## Cable or rework?

| You want to... | Choice | Tradeoff |
| --- | --- | --- |
| Avoid opening the radio | Get or make a custom cable: [CEC cable](cec-cable.md) for v1, [USB-C to TRS cable](usb-trs-cable.md) for v3/K1 | Paddle works with a purpose-built cable only, and you still have to build or acquire a cable |
| Use any off-the-shelf TRS paddle cable | [Perform the rework](rework-overview.md) | Requires opening the case and soldering |

!!! danger "Important"
    When CW mode is used with port-based input modes or the CEC cable mode, the serial port will not behave correctly while the main firmware is running. That affects CHIRP programming. Switch out of CW or out of the port input mode before using a memory programmer. The port will work normally when you boot the radio in bootloader (flash) mode.

## FAQs

### Is CEC cable input the same thing as the paddle rework?

No. CEC cable input is a separate CW input mode, which does not require opening up the radio and making a rework. However, CEC requires a custom cable to the paddle in order to work, and the CEC input mode is only valid on UVK5 v1 radios. The circuits of the K5 v3 and K1 does not support the tricks used in the CEC cable — instead those models support a [USB-C to TRS cable](usb-trs-cable.md) that does a similar job over their USB-C port. See the [CEC paddle cable page](cec-cable.md) for how it works and how to build one.

### How is the microphone affected by the rework?

The internal mic still works when the paddle is unplugged, but the PTT button of an external mic won't work anymore. Also, mics and other accessories that plug into the headset port will no longer receive +5v. While I don't know of specific accessories that need this, it could be used for example to light up buttons on an external mic.

!!! Note
    Voice modes (like FM) require the paddle be **unplugged** from the headset port, otherwise the internal mic will be disconnected and not function correctly. Unplug it when you're in a voice mode and plug it back in for CW.

### How is serial port (CHIRP programming) affected by the rework?

Serial programming will still work like normal, but the radio must be in a non-CW mode, or the CW input mode must be changed away from a port mode. While in CW modulation with a port input mode, the firmware will change the port configuration in a way that makes serial port CHIRP programming fail to connect to the computer.

Bootloader flashing mode (powering on the radio with PTT held) is not affected by the rework.

### When is CW input valid / What does the message "CW KEY STUCK" mean?

Whenever a port or CEC input mode is picked from the menu, or whenever the radio powers on with a port/CEC input mode set, the firmware will check the port to ensure the paddle keys are not stuck closed. If it reads a stuck closed condition, it will show the screen "CW KEY STUCK". This will also disable that input mode until the next power off/on (or it will ignore that menu choice, if this happens when choosing a new input mode from the menu). Power off the radio, resolve the issue, and power on again.

If you try to pick a port input mode without the rework in place, you will also get this message. If you tried to perform the rework and are getting this message when there is no key closed or connected, then you should double-check the resistors have been removed correctly per the rework instructions.

After the hardware is wired correctly, CW input works whenever the radio is in CW mode and the configured input mode is set.

!!! Note
    The "CW KEY STUCK" also commonly occurs if you program the radio from bootloader mode. After programming is complete, the radio self-reboots into the firmware, and if a port input mode is set (like CEC input) while the programming cable is still plugged in, you may see this message on reboot. Disconnect the programming cable and flip the radio off and on again, and it will reboot with the same input mode still enabled, but it will no longer be tripped by the programming cable to detect a stuck key.

## Next

- [CEC paddle cable (UV-K5 v1)](cec-cable.md)
- [USB-C to TRS cable (UV-K5 v3 / UV-K1)](usb-trs-cable.md)
- [Paddle rework overview](rework-overview.md)
