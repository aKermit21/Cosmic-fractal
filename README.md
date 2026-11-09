# Cosmic Fractal
**Cosmic Fractal — 2D Animation, Game**

more descriptive name: *Exponentially Growing Fractal Leaf* 

# Principle
Elements of a leaf-shaped fractal are drawn recursively by applying a defined transformation that turns the largest element into progressively smaller ones.
However, from time to time, one of the existing elements undergoes a spontaneous *mutation*. It begins to gradually grow, along with all of its subordinate elements. This creates — or rather modifies — a branch, which ends up usually larger than its predecessor.
After a short time, the mutation process repeats itself within the already mutated branch.

As a result, the fractal structure grows upward exponentially, and the frame rescales to cover more and more area. The structure starts from 24 cm, which is roughly the initial structure size on the screen.
After about 30 minutes of self-perpetuating *Animation*, the fractal reaches the size of the Milky Way Galaxy. More precisely, when the animation is finished, it covers the distance from Earth to the *Edge of the Galaxy*. That time, however, may be shortened by user actions — and here is where the *Game* part comes into play...

# Game
If, during the mutated growing phase, the stem *catches* light rays of a similar color, that stem becomes *Excited* (super-charged). It will then extend its size even further and faster.
Catching light happens when light rays (illustrated when the light source is in motion) cross perpendicularly to the stem axis. This is indicated by the stem color turning white.
It is up to the player to manipulate the light source while the fractal structure is growing. This is done using the arrow keys.

Since a stem usually has different colors on its two ends, the intermediate color matters. This is represented by a color flag pointing to the middle of the stem.

# ⌨ Keyboard Actions
The light source, and thus the game, is controlled by the arrow keys (or WASD keys).  
The horizontal arrows rotate the color, and the vertical arrows move the light source.

Below is a list of key functions:

| Key          | Function                                         |
| ------------ | ------------------------------------------------ |
| F1           | Help                                             |
|              |                                                  |
| ↑ Up or W    | Move light source up                             |
| ↓ Down or S  | Move light source down                           |
| ← Left or A  | Rotate light color                               |
| → Right or D | Rotate light color (reversed)                    |
|              |                                                  |
| F3           | Load next initial configuration from config file |
|              |                                                  |
| Space        | Pause / Freeze mutation animation                |
| Enter        | Resume mutations                                 |
| R            | Reset                                            |
| X            | Exit                                             |
|              |                                                  |
| L            | Toggle light on/off                              |
| G            | Switch grid ray visualization mode               |
|              |                                                  |
| J            | Dimm all colors (dJimm) by 20%                   |
| U            | Up all colors by 20% (reverse to previous)       |
|              |                                                  |
| Page Up      | Speed up drawing (less detail)                   |
| Page Down    | Slow down drawing (more detail)                  |

more complete list can be found on dedicated [documentation site](https://exfra.pcc21.com/)

# Preceding Project

This project is based on [fractal-anim](https://github.com/aKermit21/fractal-anim.git) by the same author. Both can use the same initial configuration file(s). (In fact, the previous project was used to design the initial fractal leaf shapes and colors.)

# Installation
## Dependencies
- **SFML** (2D graphics and more) — depending on the installation type, it must either be installed *manually* beforehand (see [sfml website](https://www.sfml-dev.org/)) or compiled using the included *CMake* script.
- lyra (C++ arg parser) — embedded as a subproject (see [original lyra source](https://github.com/bfgroup/Lyra))
- tomlplusplus — embedded as a subproject (also available through package managers)

## Using Installer Script
This is applicable only to **Linux** as it uses compiled binary.  
Install **sfml** and **tomlplusplus** before using for example package manager.  
Fetch Installer:
```shell
curl -O https://raw.githubusercontent.com/aKermit21/fractal-grow/main/scripts/install.sh
```
Run Installer:
```shell
chmod +x install.sh
./install.sh
```

> **_NOTE:_** `install.sh` script can be found also in project itself.

## Installing via PKGBUILD (Arch Linux)

This method is for **Arch Linux and Arch-based distributions** (Manjaro, EndeavourOS, etc.) using the pacman package manager.

### Fetch the PKGBUILD
```shell
curl -O https://raw.githubusercontent.com/aKermit21/fractal-grow/main/scripts/PKGBUILD
```

### Build and install
```shell
makepkg -si
```
This builds the package and installs it with all required dependencies.

## By Project Compilation
Clone the GitHub project.

The procedure below was tested on Linux and Windows.
On Linux, the Meson build system is recommended, and on Windows, CMake.

### Using Meson

Install **SFML** manually, preferable using package manager. Then

```shell
cd Cosmic-fractal
mkdir build-release/
meson setup build-release/
cd build-release/
meson compile
./cosfra [-h]   # to run the app directly from the build directory
```

### Using CMake

```shell
cd Cosmic-fractal
cmake -DCMAKE_BUILD_TYPE=Release -B build-dir
cmake --build build-dir --config Release
cd build-dir/bin/Release
[./]cosfra[.exe] [-h]  
```

## Running

To check available options:
```shell
[./]cosfra --help
```

It might be worth trying the demo:
```shell
[./]cosfra --demo
```

If installation was done by installer script (`install.sh`) there shall be possible also to run apllication (with default settings) using Desktop Environment launcher by searching for application name—*Cosmic Fractal*.

If animation flickers—which can happen on slow machines—increase the drawing speed by pressing `PageUp`; 
also try to adjust `--fps` (Frames per second) parameter.

Press `F1` at runtime to display list of available key actions.

## Contributions
Contributions are welcomed! The most straightforward and impactful way to help is by enhancing the **visual content** of the project.

### Add or Improve Size Comparison Images

A great place to start is by adding or replacing images that illustrate the scale of the fractal structure. This is a highly desired contribution because:

*   The current set of four images is small and could be more compelling.
*   There is significant creative potential to visualize the project's incredible size progression, from a small start to a galactic scale.

### How to Implement a New Picture

Detailed instructions for creating and adding a new image are available in our documentation (Image Scale chapter):

👉 **[Image Scale Implementation Guide](https://exfra.pcc21.com/imageScale)**

Please follow this guide carefully to ensure your contribution integrates smoothly with the project's build system and rendering logic.

### Create Mac OS Installation

Another area for enhancement is the installation procedure for Mac OS and possible Windows.

### General Contribution Guidelines

For all other contributions:

1. **Fork the repository** and create a new branch for your feature or fix.
2.  **Ensure your code builds** with the Meson build system.
3.  **Write clear commit messages** explaining the "what" and "why" of your changes.
4.  **Submit a pull request** with a detailed description of your work.

## Modifications

To modify and test changed code using Meson, it is recommended to use a separate build directory (e.g., `build-dev/`) containing a modified build settings instance:

```shell
meson setup build-dev/
cd build-dev/
meson configure --buildtype=custom --optimization=2
```
This will enable assertions and extensive logging.

# Screenshots
![Game Over](assets/images/Game-over.png "Game Over")

![Demo Runnning](assets/images/Demo-running.png "Demo running")
