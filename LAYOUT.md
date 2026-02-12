# do42 Keyboard Layout Reference

A 42-key split keyboard with 5-button d-pad (49 keys total), running ZMK firmware.
Optimized for **Neovim**, **programming** (Python, Golang, Terraform, Markdown), and
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

## Design Philosophy

- **Cross-layer coherence:** Layer 2 carries only non-shifted symbols; shifted
  symbols (`! @ # $ % ^ & * ( )`) live on Layer 3's number row.
  No symbol appears on both layers unless it serves a different ergonomic role.
- **Hand balance:** Symbol placement follows Colemak's ~47/53 L/R split,
  distributing load evenly between hands.
- **Navigation intent:** Layer 3 is the movement layer. Vim-style arrow keys
  sit on the home row; page/document navigation lives directly below them.
- **Combo-first for top symbols:** The 10 highest-frequency programming
  symbols are accessible via combos on Layer 0 without any layer hold.

---

## Layer Overview

| Layer | Name     | Access                        | Purpose                                       |
|-------|----------|-------------------------------|------------------------------------------------|
| 0     | Colemak  | Default                       | Typing with home row mods                     |
| 1     | QWERTY   | Config layer toggle (`&to 1`) | Gaming (no home row mods, no combos)          |
| 2     | Lower    | Hold `mo 2` (pos 39)         | Numbers, non-shifted programming symbols      |
| 3     | Upper    | Hold `mo 3` (pos 40)         | Shifted symbols, navigation, arrows           |
| 4     | Function | Hold `lt 4 RET` (pos 41)     | F-keys, mouse buttons, media                  |
| 5     | Config   | Hold Lower + Upper together   | Bluetooth, base layer switching, power, reset |

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
│ LCTRL │ LGUI  │               │ SPACE │  mo2  │    │  mo3  │lt4/RET│               │ RALT  │ SLCK  │
└───────┴───────┘               └───────┴───────┘    └───────┴───────┘               └───────┴───────┘
                      D-PAD: Left / Down / (none) / Up / Right
```

### Home Row Mods (Mirrored)

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

## Layer 2: Lower (Numbers + Non-Shifted Symbols)

Accessed by holding `mo 2` (position 39). Numbers on the top row enable
`Super+Number` workspace switching in Aerospace/Hyprland.

Symbols on this layer are those **not** available on Layer 3's shifted number
row. No cross-layer duplication.

```
┌───────┬───────┬───────┬───────┬───────┬───────┐    ┌───────┬───────┬───────┬───────┬───────┬───────┐
│  ESC  │   1   │   2   │   3   │   4   │   5   │    │   6   │   7   │   8   │   9   │   0   │ BSPC  │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│  TAB  │   `   │   -   │   =   │   /   │   \   │    │   (   │   )   │   [   │   ]   │   :   │   ;   │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│ LSHFT │   ~   │   _   │   |   │   +   │   "   │    │   {   │   }   │   <   │   >   │   ?   │  DEL  │
├───────┼───────┼───────┴───────┼───────┼───────┤    ├───────┼───────┼───────┴───────┼───────┼───────┤
│ LGUI  │ LALT  │               │ SPACE │ ▓▓▓▓▓ │    │  mo5  │ SPACE │               │ RALT  │ LCTRL │
└───────┴───────┘               └───────┴───────┘    └───────┴───────┘               └───────┴───────┘
                      D-PAD: Left / Down / (none) / Up / Right
```

### Symbol Placement Rationale

