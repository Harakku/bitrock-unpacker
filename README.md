# bitrock-unpacker
Extracts contents from BitRock installers.

Usage: `bitrock-unpacker.exe INSTALLER.EXE OUTPUT_DIR`

## Download

Windows binaries are available at the releases section.

## Build

Instructions from https://stackoverflow.com/a/1383674

Get some tools.

* base-tcl8.5-thread-win32-x86_64.exe or base-tcl8.5-thread-win32-ix86.exe -- https://www.activestate.com/products/tcl/downloads/
* sdx.kit -- https://web.archive.org/web/20091018121941if_/http://www.equi4.com:80/pub/sk/sdx.kit
* tclkitsh-win32.upx.exe -- https://web.archive.org/web/20161114080543if_/http://equi4.com/pub/tk/8.5.2/tclkitsh-win32.upx.exe

Your build directory should look like this. The script has been renamed to main.tcl.
```
$ tree .
.
├── base-tcl8.5-thread-win32-x86_64.exe
├── bitrock-unpack.vfs
│   └── main.tcl
└── sdx.kit
```

Run this line and append ".exe" to the output file and you're done.
```
.\tclkitsh-win32.upx.exe sdx.kit wrap bitrock-unpack -runtime .\base-tcl8.5-thread-win32-x86_64.exe
```

For more instructions, see <https://stackoverflow.com/a/1383674>.

## Modifications
A couple parts have been commented out. For example, the line `file attributes $destDir/$fileName -permissions $mode` would throw the following error.
```
bad option "-permissions": must be -archive, -hidden, -longname, -readonly, -shortname, or -system
```
