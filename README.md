## PeLib

This is the updated PE file manipulation library, taken from [RetDec](https://github.com/avast/retdec)

The [original](http://www.pelib.com/index.php) project by Sebastian Porst was further modified by Avast Software to:
* Modify directory structure, i.e. split sources and headers.
* Fix bugs.
* Handle corrupted and exotic PE files.
* Parse additional structures:
  * COFF symbol table.
  * Delay import directory.
  * Rich header.
  * Security directory.

## Use

A single target named `pelib` is exposed. It can be used as follows:
```cmake
target_link_libraries(project-that-needs-pelib pelib)
```

## Requirements

* A compiler supporting C++17
  * On Windows, only Microsoft Visual C++ is supported (Visual Studio 2019 or older).
* CMake (version >= 3.6)

## Build and Installation

* Clone the repository or download the sources into a directory named `pelib`.
  * `git clone https://github.com/iArtorias/pelib-updated.git`
* Linux:
  * `cd pelib-updated`
  * `mkdir build && cd build`
  * `cmake ..`
  * `make`
* Windows:
  * Open a command prompt (e.g. `cmd.exe`)
  * `cd pelib-updated`
  * `mkdir build && cd build`
  * `cmake .. -G<generator>`
  * `cmake --build . --config Release -- -m`
  * Alternatively, you can open `pelib.sln` generated by `cmake` in Visual Studio IDE.

You must pass the following parameters to `cmake`:
* (Windows only) `-G<generator>` is `-G"Visual Studio 16 2019" -A Win32` for 32-bit build using Visual Studio 2019, or `-G"Visual Studio 16 2019" -A x64` for 64-bit build using Visual Studio 2019. Older versions of Visual Studio may be used.

You can pass additional parameters to `cmake`:
* `-DCMAKE_BUILD_TYPE=Debug` to build with debugging information, which is useful during development. By default, the project is built in the `Release` mode. This has no effect on Windows, but the same thing can be achieved by running `cmake --build .` with the `--config Debug` parameter.

## License

The original PeLib modules:
* Copyright (c) 2004 - 2005 Sebastian Porst (webmaster@the-interweb.com), licensed under the zlib/libpng License. See the [`ZLIB_LICENSE`] file for more details.

Modules added by Avast Software:
* Copyright (c) 2017 - 2020 Avast Software, licensed under the MIT license. See the [`MIT_LICENSE`] file for more details.
