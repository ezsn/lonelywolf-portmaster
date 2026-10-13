## Notes

Thanks to [NomnomNami](https://nomnomnami.com/) for creating [LONELY WOLF TREAT](https://nomnomnami.itch.io/treat-complete), a heartwarming story about a wolf who moves into a town full of rabbits and an unexpected friendship that begins with a delicious curry.

**Playable.** This port uses mkxp-z, an open reimplementation of the RGSS runtime for RPG Maker VX Ace games. Compatibility may vary depending on the game files and handheld firmware.

Only the engine is included in the port. You must provide the game files from your own copy.

## Contents

- [Installing](#installing)
  - [1. Install the port](#1-install-the-port)
  - [2. Prepare the game files](#2-prepare-the-game-files)
  - [3. Copy the game files](#3-copy-the-game-files)
  - [4. Play](#4-play)
- [The patches folder](#the-patches-folder)
- [Controls](#controls)
- [Compile](#compile)

## Installing

You need your own copy of LONELY WOLF TREAT, a PC to prepare the files, and a handheld running PortMaster.

### 1. Install the port

Place `lonelywolf.zip` in PortMaster's `autoinstall` folder and run PortMaster to install it.

Alternatively, install it over SSH:

```bash
harbourmaster install <url-of-the-zip>
```

After installation, you should have the launcher and a `lonelywolf/` folder inside `ports/`.

### 2. Prepare the game files

Prepare the game files on your PC. If your copy requires an official update, apply it before copying the files to your handheld.

Make sure you have the required game assets, including `Game.rgss3a` or an unpacked `Data/` folder.

## 3. Copy the game files

Copy the game files into `ports/lonelywolf/`, alongside the engine.

The expected directory structure is:

```text
ports/
├── Lonely Wolf Treat.sh
└── lonelywolf/
    ├── lonelywolf.sh
    ├── lonelywolf.ini
    ├── mkxp.json
    ├── mkxp-z.aarch64
    ├── win32stub.rb
    ├── Game.exe
    ├── Game.ini
    ├── Game.rgss3a
    ├── Audio/
    ├── Fonts/
    ├── System/
    ├── Graphics/
    ├── licenses/
    ├── patches/
    ├── libs.aarch64/
    └── stdlib/
```

If your copy uses an unpacked `Data/` directory instead of `Game.rgss3a`, place `Data/` in the same `lonelywolf/` directory.

Keep `mkxp.json`, `mkxp-z.aarch64`, and `win32stub.rb` alongside the game files. The `libs.aarch64/` and `stdlib/` directories must remain in the locations expected by the launcher.

## 4. Play

Launch **Lonely Wolf Treat** from the Ports menu.

The first launch may take a little longer while the Ruby standard library is initialized.

Save files are generally written according to the engine's configuration. Back up your saves before changing game files or patches.

## The patches folder

The `lonelywolf/patches/` directory is intended for additional game content or replacement files supported by the engine.

For example, if a patch provides replacement RPG Maker folders, its structure may look like this:

```text
patches/
├── Data/
├── Graphics/
├── Audio/
└── Fonts/
```

Only use patches intended for your version of the game and compatible with mkxp-z. Do not copy Windows executables or unrelated installation files into this directory.

If the game does not require additional patches, leave the directory empty.

## Controls

The default controls depend on the handheld's controller mapping and the mkxp-z configuration.

| Button | Action |
|---|---|
| D-Pad | Movement and menu navigation |
| A | Confirm |
| B | Cancel or open menu |
| X | Dash, if supported by the game |
| Start | Open menu |

Button mappings may differ between devices and firmware versions.

## Compile

The included `mkxp-z.aarch64` is the engine binary for 64-bit ARM handhelds.

To build mkxp-z from source, follow the official instructions in the [mkxp-z repository](https://github.com/mkxp-z/mkxp-z). The required build options and dependencies may vary depending on the target device and firmware.

The port also requires the appropriate native libraries and Ruby standard library. Keep `libs.aarch64/` and `stdlib/` in the locations expected by the launcher.
