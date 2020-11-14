
Features:
 - Supports switching the light to rhythm mode! (rhythm is defined as a scene for HA)
 - Implements a pattern of sending multiple command UDP datagrams until response is received
 - Consolidates getPilot and setPilot calls using a PilotBuilder and PilotParser. Removes unnecessary UDP calls for each and every attribute (color, temperature, brightness, scene, etc.) and makes a combined getPilot/setPilot call
 - enhanced debug logging for UDP

This component does need a dependency on `pywizlight` like @sbidy's component which will be install automatically by Home Assistant.

## Bulbs
| Bulb Type | Dimmer | Color Temp | Effects | RGB | Tested? | Example Product |
|-----------|--------|------------|---------|-----|-----|-----|
| ESP01_SHDW_01 | X  |   |   |   |  | |
| ESP01_SHRGB1C_31 | X | X  | X | X | x | Phillips 555623 recessed |
| ESP01_SHTW1C_31 | X | X |   |   | X | Phillips 555599 recessed |
| ESP56_SHTW3_01 | X |  X  | X  |   | X | |
| ESP01_SHRGB_03 | X | X | X | X | X | |
| ESP01_SHDW1_31 | X |  |  |  |  | |
| ESP15_SHTW1_01I | X | X |  |  | |
| ESP03_SHRGB1W_01 | X | X | X | X | X | Philips Color &. Tunable-White A21 |
| ESP06_SHDW9_01 | X |  |  |  | X | Philips Soft White A19 |

Please report as issue your builb type with a feature list:

`echo '{"method":"getSystemConfig","params":{}}' | nc -u -w 1 <YOU BULB IP> 38899`

## Working features 
 - Brightness
 - Color (RGB)
 - White Color Temperature
 - On/Off, Toggle
 - Effects
 - Setting a rhythm as a scene

## Next improvement:
- testing with other hardware -- **Contribution required !!**
- Config Flow Support


## Install for testing 

1. Loggon to your HA or HASS with SSH
2. Got to the HA `custom_components` directory within the HA installation path (if this is not available - create this directory).
3. Run `cd custom_components`
4. Run `git clone https://github.com/sbidy/wiz_light` within the `custom_components` directory
5. Run `mv wiz_light/custom_components/wiz_light/* wiz_light/` to move the files in the correct diretory
6. Restart your HA/HASS service in the UI with `<your-URL>/config/server_control`
7. Add the bulbs to your `configuration.yaml` - You can not add the bulbs in the HA UI!! (configFlow is missing)

As an alternativ you can use the HACS platform for installation - see [HACS Website](https://hacs.xyz)

Questions? Check out the github project [pywizlight](https://github.com/sbidy/pywizlight)

## Testing
See `main.py` for how the underlying API works