**Home row left** (strongest → weakest finger):
- `/` (index) - Division, paths, Vim search
- `=` (middle) - Assignment, comparison — highest frequency operator
- `-` (ring) - Subtraction, lists, kebab-case
- `` ` `` (pinky) - Backtick: Markdown code, Golang raw strings, shell

**Home row right** (strongest → weakest finger):
- `( )` (index pair) - Function calls, tuples, precedence
- `[ ]` (middle/ring) - Arrays, indexing, slices
- `:` (pinky) - Dicts, type hints, Vim commands
- `;` (outer pinky) - Statement terminator

**Bottom row left:**
- `+` (index) - Addition
- `|` (middle) - Unix pipes, logical OR
- `_` (ring) - snake_case, Markdown italics
- `~` (pinky) - Home directory, bitwise NOT

**Bottom row right:**
- `{ }` (index pair) - Code blocks, dicts, structs
- `< >` (middle/ring) - Comparisons, generics, HTML
- `?` (pinky) - Ternary, regex, optional

**Bracket pairs** are always adjacent on the same hand for fast inward rolls.

---

## Layer 3: Upper (Shifted Symbols + Navigation + Arrows)

Accessed by holding `mo 3` (position 40). This is the **movement layer**.

Shifted number symbols on the top row double as `Super+Shift+Number` for
moving windows between workspaces.

```
┌───────┬───────┬───────┬───────┬───────┬───────┐    ┌───────┬───────┬───────┬───────┬───────┬───────┐
│   ~   │   !   │   @   │   #   │   $   │   %   │    │   ^   │   &   │   *   │   (   │   )   │  DEL  │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│  TAB  │   "   │   '   │   `   │   |   │   \   │    │  LEFT │ DOWN  │  UP   │ RIGHT │   :   │       │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│ LSHFT │       │       │       │       │       │    │       │ PGDN  │ PGUP  │ HOME  │  END  │  RET  │
├───────┼───────┼───────┴───────┼───────┼───────┤    ├───────┼───────┼───────┴───────┼───────┼───────┤
│ LGUI  │ LALT  │               │ SPACE │  mo5  │    │ ▓▓▓▓▓ │ SPACE │               │ RALT  │ LCTRL │
└───────┴───────┘               └───────┴───────┘    └───────┴───────┘               └───────┴───────┘
                      D-PAD: (none) / BRI_DN / (none) / BRI_UP / (none)
```

### Navigation Cluster

Arrow keys on home row right (Vim-style HJKL positions):

```
HOME ROW:           LEFT   DOWN   UP     RIGHT
BOTTOM ROW:                PGDN   PGUP   HOME   END
```

Page navigation sits **directly below** the arrow keys for logical spatial
grouping: DOWN→PGDN, UP→PGUP, with HOME/END to the right.

### String Delimiters

Home row left side groups all quote types: `"` `'` `` ` `` (double, single, backtick)

---

## Layer 4: Function (F-Keys + Mouse + Media)

Accessed by holding `lt 4 RET` (position 41). Tap for Enter, hold for layer.

