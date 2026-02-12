# Rainy 75 VIA v2 JSON Fix

The official JSON definition files distributed by [WOBKEY](https://www.wobkey.com/pages/rainy_75_support) for the Rainy 75 keyboard are incompatible with VIA v2, causing the following errors:

```
Fetching v2 definition failed
RGB-USB Rainy 75-USB.JSON Object: should NOT have additional properties
RGB-USB Rainy 75-USB.JSON Object: should have required property 'lighting'
```

This repository provides fixed JSON files that work with VIA v2.

## What Was Wrong

| Issue | Affected Files |
|---|---|
| Two JSON objects concatenated in a single file (invalid JSON) | `RGB-USB` |
| `keycodes` and `menus` properties (v3-only, rejected by v2 schema) | `RGB-USB`, `RGB-2.4G` |
| Missing required `lighting` property for v2 | All files |

## Fixed Files

| Connection | Model | File |
|---|---|---|
| USB | Standard / Pro (RGB) | `RGB-USB-Rainy75-USB-v2.json` |
| USB | Lite (Non-RGB) | `NonRGB-USB-Rainy-75-USB-3.0-v2.json` |
| 2.4G | Standard / Pro (RGB) | `RGB-2.4G-Rainy-75-2.4G-v2.json` |
| 2.4G | Lite (Non-RGB) | `NonRGB-2.4G-Rainy-75-2.4G-3.0-v2.json` |

### Device IDs

- USB variants: VID `0x320F` / PID `0x5055`
- 2.4G variants: VID `0x320F` / PID `0x5088`

## Setup Instructions

### 1. Connect Your Keyboard

Connect the Rainy 75 to your computer via **USB cable**. VIA requires a wired connection.

### 2. Open VIA

Go to [usevia.app](https://usevia.app) in **Google Chrome** (WebHID is required).

### 3. Enable Design Tab

Navigate to **Settings** (gear icon) and toggle **Show Design tab** to ON.

### 4. Load the JSON Definition

1. Click the **Design** tab
2. Drag and drop the appropriate `-v2.json` file for your model and connection type
3. If loaded successfully, the keyboard layout will appear with no errors

### 5. Configure Your Keymap

Switch to the **Configure** tab. You should now see your Rainy 75 layout and can remap keys.

## Notes

- The `lighting` property is set to `"none"` in all fixed files. RGB lighting control is not available through VIA with these definitions. Use the keyboard's built-in FN shortcuts to change lighting effects instead.
- The original files from WOBKEY are kept as-is for reference.
- These fixes were tested against VIA v2 schema validation.

## Troubleshooting

### Keyboard not detected

- Make sure you are using a **USB cable** (not 2.4G or Bluetooth)
- Try a different USB port or cable
- Reload the VIA web app and re-import the JSON file

### GMMK Numpad misidentification

- Ensure the JSON file matches your connection type (USB vs 2.4G)
- Clear VIA cache: open browser DevTools (F12) > Application > Clear site data

### FN key not working / F4 blinking green

This indicates a firmware issue. Follow the recovery steps:

1. Disconnect the keyboard
2. Flip the toggle switch under the Caps Lock keycap to **OFF**
3. Hold **ESC** and reconnect via USB (enters recovery mode)
4. Download the correct firmware from [WOBKEY Support](https://www.wobkey.com/pages/rainy_75_support) and run the updater
5. After completion, flip the switch back to **ON**

## Links

- [WOBKEY Rainy 75 Support](https://www.wobkey.com/pages/rainy_75_support)
- [VIA Web App](https://usevia.app)
- [VIA v2 vs v3 Definition Issue](https://github.com/the-via/app/issues/184)
