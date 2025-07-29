- [Audio](#audio)
  - [No audio](#no-audio)
  - [Audio only](#audio-only)
  - [Source](#source)
    - [Duplication](#duplication)
  - [Codec](#codec)
  - [Encoder](#encoder)
  - [Bit rate](#bit-rate)
  - [Buffering](#buffering)
- [Build scrcpy](#build-scrcpy)
  - [Branches](#branches)
  - [Requirements](#requirements)
  - [System-specific steps](#system-specific-steps)
    - [Linux](#linux)
      - [Debian/Ubuntu](#debianubuntu)
      - [Fedora](#fedora)
    - [Windows](#windows)
      - [Cross-compile from Linux](#cross-compile-from-linux)
      - [In MSYS2](#in-msys2)
    - [Mac OS](#mac-os)
    - [Docker](#docker)
  - [Common steps](#common-steps)
    - [Build](#build)
      - [Option 1: Build everything from sources](#option-1-build-everything-from-sources)
      - [Option 2: Use prebuilt server](#option-2-use-prebuilt-server)
    - [Run without installing:](#run-without-installing)
    - [Install](#install)
    - [Uninstall](#uninstall)
- [Camera](#camera)
  - [List](#list)
  - [Selection](#selection)
    - [Size selection](#size-selection)
  - [Rotation](#rotation)
  - [Frame rate](#frame-rate)
  - [High speed capture](#high-speed-capture)
  - [Brace expansion tip](#brace-expansion-tip)
  - [Webcam](#webcam)
- [Connection](#connection)
  - [Selection](#selection-1)
  - [TCP/IP (wireless)](#tcpip-wireless)
    - [Automatic](#automatic)
    - [Manual](#manual)
  - [Autostart](#autostart)
- [Control](#control)
  - [Read-only](#read-only)
  - [Keyboard and mouse](#keyboard-and-mouse)
  - [Control only](#control-only)
  - [Copy-paste](#copy-paste)
  - [Pinch-to-zoom, rotate and tilt simulation](#pinch-to-zoom-rotate-and-tilt-simulation)
  - [File drop](#file-drop)
    - [Install APK](#install-apk)
    - [Push file to device](#push-file-to-device)
- [scrcpy for developers](#scrcpy-for-developers)
  - [Overview](#overview)
  - [Server](#server)
    - [Privileges](#privileges)
    - [Hidden methods](#hidden-methods)
    - [Execution](#execution)
    - [Components](#components)
    - [Screen video encoding](#screen-video-encoding)
    - [Audio encoding](#audio-encoding)
    - [Input events injection](#input-events-injection)
  - [Client](#client)
    - [Initialization](#initialization)
    - [Video and audio streams](#video-and-audio-streams)
    - [Controller](#controller)
  - [Protocol](#protocol)
    - [Connection](#connection-1)
    - [Video and audio](#video-and-audio)
    - [Controls](#controls)
  - [Standalone server](#standalone-server)
  - [Hack](#hack)
    - [Debug the server](#debug-the-server)
- [Device](#device)
  - [Stay awake](#stay-awake)
  - [Screen off timeout](#screen-off-timeout)
  - [Turn screen off](#turn-screen-off)
  - [Show touches](#show-touches)
  - [Power off on close](#power-off-on-close)
  - [Power on on start](#power-on-on-start)
  - [Start Android app](#start-android-app)
- [Gamepad](#gamepad)
  - [Physical gamepad simulation](#physical-gamepad-simulation)
    - [UHID](#uhid)
    - [AOA](#aoa)
- [Keyboard](#keyboard)
  - [SDK keyboard](#sdk-keyboard)
    - [Text injection preference](#text-injection-preference)
    - [Key repeat](#key-repeat)
  - [Physical keyboard simulation](#physical-keyboard-simulation)
    - [UHID](#uhid-1)
    - [AOA](#aoa-1)
- [On Linux](#on-linux)
  - [Install](#install-1)
    - [From the official release](#from-the-official-release)
    - [From your package manager](#from-your-package-manager)
    - [From an install script](#from-an-install-script)
  - [Run](#run)
- [On macOS](#on-macos)
  - [Install](#install-2)
    - [From the official release](#from-the-official-release-1)
    - [From a package manager](#from-a-package-manager)
  - [Run](#run-1)
- [Mouse](#mouse)
  - [SDK mouse](#sdk-mouse)
    - [Mouse hover](#mouse-hover)
  - [Physical mouse simulation](#physical-mouse-simulation)
    - [UHID](#uhid-2)
    - [AOA](#aoa-2)
  - [Mouse bindings](#mouse-bindings)
- [OTG](#otg)
  - [OTG issues on Windows](#otg-issues-on-windows)
  - [Control only](#control-only-1)
- [Recording](#recording)
  - [Format](#format)
  - [Rotation](#rotation-1)
  - [No playback](#no-playback)
  - [Time limit](#time-limit)
- [Shortcuts](#shortcuts)
- [Tunnels](#tunnels)
  - [Remote ADB server](#remote-adb-server)
  - [SSH tunnel](#ssh-tunnel)
- [Video4Linux](#video4linux)
  - [Buffering](#buffering-1)
- [Video](#video)
  - [Source](#source-1)
  - [Size](#size)
  - [Bit rate](#bit-rate-1)
  - [Frame rate](#frame-rate-1)
  - [Codec](#codec-1)
  - [Encoder](#encoder-1)
  - [Orientation](#orientation)
  - [Angle](#angle)
  - [Crop](#crop)
  - [Display](#display)
  - [Buffering](#buffering-2)
  - [No playback](#no-playback-1)
  - [No video](#no-video)
  - [Video4Linux](#video4linux-1)
- [Virtual display](#virtual-display)
  - [New display](#new-display)
  - [Start app](#start-app)
  - [System decorations](#system-decorations)
  - [Destroy on close](#destroy-on-close)
  - [Display IME policy](#display-ime-policy)
- [Window](#window)
  - [Disable window](#disable-window)
  - [Title](#title)
  - [Position and size](#position-and-size)
  - [Borderless](#borderless)
  - [Always on top](#always-on-top)
  - [Fullscreen](#fullscreen)
  - [Disable screensaver](#disable-screensaver)
- [On Windows](#on-windows)
  - [Install](#install-3)
    - [From the official release](#from-the-official-release-2)
    - [From a package manager](#from-a-package-manager-1)
  - [Run](#run-2)

# Audio

Audio forwarding is supported for devices with Android 11 or higher, and it is
enabled by default:

 - For **Android 12 or newer**, it works out-of-the-box.
 - For **Android 11**, you'll need to ensure that the device screen is unlocked
   when starting scrcpy. A fake popup will briefly appear to make the system
   think that the shell app is in the foreground. Without this, audio capture
   will fail.
 - For **Android 10 or earlier**, audio cannot be captured and is automatically
   disabled.

If audio capture fails, then mirroring continues with video only (since audio is
enabled by default, it is not acceptable to make scrcpy fail if it is not
available), unless `--require-audio` is set.


## No audio

To disable audio:

```
scrcpy --no-audio
```

To disable only the audio playback, see [no playback](video.md#no-playback).

## Audio only

To play audio only, disable video and control:

```bash
scrcpy --no-video --no-control
```

To play audio without a window:

```bash
# --no-video and --no-control are implied by --no-window
scrcpy --no-window
# interrupt with Ctrl+C
```

Without video, the audio latency is typically not critical, so it might be
interesting to add [buffering](#buffering) to minimize glitches:

```
scrcpy --no-video --audio-buffer=200
```

## Source

By default, the device audio output is forwarded.

It is possible to capture the device microphone instead:

```
scrcpy --audio-source=mic
```

For example, to use the device as a dictaphone and record a capture directly on
the computer:

```
scrcpy --audio-source=mic --no-video --no-playback --record=file.opus
```

Many sources are available:

 - `output` (default): forwards the whole audio output, and disables playback on the device (mapped to [`REMOTE_SUBMIX`](https://developer.android.com/reference/android/media/MediaRecorder.AudioSource#REMOTE_SUBMIX)).
 - `playback`: captures the audio playback (Android apps can opt-out, so the whole output is not necessarily captured).
 - `mic`: captures the microphone (mapped to [`MIC`](https://developer.android.com/reference/android/media/MediaRecorder.AudioSource#MIC)).
 - `mic-unprocessed`: captures the microphone unprocessed (raw) sound (mapped to [`UNPROCESSED`](https://developer.android.com/reference/android/media/MediaRecorder.AudioSource#UNPROCESSED)).
 - `mic-camcorder`: captures the microphone tuned for video recording, with the same orientation as the camera if available (mapped to [`CAMCORDER`](https://developer.android.com/reference/android/media/MediaRecorder.AudioSource#CAMCORDER)).
 - `mic-voice-recognition`: captures the microphone tuned for voice recognition (mapped to [`VOICE_RECOGNITION`](https://developer.android.com/reference/android/media/MediaRecorder.AudioSource#VOICE_RECOGNITION)).
 - `mic-voice-communication`: captures the microphone tuned for voice communications (it will for instance take advantage of echo cancellation or automatic gain control if available) (mapped to [`VOICE_COMMUNICATION`](https://developer.android.com/reference/android/media/MediaRecorder.AudioSource#VOICE_COMMUNICATION)).
 - `voice-call`: captures voice call (mapped to [`VOICE_CALL`](https://developer.android.com/reference/android/media/MediaRecorder.AudioSource#VOICE_CALL)).
 - `voice-call-uplink`: captures voice call uplink only (mapped to [`VOICE_UPLINK`](https://developer.android.com/reference/android/media/MediaRecorder.AudioSource#VOICE_UPLINK)).
 - `voice-call-downlink`: captures voice call downlink only (mapped to [`VOICE_DOWNLINK`](https://developer.android.com/reference/android/media/MediaRecorder.AudioSource#VOICE_DOWNLINK)).
 - `voice-performance`: captures audio meant to be processed for live performance (karaoke), includes both the microphone and the device playback (mapped to [`VOICE_PERFORMANCE`](https://developer.android.com/reference/android/media/MediaRecorder.AudioSource#VOICE_PERFORMANCE)).

### Duplication

An alternative device audio capture method is also available (only for Android
13 and above):

```
scrcpy --audio-source=playback
```

This audio source supports keeping the audio playing on the device while
mirroring, with `--audio-dup`:

```bash
scrcpy --audio-source=playback --audio-dup
# or simply:
scrcpy --audio-dup  # --audio-source=playback is implied
```

However, it requires Android 13, and Android apps can opt-out (so they are not
captured).


See [#4380](https://github.com/Genymobile/scrcpy/issues/4380).


## Codec

The audio codec can be selected. The possible values are `opus` (default),
`aac`, `flac` and `raw` (uncompressed PCM 16-bit LE):

```bash
scrcpy --audio-codec=opus  # default
scrcpy --audio-codec=aac
scrcpy --audio-codec=flac
scrcpy --audio-codec=raw
```

In particular, if you get the following error:

> Failed to initialize audio/opus, error 0xfffffffe

then your device has no Opus encoder: try `scrcpy --audio-codec=aac`.

For advanced usage, to pass arbitrary parameters to the [`MediaFormat`],
check `--audio-codec-options` in the manpage or in `scrcpy --help`.

For example, to change the [FLAC compression level]:

```bash
scrcpy --audio-codec=flac --audio-codec-options=flac-compression-level=8
```

[`MediaFormat`]: https://developer.android.com/reference/android/media/MediaFormat
[FLAC compression level]: https://developer.android.com/reference/android/media/MediaFormat#KEY_FLAC_COMPRESSION_LEVEL


## Encoder

Several encoders may be available on the device. They can be listed by:

```bash
scrcpy --list-encoders
```

To select a specific encoder:

```bash
scrcpy --audio-codec=opus --audio-encoder='c2.android.opus.encoder'
```


## Bit rate

The default audio bit rate is 128Kbps. To change it:

```bash
scrcpy --audio-bit-rate=64K
scrcpy --audio-bit-rate=64000  # equivalent
```

_This parameter does not apply to RAW audio codec (`--audio-codec=raw`)._


## Buffering

Audio buffering is unavoidable. It must be kept small enough so that the latency
is acceptable, but large enough to minimize buffer underrun (causing audio
glitches).

The default buffer size is set to 50ms. It can be adjusted:

```bash
scrcpy --audio-buffer=40   # smaller than default
scrcpy --audio-buffer=100  # higher than default
```

Note that this option changes the _target_ buffering. It is possible that this
target buffering might not be reached (on frequent buffer underflow typically).

If you don't interact with the device (to watch a video for example), a higher
latency (for both [video](video.md#buffering) and audio) might be preferable to
avoid glitches and smooth the playback:

```
scrcpy --video-buffer=200 --audio-buffer=200
```

It is also possible to configure another audio buffer (the audio output buffer),
by default set to 5ms. Don't change it, unless you get some [robotic and glitchy
sound][#3793]:

```bash
# Only if absolutely necessary
scrcpy --audio-output-buffer=10
```

[#3793]: https://github.com/Genymobile/scrcpy/issues/3793

# Build scrcpy

Here are the instructions to build _scrcpy_ (client and server).

If you just want to build and install the latest release, follow the simplified
process described in [doc/linux.md](linux.md).

## Branches

There are two main branches:
 - `master`: contains the latest release. It is the home page of the project on
   GitHub.
 - `dev`: the current development branch. Every commit present in `dev` will be
   in the next release.

If you want to contribute code, please base your commits on the latest `dev`
branch.


## Requirements

You need [adb]. It is available in the [Android SDK platform
tools][platform-tools], or packaged in your distribution (`adb`).

On Windows, download the [platform-tools][platform-tools-windows] and extract
the following files to a directory accessible from your `PATH`:
 - `adb.exe`
 - `AdbWinApi.dll`
 - `AdbWinUsbApi.dll`

It is also available in scrcpy releases.

The client requires [FFmpeg] and [LibSDL2]. Just follow the instructions.

[adb]: https://developer.android.com/studio/command-line/adb.html
[platform-tools]: https://developer.android.com/studio/releases/platform-tools.html
[platform-tools-windows]: https://dl.google.com/android/repository/platform-tools-latest-windows.zip
[ffmpeg]: https://en.wikipedia.org/wiki/FFmpeg
[LibSDL2]: https://en.wikipedia.org/wiki/Simple_DirectMedia_Layer



## System-specific steps

### Linux

Install the required packages from your package manager.

#### Debian/Ubuntu

```bash
# runtime dependencies
sudo apt install ffmpeg libsdl2-2.0-0 adb libusb-1.0-0

# client build dependencies
sudo apt install gcc git pkg-config meson ninja-build libsdl2-dev \
                 libavcodec-dev libavdevice-dev libavformat-dev libavutil-dev \
                 libswresample-dev libusb-1.0-0-dev

# server build dependencies
sudo apt install openjdk-17-jdk
```

On old versions (like Ubuntu 16.04), `meson` is too old. In that case, install
it from `pip3`:

```bash
sudo apt install python3-pip
pip3 install meson
```


#### Fedora

```bash
# enable RPM fusion free
sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm

# client build dependencies
sudo dnf install SDL2-devel ffms2-devel libusb1-devel libavdevice-free-devel meson gcc make

# server build dependencies
sudo dnf install java-devel
```



### Windows

#### Cross-compile from Linux

This is the preferred method (and the way the release is built).

From _Debian_, install _mingw_:

```bash
sudo apt install mingw-w64 mingw-w64-tools libz-mingw-w64-dev
```

You also need the JDK to build the server:

```bash
sudo apt install openjdk-17-jdk
```

Then generate the releases:

```bash
./release.sh
```

It will generate win32 and win64 releases into `dist/`.


#### In MSYS2

From Windows, you need [MSYS2] to build the project. From an MSYS2 terminal,
install the required packages:

[MSYS2]: http://www.msys2.org/

```bash
# runtime dependencies
pacman -S mingw-w64-x86_64-SDL2 \
          mingw-w64-x86_64-ffmpeg \
          mingw-w64-x86_64-libusb

# client build dependencies
pacman -S mingw-w64-x86_64-make \
          mingw-w64-x86_64-gcc \
          mingw-w64-x86_64-pkg-config \
          mingw-w64-x86_64-meson
```

For a 32 bits version, replace `x86_64` by `i686`:

```bash
# runtime dependencies
pacman -S mingw-w64-i686-SDL2 \
          mingw-w64-i686-ffmpeg \
          mingw-w64-i686-libusb

# client build dependencies
pacman -S mingw-w64-i686-make \
          mingw-w64-i686-gcc \
          mingw-w64-i686-pkg-config \
          mingw-w64-i686-meson
```

Java (>= 7) is not available in MSYS2, so if you plan to build the server,
install it manually and make it available from the `PATH`:

```bash
export PATH="$JAVA_HOME/bin:$PATH"
```

### Mac OS

Install the packages with [Homebrew]:

[Homebrew]: https://brew.sh/

```bash
# runtime dependencies
brew install sdl2 ffmpeg libusb

# client build dependencies
brew install pkg-config meson
```

Additionally, if you want to build the server, install Java 17 from Caskroom, and
make it available from the `PATH`:

```bash
brew tap homebrew/cask-versions
brew install adoptopenjdk/openjdk/adoptopenjdk17
export JAVA_HOME="$(/usr/libexec/java_home --version 1.17)"
export PATH="$JAVA_HOME/bin:$PATH"
```

### Docker

See [pierlon/scrcpy-docker](https://github.com/pierlon/scrcpy-docker).


## Common steps

**As a non-root user**, clone the project:

```bash
git clone https://github.com/Genymobile/scrcpy
cd scrcpy
```


### Build

You may want to build only the client: the server binary, which will be pushed
to the Android device, does not depend on your system and architecture. In that
case, use the [prebuilt server] (so you will not need Java or the Android SDK).

[prebuilt server]: #option-2-use-prebuilt-server


#### Option 1: Build everything from sources

Install the [Android SDK] (_Android Studio_), and set `ANDROID_SDK_ROOT` to its
directory. For example:

[Android SDK]: https://developer.android.com/studio/index.html

```bash
# Linux
export ANDROID_SDK_ROOT=~/Android/Sdk
# Mac
export ANDROID_SDK_ROOT=~/Library/Android/sdk
# Windows
set ANDROID_SDK_ROOT=%LOCALAPPDATA%\Android\sdk
```

Then, build:

```bash
meson setup x --buildtype=release --strip -Db_lto=true
ninja -Cx  # DO NOT RUN AS ROOT
```

_Note: `ninja` [must][ninja-user] be run as a non-root user (only `ninja
install` must be run as root)._

[ninja-user]: https://github.com/Genymobile/scrcpy/commit/4c49b27e9f6be02b8e63b508b60535426bd0291a


#### Option 2: Use prebuilt server

 - [`scrcpy-server-v3.3.1`][direct-scrcpy-server]  
   <sub>SHA-256: `a0f70b20aa4998fbf658c94118cd6c8dab6abbb0647a3bdab344d70bc1ebcbb8`</sub>

[direct-scrcpy-server]: https://github.com/Genymobile/scrcpy/releases/download/v3.3.1/scrcpy-server-v3.3.1

Download the prebuilt server somewhere, and specify its path during the Meson
configuration:

```bash
meson setup x --buildtype=release --strip -Db_lto=true \
    -Dprebuilt_server=/path/to/scrcpy-server
ninja -Cx  # DO NOT RUN AS ROOT
```

The server only works with a matching client version (this server works with the
`master` branch).


### Run without installing:

```bash
./run x [options]
```


### Install

After a successful build, you can install _scrcpy_ on the system:

```bash
sudo ninja -Cx install    # without sudo on Windows
```

This installs several files:

 - `/usr/local/bin/scrcpy` (main app)
 - `/usr/local/share/scrcpy/scrcpy-server` (server to push to the device)
 - `/usr/local/share/man/man1/scrcpy.1` (manpage)
 - `/usr/local/share/icons/hicolor/256x256/apps/icon.png` (app icon)
 - `/usr/local/share/zsh/site-functions/_scrcpy` (zsh completion)
 - `/usr/local/share/bash-completion/completions/scrcpy` (bash completion)

You can then run `scrcpy`.


### Uninstall

```bash
sudo ninja -Cx uninstall  # without sudo on Windows
```

# Camera

Camera mirroring is supported for devices with Android 12 or higher.

To capture the camera instead of the device screen:

```
scrcpy --video-source=camera
```

By default, it automatically switches [audio source](audio.md#source) to
microphone (as if `--audio-source=mic` were also passed).

```bash
scrcpy --video-source=display  # default is --audio-source=output
scrcpy --video-source=camera   # default is --audio-source=mic
scrcpy --video-source=display --audio-source=mic    # force display AND microphone
scrcpy --video-source=camera --audio-source=output  # force camera AND device audio output
```

Audio can be disabled:

```bash
# audio not captured at all
scrcpy --video-source=camera --no-audio
scrcpy --video-source=camera --no-audio --record=file.mp4

# audio captured and recorded, but not played
scrcpy --video-source=camera --no-audio-playback --record=file.mp4
```


## List

To list the cameras available (with their declared valid sizes and frame rates):

```
scrcpy --list-cameras
scrcpy --list-camera-sizes
```

_Note that the sizes and frame rates are declarative. They are not accurate on
all devices: some of them are declared but not supported, while some others are
not declared but supported._


## Selection

It is possible to pass an explicit camera id (as listed by `--list-cameras`):

```
scrcpy --video-source=camera --camera-id=0
```

Alternatively, the camera may be selected automatically:

```bash
scrcpy --video-source=camera                           # use the first camera
scrcpy --video-source=camera --camera-facing=front     # use the first front camera
scrcpy --video-source=camera --camera-facing=back      # use the first back camera
scrcpy --video-source=camera --camera-facing=external  # use the first external camera
```

If `--camera-id` is specified, then `--camera-facing` is forbidden (the id
already determines the camera):

```bash
scrcpy --video-source=camera --camera-id=0 --camera-facing=front  # error
```


### Size selection

It is possible to pass an explicit camera size:

```
scrcpy --video-source=camera --camera-size=1920x1080
```

The given size may be listed among the declared valid sizes
(`--list-camera-sizes`), but may also be anything else (some devices support
arbitrary sizes):

```
scrcpy --video-source=camera --camera-size=1840x444
```

Alternatively, a declared valid size (among the ones listed by
`list-camera-sizes`) may be selected automatically.

Two constraints are supported:
 - `-m`/`--max-size` (already used for display mirroring), for example `-m1920`;
 - `--camera-ar` to specify an aspect ratio (`<num>:<den>`, `<value>` or
   `sensor`).

Some examples:

```bash
scrcpy --video-source=camera                          # use the greatest width and the greatest associated height
scrcpy --video-source=camera -m1920                   # use the greatest width not above 1920 and the greatest associated height
scrcpy --video-source=camera --camera-ar=4:3          # use the greatest size with an aspect ratio of 4:3 (+/- 10%)
scrcpy --video-source=camera --camera-ar=1.6          # use the greatest size with an aspect ratio of 1.6 (+/- 10%)
scrcpy --video-source=camera --camera-ar=sensor       # use the greatest size with the aspect ratio of the camera sensor (+/- 10%)
scrcpy --video-source=camera -m1920 --camera-ar=16:9  # use the greatest width not above 1920 and the closest to 16:9 aspect ratio
```

If `--camera-size` is specified, then `-m`/`--max-size` and `--camera-ar` are
forbidden (the size is determined by the value given explicitly):

```bash
scrcpy --video-source=camera --camera-size=1920x1080 -m3000  # error
```


## Rotation

To rotate the captured video, use the [video orientation](video.md#orientation)
option:

```
scrcpy --video-source=camera --camera-size=1920x1080 --orientation=90
```


## Frame rate

By default, camera is captured at Android's default frame rate (30 fps).

To configure a different frame rate:

```
scrcpy --video-source=camera --camera-fps=60
```


## High speed capture

The Android camera API also supports a [high speed capture mode][high speed].

This mode is restricted to specific resolutions and frame rates, listed by
`--list-camera-sizes`.

```
scrcpy --video-source=camera --camera-size=1920x1080 --camera-fps=240
```

[high speed]: https://developer.android.com/reference/android/hardware/camera2/CameraConstrainedHighSpeedCaptureSession


## Brace expansion tip

All camera options start with `--camera-`, so if your shell supports it, you can
benefit from [brace expansion] (for example, it is supported _bash_ and _zsh_):

```bash
scrcpy --video-source=camera --camera-{facing=back,ar=16:9,high-speed,fps=120}
```

This will be expanded as:

```bash
scrcpy --video-source=camera --camera-facing=back --camera-ar=16:9 --camera-high-speed --camera-fps=120
```

[brace expansion]: https://www.gnu.org/software/bash/manual/html_node/Brace-Expansion.html


## Webcam

Combined with the [V4L2](v4l2.md) feature on Linux, the Android device camera
may be used as a webcam on the computer.

# Connection

## Selection

If exactly one device is connected (i.e. listed by `adb devices`), then it is
automatically selected.

However, if there are multiple devices connected, you must specify the one to
use in one of 4 ways:
 - by its serial:
   ```bash
   scrcpy --serial=0123456789abcdef
   scrcpy -s 0123456789abcdef   # short version

   # the serial is the ip:port if connected over TCP/IP (same behavior as adb)
   scrcpy --serial=192.168.1.1:5555
   ```
 - the one connected over USB (if there is exactly one):
   ```bash
   scrcpy --select-usb
   scrcpy -d   # short version
   ```
 - the one connected over TCP/IP (if there is exactly one):
   ```bash
   scrcpy --select-tcpip
   scrcpy -e   # short version
   ```
 - a device already listening on TCP/IP (see [below](#tcpip-wireless)):
   ```bash
   scrcpy --tcpip=192.168.1.1:5555
   scrcpy --tcpip=192.168.1.1        # default port is 5555
   ```

The serial may also be provided via the environment variable `ANDROID_SERIAL`
(also used by `adb`):

```bash
# in bash
export ANDROID_SERIAL=0123456789abcdef
scrcpy
```

```cmd
:: in cmd
set ANDROID_SERIAL=0123456789abcdef
scrcpy
```

```powershell
# in PowerShell
$env:ANDROID_SERIAL = '0123456789abcdef'
scrcpy
```


## TCP/IP (wireless)

_Scrcpy_ uses `adb` to communicate with the device, and `adb` can [connect] to a
device over TCP/IP. The device must be connected on the same network as the
computer.

[connect]: https://developer.android.com/studio/command-line/adb.html#wireless


### Automatic

An option `--tcpip` allows to configure the connection automatically. There are
two variants.

If _adb_ TCP/IP mode is disabled on the device (or if you don't know the IP
address), connect the device over USB, then run:

```bash
scrcpy --tcpip   # without arguments
```

It will automatically find the device IP address and adb port, enable TCP/IP
mode if necessary, then connect to the device before starting.

If the device (accessible at 192.168.1.1 in this example) already listens on a
port (typically 5555) for incoming _adb_ connections, then run:

```bash
scrcpy --tcpip=192.168.1.1       # default port is 5555
scrcpy --tcpip=192.168.1.1:5555
```

Prefix the address with a '+' to force a reconnection:

```bash
scrcpy --tcpip=+192.168.1.1
```


### Manual

Alternatively, it is possible to enable the TCP/IP connection manually using
`adb`:

1. Plug the device into a USB port on your computer.
2. Connect the device to the same Wi-Fi network as your computer.
3. Get your device IP address, in Settings → About phone → Status, or by
   executing this command:

    ```bash
    adb shell ip route | awk '{print $9}'
    ```

4. Enable `adb` over TCP/IP on your device: `adb tcpip 5555`.
5. Unplug your device.
6. Connect to your device: `adb connect DEVICE_IP:5555` _(replace `DEVICE_IP`
with the device IP address you found)_.
7. Run `scrcpy` as usual.
8. Run `adb disconnect` once you're done.

Since Android 11, a [wireless debugging option][adb-wireless] allows you to
bypass having to physically connect your device to your computer.

[adb-wireless]: https://developer.android.com/studio/command-line/adb#wireless-android11-command-line


## Autostart

A small tool (by the scrcpy author) allows you to run arbitrary commands
whenever a new Android device is connected: [AutoAdb]. It can be used to start
scrcpy:

```bash
autoadb scrcpy -s '{}'
```

[AutoAdb]: https://github.com/rom1v/autoadb

# Control

## Read-only

To disable controls (everything which can interact with the device: input keys,
mouse events, drag&drop files):

```bash
scrcpy --no-control
scrcpy -n   # short version
```

## Keyboard and mouse

Read [keyboard](keyboard.md) and [mouse](mouse.md).


## Control only

To control the device without mirroring:

```bash
scrcpy --no-video --no-audio
```

By default, the mouse is disabled when video playback is turned off.

To control the device using a relative mouse, enable UHID mouse mode:

```bash
scrcpy --no-video --no-audio --mouse=uhid
scrcpy --no-video --no-audio -M  # short version
```

To also use a UHID keyboard, set it explicitly:

```bash
scrcpy --no-video --no-audio --mouse=uhid --keyboard=uhid
scrcpy --no-video --no-audio -MK  # short version
```

To use AOA instead (over USB only):

```bash
scrcpy --no-video --no-audio --keyboard=aoa --mouse=aoa
```


## Copy-paste

Any time the Android clipboard changes, it is automatically synchronized to the
computer clipboard.

Any <kbd>Ctrl</kbd> shortcut is forwarded to the device. In particular:
 - <kbd>Ctrl</kbd>+<kbd>c</kbd> typically copies
 - <kbd>Ctrl</kbd>+<kbd>x</kbd> typically cuts
 - <kbd>Ctrl</kbd>+<kbd>v</kbd> typically pastes (after computer-to-device
   clipboard synchronization)

This typically works as you expect.

The actual behavior depends on the active application though. For example,
_Termux_ sends SIGINT on <kbd>Ctrl</kbd>+<kbd>c</kbd> instead, and _K-9 Mail_
composes a new message.

To copy, cut and paste in such cases (but only supported on Android >= 7):
 - <kbd>Alt</kbd>+<kbd>c</kbd> injects `COPY`
 - <kbd>Alt</kbd>+<kbd>x</kbd> injects `CUT`
 - <kbd>Alt</kbd>+<kbd>v</kbd> injects `PASTE` (after computer-to-device
   clipboard synchronization)

In addition, <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>v</kbd> injects the computer
clipboard text as a sequence of key events. This is useful when the component
does not accept text pasting (for example in _Termux_), but it can break
non-ASCII content.

**WARNING:** Pasting the computer clipboard to the device (either via
<kbd>Ctrl</kbd>+<kbd>v</kbd> or <kbd>Alt</kbd>+<kbd>v</kbd>) copies the content
into the Android clipboard. As a consequence, any Android application could read
its content. You should avoid pasting sensitive content (like passwords) that
way.

Some Android devices do not behave as expected when setting the device clipboard
programmatically. An option `--legacy-paste` is provided to change the behavior
of <kbd>Ctrl</kbd>+<kbd>v</kbd> and <kbd>Alt</kbd>+<kbd>v</kbd> so that they
also inject the computer clipboard text as a sequence of key events (the same
way as <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>v</kbd>).

To disable automatic clipboard synchronization, use
`--no-clipboard-autosync`.


## Pinch-to-zoom, rotate and tilt simulation

To simulate "pinch-to-zoom": <kbd>Ctrl</kbd>+_click-and-move_.

More precisely, hold down <kbd>Ctrl</kbd> while pressing the left-click button.
Until the left-click button is released, all mouse movements scale and rotate
the content (if supported by the app) relative to the center of the screen.

https://github.com/Genymobile/scrcpy/assets/543275/26c4a920-9805-43f1-8d4c-608752d04767

To simulate a vertical tilt gesture: <kbd>Shift</kbd>+_click-and-move-up-or-down_.

https://github.com/Genymobile/scrcpy/assets/543275/1e252341-4a90-4b29-9d11-9153b324669f

Similarly, to simulate a horizontal tilt gesture:
<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+_click-and-move-left-or-right_.

Technically, _scrcpy_ generates additional touch events from a "virtual finger"
at a location inverted through the center of the screen. When pressing
<kbd>Ctrl</kbd> the _x_ and _y_ coordinates are inverted. Using <kbd>Shift</kbd>
only inverts _x_, whereas using <kbd>Ctrl</kbd>+<kbd>Shift</kbd> only inverts
_y_.

This only works for the default mouse mode (`--mouse=sdk`).


## File drop

### Install APK

To install an APK, drag & drop an APK file (ending with `.apk`) to the _scrcpy_
window.

There is no visual feedback, a log is printed to the console.


### Push file to device

To push a file to `/sdcard/Download/` on the device, drag & drop a (non-APK)
file to the _scrcpy_ window.

There is no visual feedback, a log is printed to the console.

The target directory can be changed on start:

```bash
scrcpy --push-target=/sdcard/Movies/
```

# scrcpy for developers

## Overview

This application is composed of two parts:
 - the server (`scrcpy-server`), to be executed on the device,
 - the client (the `scrcpy` binary), executed on the host computer.

The client is responsible to push the server to the device and start its
execution.

The client and the server establish communication using separate sockets for
video, audio and controls. Any of them may be disabled (but not all), so
there are 1, 2 or 3 socket(s).

The server initially sends the device name on the first socket (it is used for
the scrcpy window title), then each socket is used for its own purpose. All
reads and writes are performed from a dedicated thread for each socket, both on
the client and on the server.

If video is enabled, then the server sends a raw video stream (H.264 by default)
of the device screen, with some additional headers for each packet. The client
decodes the video frames, and displays them as soon as possible, without
buffering (unless `--video-buffer=delay` is specified) to minimize latency. The
client is not aware of the device rotation (which is handled by the server), it
just knows the dimensions of the video frames it receives.

Similarly, if audio is enabled, then the server sends a raw audio stream (OPUS
by default) of the device audio output (or the microphone if
`--audio-source=mic` is specified), with some additional headers for each
packet. The client decodes the stream, attempts to keep a minimal latency by
maintaining an average buffering. The [blog post][scrcpy2] of the scrcpy v2.0
release gives more details about the audio feature.

If control is enabled, then the client captures relevant keyboard and mouse
events, that it transmits to the server, which injects them to the device. This
is the only socket which is used in both direction: input events are sent from
the client to the device, and when the device clipboard changes, the new content
is sent from the device to the client to support seamless copy-paste.

[scrcpy2]: https://blog.rom1v.com/2023/03/scrcpy-2-0-with-audio/

Note that the client-server roles are expressed at the application level:

 - the server _serves_ video and audio streams, and handle requests from the
   client,
 - the client _controls_ the device through the server.

However, by default (when `--force-adb-forward` is not set), the roles are
reversed at the network level:

 - the client opens a server socket and listen on a port before starting the
   server,
 - the server connects to the client.

This role inversion guarantees that the connection will not fail due to race
conditions without polling.


## Server


### Privileges

Capturing the screen requires some privileges, which are granted to `shell`.

The server is a Java application (with a [`public static void main(String...
args)`][main] method), compiled against the Android framework, and executed as
`shell` on the Android device.

[main]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/server/src/main/java/com/genymobile/scrcpy/Server.java#L193

To run such a Java application, the classes must be [_dexed_][dex] (typically,
to `classes.dex`). If `my.package.MainClass` is the main class, compiled to
`classes.dex`, pushed to the device in `/data/local/tmp`, then it can be run
with:

    adb shell CLASSPATH=/data/local/tmp/classes.dex app_process / my.package.MainClass

_The path `/data/local/tmp` is a good candidate to push the server, since it's
readable and writable by `shell`, but not world-writable, so a malicious
application may not replace the server just before the client executes it._

Instead of a raw _dex_ file, `app_process` accepts a _jar_ containing
`classes.dex` (e.g. an [APK]). For simplicity, and to benefit from the gradle
build system, the server is built to an (unsigned) APK (renamed to
`scrcpy-server.jar`).

[dex]: https://en.wikipedia.org/wiki/Dalvik_(software)
[apk]: https://en.wikipedia.org/wiki/Android_application_package


### Hidden methods

Although compiled against the Android framework, [hidden] methods and classes are
not directly accessible (and they may differ from one Android version to
another).

They can be called using reflection though. The communication with hidden
components is provided by [_wrappers_ classes][wrappers] and [aidl].

[hidden]: https://stackoverflow.com/a/31908373/1987178
[wrappers]: https://github.com/Genymobile/scrcpy/tree/master/server/src/main/java/com/genymobile/scrcpy/wrappers
[aidl]: https://github.com/Genymobile/scrcpy/tree/master/server/src/main/aidl



### Execution

The server is started by the client basically by executing the following
commands:

```bash
adb push scrcpy-server /data/local/tmp/scrcpy-server.jar
adb forward tcp:27183 localabstract:scrcpy
adb shell CLASSPATH=/data/local/tmp/scrcpy-server.jar app_process / com.genymobile.scrcpy.Server 2.1
```

The first argument (`2.1` in the example) is the client scrcpy version. The
server fails if the client and the server do not have the exact same version.
The protocol between the client and the server may change from version to
version (see [protocol](#protocol) below), and there is no backward or forward
compatibility (there is no point to use different client and server versions).
This check allows to detect misconfiguration (running an older or newer server
by mistake).

It is followed by any number of arguments, in the form of `key=value` pairs.
Their order is irrelevant. The possible keys and associated value types can be
found in the [server][server-options] and [client][client-options] code.

[server-options]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/server/src/main/java/com/genymobile/scrcpy/Options.java#L181
[client-options]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/app/src/server.c#L226

For example, if we execute `scrcpy -m1920 --no-audio`, then the server
execution will look like this:

```bash
# scid is a random number to identify different clients running on the same device
adb shell CLASSPATH=/data/local/tmp/scrcpy-server.jar app_process / com.genymobile.scrcpy.Server 2.1 scid=12345678 log_level=info audio=false max_size=1920
```

### Components

When executed, its [`main()`][main] method is executed (on the "main" thread).
It parses the arguments, establishes the connection with the client and starts
the other "components":
 - the **video** streamer: it captures the video screen and send encoded video
   packets on the _video_ socket (from the _video_ thread).
 - the **audio** streamer: it uses several threads to capture raw packets,
   submits them to encoding and retrieve encoded packets, which it sends on the
   _audio_ socket.
 - the **controller**: it receives _control messages_ (typically input events)
   on the _control_ socket from one thread, and sends _device messages_ (e.g. to
   transmit the device clipboard content to the client) on the same _control
   socket_ from another thread. Thus, the _control_ socket is used in both
   directions (contrary to the _video_ and _audio_ sockets).


### Screen video encoding

The encoding is managed by [`ScreenEncoder`].

The video is encoded using the [`MediaCodec`] API. The codec encodes the content
of a `Surface` associated to the display, and writes the encoding packets to the
client (on the _video_ socket).

[`ScreenEncoder`]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/server/src/main/java/com/genymobile/scrcpy/ScreenEncoder.java
[`MediaCodec`]: https://developer.android.com/reference/android/media/MediaCodec.html

On device rotation (or folding), the encoding session is [reset] and restarted.

New frames are produced only when changes occur on the surface. This avoids to
send unnecessary frames, but by default there might be drawbacks:

 - it does not send any frame on start if the device screen does not change,
 - after fast motion changes, the last frame may have poor quality.

Both problems are [solved][repeat] by the flag
[`KEY_REPEAT_PREVIOUS_FRAME_AFTER`][repeat-flag].

[reset]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/server/src/main/java/com/genymobile/scrcpy/ScreenEncoder.java#L179
[rotation]: https://github.com/Genymobile/scrcpy/blob/ffe0417228fb78ab45b7ee4e202fc06fc8875bf3/server/src/main/java/com/genymobile/scrcpy/ScreenEncoder.java#L90
[repeat]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/server/src/main/java/com/genymobile/scrcpy/ScreenEncoder.java#L246-L247
[repeat-flag]: https://developer.android.com/reference/android/media/MediaFormat.html#KEY_REPEAT_PREVIOUS_FRAME_AFTER


### Audio encoding

Similarly, the audio is [captured] using an [`AudioRecord`], and [encoded] using
the [`MediaCodec`] asynchronous API.

More details are available on the [blog post][scrcpy2] introducing the audio feature.

[captured]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/server/src/main/java/com/genymobile/scrcpy/AudioCapture.java
[encoded]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/server/src/main/java/com/genymobile/scrcpy/AudioEncoder.java
[`AudioRecord`]: https://developer.android.com/reference/android/media/AudioRecord


### Input events injection

_Control messages_ are received from the client by the [`Controller`] (run in a
separate thread). There are several types of input events:
 - keycode (cf [`KeyEvent`]),
 - text (special characters may not be handled by keycodes directly),
 - mouse motion/click,
 - mouse scroll,
 - other commands (e.g. to switch the screen on or to copy the clipboard).

Some of them need to inject input events to the system. To do so, they use the
_hidden_ method [`InputManager.injectInputEvent()`] (exposed by the
[`InputManager` wrapper][inject-wrapper]).

[`Controller`]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/server/src/main/java/com/genymobile/scrcpy/Controller.java
[`KeyEvent`]: https://developer.android.com/reference/android/view/KeyEvent.html
[`MotionEvent`]: https://developer.android.com/reference/android/view/MotionEvent.html
[`InputManager.injectInputEvent()`]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/server/src/main/java/com/genymobile/scrcpy/wrappers/InputManager.java#L34
[inject-wrapper]: https://github.com/Genymobile/scrcpy/blob/ffe0417228fb78ab45b7ee4e202fc06fc8875bf3/server/src/main/java/com/genymobile/scrcpy/wrappers/InputManager.java#L27



## Client

The client relies on [SDL], which provides cross-platform API for UI, input
events, threading, etc.

The video and audio streams are decoded by [FFmpeg].

[SDL]: https://www.libsdl.org
[ffmpeg]: https://ffmpeg.org/


### Initialization

The client parses the command line arguments, then [runs one of two code
paths][run]:
 - scrcpy in "normal" mode ([`scrcpy.c`])
 - scrcpy in [OTG mode](otg.md) ([`scrcpy_otg.c`])

[run]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/app/src/main.c#L81-L82
[`scrcpy.c`]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/app/src/scrcpy.c#L292-L293
[`scrcpy_otg.c`]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/app/src/usb/scrcpy_otg.c#L51-L52

In the remaining of this document, we assume that the "normal" mode is used
(read the code for the OTG mode).

On startup, the client:
 - opens the _video_, _audio_ and _control_ sockets;
 - pushes and starts the server on the device;
 - initializes its components (demuxers, decoders, recorder…).


### Video and audio streams

Depending on the arguments passed to `scrcpy`, several components may be used.
Here is an overview of the video and audio components:

```
                                                 V4L2 sink
                                               /
                                       decoder
                                     /         \
        VIDEO -------------> demuxer             display
                                     \
                                       recorder
                                     /
        AUDIO -------------> demuxer
                                     \
                                       decoder --- audio player
```

The _demuxer_ is responsible to extract video and audio packets (read some
header, split the video stream into packets at correct boundaries, etc.).

The demuxed packets may be sent to a _decoder_ (one per stream, to produce
frames) and to a recorder (receiving both video and audio stream to record a
single file). The packets are encoded on the device (by `MediaCodec`), but when
recording, they are _muxed_ (asynchronously) into a container (MKV or MP4) on
the client side.

Video frames are sent to the screen/display to be rendered in the scrcpy window.
They may also be sent to a [V4L2 sink](v4l2.md).

Audio "frames" (an array of decoded samples) are sent to the audio player.


### Controller

The _controller_ is responsible to send _control messages_ to the device. It
runs in a separate thread, to avoid I/O on the main thread.

On SDL event, received on the main thread, the _input manager_ creates
appropriate _control messages_. It is responsible to convert SDL events to
Android events. It then pushes the _control messages_ to a queue hold by the
controller. On its own thread, the controller takes messages from the queue,
that it serializes and sends to the client.


## Protocol

The protocol between the client and the server must be considered _internal_: it
may (and will) change at any time for any reason. Everything may change (the
number of sockets, the order in which the sockets must be opened, the data
format on the wire…) from version to version. A client must always be run with a
matching server version.

This section documents the current protocol in scrcpy v2.1.

### Connection

Firstly, the client sets up an adb tunnel:

```bash
# By default, a reverse redirection: the computer listens, the device connects
adb reverse localabstract:scrcpy_<SCID> tcp:27183

# As a fallback (or if --force-adb forward is set), a forward redirection:
# the device listens, the computer connects
adb forward tcp:27183 localabstract:scrcpy_<SCID>
```

(`<SCID>` is a 31-bit random number, so that it does not fail when several
scrcpy instances start "at the same time" for the same device.)

Then, up to 3 sockets are opened, in that order:
 - a _video_ socket
 - an _audio_ socket
 - a _control_ socket

Each one may be disabled (respectively by `--no-video`, `--no-audio` and
`--no-control`, directly or indirectly). For example, if `--no-audio` is set,
then the _video_ socket is opened first, then the _control_ socket.

On the _first_ socket opened (whichever it is), if the tunnel is _forward_, then
a [dummy byte] is sent from the device to the client. This allows to detect a
connection error (the client connection does not fail as long as there is an adb
forward redirection, even if nothing is listening on the device side).

Still on this _first_ socket, the device sends some [metadata][device meta] to
the client (currently only the device name, used as the window title, but there
might be other fields in the future).

[dummy byte]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/server/src/main/java/com/genymobile/scrcpy/DesktopConnection.java#L93
[device meta]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/server/src/main/java/com/genymobile/scrcpy/DesktopConnection.java#L151

You can read the [client][client-connection] and [server][server-connection]
code for more details.

[client-connection]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/app/src/server.c#L465-L466
[server-connection]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/server/src/main/java/com/genymobile/scrcpy/DesktopConnection.java#L63

Then each socket is used for its intended purpose.

### Video and audio

On the _video_ and _audio_ sockets, the device first sends some [codec
metadata]:
 - On the _video_ socket, 12 bytes:
   - the codec id (`u32`) (H264, H265 or AV1)
   - the initial video width (`u32`)
   - the initial video height (`u32`)
 - On the _audio_ socket, 4 bytes:
   - the codec id (`u32`) (OPUS, AAC or RAW)

[codec metadata]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/server/src/main/java/com/genymobile/scrcpy/Streamer.java#L33-L51

Then each packet produced by `MediaCodec` is sent, prefixed by a 12-byte [frame
header]:
 - config packet flag (`u1`)
 - key frame flag (`u1`)
 - PTS (`u62`)
 - packet size (`u32`)

Here is a schema describing the frame header:

```
    [. . . . . . . .|. . . .]. . . . . . . . . . . . . . . ...
     <-------------> <-----> <-----------------------------...
           PTS        packet        raw packet
                       size
     <--------------------->
           frame header

The most significant bits of the PTS are used for packet flags:

     byte 7   byte 6   byte 5   byte 4   byte 3   byte 2   byte 1   byte 0
    CK...... ........ ........ ........ ........ ........ ........ ........
    ^^<------------------------------------------------------------------->
    ||                                PTS
    | `- key frame
     `-- config packet
```

[frame header]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/server/src/main/java/com/genymobile/scrcpy/Streamer.java#L83


### Controls

Controls messages are sent via a custom binary protocol.

The only documentation for this protocol is the set of unit tests on both sides:
 - `ControlMessage` (from client to device): [serialization](https://github.com/Genymobile/scrcpy/blob/master/app/tests/test_control_msg_serialize.c) | [deserialization](https://github.com/Genymobile/scrcpy/blob/master/server/src/test/java/com/genymobile/scrcpy/ControlMessageReaderTest.java)
 - `DeviceMessage` (from device to client) [serialization](https://github.com/Genymobile/scrcpy/blob/master/server/src/test/java/com/genymobile/scrcpy/DeviceMessageWriterTest.java) | [deserialization](https://github.com/Genymobile/scrcpy/blob/master/app/tests/test_device_msg_deserialize.c)


## Standalone server

Although the server is designed to work for the scrcpy client, it can be used
with any client which uses the same protocol.

For simplicity, some [server-specific options] have been added to produce raw
streams easily:
 - `send_device_meta=false`: disable the device metata (in practice, the device
   name) sent on the _first_ socket
 - `send_frame_meta=false`: disable the 12-byte header for each packet
 - `send_dummy_byte`: disable the dummy byte sent on forward connections
 - `send_codec_meta`: disable the codec information (and initial device size for
   video)
 - `raw_stream`: disable all the above

[server-specific options]: https://github.com/Genymobile/scrcpy/blob/a3cdf1a6b86ea22786e1f7d09b9c202feabc6949/server/src/main/java/com/genymobile/scrcpy/Options.java#L309-L329

Concretely, here is how to expose a raw H.264 stream on a TCP socket:

```bash
adb push scrcpy-server-v2.1 /data/local/tmp/scrcpy-server-manual.jar
adb forward tcp:1234 localabstract:scrcpy
adb shell CLASSPATH=/data/local/tmp/scrcpy-server-manual.jar \
    app_process / com.genymobile.scrcpy.Server 2.1 \
    tunnel_forward=true audio=false control=false cleanup=false \
    raw_stream=true max_size=1920
```

As soon as a client connects over TCP on port 1234, the device will start
streaming the video. For example, VLC can play the video (although you will
experience a very high latency, more details [here][vlc-0latency]):

```
vlc -Idummy --demux=h264 --network-caching=0 tcp://localhost:1234
```

[vlc-0latency]: https://code.videolan.org/rom1v/vlc/-/merge_requests/20


## Hack

For more details, go read the code!

If you find a bug, or have an awesome idea to implement, please discuss and
contribute ;-)


### Debug the server

The server is pushed to the device by the client on startup.

To debug it, enable the server debugger during configuration:

```bash
meson setup x -Dserver_debugger=true
# or, if x is already configured
meson configure x -Dserver_debugger=true
```

Then recompile, and run scrcpy.

For Android < 11, it will start a debugger on port 5005 on the device and wait:
Redirect that port to the computer:

```bash
adb forward tcp:5005 tcp:5005
```

For Android >= 11, first find the listening port:

```bash
adb jdwp
# press Ctrl+C to interrupt
```

Then redirect the resulting PID:

```bash
adb forward tcp:5005 jdwp:XXXX  # replace XXXX
```

In Android Studio, _Run_ > _Debug_ > _Edit configurations..._ On the left, click
on `+`, _Remote_, and fill the form:

 - Host: `localhost`
 - Port: `5005`

Then click on _Debug_.

# Device

Some command line arguments perform actions on the device itself while scrcpy is
running.

## Stay awake

To prevent the device from sleeping after a delay **when the device is plugged
in**:

```bash
scrcpy --stay-awake
scrcpy -w
```

The initial state is restored when _scrcpy_ is closed.

If the device is not plugged in (i.e. only connected over TCP/IP),
`--stay-awake` has no effect (this is the Android behavior).

This changes the value of [`stay_on_while_plugged_in`], setting which can be
changed manually:

[`stay_on_while_plugged_in`]: https://developer.android.com/reference/android/provider/Settings.Global#STAY_ON_WHILE_PLUGGED_IN


```bash
# get the current show_touches value
adb shell settings get global stay_on_while_plugged_in
# enable for AC/USB/wireless chargers
adb shell settings put global stay_on_while_plugged_in 7
# disable
adb shell settings put global stay_on_while_plugged_in 0
```


## Screen off timeout

The Android screen automatically turns off after some delay.

To change this delay while scrcpy is running:

```bash
scrcpy --screen-off-timeout=300  # 300 seconds (5 minutes)
```

The initial value is restored on exit.

It is possible to change this setting manually:

```bash
# get the current screen_off_timeout value
adb shell settings get system screen_off_timeout
# set a new value (in milliseconds)
adb shell settings put system screen_off_timeout 30000
```

Note that the Android value is in milliseconds, but the scrcpy command line
argument is in seconds.


## Turn screen off

It is possible to turn the device screen off while mirroring on start with a
command-line option:

```bash
scrcpy --turn-screen-off
scrcpy -S   # short version
```

Or by pressing <kbd>Alt</kbd>+<kbd>o</kbd> at any time (see
[shortcuts](shortcuts.md)).

To turn it back on, press <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>o</kbd>.

On Android, the `POWER` button always turns the screen on. For convenience, if
`POWER` is sent via _scrcpy_ (via right-click or <kbd>Alt</kbd>+<kbd>p</kbd>),
it will force to turn the screen off after a small delay (on a best effort
basis). The physical `POWER` button will still cause the screen to be turned on.

It can also be useful to prevent the device from sleeping:

```bash
scrcpy --turn-screen-off --stay-awake
scrcpy -Sw   # short version
```

Since Android 15, it is possible to change this setting manually:

```
# turn screen off (0 for main display)
adb shell cmd display power-off 0
# turn screen on
adb shell cmd display power-on 0
```


## Show touches

For presentations, it may be useful to show physical touches (on the physical
device). Android exposes this feature in _Developers options_.

_Scrcpy_ provides an option to enable this feature on start and restore the
initial value on exit:

```bash
scrcpy --show-touches
scrcpy -t   # short version
```

Note that it only shows _physical_ touches (by a finger on the device).

It is possible to change this setting manually:

```bash
# get the current show_touches value
adb shell settings get system show_touches
# enable show_touches
adb shell settings put system show_touches 1
# disable show_touches
adb shell settings put system show_touches 0
```

## Power off on close

To turn the device screen off when closing _scrcpy_:

```bash
scrcpy --power-off-on-close
```

## Power on on start

By default, on start, the device is powered on. To prevent this behavior:

```bash
scrcpy --no-power-on
```


## Start Android app

To list the Android apps installed on the device:

```bash
scrcpy --list-apps
```

An app, selected by its package name, can be launched on start:

```
scrcpy --start-app=org.mozilla.firefox
```

This feature can be used to run an app in a [virtual
display](virtual_display.md):

```
scrcpy --new-display=1920x1080 --start-app=org.videolan.vlc
```

The app can be optionally forced-stop before being started, by adding a `+`
prefix:

```
scrcpy --start-app=+org.mozilla.firefox
```

For convenience, it is also possible to select an app by its name, by adding a
`?` prefix:

```
scrcpy --start-app=?firefox
```

But retrieving app names may take some time (sometimes several seconds), so
passing the package name is recommended.

The `+` and `?` prefixes can be combined (in that order):

```
scrcpy --start-app=+?firefox
```

# Gamepad

Several gamepad input modes are available:

 - `--gamepad=disabled` (default)
 - `--gamepad=uhid` (or `-G`): simulates physical HID gamepads using the UHID
   kernel module on the device
 - `--gamepad=aoa`: simulates physical HID gamepads using the AOAv2 protocol


## Physical gamepad simulation

Two modes allow to simulate physical HID gamepads on the device, one for each
physical gamepad plugged into the computer.


### UHID

This mode simulates physical HID gamepads using the [UHID] kernel module on the
device.

[UHID]: https://kernel.org/doc/Documentation/hid/uhid.txt

To enable UHID gamepads, use:

```bash
scrcpy --gamepad=uhid
scrcpy -G  # short version
```

Note: UHID may not work on old Android versions due to permission errors.


### AOA

This mode simulates physical HID gamepads using the [AOAv2] protocol.

[AOAv2]: https://source.android.com/devices/accessories/aoa2#hid-support

To enable AOA gamepads, use:

```bash
scrcpy --gamepad=aoa
```

Contrary to the other mode, it works at the USB level directly (so it only works
over USB).

It does not use the scrcpy server, and does not require `adb` (USB debugging).
Therefore, it is possible to control the device (but not mirror) even with USB
debugging disabled (see [OTG](otg.md)).

Note: For some reason, in this mode, Android detects multiple physical gamepads
as a single misbehaving one. Use UHID if you need multiple gamepads.

Note: On Windows, it may only work in [OTG mode](otg.md), not while mirroring
(it is not possible to open a USB device if it is already open by another
process like the _adb daemon_).

# Keyboard

Several keyboard input modes are available:

 - `--keyboard=sdk` (default)
 - `--keyboard=uhid` (or `-K`): simulates a physical HID keyboard using the UHID
   kernel module on the device
 - `--keyboard=aoa`: simulates a physical HID keyboard using the AOAv2 protocol
 - `--keyboard=disabled`

By default, `sdk` is used, but if you use scrcpy regularly, it is recommended to
use [`uhid`](#uhid) and configure the keyboard layout once and for all.


## SDK keyboard

In this mode (`--keyboard=sdk`, or if the parameter is omitted), keyboard input
events are injected at the Android API level. It works everywhere, but it is
limited to ASCII and some other characters.

Note that on some devices, an additional option must be enabled in developer
options for this keyboard mode to work. See
[prerequisites](/README.md#prerequisites).

Additional parameters (specific to `--keyboard=sdk`) described below allow to
customize the behavior.


### Text injection preference

Two kinds of [events][textevents] are generated when typing text:
 - _key events_, signaling that a key is pressed or released;
 - _text events_, signaling that a text has been entered.

By default, numbers and "special characters" are inserted using text events, but
letters are injected using key events, so that the keyboard behaves as expected
in games (typically for WASD keys).

But this may [cause issues][prefertext]. If you encounter such a problem, you
can inject letters as text (or just switch to [UHID](#uhid)):

```bash
scrcpy --prefer-text
```

(but this will break keyboard behavior in games)

On the contrary, you could force to always inject raw key events:

```bash
scrcpy --raw-key-events
```

[textevents]: https://blog.rom1v.com/2018/03/introducing-scrcpy/#handle-text-input
[prefertext]: https://github.com/Genymobile/scrcpy/issues/650#issuecomment-512945343


### Key repeat

By default, holding a key down generates repeated key events. Ths can cause
performance problems in some games, where these events are useless anyway.

To avoid forwarding repeated key events:

```bash
scrcpy --no-key-repeat
```


## Physical keyboard simulation

Two modes allow to simulate a physical HID keyboard on the device.

To work properly, it is necessary to configure (once and for all) the keyboard
layout on the device to match that of the computer.

The configuration page can be opened in one of the following ways:
 - from the scrcpy window (when `uhid` or `aoa` is used), by pressing
   <kbd>Alt</kbd>+<kbd>k</kbd> (see [shortcuts](shortcuts.md))
 - from the device, in Settings → System → Languages and input → Physical
   devices
 - from a terminal on the computer, by executing `adb shell am start -a
   android.settings.HARD_KEYBOARD_SETTINGS`

From this configuration page, it is also possible to enable or disable on-screen
keyboard.


### UHID

This mode simulates a physical HID keyboard using the [UHID] kernel module on the
device.

[UHID]: https://kernel.org/doc/Documentation/hid/uhid.txt

To enable UHID keyboard, use:

```bash
scrcpy --keyboard=uhid
scrcpy -K  # short version
```

Once the keyboard layout is configured (see above), it is the best mode for
using the keyboard while mirroring:

 - it works for all characters and IME (contrary to `--keyboard=sdk`)
 - the on-screen keyboard can be disabled (contrary to `--keyboard=sdk`)
 - it works over TCP/IP (wirelessly) (contrary to `--keyboard=aoa`)
 - there are no issues on Windows (contrary to `--keyboard=aoa`)

One drawback is that it may not work on old Android versions due to permission
errors.


### AOA

This mode simulates a physical HID keyboard using the [AOAv2] protocol.

[AOAv2]: https://source.android.com/devices/accessories/aoa2#hid-support

To enable AOA keyboard, use:

```bash
scrcpy --keyboard=aoa
```

Contrary to the other modes, it works at the USB level directly (so it only
works over USB).

It does not use the scrcpy server, and does not require `adb` (USB debugging).
Therefore, it is possible to control the device (but not mirror) even with USB
debugging disabled (see [OTG](otg.md)).

Note: On Windows, it may only work in [OTG mode](otg.md), not while mirroring
(it is not possible to open a USB device if it is already open by another
process like the _adb daemon_).

# On Linux

## Install

### From the official release

Download a static build of the [latest release]:

 - [`scrcpy-linux-x86_64-v3.3.1.tar.gz`][direct-linux-x86_64] (x86_64)  
   <sub>SHA-256: `bbfe54c6b178adafeaffbbfbbc1548a74486553170c63e63bdd41863ad123422`</sub>

[latest release]: https://github.com/Genymobile/scrcpy/releases/latest
[direct-linux-x86_64]: https://github.com/Genymobile/scrcpy/releases/download/v3.3.1/scrcpy-linux-x86_64-v3.3.1.tar.gz

and extract it.

_Static builds of scrcpy for Linux are still experimental._


### From your package manager

<a href="https://repology.org/project/scrcpy/versions"><img src="https://repology.org/badge/vertical-allrepos/scrcpy.svg" alt="Packaging status" align="right"></a>

Scrcpy is packaged in several distributions and package managers:

 - Debian/Ubuntu: ~~`apt install scrcpy`~~ _(obsolete version)_
 - Arch Linux: `pacman -S scrcpy`
 - Fedora: `dnf copr enable zeno/scrcpy && dnf install scrcpy`
 - Gentoo: `emerge scrcpy`
 - Snap: ~~`snap install scrcpy`~~ _(obsolete version)_
 - … (see [repology](https://repology.org/project/scrcpy/versions))


### From an install script

To install the latest release from `master`, follow this simplified process.

First, you need to install the required packages:

```bash
# for Debian/Ubuntu
sudo apt install ffmpeg libsdl2-2.0-0 adb wget \
                 gcc git pkg-config meson ninja-build libsdl2-dev \
                 libavcodec-dev libavdevice-dev libavformat-dev libavutil-dev \
                 libswresample-dev libusb-1.0-0 libusb-1.0-0-dev
```

Then clone the repo and execute the installation script
([source](/install_release.sh)):

```bash
git clone https://github.com/Genymobile/scrcpy
cd scrcpy
./install_release.sh
```

When a new release is out, update the repo and reinstall:

```bash
git pull
./install_release.sh
```

To uninstall:

```bash
sudo ninja -Cbuild-auto uninstall
```

_Note that this simplified process only works for released versions (it
downloads a prebuilt server binary), so for example you can't use it for testing
the development branch (`dev`)._

_See [build.md](build.md) to build and install the app manually._


## Run

_Make sure that your device meets the [prerequisites](/README.md#prerequisites)._

Once installed, run from a terminal:

```bash
scrcpy
```

or with arguments (here to disable audio and record to `file.mkv`):

```bash
scrcpy --no-audio --record=file.mkv
```

Documentation for command line arguments is available:
 - `man scrcpy`
 - `scrcpy --help`
 - on [github](/README.md)

# On macOS

## Install

### From the official release

Download a static build of the [latest release]:

 - [`scrcpy-macos-aarch64-v3.3.1.tar.gz`][direct-macos-aarch64] (aarch64)  
   <sub>SHA-256: `907b925900ebd8499c1e47acc9689a95bd3a6f9930eb1d7bdfbca8375ae4f139`</sub>

 - [`scrcpy-macos-x86_64-v3.3.1.tar.gz`][direct-macos-x86_64] (x86_64)  
   <sub>SHA-256: `69772491dad718eea82fc65c8e89febff7d41c4ce6faff02f4789a588d10fd7d`</sub>

[latest release]: https://github.com/Genymobile/scrcpy/releases/latest
[direct-macos-aarch64]: https://github.com/Genymobile/scrcpy/releases/download/v3.3.1/scrcpy-macos-aarch64-v3.3.1.tar.gz
[direct-macos-x86_64]: https://github.com/Genymobile/scrcpy/releases/download/v3.3.1/scrcpy-macos-x86_64-v3.3.1.tar.gz

and extract it.

_Static builds of scrcpy for macOS are still experimental._


### From a package manager

Scrcpy is available in [Homebrew]:

```bash
brew install scrcpy
```

[Homebrew]: https://brew.sh/

You need `adb`, accessible from your `PATH`. If you don't have it yet:

```bash
brew install --cask android-platform-tools
```

Alternatively, Scrcpy is also available in [MacPorts], which sets up `adb` for you:

```bash
sudo port install scrcpy
```

[MacPorts]: https://www.macports.org/

_See [build.md](build.md) to build and install the app manually._


## Run

_Make sure that your device meets the [prerequisites](/README.md#prerequisites)._

Once installed, run from a terminal:

```bash
scrcpy
```

or with arguments (here to disable audio and record to `file.mkv`):

```bash
scrcpy --no-audio --record=file.mkv
```

Documentation for command line arguments is available:
 - `man scrcpy`
 - `scrcpy --help`
 - on [github](/README.md)

# Mouse

Several mouse input modes are available:

 - `--mouse=sdk` (default)
 - `--mouse=uhid` (or `-M`): simulates a physical HID mouse using the UHID
   kernel module on the device
 - `--mouse=aoa`: simulates a physical HID mouse using the AOAv2 protocol
 - `--mouse=disabled`


## SDK mouse

In this mode (`--mouse=sdk`, or if the parameter is omitted), mouse input events
are injected at the Android API level with absolute coordinates.

Note that on some devices, an additional option must be enabled in developer
options for this mouse mode to work. See
[prerequisites](/README.md#prerequisites).

### Mouse hover

By default, mouse hover (mouse motion without any clicks) events are forwarded
to the device. This can be disabled with:

```
scrcpy --no-mouse-hover
```

## Physical mouse simulation

Two modes allow to simulate a physical HID mouse on the device.

In these modes, the computer mouse is "captured": the mouse pointer disappears
from the computer and appears on the Android device instead.

The [shortcut mod](shortcuts.md) (either <kbd>Alt</kbd> or <kbd>Super</kbd> by
default) toggle (disable or enable) the mouse capture. Use one of them to give
the control of the mouse back to the computer.


### UHID

This mode simulates a physical HID mouse using the [UHID] kernel module on the
device.

[UHID]: https://kernel.org/doc/Documentation/hid/uhid.txt

To enable UHID mouse, use:

```bash
scrcpy --mouse=uhid
scrcpy -M  # short version
```

Note: UHID may not work on old Android versions due to permission errors.


### AOA

This mode simulates a physical HID mouse using the [AOAv2] protocol.

[AOAv2]: https://source.android.com/devices/accessories/aoa2#hid-support

To enable AOA mouse, use:

```bash
scrcpy --mouse=aoa
```

Contrary to the other modes, it works at the USB level directly (so it only
works over USB).

It does not use the scrcpy server, and does not require `adb` (USB debugging).
Therefore, it is possible to control the device (but not mirror) even with USB
debugging disabled (see [OTG](otg.md)).

Note: On Windows, it may only work in [OTG mode](otg.md), not while mirroring
(it is not possible to open a USB device if it is already open by another
process like the _adb daemon_).


## Mouse bindings

By default, with SDK mouse:
 - right-click triggers `BACK` (or `POWER` on)
 - middle-click triggers `HOME`
 - the 4th click triggers `APP_SWITCH`
 - the 5th click expands the notification panel

The secondary clicks may be forwarded to the device instead by pressing the
<kbd>Shift</kbd> key (e.g. <kbd>Shift</kbd>+right-click injects a right click to
the device).

In AOA and UHID mouse modes, the default bindings are reversed: all clicks are
forwarded by default, and pressing <kbd>Shift</kbd> gives access to the
shortcuts (since the cursor is handled on the device side, it makes more sense
to forward all mouse buttons by default in these modes).

The shortcuts can be configured using `--mouse-bind=xxxx:xxxx` for any mouse
mode. The argument must be one or two sequences (separated by `:`) of exactly 4
characters, one for each secondary click:

```
                  .---- Shift + right click
       SECONDARY  |.--- Shift + middle click
        BINDINGS  ||.-- Shift + 4th click
                  |||.- Shift + 5th click
                  ||||
                  vvvv
--mouse-bind=xxxx:xxxx
             ^^^^
             ||||
   PRIMARY   ||| `- 5th click
  BINDINGS   || `-- 4th click
             | `--- middle click
              `---- right click
```

Each character must be one of the following:

 - `+`: forward the click to the device
 - `-`: ignore the click
 - `b`: trigger shortcut `BACK` (or turn screen on if off)
 - `h`: trigger shortcut `HOME`
 - `s`: trigger shortcut `APP_SWITCH`
 - `n`: trigger shortcut "expand notification panel"

For example:

```bash
scrcpy --mouse-bind=bhsn:++++  # the default mode for SDK mouse
scrcpy --mouse-bind=++++:bhsn  # the default mode for AOA and UHID
scrcpy --mouse-bind=++bh:++sn  # forward right and middle clicks,
                               # use 4th and 5th for BACK and HOME,
                               # use Shift+4th and Shift+5th for APP_SWITCH
                               # and expand notification panel
```

The second sequence of bindings may be omitted. In that case, it is the same as
the first one:

```bash
scrcpy --mouse-bind=bhsn
scrcpy --mouse-bind=bhsn:bhsn  # equivalent
```

# OTG

By default, _scrcpy_ injects input events at the Android API level. As an
alternative, it is possible to send HID events, so that scrcpy behaves as if it
was a [physical keyboard] and/or a [physical mouse] connected to the Android
device (see [keyboard](keyboard.md) and [mouse](mouse.md)).

[physical keyboard]: keyboard.md#physical-keyboard-simulation
[physical mouse]: mouse.md#physical-mouse-simulation

A special mode (OTG) allows to control the device using AOA
[keyboard](keyboard.md#aoa), [mouse](mouse.md#aoa) and
[gamepad](gamepad.md#aoa), without using _adb_ at all (so USB debugging is not
necessary). In this mode, video and audio are disabled, and `--keyboard=aoa` and
`--mouse=aoa` are implicitly set. However, gamepads are disabled by default, so
`--gamepad=aoa` (or `-G` in OTG mode) must be explicitly set.

Therefore, it is possible to run _scrcpy_ with only physical keyboard, mouse and
gamepad simulation, as if the computer keyboard, mouse and gamepads were plugged
directly to the device via an OTG cable.

To enable OTG mode:

```bash
scrcpy --otg
# Pass the serial if several USB devices are available
scrcpy --otg -s 0123456789abcdef
```

It is possible to disable keyboard or mouse:

```bash
scrcpy --otg --keyboard=disabled
scrcpy --otg --mouse=disabled
```

and to enable gamepads:

```bash
scrcpy --otg --gamepad=aoa
scrcpy --otg -G  # short version
```

It only works if the device is connected over USB.

## OTG issues on Windows

See [FAQ](/FAQ.md#otg-issues-on-windows).


## Control only

Note that the purpose of OTG is to control the device without USB debugging
(adb).

If you want to solely control the device without mirroring while USB debugging
is enabled, then OTG mode is not necessary.

Instead, disable video and audio, and select UHID (or AOA):

```bash
scrcpy --no-video --no-audio --keyboard=uhid --mouse=uhid --gamepad=uhid
scrcpy --no-video --no-audio -KMG  # short version
scrcpy --no-video --no-audio --keyboard=aoa --mouse=aoa --gamepad=aoa
```

One benefit of UHID is that it also works wirelessly.

# Recording

To record video and audio streams while mirroring:

```bash
scrcpy --record=file.mp4
scrcpy -r file.mkv
```

To record only the video:

```bash
scrcpy --no-audio --record=file.mp4
```

To record only the audio:

```bash
scrcpy --no-video --record=file.opus
scrcpy --no-video --audio-codec=aac --record=file.aac
scrcpy --no-video --audio-codec=flac --record=file.flac
scrcpy --no-video --audio-codec=raw --record=file.wav
# .m4a/.mp4 and .mka/.mkv are also supported for opus, aac and flac
```

Timestamps are captured on the device, so [packet delay variation] does not
impact the recorded file, which is always clean (only if you use `--record` of
course, not if you capture your scrcpy window and audio output on the computer).

[packet delay variation]: https://en.wikipedia.org/wiki/Packet_delay_variation


## Format

The video and audio streams are encoded on the device, but are muxed on the
client side. Several formats (containers) are supported:
 - MP4 (`.mp4`, `.m4a`, `.aac`)
 - Matroska (`.mkv`, `.mka`)
 - OPUS (`.opus`)
 - FLAC (`.flac`)
 - WAV (`.wav`)

The container is automatically selected based on the filename.

It is also possible to explicitly select a container (in that case the filename
needs not end with a known extension):

```
scrcpy --record=file --record-format=mkv
```


## Rotation

The video can be recorded rotated. See [video
orientation](video.md#orientation).


## No playback

To disable playback and control while recording:

```bash
scrcpy --no-playback --no-control --record=file.mp4
```

It is also possible to disable video and audio playback separately:

```bash
# Record both video and audio, but only play video
scrcpy --record=file.mkv --no-audio-playback
```

To also disable the window:

```bash
scrcpy --no-playback --no-window --record=file.mp4
# interrupt recording with Ctrl+C
```

## Time limit

To limit the recording time:

```bash
scrcpy --record=file.mkv --time-limit=20  # in seconds
```

The `--time-limit` option is not limited to recording, it also impacts simple
mirroring:

```
scrcpy --time-limit=20
```

# Shortcuts

Actions can be performed on the scrcpy window using keyboard and mouse
shortcuts.

In the following list, <kbd>Alt</kbd>+ is the shortcut modifier. By default, it's
(left) <kbd>Alt</kbd> or (left) <kbd>Super</kbd>.

It can be changed using `--shortcut-mod`. Possible keys are `lctrl`, `rctrl`,
`lalt`, `ralt`, `lsuper` and `rsuper`. For example:

```bash
# use RCtrl for shortcuts
scrcpy --shortcut-mod=rctrl

# use either LCtrl or LSuper for shortcuts
scrcpy --shortcut-mod=lctrl,lsuper
```

_<kbd>[Super]</kbd> is typically the <kbd>Windows</kbd> or <kbd>Cmd</kbd> key._

[Super]: https://en.wikipedia.org/wiki/Super_key_(keyboard_button)

 | Action                                      |   Shortcut
 | ------------------------------------------- |:-----------------------------
 | Switch fullscreen mode                      | <kbd>Alt</kbd>+<kbd>f</kbd>
 | Rotate display left                         | <kbd>Alt</kbd>+<kbd>←</kbd> _(left)_
 | Rotate display right                        | <kbd>Alt</kbd>+<kbd>→</kbd> _(right)_
 | Flip display horizontally                   | <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>←</kbd> _(left)_ \| <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>→</kbd> _(right)_
 | Flip display vertically                     | <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>↑</kbd> _(up)_ \| <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>↓</kbd> _(down)_
 | Pause or re-pause display                   | <kbd>Alt</kbd>+<kbd>z</kbd>
 | Unpause display                             | <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>z</kbd>
 | Reset video capture/encoding                | <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>r</kbd>
 | Resize window to 1:1 (pixel-perfect)        | <kbd>Alt</kbd>+<kbd>g</kbd>
 | Resize window to remove black borders       | <kbd>Alt</kbd>+<kbd>w</kbd> \| _Double-left-click¹_
 | Click on `HOME`                             | <kbd>Alt</kbd>+<kbd>h</kbd> \| _Middle-click_
 | Click on `BACK`                             | <kbd>Alt</kbd>+<kbd>b</kbd> \| <kbd>Alt</kbd>+<kbd>Backspace</kbd> \| _Right-click²_
 | Click on `APP_SWITCH`                       | <kbd>Alt</kbd>+<kbd>s</kbd> \| _4th-click³_
 | Click on `MENU` (unlock screen)⁴            | <kbd>Alt</kbd>+<kbd>m</kbd>
 | Click on `VOLUME_UP`                        | <kbd>Alt</kbd>+<kbd>↑</kbd> _(up)_
 | Click on `VOLUME_DOWN`                      | <kbd>Alt</kbd>+<kbd>↓</kbd> _(down)_
 | Click on `POWER`                            | <kbd>Alt</kbd>+<kbd>p</kbd>
 | Power on                                    | _Right-click²_
 | Turn device screen off (keep mirroring)     | <kbd>Alt</kbd>+<kbd>o</kbd>
 | Turn device screen on                       | <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>o</kbd>
 | Rotate device screen                        | <kbd>Alt</kbd>+<kbd>r</kbd>
 | Expand notification panel                   | <kbd>Alt</kbd>+<kbd>n</kbd> \| _5th-click³_
 | Expand settings panel                       | <kbd>Alt</kbd>+<kbd>n</kbd>+<kbd>n</kbd> \| _Double-5th-click³_
 | Collapse panels                             | <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>n</kbd>
 | Copy to clipboard⁵                          | <kbd>Alt</kbd>+<kbd>c</kbd>
 | Cut to clipboard⁵                           | <kbd>Alt</kbd>+<kbd>x</kbd>
 | Synchronize clipboards and paste⁵           | <kbd>Alt</kbd>+<kbd>v</kbd>
 | Inject computer clipboard text              | <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>v</kbd>
 | Open keyboard settings (HID keyboard only)  | <kbd>Alt</kbd>+<kbd>k</kbd>
 | Enable/disable FPS counter (on stdout)      | <kbd>Alt</kbd>+<kbd>i</kbd>
 | Pinch-to-zoom/rotate                        | <kbd>Ctrl</kbd>+_click-and-move_
 | Tilt vertically (slide with 2 fingers)      | <kbd>Shift</kbd>+_click-and-move_
 | Tilt horizontally (slide with 2 fingers)    | <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+_click-and-move_
 | Drag & drop APK file                        | Install APK from computer
 | Drag & drop non-APK file                    | [Push file to device](control.md#push-file-to-device)

_¹Double-click on black borders to remove them._  
_²Right-click turns the screen on if it was off, presses BACK otherwise._  
_³4th and 5th mouse buttons, if your mouse has them._  
_⁴For react-native apps in development, `MENU` triggers development menu._  
_⁵Only on Android >= 7._

Shortcuts with repeated keys are executed by releasing and pressing the key a
second time. For example, to execute "Expand settings panel":

 1. Press and keep pressing <kbd>Alt</kbd>+.
 2. Then double-press <kbd>n</kbd>.
 3. Finally, release <kbd>Alt</kbd>+.

All <kbd>Ctrl</kbd>+_key_ shortcuts are forwarded to the device, so they are
handled by the active application.

# Tunnels

Scrcpy is designed to mirror local Android devices. Tunnels allow to connect to
a remote device (e.g. over the Internet).

To connect to a remote device, it is possible to connect a local `adb` client to
a remote `adb` server (provided they use the same version of the _adb_
protocol).


## Remote ADB server

To connect to a remote _adb server_, make the server listen on all interfaces:

```bash
adb kill-server
adb -a nodaemon server start
# keep this open
```

**Warning: all communications between clients and the _adb server_ are
unencrypted.**

Suppose that this server is accessible at 192.168.1.2. Then, from another
terminal, run `scrcpy`:

```bash
# in bash
export ADB_SERVER_SOCKET=tcp:192.168.1.2:5037
scrcpy --tunnel-host=192.168.1.2
```

```cmd
:: in cmd
set ADB_SERVER_SOCKET=tcp:192.168.1.2:5037
scrcpy --tunnel-host=192.168.1.2
```

```powershell
# in PowerShell
$env:ADB_SERVER_SOCKET = 'tcp:192.168.1.2:5037'
scrcpy --tunnel-host=192.168.1.2
```

By default, `scrcpy` uses the local port used for `adb forward` tunnel
establishment (typically `27183`, see `--port`). It is also possible to force a
different tunnel port (it may be useful in more complex situations, when more
redirections are involved):

```
scrcpy --tunnel-port=1234
```


## SSH tunnel

To communicate with a remote _adb server_ securely, it is preferable to use an
SSH tunnel.

First, make sure the _adb server_ is running on the remote computer:

```bash
adb start-server
```

Then, establish an SSH tunnel:

```bash
# local  5038 --> remote  5037
# local 27183 <-- remote 27183
ssh -CN -L5038:localhost:5037 -R27183:localhost:27183 your_remote_computer
# keep this open
```

From another terminal, run `scrcpy`:

```bash
# in bash
export ADB_SERVER_SOCKET=tcp:localhost:5038
scrcpy
```

```cmd
:: in cmd
set ADB_SERVER_SOCKET=tcp:localhost:5038
scrcpy
```

```powershell
# in PowerShell
$env:ADB_SERVER_SOCKET = 'tcp:localhost:5038'
scrcpy
```

To avoid enabling remote port forwarding, you could force a forward connection
instead (notice the `-L` instead of `-R`):

```bash
# local  5038 --> remote  5037
# local 27183 --> remote 27183
ssh -CN -L5038:localhost:5037 -L27183:localhost:27183 your_remote_computer
# keep this open
```

From another terminal, run `scrcpy`:

```bash
# in bash
export ADB_SERVER_SOCKET=tcp:localhost:5038
scrcpy --force-adb-forward
```

```cmd
:: in cmd
set ADB_SERVER_SOCKET=tcp:localhost:5038
scrcpy --force-adb-forward
```

```powershell
# in PowerShell
$env:ADB_SERVER_SOCKET = 'tcp:localhost:5038'
scrcpy --force-adb-forward
```

# Video4Linux

On Linux, it is possible to send the video stream to a [v4l2] loopback device,
so that the Android device can be opened like a webcam by any v4l2-capable tool.

[v4l2]: https://en.wikipedia.org/wiki/Video4Linux

The module `v4l2loopback` must be installed:

```bash
sudo apt install v4l2loopback-dkms
```

To create a v4l2 device:

```bash
sudo modprobe v4l2loopback
```

This will create a new video device in `/dev/videoN`, where `N` is an integer
(more [options](https://github.com/umlaeute/v4l2loopback#options) are available
to create several devices or devices with specific IDs).

If you encounter problems detecting your device with Chrome/WebRTC, you can try
`exclusive_caps` mode:

```
sudo modprobe v4l2loopback exclusive_caps=1
```

To list the enabled devices:

```bash
# requires v4l-utils package
v4l2-ctl --list-devices

# simple but might be sufficient
ls /dev/video*
```

To start `scrcpy` using a v4l2 sink:

```bash
scrcpy --v4l2-sink=/dev/videoN
scrcpy --v4l2-sink=/dev/videoN --no-video-playback  # disable playback window
```

(replace `N` with the device ID, check with `ls /dev/video*`)

Once enabled, you can open your video stream with a v4l2-capable tool:

```bash
ffplay -i /dev/videoN
vlc v4l2:///dev/videoN   # VLC might add some buffering delay
```

For example, you could capture the video within [OBS] or within your video
conference tool.

[OBS]: https://obsproject.com/


## Buffering

By default, there is no video buffering, to get the lowest possible latency.

As for the [video display](video.md#buffering), it is possible to add
buffering to delay the v4l2 stream:

```bash
scrcpy --v4l2-buffer=300     # add 300ms buffering for v4l2 sink
```

# Video

## Source

By default, scrcpy mirrors the device screen.

It is possible to capture the device camera instead.

See the dedicated [camera](camera.md) page.


## Size

By default, scrcpy attempts to mirror at the Android device resolution.

It might be useful to mirror at a lower definition to increase performance. To
limit both width and height to some maximum value (here 1024):

```bash
scrcpy --max-size=1024
scrcpy -m 1024   # short version
```

The other dimension is computed so that the Android device aspect ratio is
preserved. That way, a device in 1920×1080 will be mirrored at 1024×576.

If encoding fails, scrcpy automatically tries again with a lower definition
(unless `--no-downsize-on-error` is enabled).

For camera mirroring, the `--max-size` value is used to select the camera source
size instead (among the available resolutions).


## Bit rate

The default video bit rate is 8 Mbps. To change it:

```bash
scrcpy --video-bit-rate=2M
scrcpy --video-bit-rate=2000000  # equivalent
scrcpy -b 2M                     # short version
```


## Frame rate

The capture frame rate can be limited:

```bash
scrcpy --max-fps=15
```

The actual capture frame rate may be printed to the console:

```
scrcpy --print-fps
```

It may also be enabled or disabled at anytime with <kbd>Alt</kbd>+<kbd>i</kbd>
(see [shortcuts](shortcuts.md)).

The frame rate is intrinsically variable: a new frame is produced only when the
screen content changes. For example, if you play a fullscreen video at 24fps on
your device, you should not get more than 24 frames per second in scrcpy.


## Codec

The video codec can be selected. The possible values are `h264` (default),
`h265` and `av1`:

```bash
scrcpy --video-codec=h264  # default
scrcpy --video-codec=h265
scrcpy --video-codec=av1
```

H265 may provide better quality, but H264 should provide lower latency.
AV1 encoders are not common on current Android devices.

For advanced usage, to pass arbitrary parameters to the [`MediaFormat`],
check `--video-codec-options` in the manpage or in `scrcpy --help`.

[`MediaFormat`]: https://developer.android.com/reference/android/media/MediaFormat


## Encoder

Several encoders may be available on the device. They can be listed by:

```bash
scrcpy --list-encoders
```

Sometimes, the default encoder may have issues or even crash, so it is useful to
try another one:

```bash
scrcpy --video-codec=h264 --video-encoder=OMX.qcom.video.encoder.avc
```


## Orientation

The orientation may be applied at 3 different levels:
 - The [shortcut](shortcuts.md) <kbd>Alt</kbd>+<kbd>r</kbd> requests the
   device to switch between portrait and landscape (the current running app may
   refuse, if it does not support the requested orientation).
 - `--capture-orientation` changes the mirroring orientation (the orientation
   of the video sent from the device to the computer). This affects the
   recording.
 - `--orientation` is applied on the client side, and affects display and
   recording. For the display, it can be changed dynamically using
   [shortcuts](shortcuts.md).

To capture the video with a specific orientation:

```bash
scrcpy --capture-orientation=0
scrcpy --capture-orientation=90       # 90° clockwise
scrcpy --capture-orientation=180      # 180°
scrcpy --capture-orientation=270      # 270° clockwise
scrcpy --capture-orientation=flip0    # hflip
scrcpy --capture-orientation=flip90   # hflip + 90° clockwise
scrcpy --capture-orientation=flip180  # hflip + 180°
scrcpy --capture-orientation=flip270  # hflip + 270° clockwise
```

The capture orientation can be locked by using `@`, so that a physical device
rotation does not change the captured video orientation:

```bash
scrcpy --capture-orientation=@         # locked to the initial orientation
scrcpy --capture-orientation=@0        # locked to 0°
scrcpy --capture-orientation=@90       # locked to 90° clockwise
scrcpy --capture-orientation=@180      # locked to 180°
scrcpy --capture-orientation=@270      # locked to 270° clockwise
scrcpy --capture-orientation=@flip0    # locked to hflip
scrcpy --capture-orientation=@flip90   # locked to hflip + 90° clockwise
scrcpy --capture-orientation=@flip180  # locked to hflip + 180°
scrcpy --capture-orientation=@flip270  # locked to hflip + 270° clockwise
```

The capture orientation transform is applied after `--crop`, but before
`--angle`.

To orient the video (on the client side):

```bash
scrcpy --orientation=0
scrcpy --orientation=90       # 90° clockwise
scrcpy --orientation=180      # 180°
scrcpy --orientation=270      # 270° clockwise
scrcpy --orientation=flip0    # hflip
scrcpy --orientation=flip90   # hflip + 90° clockwise
scrcpy --orientation=flip180  # vflip (hflip + 180°)
scrcpy --orientation=flip270  # hflip + 270° clockwise
```

The orientation can be set separately for display and record if necessary, via
`--display-orientation` and `--record-orientation`.

The rotation is applied to a recorded file by writing a display transformation
to the MP4 or MKV target file. Flipping is not supported, so only the 4 first
values are allowed when recording.


## Angle

To rotate the video content by a custom angle (in degrees, clockwise):

```
scrcpy --angle=23
```

The center of rotation is the center of the visible area.

This transformation is applied after `--crop` and `--capture-orientation`.


## Crop

The device screen may be cropped to mirror only part of the screen.

This is useful, for example, to mirror only one eye of the Oculus Go:

```bash
scrcpy --crop=1224:1440:0:0   # 1224x1440 at offset (0,0)
```

The values are expressed in the device natural orientation (portrait for a
phone, landscape for a tablet).

Cropping is performed before `--capture-orientation` and `--angle`.

For display mirroring, `--max-size` is applied after cropping. For camera,
`--max-size` is applied first (because it selects the source size rather than
resizing the content).


## Display

If several displays are available on the Android device, it is possible to
select the display to mirror:

```bash
scrcpy --display-id=1
```

The list of display ids can be retrieved by:

```bash
scrcpy --list-displays
```

A secondary display may only be controlled if the device runs at least Android
10 (otherwise it is mirrored as read-only).

It is also possible to create a [virtual display](virtual_display.md).


## Buffering

By default, there is no video buffering, to get the lowest possible latency.

Buffering can be added to delay the video stream and compensate for jitter to
get a smoother playback (see [#2464]).

[#2464]: https://github.com/Genymobile/scrcpy/issues/2464

The configuration is available independently for the display,
[v4l2 sinks](video.md#video4linux) and [audio](audio.md#buffering) playback.

```bash
scrcpy --video-buffer=50     # add 50ms buffering for video playback
scrcpy --audio-buffer=200    # set 200ms buffering for audio playback
scrcpy --v4l2-buffer=300     # add 300ms buffering for v4l2 sink
```

They can be applied simultaneously:

```bash
scrcpy --video-buffer=50 --v4l2-buffer=300
```


## No playback

It is possible to capture an Android device without playing video or audio on
the computer. This option is useful when [recording](recording.md) or when
[v4l2](#video4linux) is enabled:

```bash
scrcpy --v4l2-sink=/dev/video2 --no-playback
scrcpy --record=file.mkv --no-playback
# interrupt with Ctrl+C
```

It is also possible to disable video and audio playback separately:

```bash
# Send video to V4L2 sink without playing it, but keep audio playback
scrcpy --v4l2-sink=/dev/video2 --no-video-playback

# Record both video and audio, but only play video
scrcpy --record=file.mkv --no-audio-playback
```


## No video

To disable video forwarding completely, so that only audio is forwarded:

```
scrcpy --no-video
```


## Video4Linux

See the dedicated [Video4Linux](v4l2.md) page.

# Virtual display

## New display

To mirror a new virtual display instead of the device screen:

```bash
scrcpy --new-display=1920x1080
scrcpy --new-display=1920x1080/420  # force 420 dpi
scrcpy --new-display         # use the main display size and density
scrcpy --new-display=/240    # use the main display size and 240 dpi
```

The new virtual display is destroyed on exit.

## Start app

On some devices, a launcher is available in the virtual display.

When no launcher is available (or if is explicitly disabled by
[`--no-vd-system-decorations`](#system-decorations)), the virtual display is
empty. In that case, you must [start an Android
app](device.md#start-android-app).

For example:

```bash
scrcpy --new-display=1920x1080 --start-app=org.videolan.vlc
```

The app may itself be a launcher. For example, to run the open source [Fossify
Launcher]:

```bash
scrcpy --new-display=1920x1080 --no-vd-system-decorations --start-app=org.fossify.home
```

[Fossify Launcher]: https://f-droid.org/en/packages/org.fossify.home/


## System decorations

By default, virtual display system decorations are enabled. To disable them, use
`--no-vd-system-decorations`:

```
scrcpy --new-display --no-vd-system-decorations
```

This is useful for some devices which might display a broken UI, or to disable
any default launcher UI available in virtual displays.

Note that if no app is started, no content will be rendered, so no video frame
will be produced at all.


## Destroy on close

By default, when the virtual display is closed, the running apps are destroyed.

To move them to the main display instead, use:

```
scrcpy --new-display --no-vd-destroy-content
```


## Display IME policy

By default, the virtual display IME appears on the default display.

To make it appear on the local display, use `--display-ime-policy=local`:

```bash
scrcpy --display-id=1 --display-ime-policy=local
scrcpy --new-display --display-ime-policy=local
```

# Window

## Disable window

To disable window (may be useful for recording or for playing audio only):

```bash
scrcpy --no-window --record=file.mp4
# Ctrl+C to interrupt
```

## Title

By default, the window title is the device model. It can be changed:

```bash
scrcpy --window-title='My device'
```

## Position and size

The initial window position and size may be specified:

```bash
scrcpy --window-x=100 --window-y=100 --window-width=800 --window-height=600
```

## Borderless

To disable window decorations:

```bash
scrcpy --window-borderless
```

## Always on top

To keep the window always on top:

```bash
scrcpy --always-on-top
```

## Fullscreen

The app may be started directly in fullscreen:

```bash
scrcpy --fullscreen
scrcpy -f   # short version
```

Fullscreen mode can then be toggled dynamically with <kbd>Alt</kbd>+<kbd>f</kbd>
(see [shortcuts](shortcuts.md)).


## Disable screensaver

By default, _scrcpy_ does not prevent the screensaver from running on the
computer. To disable it:

```bash
scrcpy --disable-screensaver
```

# On Windows

## Install

### From the official release

Download the [latest release]:

 - [`scrcpy-win64-v3.3.1.zip`][direct-win64] (64-bit)  
   <sub>SHA-256: `4fcad494772a3ae5de9a133149f8856d2fc429b41795f7cf7c754e0c1bb6fbc0`</sub>
 - [`scrcpy-win32-v3.3.1.zip`][direct-win32] (32-bit)  
   <sub>SHA-256: `ccdf1b4f5d19dfe760446a107e55b0a010a00e097d46533a161499c9333a20a6`</sub>

[latest release]: https://github.com/Genymobile/scrcpy/releases/latest
[direct-win64]: https://github.com/Genymobile/scrcpy/releases/download/v3.3.1/scrcpy-win64-v3.3.1.zip
[direct-win32]: https://github.com/Genymobile/scrcpy/releases/download/v3.3.1/scrcpy-win32-v3.3.1.zip

and extract it.


### From a package manager

From [WinGet] (ADB and other dependencies will be installed alongside scrcpy):

```bash
winget install --exact Genymobile.scrcpy
```

From [Chocolatey]:

```bash
choco install scrcpy
choco install adb    # if you don't have it yet
```

From [Scoop]:

```bash
scoop install scrcpy
scoop install adb    # if you don't have it yet
```

[WinGet]: https://github.com/microsoft/winget-cli
[Chocolatey]: https://chocolatey.org/
[Scoop]: https://scoop.sh

_See [build.md](build.md) to build and install the app manually._


## Run

_Make sure that your device meets the [prerequisites](/README.md#prerequisites)._

Scrcpy is a command line application: it is mainly intended to be executed from
a terminal with command line arguments.

To open a terminal at the expected location, double-click on
`open_a_terminal_here.bat` in your scrcpy directory, then type your command. For
example, without arguments:

```bash
scrcpy
```

or with arguments (here to disable audio and record to `file.mkv`):

```
scrcpy --no-audio --record=file.mkv
```

Documentation for command line arguments is available:
 - `scrcpy --help`
 - on [github](/README.md)

To start scrcpy directly without opening a terminal, double-click on one of
these files:
 - `scrcpy-console.bat`: start with a terminal open (it will close when scrcpy
   terminates, unless an error occurs);
 - `scrcpy-noconsole.vbs`: start without a terminal (but you won't see any error
   message).

_Avoid double-clicking on `scrcpy.exe` directly: on error, the terminal would
close immediately and you won't have time to read any error message (this
executable is intended to be run from the terminal). Use `scrcpy-console.bat`
instead._

If you plan to always use the same arguments, create a file `myscrcpy.bat`
(enable [show file extensions] to avoid confusion) containing your command, For
example:

```bash
scrcpy --prefer-text --turn-screen-off --stay-awake
```

[show file extensions]: https://www.howtogeek.com/205086/beginner-how-to-make-windows-show-file-extensions/

Then just double-click on that file.

You could also edit (a copy of) `scrcpy-console.bat` or `scrcpy-noconsole.vbs`
to add some arguments.
