<div align="center">
<h1>MRPODS <img src="https://raw.githubusercontent.com/sheafdynamics/mrpods/main/logo/logox32.png" width="32" height="32" alt="MRPODS Logo">
</h1>

<p>Machine-Readable Printed Optical Data Sheets</p>
</div>

---
Back up digital files to paper.
Rewrite and continuation of Oleh Yuschuk's [PaperBack](https://ollydbg.de/Paperbak/) in modern C++.

Showcase
-------------
<img src="https://raw.githubusercontent.com/sheafdynamics/mrpods/main/showcase/screenshot-1.png" width="500" alt="Screenshot">
<img src="https://raw.githubusercontent.com/sheafdynamics/mrpods/main/showcase/mrpods_decoding.gif" width="500" alt="Screenshot">
<img src="https://raw.githubusercontent.com/sheafdynamics/mrpods/main/showcase/mrpods_sheet.gif" width="500" alt="Screenshot">

Improvements Over Original PaperBack v1.10
-------------
* Due to how the original was written and how much Windows has changed over time, PaperBack v1.10 has an issue breaking out of the main WinMain loop.
* New faster 64-bit version and faster 32-bit version over the original Borland 32-bit only version.
* Even without performance optimizations, MRPODS is about 30% faster decoding bitmaps.
* Ease of build and compile with Visual Studio 2022.

Build Status
-------------
|       | x86  | x64  |
|-------|------|------|
| Debug | Ready     | Builds with scanner disabled     |
| Release | Ready | Builds with scanner disabled    |

Legacy Compatibility
-------------
| Feature               | MRPODS          | PaperBack v1.10           |
|-----------------------|---------------------|--------------------|
| Encode/Decode Data   | :white_check_mark:  | :white_check_mark: |
| Encrypt/Decrypt Data*   | :x:  | :white_check_mark: |

*Built-in AES-192 has been deprecated. If you need to decode legacy AES-192 data, please use PaperBack v1.10. MRPODS cannot physically decrypt PaperBack v1.10 AES data. If MRPODS identifies legacy PaperBack v1.x AES-192 data in the buffer, a message stating AES has been deprecated will be shown, and nothing further can be done to actually decode the data.

The AES functionality has been removed from MRPODS to simplify the codebase and address concerns related to custom cryptographic implementations. Consequently, Michael Mohr's contributions related to AES have been omitted from the current codebase, and his name has been removed from the copyright disclaimer to prevent any potential confusion.

Memory Design and Visual Studio mrpods.vcxproj
-------------
The software has been transitioned from legacy Borland C++ code to function reliably on modern systems without memory issues. While the design and logic flow have been preserved, users are advised to closely adhere to the compiler options specified for each build target. These settings have been validated for decoding documents created with the original PaperBack v1.10 and should remain unchanged without subsequent individual testing. Additionally, compilation optimizations are disabled to maintain stability without further code modifications.

TODO:
-------------
* Add a scanning bridge or switch to WIA to resolve TWAIN x86 dependency in x64. 

Project Goals
-------------
The goal of this project is to make the PaperBack project compatible with Visual Studio and modern C++ standards so that it may be compiled without the Borland compiler. This will allow for easier development of additional features such as native x64 support, improved UI, and more.

Compilation
-------------
1. Clone or download repository zip.
2. Install Visual Studio 2022 (Community Edition without logging in is fine)
3. Install the following Visual Studio components: Desktop development with C++, C++ MFC for latest v143 build tools (x86 & x64), C++ Clang tools for Windows (16.0.5 - x64/x86)
4. Open mrpods.sln solution
5. Build Release x86.

Changelog
---------
Version 1.20 - First stable release in x86. Fixed two memory issues (one due to rewrite, another from original code), properly removed AES functionality, preliminary support for x64 version.

Version 1.10 - Initial release. Based off PaperBack v1.10. AES functionality is commented out at the moment, and there is no graceful handling of existing AES documents from PaperBack.

Similar Tools (Not Recommended)
-------------
The following tools are either failed attempts to rewrite PaperBack or do not contain all of the features and functionality that the original software provides - a rough 17 years.
* https://github.com/intra2net/paperbackup
* https://github.com/za3k/qr-backup
* https://github.com/piql/boxing
* https://github.com/jabcode/jabcode
* https://github.com/colindean/optar
* https://www.jabberwocky.com/software/paperkey/
* https://github.com/makocodeproject/makocode
* https://github.com/avarner9/paperbak
* https://github.com/colorsafe/colorsafe/issues/17
* https://github.com/fdobrovolny/python-paperbak

Bzip2
-------------
Huge thank you to Phil Ross for his Visual Studio libbz2.dll Build found here: https://github.com/philr/bzip2-windows 

https://github.com/philr/bzip2-windows/releases/tag/v1.0.8.0

Windows binaries (32-bit and 64-bit) for bzip2 version 1.0.8.

Source code for bzip2 can be obtained from https://www.sourceware.org/pub/bzip2/bzip2-1.0.8.tar.gz.

All binaries depend on the Visual Studio 2015 C Runtime Library (vcruntime140.dll). This can be installed using the Visual C++ Redistributable Packages for Visual Studio 2015, 2017 and 2019 installer. See Microsoft's Latest Supported Visual C++ Downloads page for download links.

Editing Resource.rc and Icons
-------------
OPTIONS.RC and Resource.rc are legacy Borland files so one way you can edit the program icon is by right clicking Resource.rc in the solution explorer > Open with > C++ Source Code Editor

Edit the icon as needed, if you are building 32-bit release, use logox32.ico

If you are building 64-bit release, use logox64.ico

// OS taskbar icon (HIDPI)

IDI_ICON1               ICON                    "logo\\logox64.ico"

// Title bar icon (tiny)

ICON_MAIN               ICON                    "logo\\logox64.ico"
Logos converted from .png to .ico with https://redketchup.io/

Copyright
-------------
MRPODS  
built off PaperBack v1.10  

Copyright © 2024 Ray Doll (rewrite)  
Copyright © 2007 Oleh Yuschuk (creator)  
  
Reed-Solomon ECC:  
Copyright © 2002 Phil Karn (GPL)  
  
Bzip2 data compression  
Copyright © 1996-2010 Julian R. Seward (see sources)  
  
----- THIS SOFTWARE IS FREE -----  
Released under GNU Public License (GPL 3+)  
Full sources available  
at: https://github.com/sheafdynamics/mrpods 