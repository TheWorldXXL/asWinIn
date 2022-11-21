# Installing & Compiling Aseprite for Windows
## Necessities 
##  1. Aseprite-v1.2.40-Source (Or most recent version)
You can simply just download it off of the github repository releases and such or use following link. <br />Github: [Aseprite](https://github.com/aseprite/aseprite/releasesE)<br />
Download: 
[Aseprite-v1.2.40-Source.zip](https://github.com/aseprite/aseprite/releases/download/v1.2.40/Aseprite-v1.2.40-Source.zip)
##  2. CMake
If not already installed open powershell and type "winget      CMake" to get the package manager to install CMake for you on the computer or you can use the linked installer. <br />Website: [Download CMake](https://cmake.org/download/) <br />Download:
[CMake Installer](https://github.com/Kitware/CMake/releases/download/v3.25.0/cmake-3.25.0-windows-x86_64.msi)
##  3. Get the Skia zip files
Download the windows version off either github or with the following link to the verison I used. <br />Github: [Skia for Aseprite](https://github.com/aseprite/skia/releases) <br />Download: [Skia-Windows-Release-x64.zip](https://github.com/aseprite/skia/releases/download/m102-861e4743af/Skia-Windows-Release-x64.zip)
##  4. Get the Ninja zip files
You can also download off their website or github page. <br />Github: [Ninja](https://github.com/ninja-build/ninja/releases)<br />Download:
[ninja-win.zip](https://github.com/ninja-build/ninja/releases/download/v1.11.1/ninja-win.zip)
##  5. Micrsoft VS Build Tools 2022 
You can install either off of their website or use the following link. You could also potentially use any other Windows terminal in theory but I cannot guarrantee it will work.<br />Website: <br />Download:
[Microsoft VS Build Tools 2022](https://aka.ms/vs/17/release/vs_BuildTools.exe)

---

## Installation


1.    Find the folder where CMake was installed. It"s likely to be in your `C:\ProgramFiles` directory on your disk if you used winget or it will be wherever you installed it to.<br /><br />
2.    You open up the "ninja-win.zip" file<br /><br />
2.1.   You can either extract the ninja.exe (the executable) inside of the bin folder of CMake `C:\INSERT-FILE-PATH\CMake\bin`<br /><br />
2.2.   Alternatively you can simply open the zip file and copy and paste the ninja executable inside the `CMake\bin` folder<br /><br />
3.    Go back to your `C:\` directory and create a folder called "deps"<br/><br />
3.1.   Inside of the `C:\deps` directory create another folder called "skia"<br /><br />
3.2.   Open up the `Skia-Windows-Release-x64.zip` and extract the file zip file inside of `C:\deps\skia` make sure that there is **No Duplicate Files**<br /><br />
4.    Go back to your `C:\` directory and create another folder titled "aseprite"<br /><br />
4.1.   Either copy the contents of the "Aseprite-v1.2.40-Source.zip" into the `C:\aseprite` directory<br /><br />
4.1.1. Alternatively you can also copy and paste the contents of the "Aseprite-v1.2.40-Source.zip" file into the `C:\aseprite` folder as well<br /><br />
4.2.  Once you"ve extracted the contents into the aseprite directory create a new directory/folder titled "build"
4.3.   Open the terminal you wish to use<br /><br />
4.3.1.     NOTE: The only terminal I know for sure works is Visual Studio build tools, though it is likely that you can use any terminal that will let you use CMake and Ninja, for this tutorial we will use "VS Build Tools 2022"<br /><br />
4.3.2. You can search for the "VS Build Tools 2022" terminal to open it<br /><br />
4.3.3. Alternatively you can also open "Command Prompt" and enter this command "`call C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\Tools\VsDevCmd.bat" -arch=x64`"<br /><br />
5. The VS Terminal should now be open in which you can then enter the comand "`cd C:/aseprite/build`"<br /><br />
5.1.  Once you in the build directory you want to generate the build environment using CMake. Enter the command "`cmake -DCMAKE_BUILD_TYPE=RelWithDebInfo -DLAF_BACKEND=skia -DSKIA_DIR=C:\deps\skia-DSKIA_LIBRARY_DIR=C:\deps\skia\out\Release-x64 -DSKIA_LIBRARY=C:\deps\skia\out\Release-x64\skia.lib -G Ninja ..`".<br /><br />
5.2. The previous process may take awhile, but once that process has completed. You will not it has completed when it says "Configuration Done" and "Generating Done".<br /><br />
5.3. Type the command "`ninja aseprite`" **NOTE:** This processes will also take a while as there is usually around 1500 files to compile.<br /><br /> 
5.4. Once that process has compilied if it has worked successfully you should be able to enter the `C:\aseprite\build\bin` directory and see a directory titled 'data' and the 'aseprite.exe' executable. Which you should then be able to double click to open to be able to use aseprite.

## Optional Steps (Recommended)

---

Once you have completed the normal steps you should be left with something like this if you use the search bar to find `Aseprite` it will either give you the app with none of your normal application options or a best match.

No Application Options:

<img src="https://cdn.discordapp.com/attachments/244502209318879232/1044025108513169590/image.png" alt= "Aseprite application as show if you try to search initially" width="400px">
<br /><br />
Best Match:

<img src="(https://cdn.discordapp.com/attachments/244502209318879232/1044025278055325736/image.png)" alt= "Aseprite searched on windows search bar with best match" width="400px">
<br /><br />


**NOTE:** The following steps are completely optional but are necessary if you want to do anything such as, pinning the `Aseprite` application to your taskbar or having shortcuts for it.

1. Create a new folder in either `C:\Program Files` or `C:\Program Files(x86)` titled "Aseprite".

**NOTE:** To my current knowledge it does not matter which you have the folder in, you can even have them in both if you wish but it's likely that it'll only open the one you set the shortcut to.

2. Go back to the `C:\asesprite\build\bin` and and copy both the data directory and the aseprite executable and paste them into the `C:\Program Files\Aseprite` or `C:\Program Files(x86)\Aseprite` (or both if you created both) directories that you created.

3. Now that you've done create a shortcut to the `Aseprite.exe` executable.

    3.1. You'll likely get the notifaction that the system is not able to create a shortcut in the Program Files directory that you pasted it to. You may select yes if you want a Aseprite shortcut to appear on your desktop.

4. Copy the shortcut that was created on your Desktop and go back to the `C:\` directory enter the `C:\ProgramData` directory.

    4.1. This directory will more likely than not be hidden by default so you will not be able to see it normally. You can change this by going to the `C:\` directry in either "Command Prompt" or "Powershell" (Personally I used powershell). To then type the command `attrib -h ProgramData` to now make it visual.

    4.1.1 Make sure to type the command `attrib +h ProgramData` if you want the directory to be hidden again once you're done.

    4.2. Alternatively you can also simply copy and paste or type in the the directory path  `C:\ProgramData\Microsoft\Windows\Start Menu\Programs`.

5. Once you have successfully completed all these steps you should have these options.

<img src="https://cdn.discordapp.com/attachments/244502209318879232/1044022280335921193/image.png" alt="Aseprite as shown on search bar with all options availabe" width="400px"/>