```
┌───────┬───────┬───────┬───────┬───────┬───────┐    ┌───────┬───────┬───────┬───────┬───────┬───────┐
│  ESC  │  F1   │  F2   │  F3   │  F4   │  F5   │    │  F6   │  F7   │  F8   │  F9   │  F10  │  DEL  │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│  TAB  │  F11  │  F12  │       │       │       │    │  MB4  │  MB1  │  MB3  │  MB2  │  MB5  │       │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│ LSHFT │       │       │       │       │       │    │       │       │       │       │       │       │
├───────┼───────┼───────┴───────┼───────┼───────┤    ├───────┼───────┼───────┴───────┼───────┼───────┤
│ LCTRL │ LGUI  │               │       │       │    │       │ ▓▓▓▓▓ │               │ RALT  │ SLCK  │
└───────┴───────┘               └───────┴───────┘    └───────┴───────┘               └───────┴───────┘
                      D-PAD: Home / ScrollDn / (none) / ScrollUp / End
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
Default timeout: 45ms. Require prior idle: 150ms.

### Navigation Combos

| Combo     | Keys (Colemak) | Positions | Output   | Use Case                    |
|-----------|----------------|-----------|----------|-----------------------------|
| Escape    | Q + W          | 1 + 2     | `ESC`    | Vim normal mode             |
| Tab       | W + F          | 2 + 3     | `TAB`    | Indentation, completion     |
| Delete    | L + U          | 7 + 8     | `DEL`    | Forward delete              |
| Backspace | Y + ;          | 9 + 10    | `BSPC`   | Delete backward             |
| Caps Word | Space + lt4    | 38 + 41   | CapsWord | SCREAMING_SNAKE_CASE (50ms) |

### High-Frequency Symbol Combos

| Combo      | Keys (Colemak) | Positions | Output | Use Case                         |
|------------|----------------|-----------|--------|----------------------------------|
| Colon      | S + T          | 15 + 16   | `:`    | Vim command mode                 |
| Slash      | T + G          | 16 + 17   | `/`    | Vim search, paths, division      |
| Underscore | N + E          | 19 + 20   | `_`    | snake_case variables             |
| Equals     | E + I          | 20 + 21   | `=`    | Assignments, comparisons         |
| Pipe       | D + V          | 28 + 29   | `\|`   | Unix pipes, logical OR           |

### Multi-Character Operator Combos

| Combo        | Keys (Colemak) | Positions   | Output | Use Case                      |
|--------------|----------------|-------------|--------|-------------------------------|
| Arrow        | I + O          | 21 + 22     | `->`   | Golang, Rust, C pointers      |
| Double Colon | O + '          | 22 + 23     | `::`   | Rust paths, C++ namespaces    |
| Walrus       | S + T + G      | 15 + 16 + 17 | `:=` | Golang short declaration (50ms) |

### Special Symbol Combos

| Combo     | Keys (Colemak) | Positions | Output | Use Case                          |
|-----------|----------------|-----------|--------|-----------------------------------|
| Dollar    | A + R          | 13 + 14   | `$`    | Shell vars, Terraform, regex      |
| Ampersand | H + ,          | 31 + 32   | `&`    | Golang address-of, bitwise AND    |

---

## Symbol Access Matrix

Quick reference for finding any symbol across layers and combos.

| Symbol | Combo         | Layer 2 | Layer 3     | Best Access        |
|--------|---------------|---------|-------------|--------------------|
| `:`    | S+T           | pos 22  | pos 22      | Combo (instant)    |
| `_`    | N+E           | pos 26  | -           | Combo (instant)    |
| `=`    | E+I           | pos 15  | -           | Combo (instant)    |
| `/`    | T+G           | pos 16  | -           | Combo (instant)    |
| `\|`   | D+V           | pos 27  | pos 16      | Combo (instant)    |
| `->`   | I+O           | -       | -           | Combo only         |
| `::`   | O+'           | -       | -           | Combo only         |
| `:=`   | S+T+G         | -       | -           | Combo only         |
| `$`    | A+R           | -       | Shift+4     | Combo (faster)     |
| `&`    | H+,           | -       | Shift+7     | Combo (faster)     |
| `-`    | -             | pos 14  | -           | Layer 2            |
| `` ` ``| -             | pos 13  | pos 15      | Layer 2            |
| `\`    | -             | pos 17  | pos 17      | Layer 2            |
| `( )`  | -             | pos 18-19 | Shift+9-0 | Layer 2            |
| `[ ]`  | -             | pos 20-21 | -         | Layer 2            |
| `{ }`  | -             | pos 30-31 | -         | Layer 2            |
| `< >`  | -             | pos 32-33 | -         | Layer 2            |
| `"`    | -             | pos 29  | pos 13      | Layer 2/3          |
| `'`    | -             | -       | pos 14      | Layer 3            |
| `~`    | -             | pos 25  | Shift+`     | Layer 2            |
| `+`    | -             | pos 28  | -           | Layer 2            |
| `?`    | -             | pos 34  | -           | Layer 2            |
| `;`    | -             | pos 23  | -           | Layer 2            |
| `@`    | -             | -       | Shift+2     | Layer 3 only       |
| `#`    | -             | -       | Shift+3     | Layer 3 only       |
| `*`    | -             | -       | Shift+8     | Layer 3 only       |
| `!`    | -             | -       | Shift+1     | Layer 3 only       |
| `%`    | -             | -       | Shift+5     | Layer 3 only       |
| `^`    | -             | -       | Shift+6     | Layer 3 only       |

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

**Option A: D-pad (base layer, no layer hold):**
1. Hold `A` to activate LGUI
2. Use d-pad arrows directly on Layer 0

**Option B: Vim-style (Layer 3 home row):**
1. Hold `A` to activate LGUI
2. Hold `mo 3` to activate Upper layer
3. Use arrow cluster at HJKL positions (LEFT/DOWN/UP/RIGHT)

---

## Behavior Timing

| Behavior        | Parameter              | Value  |
|-----------------|------------------------|--------|
| Home row mods   | tapping-term-ms        | 180ms  |
| Home row mods   | quick-tap-ms           | 150ms  |
| Home row mods   | require-prior-idle-ms  | 150ms  |
| Layer-tap (`lt`) | tapping-term-ms       | 140ms  |
| Layer-tap (`lt`) | require-prior-idle-ms | 150ms  |
| Combos (2-key)  | timeout-ms             | 45ms   |
| Combos (3-key)  | timeout-ms             | 50ms   |
| Combos          | require-prior-idle-ms  | 150ms  |
| Macros          | wait-ms / tap-ms       | 10ms   |

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
