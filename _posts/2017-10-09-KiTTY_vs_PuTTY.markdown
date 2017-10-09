---
layout: post
title: KiTTY vs PuTTY 
date:  Mon 09 Oct 2017 02:01:04 PM EDT
categories: howto
---

## Summary

Do you work on Linux machines?  Do you only have a Windows machine from which to connect?  Then you're probably already
using PuTTY.

Well, step aside PuTTY, there's a new terminal client in town.

KiTTY is a fork of the original PuTTY software, with loads of new features including a portable version that saves all
of your sessions and settings into an INI file in the same folder.

---

## Installation

1. Download [KiTTY Portable](http://www.fosshub.com/KiTTY.html)
1. ???
1. PROFIT!

Just kidding.  There are no other steps.  The download is an exe that's ready to go.  Just double-click on it and enter
your connection parameters (should be familiar if you've ever used PuTTY)

## Portability

By default, KiTTY uses the Windows registry database to save its configuration (sessions, host keys, parameters). But,
it's possible to save it into a tree directories structure and to avoid writing anything into the registry.

1. Create a new folder for KiTTY anywhere on your disk and move the KiTTY.exe into it.
1. Create a file called `kitty.ini` in the same directory where you put KiTTY binary, and add these two lines:

    kitty.ini file

        [KiTTY]
        savemode=dir

If you've already used KiTTY to connect to some machines and have some profiles saved, you can copy all the existing
configurations from the registry. 
You just have to run this command from a command line within the KiTTY directory

    kitty.exe -convert-dir

This option will create 6 sub-directories: `Commands`, `Folders`, `Launcher`, `Sessions`,  `Sessions_Commands` and
`SshHostKeys` containing the configuration files. 

## Colors

The biggest reason I started using KiTTY was to get away from those horrible PuTTY colors.  (Yes - you can change the
colors in PuTTY - but this method is much easier)

In your KiTTY directory there will be a directory named: `Sessions`.  In that folder you will find separate files for
each of your saved connections.

Open one of them (I recommend using something like [Notepad++](https://notepad-plus-plus.org/download/), but plain old
notepad should work too)

Somewhere around line 116 (Notepad++ has line numbers), you will find several color definitions (in RBG format)

You can modify each of these to change the color of the specific element.  (But without knowing which element is which -
it will be very difficult!)

Or you can simply copy/paste some pre-made schemes into the lines in your session file.

One of my favorites is a scheme named **Dotshare**:

    Colour21\221,221,221\
    Colour20\221,221,221\
    Colour19\66,113,123\
    Colour18\109,135,141\
    Colour17\133,66,255\
    Colour16\155,100,251\
    Colour15\78,159,177\
    Colour14\125,193,207\
    Colour13\243,157,33\
    Colour12\225,170,93\
    Colour11\160,207,93\
    Colour10\184,214,140\
    Colour9\210,61,61\
    Colour8\232,79,79\
    Colour7\64,64,64\
    Colour6\16,16,16\
    Colour5\215,208,199\
    Colour4\255,137,57\
    Colour3\21,21,21\
    Colour2\21,21,21\
    Colour1\255,255,255\
    Colour0\215,208,199\

Copy or rename  your original session file someplace safe, then copy the above lines and paste them into your session
file, replacing the lines that define Colour21 through Colour0.

Close and reopen KiTTY and restart your session.  Voila!  Now aren't those colors better?

No?

Then try some others:

**DarkPastel**

    Colour21\255,255,255\
    Colour20\187,187,187\
    Colour19\85,255,255\
    Colour18\85,255,255\
    Colour17\255,85,255\
    Colour16\255,85,255\
    Colour15\85,85,255\
    Colour14\85,85,255\
    Colour13\255,255,85\
    Colour12\255,255,85\
    Colour11\85,255,85\
    Colour10\85,255,85\
    Colour9\255,85,85\
    Colour8\255,85,85\
    Colour7\85,85,85\
    Colour6\0,0,0\
    Colour5\255,255,255\
    Colour4\187,187,187\
    Colour3\0,0,0\
    Colour2\0,0,0\
    Colour1\255,94,125\
    Colour0\255,255,255\

**Zenburn**

    Colour21\255,255,255\
    Colour20\245,222,179\
    Colour19\255,215,0\
    Colour18\255,160,160\
    Colour17\255,85,255\
    Colour16\255,222,173\
    Colour15\135,206,235\
    Colour14\205,133,63\
    Colour13\255,255,85\
    Colour12\240,230,140\
    Colour11\85,255,85\
    Colour10\152,251,152\
    Colour9\255,85,85\
    Colour8\187,0,0\
    Colour7\85,85,85\
    Colour6\77,77,77\
    Colour5\0,255,0\
    Colour4\0,0,0\
    Colour3\85,85,85\
    Colour2\10,10,10\
    Colour1\255,255,255\
    Colour0\255,255,255\

There are more and of course, you can create your own.


--- 


There you have it.  KiTTY over PuTTY for portability.  Color scheme changes and a host of other features unique to KiTTY
make it my terminal client software of choice when I have to use Windows.


---

## Reference(s):

* [KiTTY Homepage](http://www.9bis.net/kitty/?page=Welcome&zone=en)
* [Color Schemes](http://putty.org.ru/themes/index.html) - The page is in Russian - but you can see the RGB codes for
  each scheme by clicking on them
* [Notepad++](https://notepad-plus-plus.org/download/v6.8.6.html)

