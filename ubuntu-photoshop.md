# Adobe Photoshop CS6 on Ubuntu

## Wine 
- `sudo apt-get install wine -y` - install wine. -y - is a flag for answering "yes" on any ap-get questions
- `rm -rf ~/.wine` - remove .wine folder in home directory. You may have Wine already installed
- `WINEARCH=win32 WINEPREFIX=~/.wine winecfg` - change prefix to 32-bit arch and configure your wine. Select "Windows 7"
- `wget http://www.kegel.com/wine/winetricks` - download winetricks script 
- `sh winetricks -q vcrun2005sp1 vcrun2008 fontsmooth-rgb corefonts msxml3 msxml6 vcrun2010` - install dependencies for photoshop. This dependencies exists in repos in this moment (28.01.2018). But even now not all dependecies you can install via winetricks
- follow [this link](https://drive.google.com/folderview?id=0Bx5snn9kEq3ZfmRBeng2czU4aFZza2tLc0FUb2JpeHM4YVgtdEdNZjBxU3NkX2Q4WVVya28&usp=sharing) and download all archives 
- create wine cache folders for installing dependencies `mkdir ~/.cache/winetricks`, `mkdir ~/.cache/winetricks/gdiplus`, `mkdir ~/.cache/winetricks/ie6`, `mkdir ~/.cache/winetricks/msxml3`
- unzip archive by `unzip photoshop-req-dll-wine.zip`
- `cp NDP1.0sp2-KB830348-X86-Enu.exe ~/.cache/winetricks/gdiplus` - move patch to cache
- `cp msie60.exe ~/.cache/winetricks/ie6` - move IE to cache
- `cp msxml3.msi ~/.cache/winetricks/msxml3` - move msxml to cache
- `cp odbc32.dll ~/.wine/drive_c/windows/system32/` - move odbc to /windows/system32
- `cp odbcint.dll ~/.wine/drive_c/windows/system32/` - move odbcint to /windows/system32
- `cp atmlib.dll ~/.wine/drive_c/windows/system32/` - move atmlib to /windows/system32
- install Adobe Photoshop CS6
