# do42 Keyboard Layout Reference

A 42-key split keyboard with 5-button d-pad (49 keys total), running ZMK firmware.
Optimized for **Neovim**, **programming** (Python, Rust, C, JavaScript), and
**tiling window managers** (Aerospace on macOS, Hyprland on Linux).

## Physical Layout

```
LEFT HALF                                   RIGHT HALF
┌────┬────┬────┬────┬────┬────┐             ┌────┬────┬────┬────┬────┬────┐
│  0 │  1 │  2 │  3 │  4 │  5 │             │  6 │  7 │  8 │  9 │ 10 │ 11 │
├────┼────┼────┼────┼────┼────┤             ├────┼────┼────┼────┼────┼────┤
│ 12 │ 13 │ 14 │ 15 │ 16 │ 17 │             │ 18 │ 19 │ 20 │ 21 │ 22 │ 23 │
├────┼────┼────┼────┼────┼────┤             ├────┼────┼────┼────┼────┼────┤
│ 24 │ 25 │ 26 │ 27 │ 28 │ 29 │             │ 30 │ 31 │ 32 │ 33 │ 34 │ 35 │
├────┼────┼────┴────┼────┼────┤             ├────┼────┼────┴────┼────┼────┤
│ 36 │ 37 │         │ 38 │ 39 │             │ 40 │ 41 │         │ 42 │ 43 │
└────┴────┘         └────┴────┘             └────┴────┘         └────┴────┘
                         ┌────┐
                    DPAD │ 44 │ Left
                    ┌────┼────┼────┐
               Down │ 45 │ 46 │ 47 │ Up
                    └────┼────┼────┘
                  Right  │ 48 │
                         └────┘
```

---

## Layer Overview

| Layer | Name     | Access                        | Purpose                                        |
|-------|----------|-------------------------------|-------------------------------------------------|
| 0     | Colemak  | Default                       | Typing with home row mods                      |
| 1     | QWERTY   | Config layer toggle (`&to 1`) | Gaming (no home row mods, no combos)           |
| 2     | Lower    | Hold `mo 2` (pos 39)         | Numbers, programming symbols, window mgmt      |
| 3     | Upper    | Hold `mo 3` (pos 40)         | Shifted symbols, navigation, F-keys            |
| 4     | Function | Hold `lt 4 RET` (pos 41)     | F-keys, mouse buttons                          |
| 5     | Config   | Hold Lower + Upper together   | Bluetooth, base layer switching, power, reset  |

---

## Layer 0: Colemak (Default)

Base typing layer with home row mods (balanced flavor).

```
┌───────┬───────┬───────┬───────┬───────┬───────┐    ┌───────┬───────┬───────┬───────┬───────┬───────┐
│  ESC  │   Q   │   W   │   F   │   P   │   B   │    │   J   │   L   │   U   │   Y   │   ;   │ BSPC  │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│  TAB  │ A/GUI │ R/ALT │S/CTRL │T/SHFT │   G   │    │   M   │N/SHFT │E/CTRL │ I/ALT │ O/GUI │   '   │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│ LSHFT │   Z   │   X   │   C   │   D   │   V   │    │   K   │   H   │   ,   │   .   │   /   │  RET  │
├───────┼───────┼───────┴───────┼───────┼───────┤    ├───────┼───────┼───────┴───────┼───────┼───────┤
│ LCTRL │ LGUI  │               │ SPACE │  mo2  │    │  mo3  │lt4/RET│               │ LALT  │ SLCK  │
└───────┴───────┘               └───────┴───────┘    └───────┴───────┘               └───────┴───────┘
                      D-PAD: Home / ScrollDn / Mute / ScrollUp / End
```

### Home Row Mods

| Position | Tap | Hold   | Hand  |
|----------|-----|--------|-------|
| 13       | A   | LGUI   | Left  |
| 14       | R   | LALT   | Left  |
| 15       | S   | LCTRL  | Left  |
| 16       | T   | LSHFT  | Left  |
| 19       | N   | RSHFT  | Right |
| 20       | E   | RCTRL  | Right |
| 21       | I   | LALT   | Right |
| 22       | O   | RGUI   | Right |

**Timing:** `tapping-term-ms=180`, `quick-tap-ms=150`, `require-prior-idle-ms=150`

---

## Layer 1: QWERTY (Gaming)

Standard QWERTY without home row mods or combos. Switched to via Config layer.

```
┌───────┬───────┬───────┬───────┬───────┬───────┐    ┌───────┬───────┬───────┬───────┬───────┬───────┐
│  ESC  │   Q   │   W   │   E   │   R   │   T   │    │   Y   │   U   │   I   │   O   │   P   │ BSPC  │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│  TAB  │   A   │   S   │   D   │   F   │   G   │    │   H   │   J   │   K   │   L   │   ;   │   '   │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│ LSHFT │   Z   │   X   │   C   │   V   │   B   │    │   N   │   M   │   ,   │   .   │   /   │  ESC  │
├───────┼───────┼───────┴───────┼───────┼───────┤    ├───────┼───────┼───────┴───────┼───────┼───────┤
│ LCTRL │ LGUI  │               │ SPACE │  mo2  │    │  mo3  │lt4/RET│               │ LALT  │ SLCK  │
└───────┴───────┘               └───────┴───────┘    └───────┴───────┘               └───────┴───────┘
                      D-PAD: Left / Down / (none) / Up / Right
```

