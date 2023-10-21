# ally-motion-evdev
This is the Arch Linux package for a fork of [evdevhook2](https://github.com/v1993/evdevhook2) that exposes the bmi323 device as created by [rog-ally-motion-evdev]() as an UDP server for (Nintendo) emulators.

## Usage
To use this package compile it, install it and use the provided systemd service file:

```sh
# first install rog-ally-motion-evdev
makepkg -sfi
systemctl --user enable evdevhook2
```

## Contributions
A big thank goes to everybody involved:
  - All staff from the original project [evdevhook2](https://github.com/v1993/evdevhook2) for providing such a useful software
  - [TwinHaelix](https://github.com/KWottrich) for modifying the original package to provide all of us this good stuff <3
  - WarlockLord has written the systemd service file to run this program as a user service allowing the usage in game mode (Nintendo) emulators