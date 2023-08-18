# Unnamed SDVX clone ![language: C/C++](https://img.shields.io/badge/language-C%2FC%2B%2B-green.svg) [![Build](https://github.com/Drewol/unnamed-sdvx-clone/workflows/Build/badge.svg)](https://github.com/Drewol/unnamed-sdvx-clone/actions)
A game based on [KShootMania](http://www.kshootmania.com/) and [SDVX](https://remywiki.com/What_is_SOUND_VOLTEX).

### [**Download latest Windows build**](https://drewol.me/Downloads/Game.zip)
### [**Download latest Linux build**](https://github.com/Natsuhane-Ayari/unnamed-sdvx-clone/releases/download/v0.5.0/usc-game-v0.5.0.tar.gz)
### [**Download latest Arch Package**](https://github.com/Natsuhane-Ayari/unnamed-sdvx-clone/releases/download/v0.5.0-2/unnamed-sdvx-clone-bin-0.5.0-1-x86_64.pkg.tar.zst)
```sh
#Or install it from AUR with the command
yay -S unnamed-sdvx-clone-bin
```

### [**FAQ**](https://github.com/Drewol/unnamed-sdvx-clone/wiki/F.-A.-Q.)

#### [**Skinning Documentation**](https://unnamed-sdvx-clone.readthedocs.io/en/latest/index.html)

#### Demo Videos:
[![Gameplay Video](http://img.youtube.com/vi/1GCraT0ktrc/2.jpg)](https://youtu.be/1GCraT0ktrc)
[![Portrait Gameplay](http://img.youtube.com/vi/kP1tD6bkPa4/2.jpg)](https://youtu.be/kP1tD6bkPa4)
[![Various Settings](http://img.youtube.com/vi/_g9Xv5RDwa0/2.jpg)](https://youtu.be/_g9Xv5RDwa0)

### Current features:
- Completely skinnable GUI
- OGG/MP3 Audio streaming (with preloading for gameplay performance)
- Uses KShoot charts (`*.ksh`) (1.6 supported)
- Functional gameplay and scoring
- Saving of local scores
- Autoplay
- Basic controller support
- Changeable settings and key mapping
- Supports new sound FX method (real-time sound FX) and old sound FX method (separate NOFX & sound effected music files)
- Song database cache for near-instant game startup (sqlite3)
- Song database searching
- Linux/Windows/macOS support
- Song select UI/Controls to change HiSpeed and other game settings

### Features currently in progress:
- Lighting peripheral support
- More gauge types

### A better way to download Charts
- The ```usc-dlcha``` command is added to download Chart more convenientl
<br>Visit the [KSM](https://ksm.dev/) website, right click on **download**, and copy the link<br>
![Copy link](https://raw.githubusercontent.com/Natsuhane-Ayari/unnamed-sdvx-clone/develop/Screenshot/1.jpeg)
<br>Use the usc-dlcha command on the terminal, Ctrl+Shift+V to paste the link and press Enter, you can quickly download the Chart and import it into the game<br>
<img align="left" alt="usc-dlcha" width="40%" src="https://raw.githubusercontent.com/Natsuhane-Ayari/unnamed-sdvx-clone/develop/Screenshot/Screenshot_20230818_201022.png">
<img alt="In Game" width="50%" src="https://raw.githubusercontent.com/Natsuhane-Ayari/unnamed-sdvx-clone/develop/Screenshot/2.jpeg">


#
If something breaks in the song database, delete "maps.db". **Please note this will also wipe saved scores.**

## Controls
### Default bindings (Customizable):
- Start: \[1\]
- BTN (White notes , A/B/C/D): \[D\] \[F\] \[J\] \[K\]
- FX (Yellow notes, L/R): \[C\] \[M\]
- VOL-L (Cyan laser, Move left / right): \[W\] \[E\]
- VOL-R (Magenta laser): \[O\] \[P\]

### Song Select:
- Use the arrow keys or knobs to select a song and difficulty
- Use \[Page Down\]/\[Page Up\] to scroll faster
- \[F2\] to select a random song
- \[F8\] demo mode (continuously autoplay random songs)
- \[F9\] to reload the skin
- \[F11\] to open the the currently selected chart in the editor specified by the `EditorPath` setting
- \[F12\] to open the directory of the currently selected song in your file explorer
- \[Enter\] or \[Start\] to start a song
- \[Ctrl\]+\[Start\] to start song with autoplay
- \[FX-L\] to open up filter select to filter the displayed songs
- \[Start\] when selecting filters to toggle between level and folder filters
- \[FX-L\] + \[FX-R\] to open up game settings (Hard gauge, Random, Mirror, etc.)
- \[TAB\] to open the Search bar on the top to search for songs
- \[BT-B + BT-C\] Add song to collection (such as favourites)

## How to run:
Just run 'usc-game.sh'.

#### Command line flags (all are optional):
- `-notitle` - Skips the title menu launching the game directly into song select.
- `-mute` - Mutes all audio output
- `-autoplay` - Plays chart automatically, no user input required
- `-autobuttons` Like autoplay, but just for the buttons. You only have to control the lasers
- `-autoskip` - Skips beginning of song to the first chart note
- `-debug` - Used to show relevant debug info in game such as hit timings, and scoring debug info
- `-test` - Runs test scene, for development purposes only

## How to build:

### Windows:
It is not required to build from source. A download link to a pre-built copy of the game is located at the beginning of this README.
The recommended Visual Studio version is 2017, if you want to use a different version then you
will need to edit the 'GenerateWin64ProjectFiles.bat' if you want to follow the guide below.

0. Clone the project using `git` and then run `git submodule update --init --recursive` to download the required submodules.
1. Install [CMake](https://cmake.org/download/)
2. Install [vcpkg](https://github.com/microsoft/vcpkg)
3. Install the packages listed in 'build.windows'
4. Run 'GenerateWin64ProjectFiles.bat' from the root of the project
    * If this fails, try using the `-DCMAKE_TOOLCHAIN_FILE=[VCPKG_ROOT]\scripts\buildsystems\vcpkg.cmake` flag that vcpkg should give you on install
5. Build the generated Visual Studio project 'FX.sln'
6. Run the executable made in the 'bin' folder

To run from Visual Studio, go to Properties for Main > Debugging > Working Directory and set it to '$(OutDir)' or '..\\bin'

### Linux:
0. Clone the project using `git` and then run `git submodule update --init --recursive` to download the required submodules.
1. Install [CMake](https://cmake.org/download/)
2. Check 'build.linux' for libraries to install
3. Run `cmake -DCMAKE_BUILD_TYPE=Release .` and then `make` from the root of the project
4. Run the executable made in the 'bin' folder

### macOS:
0. Clone the project using `git` and then run `git submodule update --init --recursive` to download the required submodules.
1. Install dependencies
	* [Homebrew](https://github.com/Homebrew/brew): `brew install cmake freetype libvorbis sdl2 libpng jpeg libarchive libiconv`
2. Run `mac-cmake.sh` and then `make` from the root of the project.
3. Run the executable made in the 'bin' folder.

### Embedded (Raspberry Pi):
0. Clone the project using `git` and then run `git submodule update --init --recursive` to download the required submodules.
1. Install the libraries listed in 'build.linux'
	* For things that are not in the package manager repository or too low of a version you have to download and build yourself
	* SDL2 Can be installed using the instructions found [here](https://wiki.libsdl.org/Installation#Raspberry_Pi)
2. Run `cmake -DEMBEDDED=ON -DCMAKE_BUILD_TYPE=Release .`
3. If cmake completes succesfully run `make`
4. Run the executable made in the 'bin' folder
