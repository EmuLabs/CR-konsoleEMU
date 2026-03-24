# KonsoleEMU

KonsoleEMU is a customized Konsole fork focused on pane workflows, keyboard ergonomics, and split-view quality-of-life improvements.

## Features Added In This Project

### Pane creation and layout
- Split with explicit placement for the new pane:
  - `Split View Left/Right (New Pane on Left)`
  - `Split View Top/Bottom (New Pane Above)`
- Original split actions remain available (new pane on right / below).

### Pane resizing (axis-based)
- Added independent resize actions so size changes can target a fixed screen axis regardless of nested split orientation:
  - `Expand View (Height)`
  - `Shrink View (Height)`
  - `Expand View (Width)`
  - `Shrink View (Width)`
- These actions are intentionally registered without default shortcuts so you can bind them in `Settings -> Configure Keyboard Shortcuts`.

### Pane detaching improvements
- Added a pane-header detach button (`tab-detach`) to detach the current pane into a new window.
- Added drag-to-detach: drag a pane titlebar outside the KonsoleEMU window and release to detach.

### Pane drag-and-drop improvements
- Added direct pane swap by dropping one pane titlebar onto the center of another pane.
- Swap works both within one window and across KonsoleEMU windows in the same process.
- Existing edge-drop behavior (insert/split by edge) is preserved.

### Selection mode enhancements
- Improved Konsole selection mode behavior for more mobile-friendly interaction and smoother pane-centric workflows.

## Build and Install

### 1) Configure

```sh
cmake -S /home/q/git/CR-konsoleEMU \
  -B /home/q/git/CR-konsoleEMU/build-local \
  -DCMAKE_BUILD_TYPE=Release \
  -DCMAKE_INSTALL_PREFIX=$HOME/.local
```

### 2) Build

```sh
cmake --build /home/q/git/CR-konsoleEMU/build-local -j
```

### 3) Install

```sh
cmake --install /home/q/git/CR-konsoleEMU/build-local
```

### 4) Run

```sh
source /home/q/git/CR-konsoleEMU/build-local/prefix.sh
$HOME/.local/bin/konsole
```

## Update Cycle

Rebuild and reinstall after changes:

```sh
cmake --build /home/q/git/CR-konsoleEMU/build-local -j
cmake --install /home/q/git/CR-konsoleEMU/build-local
```

## Notes

- Custom actions can be rebound from `Settings -> Configure Keyboard Shortcuts`.
- This local install path (`$HOME/.local`) allows KonsoleEMU to coexist with system Konsole.

