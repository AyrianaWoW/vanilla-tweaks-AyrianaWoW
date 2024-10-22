# Vanilla-Tweaks

  - These are some custom patches for the old 1.12.1 World of Warcraft client, which lacks many of the conveniences of more modern clients.
  - All instructions are for the Windows Operating System (Win7 SP1 or higher).
  - These instructions have been modified by AyrianaWoW based on the [original version](https://github.com/brndd/vanilla-tweaks/) by the author brndd.

## Modifications

  - **Farclip** will be set to a reasonable value of 1000 instead of the absurdly-high 10000 that is the Vanilla Tweaks drag & drop default.
  - **FOV** (field of view) will be set to 2.355 to match a comfortable value for 1920 x 1080 resolution with a 16:9 aspect ratio.
  - **Nameplate Range Change** will be increased to 60 yards with these instructions.
  - **Quickloot Reverse Patch** will be DISABLED with these instructions.

## Current patches
All of the below patches remain unaltered and unchanged from the default version.

- **Widescreen FoV fix**
- **Sound in background patch**
- **Sound channel count default increase**
  - By default the game only uses 12 channels to play sound. This is essentially the number of sounds that can play at the same time, so the low default value means many sound effects in group content do not play.
  - Increased to 64 by default. The default in TBC is 32. The default in newer expansions is 64. 
  - This can also be set with ``SET SoundSoftwareChannels "64"`` in the Config.wtf file in your WoW directory, but this patcher changes the default value so that it survives Config.wtf deletions.
  - Values above 64 have been reported to cause crashes. If you run into performance issues, try decreasing this setting further.
- **Farclip (max render distance) increase**
  - Farclip is changed with ``SET farclip "777"`` in the Config.wtf file in your WoW directory (777 is the default maximum, recommended not to exceed 4000 at most due to vanilla client limitations).
  - **Frilldistance (max grass render distance) increase**
  - Frilldistance is set to a default of 300 when using vanilla-tweaks and is the maximum recommended value for this setting.
  - Frill density (grass density) is changed with ``SET frilldensity 64`` in the Config.wtf file in your WoW directory. Please note that 256 is the maximum recommended value for this setting therefore 64 is used as an example for improved performance.
  - It is not recommended to go beyond these values as they has a significant performance impact even on modern hardware.
- **CameraDistanceMax limit increase**
  - Allows you to increase the CameraDistanceMax limit. This only changes the max value settable.
  - Unchanged by default. Default maximum value is 50.
  - Can be customized in your Config.wtf file in your WoW directory with the following commands ``SET cameraDistanceMax "50"`` and ``SET cameraDistanceMaxFactor "5"``
- **Large Address Aware patch**
  - This allows the game to use more than 2GB of memory by setting a flag in the executable header. See https://codekabinett.com/rdumps.php?Lang=2&targetDoc=largeaddressaware-msaccess-exe for more information.
  - If you experience inexplicable crashes, try disabling this patch, and if you manage to reproduce them let me know via an issue. The client *should* have no issues being Large Address Aware, but you never know.
  - I've personally verified the PE headers of the WoW.exe to determine that the 'Large Address Aware' patch does indeed work as intended.
  - If using any 'HD Patches' in the form of MPQ files, just know that they REQUIRE this patch to be enabled but even WITH this patch you may still encounter unexpected 'Error 132' (generic error) crashes. This is a byproduct of the old v1.12.1 Vanilla Client.
- **Camera skip glitch fix**
  - Fixes the glitch where the camera sometimes skips to face a random direction when rotated.

## Usage

  - Download the release matching your operating system from the [releases page](https://github.com/brndd/vanilla-tweaks/releases). Extract the executable from the archive into your WoW directory.
  - For the Windows OS, the filename should end in ``x86_64-pc-windows-gnu.zip``

### Easy Drag & Drop Instructions without Customizations

  - Open your WoW directory and drag WoW.exe on top of vanilla_tweaks.exe. This will create a new file called WoW_tweaked.exe, which has all the patches applied with their default settings and NO customizations.
  - Place a backup copy of your original WoW.exe in a safe location, then rename your WoW_tweaked.exe to WoW.exe and use the new WoW.exe to start the game instead.

### Detailed Instructions with Customized Settings

  - To customize the values changed by the patches, or to disable some patches, you must run vanilla-tweaks from the command line.
  - Go to your user directory by opening a new file window or folder and typing this into the address bar: ``%HOMEPATH%``.  This will open your user home directory which includes your username.
  - Once open, you want to make a new folder in that directory with any name (for this example we will call it ``fixme`` as the folder name).
  - Place a COPY of your original WoW.exe in this ``fixme`` folder and make sure the copy matches the file hashes below and is named ``WoW.exe`` as the filename.
  - On Windows, open the 'Run' command (Windows Key + R) and then type in ``powershell.exe`` to open Windows Powershell.
  - Once open, type ``cd fixme`` and press ENTER to confirm so you end up in your working directory with the WoW.exe to be modified.
  - After you are in the proper directory type ``dir`` and press ENTER to confirm the command then verify the output says WoW.exe is in that directory.
  - You are finally ready to follow the commands below to tweak how you like!

### File hashes
Your WoW.exe must match the following file hashes and be an original UNMODIFIED Vanilla WoW.exe file. I cannot provide this for you nor assist you in obtaining it.
```
CRC-32:   36F50F01
MD5:   FB6309BC9B9286F124D1980D95203D37
SHA-1:   C28193586A1751A416AF6467FCE6366A352B88E8
SHA-256:   CB1F3B12D7EE88FFC302855FFF940A5CA34F96D910EA0B8A55B18D3EEF9319DD
```
To see a full list of the available options, you may use the `--help` parameter:

```sh
./vanilla-tweaks --help
```

With your powershell terminal open in your WoW directory, you may then run vanilla-tweaks with custom parameters like this:

```sh
./vanilla-tweaks --farclip 1000 --fov 2.355 --nameplatedistance 60 --no-quickloot WoW.exe
```

Remember to make sure it has the ``WoW.exe`` at the end so it knows which EXE file to modify.

The example above performs the following changes:
  - Farclip is set to a reasonable value of 1000 instead of the default of 10000.
  - FOV (field of view) value is set to 2.355 for a more comfortable widescreen FOV optimized for 1920 x 1080 resolution; please consult the FOV Values list below for alternatives to use. You can also remove this value if you wish to leave the FOV unaltered or tweak it using other methods like [SuperWoW](https://github.com/balakethelock/SuperWoW).
  - Nameplate distance is set to 60 instead of 41.
  - Quickloot will be DISABLED so that one can use other Quickloot customization methods like the one included in [Vanilla Fixes](https://github.com/hannesmann/vanillafixes/releases) instead.


List of useful FOV Values:
```
1.57 (default) is 90 degrees Horizontal FOV
2.094 is 120 degrees Horizontal FOV
2.355 is 135 degrees Horizontal FOV
3.14 is 180 degrees Horizontal FOV
```

Detailed list of available options for Vanilla Tweaks (minus a few unnecessary mentions):
```
--farclip 1000
```
You can change the default value of 777 to any number up to 10000, but using values beyond 4000 for the Vanilla client may lead to significant issues even on modern hardware due to technical engine limitations.

```
--fov 2.355
```
There's a list of useful FOV Values just above this post.  I believe 135 degrees (2.355) is the most comfortable FOV for the 1920 x 1080 monitor resolution.

```
--frilldistance 300
```
While the default game value is 70, the vanilla-tweaks default is 300 so you can adjust this if you like for fidelity/performance.

```
--maxcameradistance 50
```
Adjusts the maximum zoom out camera distance in WoW to allow for greater visibility of surroundings, especially during raid boss fights and/or when fighting enemies with large models.

```
--nameplatedistance 60
```
The game default is 20, while the WoW classic and Vanilla Tweaks default is 41.  I recommend a value of 60 for easier situational awareness in PvE scenarios.

```
--no-cameraskipfix
```
If set, do NOT patch the fix for the camera sometimes skipping to a random direction when rotated.

```
--no-farclip
```
If set, do NOT patch farclip.

```
--no-fov
```
If set, do NOT patch FOV.

```
--no-frilldistance
```
If set, do NOT patch frilldistance.

```
--no-largeaddressaware
```
If set, do NOT patch the executable to be Large Address Aware.  It is strongly recommended NOT to use this flag unless you are playing on extremely low-end hardware with less than 3 GB of system RAM.

```
--no-nameplatedistance
```
If set, do NOT patch nameplate distance.

```
--no-quickloot
```
If set, do NOT patch quickloot.

```
--no-sound-in-background
```
If set, do NOT patch sound in background.

```
--no-soundchannels
```
If set, do NOT patch the number of sound channels.

```
--soundchannels 64
```
Default sound channel count. The default game value is 12, however a value of 64 is recommended as it matches the modern WoW clients and values above 64 may cause crashes.
