# Universe BIOS 4.0 PICKnMIX Patch

## Background

The [Universe BIOS](http://unibios.free.fr/), developed over the years by Razoola, is a highly capable universal alternate BIOS to the stock MVS and AES versions.

One feature of version 4.0 is [PICKnMIX](http://unibios.free.fr/picknmix.html) which allows certain 161-in-1 multicarts (software versions 1 & 2) to function like an original multislot MVS with 97 unique games.

Two ways of enabling it:
1. Hold Player 1 START button on cold boot
2. Hold Player 1 SELECT button on cold boot

If START is used, game selection is done by Player 1's A & B buttons.  
If SELECT is used, game selection is done by Player 1 & 2's SELECT buttons.

Holding either of the game select buttons (A/B or SELECTs, depending on chosen scheme) brings up a game list which allows scrolling and game selection.

## <font color=FF00CC>Problems</font>

Strictly not issues with the PICKnMIX feature itself but more on its activation and the 161-in-1 cart's limitations :-

On an MVS cabinet:

1. If the <font color=FF00CC>*power switch is out of reach*</font> of Player 1 START/SELECT buttons, <font color=FF00CC>*PICKnMIX can't be activated*</font>.

    (A hardware solution was developed by Arthrimus and discussed on the [arcade-projects forum](https://www.arcade-projects.com):  
    [PICKnMIX Fix: A tiny PCB for Neo Geo that automatically enables PICKnMIX on Universe Bios 4.0](https://www.arcade-projects.com/threads/picknmix-fix-a-tiny-pcb-for-neo-geo-that-automatically-enables-picknmix-on-universe-bios-4-0.13916/))

2. If a <font color=FF00CC>*memory card is detected*</font>, the 161-in-1 cart's programmed logic of holding Player 1 START button for ~5 seconds to <font color=FF00CC>*reset to the Game Select Menu (GSM) does not work*</font>.

On an AES console:

1. Holding Player 1 START button for ~5 seconds to <font color=FF00CC>*reset to Game Select Menu (GSM) does not work at all*</font>, requiring switching the console off and on to return to it.

## <font color=00CC66>Solution</font>

1. Reverse the logic and make <font color=00CC66>**PICKnMIX** *cold boot by default*</font>, and <font color=00CC66>**161-in-1 GSM** *cold boot by holding Player 1 START button*</font>.
2. Have an <font color=00CC66>*alternate warm reset* logic</font>, regardless of whether memory card is detected or not, AND working on AES consoles.
3. Critically, <font color=00CC66>*to not affect default operation*</font> of normal carts, other multicarts and Universe BIOS 4.0.

## Patch Features

<font color="00FFFF">**Cold Boot**</font>:

1. PICKnMIX *boots by default*.
2. 161-in-1 GSM *boots by holding Player 1 START* while powering on.  

<font color="orange">**Warm Reset**</font>:

At **In Game Menu** while cursor at **SOFT REBOOT SYSTEM**:  

<img src="screenshots/SOFT REBOOT SYSTEM.png" alt="Screenshot" width="400">

<br>

In either PICKnMIX or 161-in-1 mode:

1. Press A button → normal reset to the start of the current game.
2. Hold START, press A → actively resets to 161-in-1 GSM.
3. Hold SELECT, press A → actively resets to PICKnMIX mode.

(Physical RESET button always only does normal reset to the start of the current game, regardless of START/SELECT state.)

## Video demonstration

[Universe BIOS 4.0 PICKnMIX patch - part 1](https://www.youtube.com/watch?v=fJfCjKM3g7U)  
[Universe BIOS 4.0 PICKnMIX patch - part 2](https://www.youtube.com/watch?v=U4NDIo5cKlA)

## Files
- `uni-bios_4_0_PnM_patch.ips` – IPS patch file
- `uni-bios_4_0_PnM_patch.json` – Metadata (CRC checks and output filename)

## How to Apply

Use your IPS patcher of choice:  
1. Neo-Geo IPS - [https://github.com/clearpaper/nips-patcher](https://github.com/clearpaper/nips-patcher)  
2. Lunar IPS - [https://www.romhacking.net/utilities/240](https://www.romhacking.net/utilities/240)
3. Floating IPS - [https://github.com/Alcaro/Flips](https://github.com/Alcaro/Flips)

Steps (if using Neo-Geo IPS Patcher):

1. Download the latest `nips.exe` from the [nips-patcher releases](https://github.com/clearpaper/nips-patcher/releases).
2. Download the latest `uni-bios_4_0_PnM_patch.json` and `uni-bios_4_0_PnM_patch.ips` from the [uni-bios_4_0_PnM releases](https://github.com/clearpaper/uni-bios_4_0_PnM/releases) and place them into one folder.
3. Double-click `nips.exe`.
4. When prompted, select the `uni-bios_4_0_PnM_patch.json` file.
5. When prompted, select your `uni-bios_4_0.rom` from [THE UNIVERSE BIOS
\- Official Homepage -](http://unibios.free.fr/) (or possibly from your neogeo.zip file in your emulator's ROM folder)
6. A new file `uni-bios_4_0_PnM.rom` will be created in the same folder as the patch files.

## Disclaimer

This repository does **not** contain any copyrighted ROM code.  
It only provides patch data. You must own the original to apply this patch.  

The patch and documentation are provided under the [MIT License](LICENSE).  
They are provided *as is*, without warranty of any kind.
