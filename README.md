<p align="center">
    <a href="#" target="_blank"><img src="./resources/logo.png"></a>
</p>

# brightml: Machine-Learned Auto brightness

[![PyPI](https://img.shields.io/pypi/pyversions/brightml.svg?style=flat-square&logo=python)](https://pypi.python.org/pypi/brightml/)
[![PyPI](https://img.shields.io/pypi/v/brightml.svg?style=flat-square&logo=pypi)](https://pypi.python.org/pypi/brightml/)
[![HitCount](http://hits.dwyl.io/kootenpv/brightml.svg)](http://hits.dwyl.io/kootenpv/brightml)

<p align="center">
    <a href="#" target="_blank"><img src="./brightml.gif" width="50%"></a>
</p>


The goal of this package is to automatically manage brightness on laptops, with "zero config"; using machine learning.
Some do not even realise that what is "on" your screen, matters. White screens (like browser) vs coding (in black) should be accounted for.

All you have to do is to change brightness when it is not good enough yet; **brightml** learns.

It will learn to generalize based on your personal needs. To do this, it uses:

- Brightness of screen
- Ambient light sensor (if available)
- Hour of day
- whereami (indoor wifi positioning)
- Battery feature (only if discharging)
- Active application name
- Active window title

### Features

- Cross-OS (within Linux)
- Cross-vendor (intel, nvidia)
- Cross-hardware (with or without ambient light sensor, linux on macbook works)
- Seamless integration: No need to change key bindings as it monitors brightness change by user
- Uses asyncio, event-based (change of window immediately triggers prediction; no timer)
- Updates brightness on focusing different windows and on scrolling

### Goals

- Provide service files to enable by startup (systemd: done)
- Add a command to show "feature importance"
- More extensibility (plugin based)
- Cross-platform (OSX)

### Installation

    pip install brightml

Bonus: set up `whereami <https://github.com/kootenpv/whereami>`_ to include indoor positioning in the predictions.

    pip install brightml[whereami]

### Usage

Eventually we need to get some service files for the different Operating Systems, so the process starts on boot.

For now, just ready for preview, run on command line:

    sudo brightml

This will run brightml in the foreground.

To instead just show current feature values, run:

    pascal@archbook:~$ brightml features
    {
        "ambient_light": 1,
        "whereami": "bed",
        "datetime_hour": 21,
        "datetime_timezone": "UTC+02:00",
        "datetime_date": "2017-10-28",
        "datetime_full": "2017-10-28 21:52:43+02:00",
        "display_pixel_mean": 9.072666666666667,
        "display_window_name": "pascal@archbook:~",
        "display_window_class": "urxvt URxvt",
        "battery": 95.94282414091828
    }
