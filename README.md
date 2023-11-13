## Setting up SDL2 for Windows 11 using MSYS2 MINGW64 and VS Code
A guide for setting up SDL2 with C/C++ on Windows 11 using MSYS2 and VS Code.

This tutorial assumes that [VS Code](https://code.visualstudio.com/) is already installed.

## Installing MSYS2

**Installing MSYS2**

1. Visit [msys2.org](https://www.msys2.org/) and download the installer.
2. After running the installer, follow the steps to install MSYS2 and leave everything as default.
3. Once the installation is finished, MSYS2 will run the UCRT64 environment.
4. Ensure everything is up to date by typing the following command:

   ```
   pacman -Suy
   ```

   More information about updating MSYS2 can be found on this [page](https://www.msys2.org/docs/updating/).

6. Close out of the UCRT64 environment and open the MINGW64 environment by using the windows search bar.

**Installing necessary packages**

1. Run the following command to install gcc/g++, along with some other necessary tools like make.

   ```
   pacman -S --needed base-devel mingw-w64-x86_64-toolchain
   ```

3. When asked to "Enter a selection (default=all)", press enter to accept the default.
4. Once the install finishes, verify that you have gcc and g++, by running the following:

   ```
   gcc --version
   ```
   ```
   g++ --version
   ```

6. Optionally, run `pacman -Suy` again to check for updates.

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

**The next step is to set up the SDL2 header/library files.**

1. Visit the [website](https://www.libsdl.org/) for SDL2 and under Download, click SDL Releases.
2. Click on the file named "SDL2-devel-2.28.5-mingw.zip". The version number might be slightly different.
3. Extract the file.
4. Inside the SDL2-2.28.5 folder, you should see two different folders containing mingw in the name.
5. i686-w64-mingw32 contains 32-bit libraries and x86_64-w64-mingw32 contains 64-bit libraries. I use the 64-bit version.
6. Inside these folders is an include and lib folder. You need to add them to the base directory for every new project.
7. You can also add them to a single folder in the base directory. I would name this folder sdl2dev.
8. You also need to include SDL2.dll in the base directory for every new project. It is located in the bin folder.

The final project workspace should look something like this:

`C:\msys64\home\USER\sdl2\PROJECTNAME` should contain the `sdl2dev` folder, which contains the `include` and `lib` folders.

`C:\msys64\home\USER\sdl2\PROJECTNAME` should also contain SDL2.dll outside of the `sdl2dev` folder.

**Extra Notes:**

There is a way to circumvent adding the include/lib folders and SDL2.dll everytime you start a new project, but it requires messing with VS Code .json files.

Whenever you compile a program with SDL2, you need to include the paths to the SDL2 libraries and header files. An example is shown below.

**Compiling a Program**



## Developing a Sample Program

## Releasing the Program

## Notes on Cross Compiling
