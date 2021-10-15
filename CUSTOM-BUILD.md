# Building Audacity

## Prerequisites

* **python3** >= 3.5
* **conan** >= 1.32.0
* **cmake** >= 3.16
* A working C++ 17 compiler

### Linux

We use GCC 9, but any C++17 compliant compiler should work.

On Debian or Ubuntu, you can install everything required using the following commands:

```
$ sudo apt-get update
$ sudo apt-get install -y build-essential cmake git python3-pip
$ sudo pip3 install conan
$ sudo apt-get install libgtk2.0-dev libasound2-dev libavformat-dev libjack-jackd2-dev uuid-dev
```

## Linux & Other OS (my custom changes to build process)

1. Clone Audacity from the Audacity GitHub project.

    ```
    $ git clone git@github.com:ginobean/audacity.git
    $ cd audacity
    $ git checkout custom-release-3.0.5   # my 'custom' branch.

    ```

2. Configure Audacity using CMake:
   ```
   $ mkdir build && cd build

   # for RELEASE VERSION:
   $ cmake -G "Unix Makefiles" -Daudacity_use_ffmpeg=loaded -DCMAKE_BUILD_TYPE=Release  -DAUDACITY_BUILD_LEVEL=2 ..

   # for DEBUG VERSION:
   $ cmake -G "Unix Makefiles" -Daudacity_use_ffmpeg=loaded ..
   ```
   By default, Debug build will be configured. To change that, pass `-DCMAKE_BUILD_TYPE=Release` to CMake.

3. Build Audacity:
   ```
   $ make -j4  # make using 4 parallel threads.
   ```

4. Testing the build:
   Adding a "Portable Settings" folder allows Audacity to ignore the settings of any existing Audacity installation.
   ```
   $ cd bin/Debug
   $ mkdir "Portable Settings"
   $ ./audacity
   ```

5. Installing Audacity
   ```
   $ cd <build directory>

   # if you, as a normal user, have write access to directory /usr/local/
   # you can simply install 'audacity' as a normal user.
   $ make install    # install as a normal user

   # otherwise,
   $ sudo make install   # install via sudo.

   ```

## Building on Mac OS

1. Clone Audacity from the Audacity GitHub project.

    ```
    $ git clone git@github.com:ginobean/audacity.git
    $ cd audacity
    $ git checkout custom-release-3.0.5   # my 'custom' branch.
    ```

2. Configure Audacity using CMake:
   ```
   $ mkdir release-build && cd release-build
   $ # Unfortunately, the debug version of wxWidgets seems to have some
   $ # assertion failures going on, which makes the resulting Audacity app
   $ # unusable. The workaround is simply to generate the makefiles (via cmake)
   $ # for the release version, as specified here:
   $ cmake -GXcode -T buildsystem=1 -DCMAKE_BUILD_TYPE=Release -DCMAKE_CONFIGURATION_TYPES=Release  -DAUDACITY_BUILD_LEVEL=2 ..
   ```

3. Open Audacity XCode project:
   ```
   $ open Audacity.xcodeproj
   ```
   and build Audacity using the IDE.

Steps 1 and 2 are only required for first-time builds.




# EOF
