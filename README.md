## Setting up SDL2 for Windows 11 using MSYS2 MINGW64 and VS Code
A guide for setting up SDL2 with C/C++ on Windows 11 using MSYS2 and VS Code.

This tutorial assumes that [VS Code](https://code.visualstudio.com/) is already installed.

## Installing MSYS2

**Installing MSYS2**

1. Visit [msys2.org](https://www.msys2.org/) and download the installer.
2. After running the installer, follow the steps to install MSYS2 and leave everything as default.
3. Once the installation is finished, MSYS2 will run the UCRT64 environment.
4. Ensure everything is up to date by typing the following command:

   `pacman -Suy`

   More information about updating MSYS2 can be found on this [page](https://www.msys2.org/docs/updating/).

5. Close out of the UCRT64 environment and open the MINGW64 environment by using the windows search bar.

**Installing necessary packages**

1. Run the following command to install gcc/g++, along with some other necessary tools like make.

   `pacman -S --needed base-devel mingw-w64-x86_64-toolchain`

2. When asked to "Enter a selection (default=all)", press enter to accept the default.
3. Once the install finishes, verify that you have gcc and g++, by running the following:

   `gcc --version` and `g++ --version`

4. Optionally, run `pacman -Suy` again to check for updates.

**Setting up the workspace**

1. Navigate to the msys2 directory using the file explorer, which is typically located at:

   `C:\msys64`

2. Enter the home directory and enter your user folder.
3. Create a new folder in this location and name whatever you like, such as sdl2.
4. The final path to your sdl2 workspace should be:

   `C:\msys64\home\USER\sdl2`

5. Verify that you can access this folder through the MSYS2 MINGW64 terminal by typing

   `ls` then `cd sdl2`

6. You can create a new folder in this directory which will hold all the files for a project.

## Setting up SDL2

## Developing a Sample Program

## Releasing the Program

## Notes on Cross Compiling
