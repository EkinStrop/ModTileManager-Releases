# Mod Tile Manager

**by @JohnTheFarm3r**

Mod Tile Manager lets you import camera mods and control them from Quick Settings tiles, enabling or disabling mods on the fly — without rebooting.

It extracts mod packages, mounts and applies files live using root privileges, and gives each mod its own Quick Tile for instant toggling.

The app also supports **Custom Mods** (experimental) for non-camera modifications, such as display calibration configs or other system tweaks that can be toggled by restarting a specific service.

---

## What Are Camera Mods?

Camera mods are often distributed as Magisk or KSU modules (zip files) that modify camera libraries or binaries to change sensor behavior.

Mods can enable features such as:
- DCG (Dual Conversion Gain)
- ISZ, LN, QHDR
- HFR (High Frame Rate)
- Access to full resolution output for third-party apps
- Other sensor-dependent features

Root managers apply these modules systemlessly on top of stock OS files so the original files are not permanently altered. Typically, mods require a reboot when enabled or disabled via the root manager.

---

## How It Differs From Root Managers

Unlike flashing mods in Kitsune, Magisk, KSU or other Root Managers:

- **No reboot required** — The app mounts and applies mod files live using root, so you can switch mods on or off without restarting your device.
- **Quick toggles** — Each imported mod can get its own Quick Tile for instant activation or deactivation.
- **Multiple mods** — The app supports up to 50 mods, meaning up to 50 customizable tiles.
- **Custom vendor properties** — You can set vendor properties such as sensor mode to alter sensor behavior.
- **Temporary and flexible** — You do not need to keep mods permanently active in your root manager.

Most root managers (Magisk, KSU, KSUN, Magisk Alpha) cannot mount files to the `/ODM` partition. On many modern devices, key camera-related files are stored there, which means flashing camera mods often fails or works only partially.

The only known alternative capable of mounting to `/ODM` is Kitsune (a Magisk fork), but it is outdated and may cause issues with newer Android versions.

---

## Why That Matters (Example)

Imagine you want to use a DCG mod with MotionCam, but also occasionally shoot with the stock camera.

If you flash the mod in Magisk or KSU, switching between mods normally requires a reboot each time. Many mods also break stock camera behavior or only work with apps that can access RAW streams (MotionCam, GCam, PhotonCam, OpenCam).

With Mod Tile Manager you can:
- Enable the DCG mod for MotionCam using a Quick Tile
- Disable it immediately afterwards to use the stock camera
- All without rebooting and without permanently altering the system

---

## Requirements

- **Root access** is required. Applying patched files on top of the OS requires root, and there is no practical workaround because Android's security model prevents live alterations otherwise.
- **Minimum Android version:** Android 14 (the app will not work on earlier versions due to system-level changes and restrictions).
- Device support is not limited to specific models. While development focused on Xiaomi Ultra devices, Mod Tile Manager should work on any rooted Android 14+ device.

---

## Getting Started

1. Install the APK from the [Releases](https://github.com/EkinStrop/ModTileManager/releases) page.
2. Before launching the app, open your root manager and make sure that **Global Namespace Mount** is enabled. This allows files mounted by the app to be visible outside its own namespace.
3. If you are using KSU or a fork (KSUN, KSU Apatch), the option for Global Namespace Mount may not exist. There is an alternative method inside Mod Tile Manager itself (see First Launch Setup below).

## First Launch Setup

When you open Mod Tile Manager for the first time:

- The app will request root access, which you must grant.
- It will also ask for permission to display overlays and show notifications.

Enable both options so you can receive detailed feedback through overlays and notifications when activating or deactivating mods via Quick Tiles.

If your Global Namespace is not set correctly, the app will show a warning dialog.

- **For Magisk / Magisk Alpha / Kitsune users:** Make sure you enable Global Namespace in your root manager settings.
- **For KSU or fork users:** You can safely dismiss the warning, then open Side Drawer → Advanced Settings and enable "Use master mount for root commands". This forces files to be mounted globally as a workaround. *(Note: This is an experimental feature.)*

---

## How to Use

### Importing a Camera Mod (ZIP)

If your mod comes as a Magisk or KSU module:

> **Important:** Mods you can import are often called `modname_standalone.zip` or similar. Files named `modname_switcher.zip` or `modname_quicktile.zip` will **NOT** work.

1. Tap **Import Camera MOD** on a tile card
2. Select the ZIP file
3. Set a custom tile label (or keep the auto-parsed one)
4. Press **Save**
5. Tap **Add tile to QS**
6. Confirm the system dialog to add the tile to Quick Settings

Your new tile appears in the QS panel — toggle it to activate or deactivate the mod instantly.

### Using Sensor Mode Only

If your mod involves a sensor mode value rather than a ZIP:

1. Toggle **Sensor Mode Only** on a tile card
2. Enter the sensor mode number
3. Press **Save**
4. Set a custom tile label if you wish
5. Tap **Add tile to QS**

Different sensor mode numbers alter camera sensor behavior, enabling features such as DCG, ISZ, and others. The correct number depends on your device, sensor, and OS.

### Custom Mods (Experimental)

Custom Mods extend the app beyond camera modifications to support other system tweaks.

1. Tap **Import Custom MOD** on an empty tile card
2. Select your ZIP file

Key differences from Camera Mods:
- **No exclusivity** — Multiple custom mods can be active simultaneously
- Custom mods can coexist with an active camera mod
- **No camera service restart** — You define which service to restart
- **Custom Command** — A shell command executed on activation and deactivation
- **Auto-activate on boot** — Optionally activate after device boot

> Once imported as a Custom Mod, a tile cannot be changed to a Camera Mod (and vice versa). Delete and re-import if you need to change the type.

---

## Logs & Troubleshooting

Mod Tile Manager keeps a detailed log for each tile.

1. Open Side Drawer → **View Logs**
2. Select the tile you want logs for
3. Tap **Export Logs**
4. The log file will be saved as a text file in the root directory of your main storage

These logs can reveal app errors, mod issues, or incorrect configurations. They are also useful when reporting problems.

---

## Supported Devices

- **Minimum:** Android 14+
- **Root:** Required (Magisk, KSU, KSUN, Kitsune, or any root solution)
- Not limited to specific models — tested primarily on Xiaomi Ultra devices but should work on any rooted Android 14+ device

Compatibility depends on how your OS implements partitions and permissions. If you encounter issues, check the logs for details.

> **Note:** Support is only provided for the Mod Tile Manager app itself, not for third-party mods. If a mod causes instability or breaks camera functionality, that is the responsibility of the mod creator.

---

## Updates

The app includes a built-in update checker. On launch, it automatically checks for new releases from this repository. You can also manually check via **Side Drawer → Check for Updates**.

---

## Credits & Special Thanks

This app wouldn't be what it is without the amazing community that continuously tested, provided feedback, and pushed for improvements.

A very special thanks to **George** for creating the incredible camera mods that power many of these setups, and to **Paulo** for relentless testing and feedback.

### Support George's camera mod work

**BTC:** `3PuPgw2kiouSWjCwGdbpQ77UYh55wNieJ6`

**PayPal:** [paypal.me/GeorgeKiariz](https://paypal.me/GeorgeKiariz)

---

## Community

Join the Telegram community for mods, support, and discussion: [t.me/gcam15u](https://t.me/gcam15u)
