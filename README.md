# tlsh-wheel
You want to build a wheel package for the tlsh Python extension? This is what you've been looking for.

This repo is a slightly modified version of the original tlsh py_ext setup.py with a submodule pointing to the original tlsh repo and a wrapper which automatically calls the build script for the required tlsh C module in one go. The reason for this is to have a convinent way to build the tlsh module for Python which you can use via `import tlsh`. Sadly, I had to do this because the `tlsh` package on PyPi is non-functional right now.

## Requirements
* Linux
* gcc, build-essential (or the equivalent for your distro/OS) & CMake
* `wheel` for Python installed (e.g. via `pip install wheel`)

## How to build the wheel package
If the requirements are satisfied, just clone the repo, go into the directory and run:

`pip3 wheel -w dist --verbose .`

This creates a directory called `dist/` with a wheel package in it, which can be installed via pip. That's it, you should be good to go.

## Other operating systems
This script *might* work under macOS, BSD and other UNIX operating systems, as long as the requirements are set. I haven't really tested it and after all, it just calls the `build.sh` from tlsh and afterwards run the same setup.py code from the py_ext/ directory, just with adjusted paths.

This script will not work under Windows, as I haven't found an easy way to build the tlsh C module (the .dll) because the project files in the original repo only made for Visual Studio 2005 and 2008, which require you to install the whole suite just to have the build tools for them in it. 

Now, maybe I missed something here, but if you have found a way to *easily* (e.g. just call `msbuild` and get a successfully built module) build the module for Windows via `msbuild` or something similar, please provide a PR and I will intergrate your changes with much appreciation.

## Publishing on PyPi?
As I don't want to push low-quality packages such as the one online right now, I only want to do this if we also have Windows support in it. But if you're up to, feel free to do it. Just please make a package which actually works :/