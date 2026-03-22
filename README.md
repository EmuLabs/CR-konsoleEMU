# Konsole - KDE's Terminal Emulator

Konsole is a terminal program for KDE.

As well as being a standalone program, it is also used by other KDE programs
such as the Kate editor and KDevelop development environment to provide easy
access to a terminal window. Konsole's features and usage are explained and
illustrated in the Konsole handbook, which can be accessed by browsing to
`help:/konsole` in Konqueror.


## Directory Structure

| Directory          | Description                                                                                                                                                                        |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/doc/user`        | README files, primarily for advanced users, explaining various aspects of Konsole such as fonts and keyboard handling in-depth.                                                    |
| `/doc/developer`   | README files and resources for developers of Konsole. This includes information on the design of Konsole's internals and the VT100 terminal on which Konsole's emulation is based. |
| `/src`             | Source code for Konsole, including the embedded versions of Konsole which are used in Kate, KDevelop and others.                                                                   |
| `/desktop`         | .desktop files for Konsole, used to launch the program from KDE's various menus and other application launchers.                                                                   |
| `/data`            | Data files for use with Konsole as well as the keyboard setup and color schemes provided with Konsole.                                                                             |

## Contact

Up-to-date information about the latest releases can be found on Konsole's
website at https://konsole.kde.org. Discussions about Konsole's development are
held on the konsole-devel mailing list, which can be accessed at
https://mail.kde.org/mailman/listinfo/konsole-devel.

## Quick Links
- [KDE Release Schedule](https://community.kde.org/Schedules)
- [Official Homepage](https://konsole.kde.org)
- [Builds](https://invent.kde.org/utilities/konsole/-/pipelines)
- [Forums](https://discuss.kde.org/tag/konsole)
- [Konsole Bug Reports ](https://bugs.kde.org/describecomponents.cgi?product=konsole)

## Local Build and Install (KonsoleEMU)

The commands below build Konsole from source and install it under `~/.local`
so it can coexist with your system Konsole package.

1. Configure with a dedicated build directory and local install prefix:

```sh
cmake -S /home/q/git/CR-konsoleEMU \
  -B /home/q/git/CR-konsoleEMU/build-local \
  -DCMAKE_BUILD_TYPE=Debug \
  -DCMAKE_INSTALL_PREFIX=$HOME/.local
```

2. Build:

```sh
cmake --build /home/q/git/CR-konsoleEMU/build-local -j
```

3. Install:

```sh
cmake --install /home/q/git/CR-konsoleEMU/build-local
```

4. Run the locally installed build:

```sh
source /home/q/git/CR-konsoleEMU/build-local/prefix.sh
$HOME/.local/bin/konsole
```

### Optional: launcher alias `konsoleemu`

To distinguish the patched build from system Konsole, create a wrapper script
named `konsoleemu` in `~/.local/bin` that launches `$HOME/.local/bin/konsole`.
This lets you run the custom build with:

```sh
konsoleemu
```

### Rebuild after source changes

```sh
cmake --build /home/q/git/CR-konsoleEMU/build-local -j
cmake --install /home/q/git/CR-konsoleEMU/build-local
```

### KonsoleEMU: split with new pane on the left

Standard Konsole splits horizontally with the **new** terminal to the **right** of the
focused one. This fork adds **Split View Left/Right (New Pane on Left)**:

- Menu: **View → Split View → Split View Left/Right (New Pane on Left)**
- Default shortcut: **Ctrl+Shift+[**

The original **Split View Left/Right** (new pane on the right) remains unchanged
(default shortcut: **Ctrl+(**).

Similarly, **Split View Top/Bottom (New Pane Above)** puts the new terminal **above**
the focused one:

- Menu: **View → Split View → Split View Top/Bottom (New Pane Above)**
- Default shortcut: **Ctrl+Shift+]**

The original **Split View Top/Bottom** (new pane below) is unchanged
(default shortcut: **Ctrl+)**).

