# Q-SYS Samsung Display Controller

> ?? **This plugin is currently untested and in active development.** Features may change, and behavior on live hardware has not been fully validated. Use at your own risk and please report any issues.


This repository contains a Q-SYS plugin (`QSYS-Samsung_Display_Controller.qplug`) designed to control Samsung Commercial Displays over Ethernet (TCP) or RS-232 using the Samsung MDC binary protocol.

## Features

- **Comprehensive Control**: Supports Power, Volume, Mute, Screen Mute, Brightness, and Contrast.
- **Input Switching**: Built-in logic to switch between standard Samsung input sources (HDMI, DP, MagicInfo, URL Launcher, etc.).
- **Virtual Remote**: A dedicated tab simulating the physical IR remote, including a full Number Pad, Navigation D-Pad, Menu buttons, and direct channel tuning macros.
- **State-Aware UI**: Prevents unintentional toggle states; the UI correctly reflects display feedback and ignores errant user clicks if the hardware state differs.
- **Startup Logic**: Allows you to configure a "Startup Source" and "Startup Mute" state when the display powers on. If the display is off and a source is selected, it will queue the source command and execute it once the display has powered on.
- **Wake on LAN**: Built-in magic packet transmission for displays that support Network Standby.

## Connection Setup

### Ethernet (TCP/IP)
1. In the display menu, go to **System → Multi Control → MDC Connection** and set it to **RJ45 MDC**.
2. Go to **Home → More Settings → System → Power Control → Network Standby** and set it to **On**. This allows the display to be powered on via TCP while in standby.
3. In Q-SYS, set the Connection Type to **TCP** and enter the display's IP Address.
4. The plugin connects over TCP port **1515** by default.

### RS-232
1. Connect a serial cable to the RS-232C port.
2. Ensure the display's MDC connection is set to RS-232.
3. In Q-SYS, set the Connection Type to **RS-232** and wire the `Serial Port` pin to your Q-SYS serial component. (Baud: 9600, Data: 8, Parity: None, Stop: 1).

### Set ID
Samsung displays use an ID for communication (1-99). Ensure the plugin's "Set ID" property matches the ID configured in the display's System menu. You can use ID `254` for Broadcast to control all daisy-chained displays simultaneously.

## Installation

1. Download `QSYS-Samsung_Display_Controller.qplug`.
2. Move it to your Q-SYS Designer plugins directory:
   `Documents\QSC\Q-Sys Designer\Plugins`
3. Restart Q-SYS Designer to access the plugin in the schematic elements.

## Release Notes
- **v1.0.0.007**: Initial release. Migrated from LG display architecture to Samsung binary MDC protocol. Added full virtual remote and state-aware command buffering.