---

## Layer 2: Lower (Numbers + Symbols + Window Management)

Accessed by holding `mo 2` (position 39). Numbers on the top row enable
`Super+Number` workspace switching in Aerospace/Hyprland.

```
┌───────┬───────┬───────┬───────┬───────┬───────┐    ┌───────┬───────┬───────┬───────┬───────┬───────┐
│  ESC  │   1   │   2   │   3   │   4   │   5   │    │   6   │   7   │   8   │   9   │   0   │ BSPC  │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│  TAB  │   -   │   *   │   =   │   _   │   |   │    │   (   │   )   │   [   │   ]   │   :   │   ;   │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│ LSHFT │   &   │   /   │   \   │   +   │   ~   │    │   {   │   }   │   <   │   >   │   ?   │  DEL  │
├───────┼───────┼───────┴───────┼───────┼───────┤    ├───────┼───────┼───────┴───────┼───────┼───────┤
│ LGUI  │ LALT  │               │ SPACE │ ▓▓▓▓▓ │    │  mo5  │ SPACE │               │ RALT  │ LCTRL │
└───────┴───────┘               └───────┴───────┘    └───────┴───────┘               └───────┴───────┘
                      D-PAD: Left / Down / (none) / Up / Right
```

### Symbol Placement Rationale

- **Home row:** Highest-frequency programming symbols (`- * = _ | ( ) [ ] : ;`)
- **Bottom row:** Operators and enclosures (`& / \ + ~ { } < > ?`)
- **Brackets paired:** `()` adjacent, `[]` adjacent, `{}` adjacent, `<>` adjacent
- **D-pad arrows:** Enable `Super+Arrow` window navigation in tiling WMs

---

## Layer 3: Upper (Shifted Symbols + Navigation + F-Keys)

Accessed by holding `mo 3` (position 40). Shifted number symbols on top row
double as `Super+Shift+Number` for moving windows between workspaces.

```
┌───────┬───────┬───────┬───────┬───────┬───────┐    ┌───────┬───────┬───────┬───────┬───────┬───────┐
│   ~   │   !   │   @   │   #   │   $   │   %   │    │   ^   │   &   │   *   │   (   │   )   │  DEL  │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│  TAB  │   "   │   '   │   `   │   |   │   \   │    │ HOME  │ PGDN  │ PGUP  │  END  │   :   │       │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│ LSHFT │  F1   │  F2   │  F3   │  F4   │  F5   │    │  F6   │  F7   │  F8   │  F9   │  F10  │  RET  │
├───────┼───────┼───────┴───────┼───────┼───────┤    ├───────┼───────┼───────┴───────┼───────┼───────┤
│ LGUI  │ LALT  │               │ SPACE │  mo5  │    │ ▓▓▓▓▓ │  F11  │               │  F12  │ LCTRL │
└───────┴───────┘               └───────┴───────┘    └───────┴───────┘               └───────┴───────┘
                      D-PAD: (none) / BRI_DN / (none) / BRI_UP / (none)
```

### Navigation Cluster

Home row right side provides Vim-friendly navigation: `HOME PGDN PGUP END`

### String Delimiters

Home row left side groups all quote types: `" ' `` (double, single, backtick)

---

## Layer 4: Function (F-Keys + Mouse)

Accessed by holding `lt 4 RET` (position 41). Tap for Enter, hold for layer.

```
┌───────┬───────┬───────┬───────┬───────┬───────┐    ┌───────┬───────┬───────┬───────┬───────┬───────┐
│  ESC  │  F1   │  F2   │  F3   │  F4   │  F5   │    │  F6   │  F7   │  F8   │  F9   │  F10  │  DEL  │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│  TAB  │  F11  │  F12  │       │       │       │    │  MB4  │  MB1  │  MB3  │  MB2  │  MB5  │       │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│ LSHFT │       │       │       │       │       │    │       │       │       │       │       │       │
├───────┼───────┼───────┴───────┼───────┼───────┤    ├───────┼───────┼───────┴───────┼───────┼───────┤
│ LCTRL │ LGUI  │               │       │       │    │       │ ▓▓▓▓▓ │               │ LALT  │ SLCK  │
└───────┴───────┘               └───────┴───────┘    └───────┴───────┘               └───────┴───────┘
                      D-PAD: (none) / (none) / (none) / (none) / (none)
```

### Mouse Buttons

| Key  | Action       |
|------|-------------|
| MB1  | Left click   |
| MB2  | Right click  |
| MB3  | Middle click |
| MB4  | Back         |
| MB5  | Forward      |

---

## Layer 5: Config (Bluetooth + System)

Accessed by holding **both** `mo 2` and `mo 3` simultaneously (tri-layer).

