<!-- Made with ❤️ by Smashtika(@yungDoom) -->

![Icon](/other/design/icon/icon.png)

<h1 align="left"> 📜 GTA V Source Code Build Guide </h1>

⚠️ *If you having any problem, let us know in the ["Issues"](https://github.com/P0L3NARUBA/gtav-sourcecode-build-guide/issues) section of this repository!*<br>
💬 *You can check out ["Discussions"](https://github.com/P0L3NARUBA/gtav-sourcecode-build-guide/discussions) for talking and discuss.*

# Contents
1. [Prerequisites](#prerequisites)
   1. [Base](#base)
   2. [Dependencies](#dependencies)
   3. [Miscellaneous](#miscellaneous)
   4. [Prebuilt Files](#prebuilt-files)
2. [Prerequisites Setup](#prerequisites-setup)
3. [Patching The Source Code](#patching-the-source-code)
4. [Building Process](#building-process)
   1. [Building The Game Binary/Executable](#building-the-game-binaryexecutable)
   2. [Building Shaders](#building-shaders)
   3. [Building Game Scripts](#building-game-scripts)
5. [Patching Game Assets](#patching-game-assets)
   1. [Main Game Assets](#main-game-assets)
   2. [Modifying the RPF Files](#modifying-the-rpf-files)
6. [Running The Game](#running-the-game)
7. [BankRelease & Debug Controls](#bankrelease--debug-controls)
8. [Known Bugs and Errors](#known-bugs-and-errors)
   1. [Known Issues](#known-issues)
      1. [Main Issues](#main-issues)
      2. [Gameplay](#gameplay)
9. [Working Status](#working-status)
   1. [Compiling](#compiling)
   2. [Main Working Status](#main-working-status)
10. [Final Thoughts](#final-thoughts)
    1. [Credits](#credits) 


## Prerequisites
### Base
 - Windows 10/11
    - [LTSC 2021](https://archive.org/download/Windows10EnterpriseLTSC202164Bit/en-us_windows_10_enterprise_ltsc_2021_x64_dvd_d289cf96.iso) Recommended, but you can use Normal Windows 10/11 too.
 - Latest Grand Theft Auto V Files from Steam, Epic Games or maybe Rockstar Games Launcher. 
 - Minimum 65GB Free Space, 140GB+ is Recommended because of the game files and programs.
 - GTAVSP.7z - Source Code<br>
    - **Download Link: [All Available Download Links](/source-code-links.md)**
    - Archive Password: `Mi76#b>9mRed`
   - You can verify the authenticity of the file by its SHA1 hash: `ca39323730ed644fa534a2946506d4287f92a799`
     - To verify with 7-Zip, right click the file and select `7-Zip > CRC SHA > SHA1`
 - [update.rpf and update2.rpf from GTA V build 2699](https://mega.nz/file/72plXYpY#B9A3vDidqPUVhfXDP5hWCS8lc90lcdGZsGfjuWkBDe8)
 - Some Patience and Technical Competence

### Dependencies
 - [Visual Studio 2012](https://files.dog/MSDN/Visual%20Studio%202012/en_visual_studio_ultimate_2012_x86_dvd_2262106.iso)
    - [Update 4 for Visual Studio 2012](https://files.dog/MSDN/Visual%20Studio%202012%20Update%204/mu_visual_studio_2012_update_4_x86_dvd_3161759.iso)
 - [DirectX SDK June 2010](https://download.microsoft.com/download/A/E/7/AE743F1F-632B-4809-87A9-AA1BB3458E31/DXSDK_Jun10.exe)
 - (OPTIONAL) [3D Studio Max 2010 SDK](https://archive.org/details/sdk-3ds-max-2010)
 - [Incredibuild 4.0](https://xoreax-incredibuild.software.informer.com/4.0/)
    - This is only needed for compiling Shaders and Game Scripts.
 - [7-Zip](https://7-zip.org/a/7z2301-x64.exe)
    - For extracting the archives.
 - [OpenIV](https://openiv.com/WebIV/guest.php?get=1)
    - For editing the game files.  

### Miscellaneous
 - [Rush Patches](https://github.com/WH0LEWHALE/gtav-sourcecode-build-guide/files/14641602/rush_patches-master.zip)
 - [DLL Patches](https://github.com/P0L3NARUBA/gtav-sourcecode-build-guide/files/14965810/dll_patches_x.zip)
 - (OPTIONAL) [3rdParty Folder](https://mega.nz/file/SqojFJZL#eYINo1pnspuTvdbocz4cA7NYZA8BN2H2nm7YEXuzlFw)
 - (OPTIONAL) [gIKgDXuVHNzIgXkiwpB.zip - Art Asset Leak](https://big.fileditchnew.ch/b9/gIKgDXuVHNzIgXkiwpB.zip)
    - [Mirror Link](https://www.bojarcz.uk/gIKgDXuVHNzIgXkiwpB.zip)
 - [Network Fix](https://github.com/P0L3NARUBA/gtav-sourcecode-build-guide/files/15209424/Network.Fix.zip)
    - This will fix the Studio or IP related issues.

### Prebuilt Files
 - [Shaders](https://github.com/WH0LEWHALE/gtav-sourcecode-build-guide/files/14649717/common.zip)
 - [Scripts](https://drive.google.com/file/d/1AVMC_MBPpqKp0BIrOI-_lLq98QmwRn46/view) (Already included in *update.rpf and update2.rpf from GTA V build 2699*, Just for backup purposes.)

___

> [!NOTE]
> It is recommended to create a virtual machine, Although the build process can be done on your Real PC too!<br>
> in Windows, **VMWare, Hyper-V or VirtualBox** are recommended to run the Virtual Machine.<br>
> in Linux, **virt-manager** are recommended to run the Virtual Machine.

## Prerequisites Setup
1. Install DirectX SDK June 2010
   - **If you get error S1023, Uninstall `Visual C++ 2010 Redistributable` & Reinstall DirectX SDK - (June 2010).**
2. Install 7-Zip
3. Install Visual Studio 2012
   - Uncheck all optional components in the installer **except "Microsoft Foundation Classes for C++"** to save space due to none of them are needed for the build.
4. Install Update 4 for Visual Studio 2012
5. Install Incredibuild 4.0
   - If you encounter the error that the installer is "Blocked by your administrator", follow these steps:
      1. Hold Shift and right click the `incredibuild4_0.exe` file, select "Copy as path"
      2. Open Command Prompt as Administrator
      3. Paste the path and press Enter
   - Select to install "Incredibuild Agent", "Incredibuild Coordinator", and the extension for Visual Studio
6. Install OpenIV
7. (OPTIONAL) Install 3D Studio Max 2010 SDK
8. Create X:\ Drive by following the steps at the bottom:
    1. Open Command Prompt
    2. Create a new folder called "GTA" to the Desktop or anywhere that you want
    3. Run `net use X: \\localhost\c$\<Path to working folder for build> /persistent:yes`
       - Example: `net use X: \\localhost\c$\Users\<username>\Desktop\GTA /persistent:yes`
9. Create the folder `X:\gta5` and copy all folders from `GTAVSP.7z\GTA V Source` into it
10. Right click the folder `X:\gta5`, select "Properties", uncheck "Read-only", click Apply then OK
11. Open Command Prompt as Administrator and run the following commands, then close:
```batch
setx /m RS_TOOLSROOT X:\gta5\tools_ng
setx /m DXSDK_DIR "C:\Program Files (x86)\Microsoft DirectX SDK (June 2010)"
setx /m RS_CODEBRANCH X:\gta5\src\dev_ng
setx /m RS_PROJECT gta5
```
12. Put all the game files to the `X:\gta5\titleupdate\dev_ng` directory
13. To ensure changes are finalized, restart build machine/computer.

## Patching The Source Code
1. Open `rush_patches-master.zip`
2. Copy `game` and `rage` folders to `X:\gta5\src\dev_ng`, make sure to overwrite when copying
3. (OPTIONAL) To skip launcher requirement for running the game, copy `game` and `rage` folders from `rush_patches-master.zip\OPTIONAL_FIXES` to the same folder
4. Copy all folders in `dll_patches_x.zip` to `X:\gta5\tools_ng\bin`, make sure to overwrite when copying
5. Extract `Network Fix.zip` and put these 2 files to `x:\gta5\tools_ng\etc\globals`, make sure to overwrite when copying
6. (OPTIONAL) Install 3rdParty Folder, Extract and Put the folder to `X:\`.

**By far, Your Folder Structure should look like this:**
```
🖥️ X:
 ┣ 📂 3rdParty - (OPTIONAL)
 ┗ 📂 gta5
    ┣ 📂 src
    ┃ ┣ 📂 dev_ng
    ┣ 📂 script
    ┃ ┣ 📂 dev_ng 
    ┗ 📂 tools_ng
```

## Building Process

### Building The Game Binary/Executable
1. Run `X:\gta5\src\dev_ng\game\VS_Project\load_sln_unity_2012.bat`
	- If prompted with "How do you want to open this file?", check "Always use this app to open .sln files" and Select **Visual Studio 2012** then click OK
2. Once the solution loads, open the dropdown menu that says "Debug" at the top, select "Configuration Manager"
3. Change "Active Solution Platform" to "x64" and close the configuration window
4. Hold Ctrl key and click all projects under "GameLibs" and "Rage" folder, right-click and select "Properties"
5. In the "Configuration" dropdown, select "All Configurations"
6. Select `C/C++ > All options`, under "Look for options or switches", search "err" and set "Treat Warnings as Errors" to "No (/WX-)", then click "Apply" and "OK"
   - For faster compiles, search "mul" and set "Multiprocessor Compilation" to "Yes (/MP)"
      - If you get the error `C1060: Compiler is out of heap space` during build, come back to the above setting and turn it off
7. Right-click the "game" project and select "Properties" and do step 5,6 again
8. Change build the type at the top of the window from "Debug" to "BankRelease"
   - This Step is optional, you can build the game in "Debug" too but you will lost alot of performance
10. At the top of the window, select `Build > Build Solution` and wait for build to finish
11. Copy output binary to game folder.

If you confused, Watch this video:

https://github.com/P0L3NARUBA/gtav-sourcecode-build-guide/assets/146978592/a07cfd2e-a350-419e-ad9e-db6fc7a1ccff

> [!WARNING]
> Building shaders and game scripts can be skipped using the [prebuilt files above](#prebuilt-files)<br>
> For Shaders, Extract `common.zip` and just put the `common` folder to the Game Directory<br>
> For Scripts, Run OpenIV and put the `script.rpf` file to `\update2.rpf\x64\levels\gta5\script`<br>
> These steps are here to allow modding or for those who prefer to build from source as much as possible.

### Building Shaders
1. Under "Shaders", right click the "shaders_rc" project and click "Build"
2. (OPTIONAL) Build low quality shaders
   1. Right click the "shaders_rc" project and click "Properties"
   2. Select `Configuration Properties > NMake`
   3. Under "General", change all command lines from ending with `win32_40.bat` to ending with `win32_40_lq.bat`, then click "Apply" and "OK"
   4. Rebuild shaders and wait it to finish
3. Copy `X:\gta5\titleupdate\dev_ng\common` to game directory.

### Building Game Scripts
1. Open Command Prompt and Run the following commands:
```batch
X:
cd X:\gta5\src\dev_ng
setenv
cd ..\..\tools_ng\bin\RageScriptEditor
ragScriptEditor
```
3. In the editor, select `File > Open Project` and open `X:\gta5\script\dev_ng\singleplayer\GTA5_SP.scproj`
4. Select `Compiling > Intellibuild > Build Project` and wait until the compiling process finishes
5. Run OpenIV, select "Windows" under "Grand Theft Auto V"
6. Select the game folder and click "Continue"
7. Open `<Game Directory>\update\update2.rpf\x64\levels\gta5\script`
8. Delete `script.rpf`
9. Click the "Edit mode" button, and copy `X:\gta5\titleupdate\dev_ng\x64\levels\gta5\script\script.rpf` to the OpenIV window.


## Patching Game Assets

#### Main Game Assets

1. Install `update.rpf and update2.rpf from GTA V build 2699` from [Prerequisites List](#prerequisites)
2. Put `update.rpf` and `update2.rpf` files to `<Game Directory>\update\` folder
   - **Dont forget to backup your old files from update folder.**

#### Modifying the RPF Files
If you ever modify the RPF files, dont forget to encrpyt them.<br>
**Here you can see how to do it:**
1. From `rush_patches-master.zip`, copy all files in the `ARCHIVEFIX` folder to a separate location
2. Drag RPF file(s) onto `ArchiveFix.exe`
   - Don't drag the both files at the same time, **just drag one by one**.

## Running The Game
1. Make sure your compiled .exe is named "game_win64_bankrelease.exe" 
2. In the game directory, create a file named `launch.bat` and add these contents:
```batch
cd %~dp0
game_win64_bankrelease.exe -noSocialClub -nokeyboardhook -nonetlogs
```
3. (OPTIONAL) Add additional arguments:
 - `-kbgame` - Start game with game keyboard enabled
 - `-output` - Show console log of game, the game opens a little bit slow.
 - `-rag` - Enable support for RAG, the internal game debugging tool
    - `-ragUseOwnWindow` - Use it with `-rag` parameter to make game run outside of RAG Render Window
    - **DO NOT** Forget to Launch RAG Before launching the game if u using any RAG parameters
 - `-DoReleaseStartup` - Start real Story Mode on launch, Ignore if it says unknown parameter/command
    - If you dont type this parameter, you will spawned in a random location as a random character with a random clothes
 - Additional standard game arguments can be added as well.
   - [Here is the almost all the arguments list](other/LAUNCHPARAMS_GTAV.txt) 
4. (OPTIONAL) Launch RAG with the following commands in Command Prompt:
```batch
X:
cd X:\gta5\src\dev_ng
setenv
cd ..\..\tools_ng\bin\rag
rag
```
5. Run `launch.bat`

## BankRelease & Debug Controls

[Almost Every Controls & Keys](/other/controls)

# Working Status

#### Compiling
- [x] Can Compile Game
- [x] Can Compile Tools
- [x] Can Compile Game Scripts
- [x] Can Compile Shaders

#### Main Working Status
- [x] Game
  - [ ] Script Hook V and ASI Loaders
     - It doesn't work because memory offsets and certificate problems.
- [x] Tools
  - [x] RagScriptEditor
  - [x] Rag
    - [x] Rag UI
    - [x] Rag Interface 
  - [x] Map Viewer
  - [x] Shortcut Menu 
  - [x] Other Tools
    - Note that Some Perforce login required tools will not work, they need some modifications and Perforce.
      - Perforce Download Links:
        1. Helix Core: https://www.perforce.com/downloads/helix-core-free-small-teams
        2. Helix Visual Client: https://www.perforce.com/downloads/helix-visual-client-p4v


# Known Bugs and Errors

#### When I create "Vehicles" Widgets, the game crashes.
Before Opening The Save Game, just enter the game normally and dont load the save, create vehicle widgets then load the game.

#### Fatal Error: Unable to create default effect 'common:/shaders/im', cannot continue.
If u didn't put the shaders to the game directory or you dont have the low quality shaders, then this error may appear.<br>
Just try these solutions in order to make the game work:

###### Solution 1: 
Just Simply Put the shaders to the game directory and compile the low quality shaders by [following tutorial](#building-shaders).

###### Solution 2:
Just make your shaders quality "High" and dont lower that.<br>
To do this, Follow this steps:

1. Go To **\Documents\Rockstar Games\GTA V**
2. Open *settings.xml*
3. Change  `<ShaderQuality value="0" />` To `<ShaderQuality value="1" />`
4. Save the file and Done!

#### Couldn't connect to RAG.exe. Keep trying?
Just Simply Open the RAG Manually, then start **launch.bat**.

## Known Issues

### Main Issues

#### RagScriptEditor

##### RagScriptEditor crashing while at building cache.
   - This is well-known issue, You need to do everything again in VM, if you're already in a VM, Delete the Virtual Machine and start over.
   - Related Issues: [#46](https://github.com/P0L3NARUBA/gtav-sourcecode-build-guide/issues/46)

##### RagScriptEditor Building Cache stuck at zero
   - Sometimes it can happen and i think it's an processor issue, try in single core.
   - Related Issues: [#15](https://github.com/P0L3NARUBA/gtav-sourcecode-build-guide/issues/15)

### Gameplay

#### Game crashes if you open "Keybinds" Menu in *BankRelease* or *Debug* Builds
  - It's because the game tries to load a missing debug keyboard layout file
    - This can probably be fixed by just editing some lines in the source code.
   
#### When you load the Save, all of your money will be wiped to zero
  - There is a code that does this, i dont know which code but its because we are in BankRelease or Debug
     - You can just use money hacks to bring your old money.

# Final Thoughts

Thanks for reading my precious tutorial, if u liked it please consider starring or forking the repository.<br>
**Feel free to contribute the repository, you'll be welcomed if you dont make stupid thingies.**

## Credits

- [@GTA-Source-Helper](https://github.com/GTA-Source-Helper)
   - Network Fix
- [@RockstarAdvancedGameEngine](https://github.com/RockstarAdvancedGameEngine)
   - OneDrive Link for Source Code
   - Mirror Link for Art Asset Leak
- Other Contributors / Supporters
   - Thanks to all of you guys!
  
<!-- Made with ❤️ by Smashtika(@yungDoom) -->
