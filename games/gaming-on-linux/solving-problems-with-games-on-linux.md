# Solving problems with games on Linux

> In this document I describe my experience with Lutris, Proton, and Wine utilities.

## Table of Contents

1. [Where to install games](#Where-to-install-games)
2. [Wine, its variations and problem with them](#Wine-its-variations-and-problem-with-them)
   1. [Lutris](#Lutris)
   2. [Proton](#Proton)
   3. [Pure Wine](#Pure-Wine)
   4. [Steamtricks](#Steamtricks)
   5. [Linux steam integration](#Linux steam integration)
3. [Deus Ex with GMDX mod](#Deus-Ex-with-GMDX-mod)
4. [GTA III](#GTA-III)
5. [Max Payne](#Max-Payne)
6. [Super Meat Boy](#Super-Meat-Boy)
7. [Talos Principle](#Talos-Principle)
8. [References](#References)

## Where to install games

It is very important that the games are installed on the ext4 file system, otherwise they won't work. However, there are some [tweaks](https://www.reddit.com/r/SteamPlay/comments/aafhcn/steam_proton_doesnt_launch_any_games/) that might help to run them on the NTFS file system:

> For NTFS you'll need something like this: `ntfs-3g defaults,exec,uid=1000,gid=1000 0 2`
>
> > Try changing gid=1000 to gid=100 (users) and see if that helps.
>
> Make sure that you are *not* using the `windows_names` flag.
>
> For ext4, something like `ext4 defaults 0 2` and make sure you give your user permissions for the drive: `sudo chown -R USERNAME:USERNAME /media/mynewdrive`.

## Wine, its variations and problem with them

In [this discussion](https://steamcommunity.com/app/221410/discussions/0/2798319091580289893/) people think that Wine is better for gaming than Proton. Proton is the tool that tries to give the full compatibility to all the Windows games without Linux native compatibility, but in most cases it fails (AAA games). So, Wine is better but it is hard to tweak it, because you need to adjust each game individually.

### Lutris

**Issue. Flickering when using Origin and all its games**

**Solution.**



> TODO: check the links below

https://forums.lutris.net/t/please-read-before-asking-for-help/3727

https://forums.lutris.net/t/dxvk-support/6712

https://forums.lutris.net/t/dark-souls-ii-screen-flicker/689/2

https://forums.lutris.net/t/major-screen-tearing-after-lol/8318/2

https://forums.lutris.net/t/epic-games-launcher-flickering/4455/7

https://forums.lutris.net/t/lutris-origin-dragon-age/6304

https://forum.winehq.org/viewtopic.php?t=12285

https://forum.winehq.org/viewtopic.php?t=33141

https://www.reddit.com/r/Lutris/comments/jlmxkv/black_or_flickering_steam_screen_on_wine_steam/ - not yet answered

https://www.reddit.com/r/linux_gaming/comments/hqhxb5/lutrisorigin_flickering_manjaro_kde_help/

https://www.reddit.com/r/wine_gaming/comments/au0xpy/how_to_get_rid_of_blinking_epic_games_launcher_on/

https://www.reddit.com/r/linux_gaming/comments/99qyvh/lutris_and_steamplay_monster_hunter_world/

### Proton

#### Customizing Wine prefix in Proton

According to @meheezen:

> Well, you can tweak some things just like you do in WINE, since Proton is pretty much WINE with a few Valve tweaks and content.
>
> I haven't had much issues with it tho, but i don't play that many games (i did have to make some changes to WINE within Proton to get some of them to work tho).

> You can aways create an empty WINE prefix and customize it the way you want instead of using the one Steam creates for you.

> i remember having to do some tweaks to get The Sims 3 to run properly, tho i cannot seem to find the link (will update when i find it), it went something like this:
> 1- copy proton specific files from the wine prefix Steam made for you (there is some files in the pfx directory and a proton directory inside of program files)
> 2- delete the prefix
> 3- create a new one at the same place using wine
> 4- install .Net and other dependencies
> 5- copy/move back the proton specific files
> 6- play
>
> Edit: found it
> https://www.reddit.com/r/linux_gaming/comments/99e0kc/steam_playguide_create_custom_32bit_prefix_to/
>
> you just need to create the syswow64 directory to stop proton from complaining
>
> so delete prefix, create new one with wine, create that syswow64 directory within c:\windows and tweak as you want

### Pure Wine

### Steamtricks

Steamtricks app available [here](https://github.com/steamtricks/steamtricks) for Ubuntu and similar operating systems.

Also, it is available for OpenSuse [here](https://software.opensuse.org/package/steamtricks).

### Linux steam integration

Linux steam integration app for Solus project can be found [here](https://github.com/solus-project/linux-steam-integration).

## Deus Ex with GMDX mod

> Launched via Proton 5.0 (not 5.13 where I have flickering).

**Issue. Install GMDX mod.**

**Solution.**

- Install Deus Ex with Steam Play. You need to have the option to install any game with Steam Play in the Steam settings.
- Download [GMDX](https://www.moddb.com/mods/gmdx) and install it with [Wine](https://www.winehq.org/). You will have to have Wine installed. Also Wine wouldn't show all my Steam directories to to get around this I copied my Deus Ex folder to my home folder for the install. It is located in /home/yourusername/.steam/steam/steamapps/common. After GMDX installs copy the folder back to it's original location.
- Right click on Deus Ex in your steam library, go to properties and copy this into your launch options:
  INI="..\GMDXv9\System\gmdx.ini" USERINI="..\GMDXv9\System\GMDXUser.ini"

**Just in case.**

- If you have problem with launching the game, then maybe there is a problem with the launcher itself. You can replace it with [this](http://kentie.net/article/dxguide/index.htm) mod.

- If you get this error 

  ```
  Can't find 'ini:Engine.Engine.GameEngine' in configuration file
  ```

  then there is a problem with .ini files. It would be great to reinstall Deus Ex, and Proton version if the first step didn't help.

  > Sure, you can delete and pull .ini files, but it didn't help me.

## GTA III

>  Launched via Proton 5.0 (the game doesn't launch with 5.13).

It works fine with Proton 5.0. You need to press enter a few times after the launch in order to remove black screen.

> I got flickering in Proton 5.13 and unhandled exception in Proton below

Also, I turned Trails off in order to remove the motion blur.

Installed Widescreen and Silent patches. After exiting the game, I get the next error:

```
Gta 3 Unhandled exception c0000005
```

This is similar to [this](https://steamcommunity.com/app/12100/discussions/0/483367798514700344/) one. It's not critical but it's really interesting how to fix this :thinking:

Other tips from [ProtonDB](https://www.protondb.com/app/12100):

> Works fine with Proton. I copied dgvoodoo2 files, enabled d3d8 as native in winecfg and then this game worked as well with DXVK (only some graphical glitches with cars).

> You have to press a button after it launches to get your screen to change to the full screen game (I press space or enter). Sometimes it makes system unresponsive when you choose to quit the game. Tab out and close from your taskbar instead. Otherwise it plays perfectly for me. Mods works as well (Silent Patch, controller support, widescreen fix). https://steamcommunity.com/sharedfiles/filedetails/?id=641839127

> Works very well. Saving the game doesn't work out of the box. You must create a folder called My Documents In (/home/username/.steam/steam/steamapps/compatdata/gameID/pfx/drive_c/users/steamuser

> Game runs flawlessly in 1920x1080. When game launches, wait for screen to blink, then click mouse button twice to start the game. Go to the video settings and change resolution, maximize draw distance and turn frame limiter off. If you are annoyed with the blur effect (it was present in win version), turn trails off. Only issue I found is that you can't save game as the GTA3 want to save it in My Documents which really sucks.

> Runs out of the box. But you should not disable vsync or disable frame limiter, because this may lead to strange effects (e.g. can't drive back when setting in car).

> Works perfectly, just install and play. (use the frame limiter (Optionally with the 60fps frame limiter mod) otherwise all the physics and menu will be broken , but that's a problem that happens on Windows too.

> **You won't have much of a problem unless you're using Wayland**
>
> Launcher:Steam
>
> Customizations:Protontricks
>
> Enabled virtual desktop.
>
> Windowing:Switching
>
> With Wayland/sway, the game freezes as soon as I switched to another workspace. Enabling the virtual desktop fixes this. This is was not an issue with XFCE.
>
> Input:Bounding
>
> With Wayland/sway, the mouse input will sometimes get "bounded", so I can't rotate the camera too much. A single mouse click fixes this.
>
> Make sure to keep the frame limiter on, otherwise you get physics glitches (known bug that affects Windows as well).

> Had to use Protontricks to set up a virtual desktop for the game to start

> Launcher:Steam
>
> Customizations:Custom Proton
>
> Proton-5.9-GE-1-NR from GloriousEggroll [GloriousEggroll](https://github.com/GloriousEggroll/proton-ge-custom/releases)
>
> This custom Proton version enables intro video (no need to skip it)

> Launcher:Steam
>
> Customizations:Custom Proton
>
> 5.11-GE-3-MF [GloriousEggroll](https://github.com/GloriousEggroll/proton-ge-custom/releases)
>
> Audio:Other
>
> Sometimes the voices sound like they come from a tin can
>
> Black screen at start (the intro cutscenes with rockstar logos) can be skipped pressing enter. Using this proton version allowed me to change resolution with no problems.

> **Game runs without issues out of the box.**
> I was also able to install mods like widescreen patch and proper xinput mod. (Used winedlloverrides commands)

## Max Payne

>  Launched via Steam Proton 5.13-2.

**Issue. A network of points appears while shooting.**

A network of points appears while shooting in Max Payne 1. It is connected to the display resolution. My monitor is 1366x768. There is a mode 1366x768x16 in the game, but you need the 32 bit version.

**Solution.**

The easiest solution is to install ["Max Payne - FixItAll"](https://steamcommunity.com/sharedfiles/filedetails/?id=1184013727) patch by community. It includes ThirteenAG's widescreen fix which makes the game 16:9 compatible. Install it with Wine.

## Super Meat Boy

> Launched via Lutris 5.21-2-x86-64.

**Issue 1. Can't launch the game.**

**Solution.**

In my case, I had to disable DXVK/VKD3D in Lutris settings.

> DXVK/VKD3D enables support for Direct3D 12 and increase compatibility and performance in Direct3D 11, 10 and 9 applications by translating their calls to Vulkan.

**Issue 2. The audio plays but sometimes sounds distorted/corrupted (in my case, it is music).**

**Solution.**

Install [Faudio](https://github.com/FNA-XNA/FAudio) as an application in the winetricks. After reading [this](https://github.com/flibitijibibo/flibitBounties/issues/4) issue, I thought that it might help me. And it helped! However, I get the next issue.

**Issue 3. After launching the game again, I get this: "Could not create XAudio2 Device".**

**Solution.**

How to fix this? You need to install [Microsoft DirectX End-User Runtimes (June 2010)](https://www.microsoft.com/download/en/details.aspx?id=8109). It seems that if you are running DirectX 9 you will not get this error, but if you are running Windows 7 with the newest DirectX 11 you might get this error when installing games that use the XAudio2 engine.

Or you can just download Directx 2010 framework from Lutris.

To fix the problem, you need to download an installation file from Microsoft from June 2010, it contains a lot of updates to the DirectX 11 package, among them the XAudio2 engine.

For other recommendations see these links: [a nice guide on Reddit](https://www.reddit.com/r/Supermeatboy/comments/6pi80k/tutorial_getting_super_meat_boy_beta_to_work_on/), [a link about Emulation mode](https://appdb.winehq.org/objectManager.php?sClass=version&iId=22177), [a notes about virtual desktop](https://appdb.winehq.org/objectManager.php?sClass=version&iId=22216).

## Talos Principle

> Launched via Steam (without Proton).
>
> This issues can be relevant for other Croteam games.

**Issue 1. CPU power saving in Croteam game.**

After a launch the game in terminal I've noticed a warning:

```bash
"WRN: CPU Power saving is enabled and performance governor is not used."
```

So, their games are launched in power saving mode.

**Solution.**

In order to fix this you can install cpufreq utilities:

```bash
$ sudo apt-get install cpufrequtils
```


and switched CPUs to performance mode:

```bash
$ sudo cpufreq-set -g performance
```

And you can play!

> Thats why devs recommend to disable all cpu power saving modes in bios.

The other options could be:

**thermald**

[thermald](https://www.archlinux.org/packages/?name=thermald) is a Linux daemon used to prevent the overheating of platforms. This daemon monitors temperature and applies compensation using available cooling methods.

By default, it monitors CPU temperature using available CPU digital temperature sensors and maintains CPU temperature under control, before HW takes aggressive correction action. If there is a skin temperature sensor in thermal sysfs, then it tries to keep skin temperature under 45C.

The associated systemd unit is `thermald.service`, which should be [started](https://wiki.archlinux.org/index.php/Start) and [enabled](https://wiki.archlinux.org/index.php/Enable).

**i7z**

[i7z](https://www.archlinux.org/packages/?name=i7z) is an i7 (and now i3, i5) CPU reporting tool for Linux. It can be launched from a Terminal with the command `i7z` or as GUI with `i7z-gui`.

**cpupower**

[cpupower](https://www.archlinux.org/packages/?name=cpupower) is a set of userspace utilities designed to assist with CPU frequency scaling. The package is not required to use scaling, but is highly recommended because it provides useful command-line utilities and a [systemd](https://wiki.archlinux.org/index.php/Systemd) service to change the governor at boot.

The configuration file for *cpupower* is located in `/etc/default/cpupower`. This configuration file is read by a bash script in `/usr/lib/systemd/scripts/cpupower` which is activated by *systemd* with `cpupower.service`. You may want to [enable](https://wiki.archlinux.org/index.php/Enable) `cpupower.service` to start at boot.

**cpupower-gui**

It's described in detail here: [link](https://wiki.archlinux.org/index.php/CPU_frequency_scaling#cpupower).

**Issue 2. Launching on a discrete GPU.** 

The games don't launches on a discrete video card. I have a laptop with hybrid graphics. Intel 4000 and AMD Radeon 8750M are cards I have.

**Solution.**

The problem is not only that the games work on an integrated video card, but that the latest version of The Talos Principle only supports Vulkan, not OpenGL. So, there are two solutions:

- In Steam properties switch the game to the "legacy - pre se2017" 'beta'. 

  > Current patch removed dx9 and open gl support (and 32 bit) which I assume is going to be pretty important when you don't have a proper gpu.

  Actually, there are many different versions. I think the legacy Linux version is the best. He here is my tests:

  ```reStructuredText
  ================================
  Testing the legacy Linux version
  --------------------------------
  The android goes somewhere when the gamepad is on. (?)
  
  With DRI_PRIME=1
      FPS ~ 60
            56 while moving
  
  Without DRI_PRIME=1
      FPS ~ 45
            35 while moving
  ==================================
  Testing the original Linux version
  ----------------------------------
  The android goes somewhere when the gamepad is on. (?)
  
  With DRI_PRIME=1
      FPS ~ 20
            15 while moving
  
  Without DRI_PRIME=1
      FPS ~ 10
            5 while moving
  ==================================
  Testing the pre-SE2017 Linux version
  ----------------------------------
  
  With DRI_PRIME=1
      FPS ~ 60
            50 while moving
  
  Without DRI_PRIME=1
      FPS ~ 28
            10
  ```

- Use Prime. GPU-intensive applications should be rendered on the more powerful discrete card. The command xrandr --setprovideroffloadsink provider sink can be used to make a render offload provider send its output to the sink provider (the provider which has a display connected). The provider and sink identifiers can be numeric (0x7d, 0x56) or a case-sensitive name (Intel, radeon).Example:

  ```bash
  $ xrandr --setprovideroffloadsink radeon Intel
  ```

  You may also use provider index instead of provider name:

  ```bash
  $ xrandr --setprovideroffloadsink 1 0
  ```

  Now, you can use your discrete card for the applications who need it the most (for example games, 3D modellers...) by prepending the `DRI_PRIME=1` environment variable:

  ```bash
  $ DRI_PRIME=1 glxinfo | grep "OpenGL renderer"
  OpenGL renderer string: Gallium 0.4 on AMD TURKS
  ```

  Then we need to launch steam with the `DRI_PRIME=1` parameter:

  ```bash
  $ DRI_PRIME=1 steam
  ```

## References

1. https://www.reddit.com/r/SteamPlay/comments/aafhcn/steam_proton_doesnt_launch_any_games/
2. https://www.reddit.com/r/linux_gaming/comments/9mwh26/guide_how_to_install_deus_ex_with_gmdx_and_steam/
3. https://steamcommunity.com/app/12100/discussions/0/483367798514700344/
4. https://www.protondb.com/app/12100
5. https://steamcommunity.com/sharedfiles/filedetails/?id=1184013727 
6. https://github.com/FNA-XNA/FAudio
7. https://github.com/flibitijibibo/flibitBounties/issues/4
8. http://newsandguides.com/solution-how-to-install-xaudio2-and-fix-could-not-find-xaudio2-error-on-windows-7/
9. [Microsoft DirectX End-User Runtimes (June 2010)](https://www.microsoft.com/download/en/details.aspx?id=8109)
10. https://www.reddit.com/r/Supermeatboy/comments/6pi80k/tutorial_getting_super_meat_boy_beta_to_work_on/
11. https://appdb.winehq.org/objectManager.php?sClass=version&iId=22177
12. https://appdb.winehq.org/objectManager.php?sClass=version&iId=22216
13. https://steamcommunity.com/app/221410/discussions/0/828934913344641612/
14. https://wiki.archlinux.org/index.php/CPU_frequency_scaling#cpupower
15. https://www.reddit.com/r/TheTalosPrinciple/comments/dwgbcd/help_playing_the_game/