# InstallPepegaLinux

Tutorial for installing and configuring NFS Most Wanted Pepega Edition Mod on Linux.

If you don't know what Pepega Edition is, it's basically a community-created modpack that puts a lot of memes into the game, as well as new cars, improved graphics, new Blacklist drivers and completely insane Challenger Series. You can find more information and downloads at [pepegamod.com](https://pepegamod.com/).

Special thanks to **/u/samcool55** for sharing his config with me :^)

This instruction has been tested on Steam Deck/SteamOS 3.2.1 and Arch Linux 6.0.2. May or may not require additional steps for different distros.

## Pre-requisites

- Lutris
- Working most wanted 1.3 installation (vanilla or Pepega patched) or working installer
- Pepega mod files + 2.0.1 update (if vanilla installation)
- NFS MW HUD Adapter (publicly available script to fix HUD layout)
- Recommended external kb + mouse on Steam Deck for comfort

## Installation

1. Either get a working installation from a windows PC (vanilla 1.3 or with Pepega already installed), or get a working custom installer and install through Wine - the point here is to have a working 1.3 installation. We do not care about controller or graphics options for now, we're just making sure the game is able to launch.

2. In a writeable directory, create a new folder for the wine prefix - homedir is fine. Name it however you want, below is just my example:

```
mkdir /home/deck/Games/nfsmw_pepega
```

  If you have a working installation, you can just copy-paste all the files into this directory. 

3. In lutris, add a new game -> Add locally installed game with settings as below:

  **Game info**:
  
  Name: whatever you want
  
  Runner: Wine

  **Game options**:

  Executable:
  - if you have a working installer, copy the path to Setup.exe here;
  - if you copied the files already, select the path to speed.exe:
```
/home/deck/Games/nfsmw_pepega/speed.exe
```

  Working directory:
```
/home/deck/Games/nfsmw_pepega
```

  Wine prefix:
```
/home/deck/Games/nfsmw_pepega
```

  Prefix architecture: Auto (default)


  **Runner options**:
  Wine version - lutris.fshack-7.2-x86_64

  **System options**: nothing to change here

4. Save config, select the game from your library and press Play. If you copied a prepared installation, skip to step 9.

5. If Wine wants to install any additional packages (i.e. Mono), let it do so.

6. If you're running an installer, as install location choose your wine prefix:
```
Z:\home\deck\Games\nfsmw_pepega
```
  In my case the directory was not visible, just input it manually.

7. Don't install any additional packages like DirectX if prompted.

8. After installation is complete, change the Executable path to speed.exe like in step 3.

9. Try playing the game. At this point Wine should configure the prefix and Most Wanted should start in it's whole 640x480 glory.
  If you copied a vanilla installation, it *should* also run. If you copied Pepega-patched installation, it will probably run, but you will definitely experience glitches like out-of-scale intro movies and missing car models. This is fine!

10. If you ran the game and created a profile, delete it and quit.

11. Back in Lutris, right-click the game and select Configure.

12. In Game options, set the Executable to Pepega Mod Version 2 Installer.exe, save and run the game.
  Note: Text in installer may not render correctly, in my case it was all black-on-black text, but all necesarry options are visible.

  Navigate like so:
```
1. Next
2. scroll readme -> Next
3. in path manually input your folder: Z:\home\deck\Games\nfsmw_pepega
4. uncheck the tickbox to backup files
5. on next screen, leave checkboxes as they are -> Next
6. same on next screen unless you want to change some options -> Install
```

13. If it looks like the installer is hung at 0%, just give it some time and it will start eventually.

14. When progress reaches 100%, check the installation log and if you notice a lot of errors like: `Copy failed:java.io.IOException: No more files`,
just finish the installer, and then copy+overwrite all files from `PepegaModFiles` folder to your game folder.

15. Now, copy+overwrite the files from patch 2.0.1 directory - choose if you want light cones or not (I recommend using them).

16. Back in game configuration, switch the executable back to speed.exe.

17. In Lutris menu, press the up arrow next to Wine logo, and select 'Wine configuration'.

18. Go to 'Libraries' tab, and in 'New override for library' find and Add overrides for following libs:

```
D3DX9_43
dinput8
winhttp
```
  Apply and close the config.

19. Now copy the `NFSMWHUDAdapter.asi` file to `scripts` folder in gamedir.

20. Final thing to do is open the `NFSMostWanted.WidescreenFix.ini` file with your favorite text editor and set the following options:

```
ResX = 1280 
ResY = 800
^These values are for steamdeck native resolution, adjust accordingly for your display

ImproveGamepadSupport = 1 //This will make the in-game keybinds display Xbox symbols
```

21. Save the changes and try running the game. If you followed the instruction correctly, you should be greeted by Team Pepega splash screen.

22. If you're on Steam Deck, in Lutris menu right-click the game and select "Create Steam shortcut". Now you can exit to Game Mode and you'll see a new non-steam game in your library, with full gamepad support on default settings.

23. Congratulations, and welcome to Cockport.
