NR7Y CW firmware README

> [!IMPORTANT]
> This firmware only works on "V3" hardware or the K1 radio. Most (nearly all) V3 radios are marked as such on the label under the battery, and are often marketed as V3 specifically. K1 means either model, the UV-K1 or UV-K1(8).

The flash tool you use must support the V3/K1 hardware. I suggest flashing using the web site [F4HWN's UVTools2](https://armel.github.io/uvtools2/). Chrome is required.

> [!NOTE]
> After flashing, I *strongly advise* resetting the eeprom to ensure there are no lingering settings from other firmware versions. 
 1. Hold down PTT and Side Button 1 while turning the radio on.
 2. Release buttons, menu will be automatically presented.
 3. Go up to Reset and pick ALL. 

# CW (Morse Code) Firmware Mod Guide

This firmware is built on top of [Armel (F4HWN)'s Fusion firmware](https://github.com/armel/uv-k5-firmware-custom), which adds a large number of enhancements over the base egzumer firmware. For documentation on those features, visit the [F4HWN wiki](https://github.com/armel/uv-k5-firmware-custom/wiki).

This guide describes the CW (Continuous Wave / Morse Code) menu options added to the firmware.

## Accessing CW Mode

1. Set your VFO modulation to **CW** mode (in the modulation menu), or long-press **0 (FM)** to change modulations
2. Configure CW parameters in the menu system (Menu > CWfreq, CWvol, etc.)
3. PTT is a CW straight key by default

## Code Practice Oscillator (CPO)

The CPO mode provides local practice: no RX or TX, sidetone only, on-screen decode while you send.
- Launch with **Function then long-press 5** while in CW mode
- Exit by tapping **EXIT**
- Use the Up/Down keys to adjust WPM, which will save on exit
- Tap **'*'** to keep the backlight on/off
- Tap **4** to enable/disable flashlight sending

## CW Menu Options

#### CWfreq - CW Sidetone Frequency

Sets the audio frequency for the CW sidetone heard locally when transmitting. This is also used as the BFO (Beat Frequency Oscillator) offset when receiving CW signals.

#### CWvol - CW Sidetone Volume Level

Controls the volume level of the CW sidetone heard when transmitting. The lowest value is "OFF"

#### CWkmod - CW Keyer Mode

Selects the keyer mode when using paddle inputs (dual-lever key). These modes are modeled after Elecraft mode A/B behavior. 

**Note:** Keyer mode only applies when using paddle inputs (buttons or port paddles). When using handkey modes, the keyer is disabled and this setting has no effect.

#### CWwpm - CW Speed (Words Per Minute)

Sets the sending speed for the automatic iambic keyer in Words Per Minute. The range is 10 to 40 WPM.

**Note:** Speed only applies when using paddle inputs with the iambic keyer enabled. Handkey modes follow your manual keying speed.

#### CWkin - CW Key Input Configuration

Configures how the CW input signals are connected and interpreted.

**Note:** The port modes require an iambic key rework inside the radio. If you have already done the original straight key mod and wish to keep it, this will continue to work with "PTT HandKey" or "Side Btn Iambic".

**Note:** PTT is always active as a keyer input regardless of mode — this is a consequence of the wiring.

#### Input Options:

**1. PTT HandKey**
- PTT as a straight key (default)

**2. Port HandKey**
- Straight key via 3.5mm port (with rework); PTT is also active as straight key

**3. Side Btn Iambic**
- PTT = DAH, Side Button 1 = DIT

**4. Side Btn Iambic Reversed**
- PTT = DIT, Side Button 1 = DAH

**5. Port Iambic**
- Port tip = DIT, port ring = DAH; PTT also active as DAH

**6. Port Iambic Reversed**
- Port tip = DAH, port ring = DIT; PTT also active as DIT

**7. Port+Btn Iambic**
- Port tip or PTT = DAH; port ring or Side Button 1 = DIT

**8. Port+Btn Iambic Reversed**
- Port tip or PTT = DIT; port ring or Side Button 1 = DAH

#### CWmsg1 / CWmsg2 / CWmsg3 / CWmsg4 - CW Message Recording and Playback

Messages 1-4 may store up to 46 characters for playback (not including spaces).

Messages start empty - enter the menu and use arrows to change macro option:
- record new? - Select with 'menu' button to begin recording
- play - Select with 'menu' button to begin playback

### CW Message Recording
- Recordings are made using the currently programmed keyer settings and wpm. Attempting to record while not in CW modulation or without a keyer (while in handkey mode) will not work.
- RF is not transmitted while recording. 
- While recording is in progress, the display will show the most recently recorded characters, and a macro character count. 
- To save the macro when complete, Push the 'menu' button. 
- To exit the recording without saving, push the 'exit' button.

### CW Message Playback
There are two ways to playback the CW messages:
- Enter the menu selection for the given message, and change using up/down to 'Play', then select with 'menu' button. Playback will begin. Change using up/down to 'Repeat' and select with the 'menu' button to start repeating the message.
- Assign playback to an action button (side buttons or Menu button):
  - In the menu system choose one of menu items 23 through 27 to assign playback or repeat to side button 1 or 2 short press, 1 or 2 long press, or Menu button long press. Keep in mind that Side Button 1 is unavailable for macro sending when set as a keyer button. The assigned action is ignored.
  - After choosing the button menu item, from the action list pick "PLAY CW MSG1/2/3/4" to play the message one time for each button push, or pick "REPEAT CW MSG1/2/3/4" to activate a repeating playback for the given message.
- During message playback, the display will show the characters being sent, and a flashing arrow on the left side to indicate a message is being played. If Repeat mode is activated, the message will begin sending again after the delay time has expired.
- Message playback can be interrupted by tapping a keyer key or any keyboard key. This will also stop repeating.

#### CWmrpt - CW Message Repeat

Selects number of seconds to delay before sending the message again, when in repeat.

#### CWbkin - CW Break-In

Controls break-in. When OFF, RF TX is blocked but sidetone still plays so you can hear yourself key while monitoring RX. When Break-In is active, the top of the main screen shows **'BK'**. When Break-In is disabled, this indicator goes away.

CW break-in can also be toggled by a long-press on the **7/VOX** button while in CW mode.

**Last Updated**: May 23, 2026
