## Setting up SDL2 for Windows 11 using MSYS2 MINGW64 and VS Code
A guide for setting up SDL2 with C/C++ on Windows 11 using MSYS2 and VS Code.

This tutorial assumes that [VS Code](https://code.visualstudio.com/) is already installed.

Make sure to install the C/C++ extension.

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

**Setting up Environment Variables**

1. In the windows search bar, search for `Edit environment variables for your account` and open it.
2. Click on path, then click edit.
3. Click new, and add this to the new path: `C:\msys64\mingw64\bin`
4. Click OK, then OK again to exit out.

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
6. Inside these folders is an include and lib folder. There is also a bin folder that contains SDL2.dll.
7. Create a new folder named `sdl2dev` and drag the include and lib folder into it.
8. For every new project, include the `sdl2dev` folder and the SDL2.dll file (inside the bin folder) in the base directory.
9. For simplicity, you can move these files into another folder and copy/paste for any new project.

The final project workspace should look something like this:

`C:\msys64\home\USER\sdl2\PROJECTNAME` should contain the `sdl2dev` folder, which contains the `include` and `lib` folders.

`C:\msys64\home\USER\sdl2\PROJECTNAME` should also contain SDL2.dll outside of the `sdl2dev` folder.

Again, make sure that your project contains the include/lib folders and SDL2.dll. These are important for compiling.

**Extra Notes:**

There is a way to circumvent adding the include/lib folders and SDL2.dll everytime you start a new project, but it requires messing with VS Code .json files. 

Whenever you compile a program with SDL2, you need to include the paths to the SDL2 libraries and header files. An example is shown below.

## Compiling a Program

To compile a program, you have a few options. The first is to run a command on the terminal. The second is to use a Makefile.

Both of the below commands work for compiling a program. If your include/library paths are different, make sure to set it correctly.

```
g++ main.cpp -o main -I ./sdl2dev/include/SDL2 -L ./sdl2dev/lib -w -Wl,-subsystem,windows -lmingw32 -lSDL2main -lSDL2
```

```
g++ main.cpp -o main -IC:./sdl2dev/include/SDL2 -LC:./sdl2dev/lib -w -Wl,-subsystem,windows -lmingw32 -lSDL2main -lSDL2
```

You can also set up a Makefile to this process easier, especially if your project includes a lot of files.

**Additional Notes**

You can use -IC: or -I to set the include path for header files. The same goes for library files, with -LC: or -L.
Note that -IC:/-LC: doesn't need a space before the include path.

I'm using ./ to start the include path from the folder I'm compiling in. If something doesn't work for you, try using the full path to the include/lib files.

-w -Wl,-subsystem,windows are used to suppress warnings and remove a console window.

-lmingw32 -lSDL2main -lSDL2 are some additional flags for linking to SDL2.

## Developing a Sample Program

## Releasing the Program

## Notes on Cross Compiling
