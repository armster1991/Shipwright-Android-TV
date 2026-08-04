# Ship of Harkinian Android TV Port

An Android TV-focused fork of the Ship of Harkinian Android port.

Modified by **Armster1991**.

## Project Base

This fork is based on:

- [Waterdish/Shipwright-Android](https://github.com/Waterdish/Shipwright-Android)
- Ship of Harkinian 9.0.2 Patch 2
- Original Ship of Harkinian repository: [HarbourMasters/Shipwright](https://github.com/HarbourMasters/Shipwright)

This is an unofficial community fork and is not affiliated with Nintendo.

A legally obtained copy of The Legend of Zelda: Ocarina of Time is required.

## Platform Support

Supported, probably:

- Android 7.0 or newer
- Android TV
- Google TV
- OpenGL ES 3.0 or newer

Tested on Android 15.

## Main Changes in This Fork

- Android TV launcher support.
- Android TV banner and launcher entry.
- Default frame rate set to 30 FPS.
- Free Look enabled by default.
- Right analog stick reserved for camera control.
- D-Pad Up also triggers C-Up / Navi.
- L1 + R1 opens the Enhancements menu.
- L3 + R3 closes the application.
- Existing `oot.otr` and `oot-mq.otr` files are preserved.
- Existing user configuration files are not overwritten.
- The default controller configuration is installed only when missing.

## Installation

1. Install the APK from the Releases section of this repository.
2. Open the application.
3. Allow the requested file permissions.
4. The application will ask to set up its required files.
5. Confirm the setup and wait until it finishes.

The initial setup may take several minutes on slower Android TV devices.

Do not close the application while `Setting up files...` is displayed.

After setup:

1. Select **Yes** when asked whether you want to generate an OTR.
2. Select **Yes** when asked to search for a ROM.
3. Navigate to your legally obtained ROM and select it.
4. Wait for extraction to finish.
5. When asked whether you want to extract another ROM, select:
   - **Yes** to choose another ROM.
   - **No** to start the game.

On later launches, the application should start directly into the game.

To make the ROM selection dialog appear again, remove the generated game OTR file from the `SOH` folder. Keep a backup before removing any file.

## Storage Folder

The application stores its files in:

```text
SOH/
```

This folder is located at the root of the device storage.

Typical contents:

```text
SOH/
├── assets/
├── mods/
├── Save/
├── soh.otr
├── oot.otr
├── oot-mq.otr
└── shipofharkinian.json
```

Not every installation will contain all files shown above.

## Controller Shortcuts

- **L1 + R1:** Open the Enhancements menu.
- **L3 + R3:** Close the application.
- **D-Pad Up:** Also triggers C-Up / Navi.

L1 and R1 continue to work normally when pressed separately.

L3 and R3 continue to work normally when pressed separately.

Connect the controller before opening the application.

Avoid disconnecting and reconnecting the controller while the game is running.

## Enhancements Menu

Press **L1 + R1 together** to open the Enhancements menu.

Use the controller or touch controls to navigate the menu.

## Mods

Place compatible mods inside:

```text
SOH/mods/
```

Depending on the mod, files may need to remain inside the folder structure provided by the mod author.

Do not rename mod files unless the mod instructions explicitly require it.

Some texture packs require **Alternate Assets** to be enabled from the Enhancements menu.

Mod compatibility depends on the version of Ship of Harkinian for which the mod was created.

Mods made only for newer desktop releases may not work with this Android port.

## FAQ

### How do I add mods?

Place compatible mod files or mod folders inside:

```text
SOH/mods/
```

Follow the mod author's installation instructions when available.

### Why does the first setup take so long?

The first launch copies a large amount of data to the `SOH` folder.

On slower Android TV devices, this may take several minutes.

Wait until the setup finishes before closing the application.

### Why is the application immediately crashing?

Try the following:

1. Make a backup of your saves and OTR files.
2. Confirm that the application has storage permission.
3. Check whether the required files exist inside the `SOH` folder.
4. Remove incompatible mods temporarily.
5. Try launching again.

Avoid deleting the entire `SOH` folder unless you already have backups.

### The game opened once, but now it only shows a black screen.

Try removing:

```text
SOH/imgui.ini
```

Also avoid setting MSAA above 1 on devices that cannot handle it.

### Some buttons on my controller do not map correctly.

Some controllers have compatibility or mapping issues with Android and SDL.

Try connecting the controller before opening the application.

A different controller may be required if Android reports the device incorrectly.

### My controller is not responding.

Connect or pair the controller before opening the application.

Do not disconnect it while the game is running.

### How do I open the Enhancements menu?

Press:

```text
L1 + R1
```

### How do I close the application with the controller?

Press:

```text
L3 + R3
```

### Will the application delete my OTR files during an update?

This fork is designed not to delete or overwrite existing `oot.otr` or `oot-mq.otr` files.

Keeping backups is still recommended before installing a new build.

## Known Issues

- Reconnecting a controller while the application is running may prevent it from opening the Enhancements menu.
- Some controller models may be reported incorrectly by Android or SDL.
- Some desktop mods are incompatible with Ship of Harkinian 9.0.2 Patch 2.
- Initial setup can take several minutes on slower devices.
- High MSAA values may cause a black screen or crash on some hardware.

## Build

### Tested Build Environment

- Ubuntu Noble Numbat 24.04.2 LTS
- CMake 3.31.5
- OpenJDK 17
- Android Studio Koala 2024.1.1 Patch 2
- Android SDK 31 / Android 12
- Android SDK Build-Tools 30.0.2
- Android SDK Command-Line Tools 17.0
- Android SDK Platform-Tools 35.0.2
- Android NDK 26.0.10792818
- Android Gradle Plugin 7.0.3

These are the tested tools and versions for building the project directly.

Other versions may work, but they are not guaranteed.

## Build Instructions

Use a Linux-based operating system.

Windows builds are not officially supported by this project. Windows users can use WSL or a Linux virtual machine.

### Install OpenJDK 17

```bash
cd ~
wget -O openjdk.tar.gz https://download.java.net/java/GA/jdk17.0.2/dfd4a8d0985749f896bed50d7138ee7f/8/GPL/openjdk-17.0.2_linux-x64_bin.tar.gz
tar -xvzf openjdk.tar.gz
rm -f openjdk.tar.gz
sudo mv jdk* /opt/jdk_17
sudo rm -f /etc/profile.d/jdk.sh
echo "export JAVA_HOME=/opt/jdk_17" | sudo tee /etc/profile.d/jdk.sh
echo "export PATH=/opt/jdk_17/bin:\$PATH" | sudo tee -a /etc/profile.d/jdk.sh
sudo chmod +x /etc/profile.d/jdk.sh
source /etc/profile.d/jdk.sh
```

### Install Android Studio

```bash
cd ~
wget -O android-studio.tar.gz https://redirector.gvt1.com/edgedl/android/studio/ide-zips/2024.1.1.13/android-studio-2024.1.1.13-linux.tar.gz
tar -xvzf android-studio.tar.gz
rm -f android-studio.tar.gz
sudo mv android-studio /opt/android-studio
sudo rm -f /usr/local/bin/android-studio
sudo ln -s /opt/android-studio/bin/studio.sh /usr/local/bin/android-studio
```

Start Android Studio:

```bash
android-studio
```

Open:

```text
Tools → SDK Manager
```

Install:

- Android SDK 31 / Android 12
- Android SDK Build-Tools 30.0.2
- Android NDK 26.0.10792818
- Android SDK Command-Line Tools 17.0
- Android SDK Platform-Tools 35.0.2
- CMake 3.31.5

Then sync and build the project.

## Credits

- HarbourMasters — Ship of Harkinian
- Waterdish — Android port
- Armster1991 — Android TV modifications and fork maintenance
- Ship of Harkinian contributors
- SDL and libultraship contributors

## License

Refer to the licenses and notices included in the original Ship of Harkinian and Shipwright Android repositories.