```
┌──────────┬───────┬───────┬───────┬───────┬───────┐    ┌────────┬────────┬────────┬────────┬───────┬──────────┐
│BOOTLOADER│ to(0) │ to(1) │       │       │       │    │ BT_0   │ BT_1   │ BT_2   │ BT_3   │       │ SYS_RST  │
├──────────┼───────┼───────┼───────┼───────┼───────┤    ├────────┼────────┼────────┼────────┼───────┼──────────┤
│ OUT_TOG  │ SLCK  │       │       │       │STUDIO │    │ STUDIO │ BT_PRV │ BT_NXT │        │       │          │
├──────────┼───────┼───────┼───────┼───────┼───────┤    ├────────┼────────┼────────┼────────┼───────┼──────────┤
│          │       │       │       │       │       │    │        │        │        │        │       │          │
├──────────┼───────┼───────┴───────┼───────┼───────┤    ├────────┼────────┼────────┴────────┼───────┼──────────┤
│ EP_OFF   │ EP_ON │               │       │       │    │        │        │                 │       │ BT_CLR   │
└──────────┴───────┘               └───────┴───────┘    └────────┴────────┘                 └───────┴──────────┘
                      D-PAD: (none) / (none) / (none) / (none) / (none)
```

| Key         | Action                                     |
|-------------|--------------------------------------------|
| BOOTLOADER  | Enter bootloader mode for flashing          |
| SYS_RST     | System reset                               |
| to(0)       | Switch base layer to Colemak                |
| to(1)       | Switch base layer to QWERTY (gaming)        |
| OUT_TOG     | Toggle USB / BLE output                    |
| BT_0..3     | Select Bluetooth profile                   |
| BT_PRV/NXT  | Cycle Bluetooth profiles                   |
| BT_CLR      | Clear current Bluetooth profile             |
| EP_OFF/ON   | External power off/on                      |
| STUDIO      | ZMK Studio unlock                          |

---

## Combos (Layer 0 Only)

All combos are Colemak-only (disabled on QWERTY gaming layer).
Timeout: 45ms. Require prior idle: 150ms.

| Combo           | Keys (Colemak) | Positions | Output   | Use Case                       |
|-----------------|----------------|-----------|----------|--------------------------------|
| Escape          | Q + W          | 1 + 2     | `ESC`    | Vim normal mode                |
| Tab             | W + F          | 2 + 3     | `TAB`    | Indentation, completion        |
| Delete          | L + U          | 7 + 8     | `DEL`    | Forward delete                 |
| Backspace       | Y + ;          | 9 + 10    | `BSPC`   | Delete backward                |
| Caps Word       | Space + lt4    | 38 + 41   | CapsWord | SCREAMING_SNAKE_CASE (50ms)    |
| Colon           | S + T          | 15 + 16   | `:`      | Vim command mode               |
| Slash           | T + G          | 16 + 17   | `/`      | Vim search, paths, division    |
| Underscore      | N + E          | 19 + 20   | `_`      | snake_case variables           |
| Equals          | E + I          | 20 + 21   | `=`      | Assignments, comparisons       |
| Pipe            | D + V          | 28 + 29   | `\|`     | Unix pipes, logical OR         |

---

## Window Management Workflows

### Workspace Switching (Super + Number)

Hold `LGUI` (home row mod on `A`) + Layer 2 numbers:

1. Hold `A` to activate LGUI
2. Hold `mo 2` to activate Lower layer
3. Tap `1`-`0` for workspace 1-10

### Moving Windows (Super + Shift + Number)

Layer 3 top row has shifted number symbols (`! @ # $ %` etc.), which are
`Shift + Number`. Combined with LGUI home row mod:

1. Hold `A` to activate LGUI
2. Hold `mo 3` to activate Upper layer
3. Tap `!`-`)` which sends Shift+Number = Super+Shift+Number

### Window Navigation (Super + Arrow)

Layer 2 d-pad provides arrow keys. Combined with LGUI:

1. Hold `A` to activate LGUI
2. Hold `mo 2` to activate Lower layer
3. Use d-pad arrows for Super+Left/Down/Up/Right

---

## Behavior Timing

| Behavior        | Parameter              | Value  |
|-----------------|------------------------|--------|
| Home row mods   | tapping-term-ms        | 180ms  |
| Home row mods   | quick-tap-ms           | 150ms  |
| Home row mods   | require-prior-idle-ms  | 150ms  |
| Layer-tap (`lt`) | tapping-term-ms       | 140ms  |
| Layer-tap (`lt`) | require-prior-idle-ms | 150ms  |
| Combos          | timeout-ms             | 45ms   |
| Combos          | require-prior-idle-ms  | 150ms  |
| Caps Word combo | timeout-ms             | 50ms   |

---

## Power Management

| Setting                  | Value    | Description              |
|--------------------------|----------|--------------------------|
| Idle timeout             | 30,000ms | 30 seconds to idle       |
| Deep sleep timeout       | 900,000ms| 15 minutes to sleep      |
| BLE TX power             | +8 dBm  | Maximum range            |
| External power           | Enabled  | Controllable via Config  |
| Display                  | Disabled |                          |
| Backlight                | Disabled |                          |
