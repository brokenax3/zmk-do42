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

- **Mixed-mode layers:** Layers combine different functional zones per split.
  Layer 2 has symbols on the left and navigation on the right. Layer 3 has
  tmux commands on the left and brackets on the right. This enables hand
  alternation: hold a thumb on one side, operate keys on the other.
- **Cross-layer coherence:** Layer 2 carries non-shifted symbols and operators;
  shifted symbols (`! @ # $ % ^ & * ( )`) live on Layer 3's number row.
  `!` and `%` are intentionally duplicated on Layer 2 (pinky positions) for
  faster access without reaching Layer 3's top row.
- **Hand balance:** Symbol placement follows Colemak's ~47/53 L/R split,
  distributing load evenly between hands.
- **Navigation on Layer 2 right:** Vim-style arrow keys on the home row with
  page/document navigation directly below in matching directional
  correspondence (LEFT→HOME, DOWN→PGDN, UP→PGUP, RIGHT→END). Accessed
  via LEFT thumb hold (mo 2) + RIGHT hand keys.
- **Tmux on Layer 3 left:** All tmux operations (pane navigation, window
  management, splits, zoom, copy mode) via RIGHT thumb hold (mo 3) +
  LEFT hand keys. Pane navigation mirrors arrow positions.
- **Mnemonic combos:** All combos use cross-split key pairs with memorable
  letter hints (e.g., U+D for "UnDerscore", C+O for "COlon").
- **Combo-first for top symbols:** The highest-frequency programming symbols
  are accessible via combos on Layer 0 without any layer hold.

---

## Layer Overview

| Layer | Name     | Access                        | Purpose                                              |
|-------|----------|-------------------------------|------------------------------------------------------|
| 0     | Colemak  | Default                       | Typing with home row mods                            |
| 1     | QWERTY   | Config layer toggle (`&to 1`) | Gaming (no home row mods, no combos)                 |
| 2     | Lower    | Hold `mo 2` (pos 39)         | Numbers + symbols (left), navigation (right)         |
| 3     | Upper    | Hold `mo 3` (pos 40)         | Shifted symbols (top), tmux (left), brackets (right) |
| 4     | Function | Hold `lt 4 RET` (pos 41)     | F-keys, mouse buttons, media                         |
| 5     | Config   | Hold Lower + Upper together   | Bluetooth, base layer switching, power, reset        |

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

## Layer 2: Lower (Numbers + Symbols + Navigation)

Accessed by holding `mo 2` (position 39, LEFT thumb). Numbers on the top row
enable `Super+Number` workspace switching in Aerospace/Hyprland.

**Left split:** Programming symbols. **Right split:** Navigation cluster.
This enables hand alternation: LEFT thumb holds the layer, RIGHT hand navigates.

```
┌───────┬───────┬───────┬───────┬───────┬───────┐    ┌───────┬───────┬───────┬───────┬───────┬───────┐
│  ESC  │   1   │   2   │   3   │   4   │   5   │    │   6   │   7   │   8   │   9   │   0   │ BSPC  │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│  TAB  │   %   │   -   │   =   │   /   │   \   │    │  LEFT │ DOWN  │  UP   │ RIGHT │   :   │   '   │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│ LSHFT │   !   │   _   │   |   │   +   │   "   │    │ HOME  │ PGDN  │ PGUP  │  END  │       │  RET  │
├───────┼───────┼───────┴───────┼───────┼───────┤    ├───────┼───────┼───────┴───────┼───────┼───────┤
│ LGUI  │ LALT  │               │ SPACE │ ▓▓▓▓▓ │    │  mo5  │ SPACE │               │ RALT  │ LCTRL │
└───────┴───────┘               └───────┴───────┘    └───────┴───────┘               └───────┴───────┘
                      D-PAD: Left / Down / (none) / Up / Right
```

### Symbol Placement Rationale (Left Split)

**Home row** (strongest → weakest finger):
- `/` (index) - Division, paths, Vim search
- `=` (middle) - Assignment, comparison — highest frequency operator
- `-` (ring) - Subtraction, lists, kebab-case
- `%` (pinky) - Modulo, Python string formatting, percentage

**Bottom row:**
- `+` (index) - Addition
- `|` (middle) - Unix pipes, logical OR
- `_` (ring) - snake_case, Markdown italics
- `!` (pinky) - Negation, shebang, inequality (`!=`)

### Navigation Cluster (Right Split)

Arrow keys on home row right (Vim-style HJKL positions):

```
HOME ROW:    LEFT   DOWN   UP     RIGHT  :     '
BOTTOM ROW:  HOME   PGDN   PGUP   END
```

Each navigation key sits **directly below** its directional counterpart:
LEFT→HOME, DOWN→PGDN, UP→PGUP, RIGHT→END.

---

## Layer 3: Upper (Shifted Symbols + Tmux + Brackets)

Accessed by holding `mo 3` (position 40, RIGHT thumb). This is the
**mixed-mode layer**: tmux commands on the left, brackets/delimiters on
the right, shifted number symbols on the top row.

Shifted number symbols on the top row double as `Super+Shift+Number` for
moving windows between workspaces.

```
┌───────┬───────┬───────┬───────┬───────┬───────┐    ┌───────┬───────┬───────┬───────┬───────┬───────┐
│   ~   │   !   │   @   │   #   │   $   │   %   │    │   ^   │   &   │   *   │   (   │   )   │  DEL  │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│  TAB  │ T:WIN │ T:S-H │ T:S-V │ T:ZOOM│ T:KILL│    │   (   │   )   │   [   │   ]   │   :   │   ;   │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│ LSHFT │ T:←   │ T:↓   │ T:↑   │ T:→   │ T:COPY│    │   {   │   }   │   <   │   >   │   ?   │  DEL  │
├───────┼───────┼───────┴───────┼───────┼───────┤    ├───────┼───────┼───────┴───────┼───────┼───────┤
│ LGUI  │ LALT  │               │ SPACE │  mo5  │    │ ▓▓▓▓▓ │ SPACE │               │ RALT  │ LCTRL │
└───────┴───────┘               └───────┴───────┘    └───────┴───────┘               └───────┴───────┘
                      D-PAD: (none) / BRI_DN / (none) / BRI_UP / (none)
```

### Tmux Commands (Left Split, prefix: Ctrl+B)

**Home row — Window & pane management:**

| Position | Key | Macro         | Tmux Command | Action              |
|----------|-----|---------------|--------------|----------------------|
| 13       | A   | tmux_new_win  | `Ctrl+B C`   | Create new window    |
| 14       | R   | tmux_split_h  | `Ctrl+B %`   | Split pane horizontal|
| 15       | S   | tmux_split_v  | `Ctrl+B "`   | Split pane vertical  |
| 16       | T   | tmux_zoom     | `Ctrl+B Z`   | Toggle pane zoom     |
| 17       | G   | tmux_kill     | `Ctrl+B X`   | Kill current pane    |

**Bottom row — Pane navigation (mirrors arrow positions):**

| Position | Key | Macro      | Tmux Command   | Action              |
|----------|-----|------------|----------------|----------------------|
| 25       | Z   | tmux_left  | `Ctrl+B Left`  | Navigate left pane   |
| 26       | X   | tmux_down  | `Ctrl+B Down`  | Navigate down pane   |
| 27       | C   | tmux_up    | `Ctrl+B Up`    | Navigate up pane     |
| 28       | D   | tmux_right | `Ctrl+B Right` | Navigate right pane  |
| 29       | V   | tmux_copy  | `Ctrl+B [`     | Enter copy mode      |

**Workflow:** Hold RIGHT thumb (mo 3) → use LEFT hand for tmux operations.

### Bracket Pairs (Right Split)

**Home row right:**
- `( )` (index pair) - Function calls, tuples, precedence
- `[ ]` (middle/ring) - Arrays, indexing, slices
- `:` (pinky) - Dicts, type hints, Vim commands
- `;` (outer pinky) - Statement terminator

**Bottom row right:**
- `{ }` (index pair) - Code blocks, dicts, structs
- `< >` (middle/ring) - Comparisons, generics, HTML
- `?` (pinky) - Ternary, regex, optional

**Bracket pairs** are always adjacent on the same hand for fast inward rolls.

### Additional Tmux Macros (Unbound)

These macros are defined but not mapped to keys. Use `Ctrl+B` manually or
bind them to available positions as needed:

| Macro          | Tmux Command | Action               |
|----------------|--------------|----------------------|
| tmux_prev_win  | `Ctrl+B P`   | Previous window      |
| tmux_next_win  | `Ctrl+B N`   | Next window          |

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
│ OUT_TOG  │ SLCK  │       │       │       │       │    │        │ BT_PRV │ BT_NXT │        │       │          │
├──────────┼───────┼───────┼───────┼───────┼───────┤    ├────────┼────────┼────────┼────────┼───────┼──────────┤
│          │       │       │       │       │       │    │        │        │        │        │       │          │
├──────────┼───────┼───────┴───────┼───────┼───────┤    ├────────┼────────┼────────┴────────┼───────┼──────────┤
│ EP_OFF   │ EP_ON │               │       │       │    │        │        │                 │       │ BT_CLR   │
└──────────┴───────┘               └───────┴───────┘    └────────┴────────┘                 └───────┴──────────┘
                      D-PAD: () / (none) / (none) / (none) / (none)
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

---

## Combos (Layer 0 Only)

All combos are Colemak-only (disabled on QWERTY gaming layer). All combos
use cross-split key pairs with mnemonic letter hints for memorability.

**Timing tiers** based on conflict risk with common English words:
- **Low** (40ms timeout, 150ms idle) — cross-split or rare bigrams
- **Medium** (30ms timeout, 175ms idle) — infrequent same-hand bigrams
- **High** (25ms timeout, 200ms idle) — common word conflicts

### Navigation Combos (Low Conflict)

| Combo     | Keys (Colemak) | Positions | Output | Mnemonic     | Use Case              |
|-----------|----------------|-----------|--------|--------------|-----------------------|
| Escape    | Q + L          | 1 + 7     | `ESC`  | "Quit Left"  | Vim normal mode       |
| Tab       | W + U          | 2 + 8     | `TAB`  | "Window Up"  | Indentation, complete |
| Backspace | F + U          | 3 + 8     | `BSPC` | "Fix Undo"   | Delete backward       |
| Delete    | P + Y          | 4 + 9     | `DEL`  | "Purge Yes"  | Forward delete        |

### High-Frequency Symbol Combos

| Combo      | Keys (Colemak) | Positions | Output | Timing | Mnemonic        | Use Case                 |
|------------|----------------|-----------|--------|--------|-----------------|--------------------------|
| Underscore | U + D          | 8 + 28    | `_`    | Medium | "UnDerscore"    | snake_case variables     |
| Colon      | C + O          | 27 + 22   | `:`    | High   | "COlon"         | Vim command, dicts       |
| Slash      | F + H          | 3 + 31    | `/`    | Low    | "Forward/Hack"  | Vim search, paths        |
| Equals     | E + Q          | 20 + 1    | `=`    | Low    | "EQuals"        | Assignments, comparisons |
| Pipe       | P + I          | 4 + 21    | `\|`   | Low    | "PIPe"          | Unix pipes, logical OR   |

### Multi-Character Operator Combos

| Combo        | Keys (Colemak) | Positions | Output | Timing | Mnemonic         | Use Case                 |
|--------------|----------------|-----------|--------|--------|------------------|--------------------------|
| Arrow        | A + W          | 13 + 2    | `->`   | Medium | "ArroW"          | Golang, Rust, C pointers |
| Double Colon | C + N          | 27 + 19   | `::`   | Low    | "C++ Namespace"  | Rust paths, C++ scope    |
| Walrus       | W + L          | 2 + 7     | `:=`   | Low    | "WaLrus"         | Golang short declaration |

### Special Symbol Combos (Low Conflict)

| Combo     | Keys (Colemak) | Positions | Output | Mnemonic  | Use Case                     |
|-----------|----------------|-----------|--------|-----------|------------------------------|
| Dollar    | D + O          | 28 + 22   | `$`    | "DOllar"  | Shell vars, Terraform, regex |
| Ampersand | A + N          | 13 + 19   | `&`    | "ANd"     | Golang address-of, bitwise   |

---

## Symbol Access Matrix

Quick reference for finding any symbol across layers and combos.

| Symbol | Combo         | Layer 2 | Layer 3     | Best Access        |
|--------|---------------|---------|-------------|--------------------|
| `:`    | C+O           | pos 22  | pos 22      | Combo (instant)    |
| `_`    | U+D           | pos 26  | -           | Combo (instant)    |
| `=`    | E+Q           | pos 15  | -           | Combo (instant)    |
| `/`    | F+H           | pos 16  | -           | Combo (instant)    |
| `\|`   | P+I           | pos 27  | -           | Combo (instant)    |
| `->`   | A+W           | -       | -           | Combo only         |
| `::`   | C+N           | -       | -           | Combo only         |
| `:=`   | W+L           | -       | -           | Combo only         |
| `$`    | D+O           | -       | Shift+4     | Combo (faster)     |
| `&`    | A+N           | -       | Shift+7     | Combo (faster)     |
| `-`    | -             | pos 14  | -           | Layer 2            |
| `\`    | -             | pos 17  | -           | Layer 2            |
| `( )`  | -             | -       | pos 18-19   | Layer 3            |
| `[ ]`  | -             | -       | pos 20-21   | Layer 3            |
| `{ }`  | -             | -       | pos 30-31   | Layer 3            |
| `< >`  | -             | -       | pos 32-33   | Layer 3            |
| `"`    | -             | pos 29  | -           | Layer 2            |
| `'`    | -             | pos 23  | Layer 0     | Layer 0 (pos 23)   |
| `~`    | -             | -       | pos 0       | Layer 3            |
| `+`    | -             | pos 28  | -           | Layer 2            |
| `?`    | -             | -       | pos 34      | Layer 3            |
| `;`    | -             | -       | pos 23      | Layer 3            |
| `@`    | -             | -       | Shift+2     | Layer 3 only       |
| `#`    | -             | -       | Shift+3     | Layer 3 only       |
| `*`    | -             | -       | Shift+8     | Layer 3 only       |
| `!`    | -             | pos 25  | Shift+1     | Layer 2            |
| `%`    | -             | pos 13  | Shift+5     | Layer 2            |
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

**Option B: Layer 2 home row:**
1. Hold `A` to activate LGUI
2. Hold `mo 2` to activate Lower layer
3. Use arrow cluster (LEFT/DOWN/UP/RIGHT) on right home row

---

## Tmux Workflows

All tmux macros send the prefix `Ctrl+B` followed by the tmux command key.
Access via **RIGHT thumb hold** (mo 3) + **LEFT hand** keys.

### Pane Navigation

Hold `mo 3` (RIGHT thumb) and use LEFT bottom row (mirrors arrow layout):

```
BOTTOM ROW:  T:←    T:↓    T:↑    T:→    T:COPY
             (Z)    (X)    (C)    (D)    (V)
```

### Window & Pane Management

Hold `mo 3` (RIGHT thumb) and use LEFT home row:

```
HOME ROW:  T:WIN   T:S-H   T:S-V   T:ZOOM  T:KILL
           (A)     (R)     (S)     (T)     (G)
```

### Common Workflows

| Task                      | Keys                      |
|---------------------------|---------------------------|
| Navigate to left pane     | Hold mo3 + tap Z          |
| Navigate to right pane    | Hold mo3 + tap D          |
| Create new window         | Hold mo3 + tap A          |
| Split pane horizontally   | Hold mo3 + tap R          |
| Split pane vertically     | Hold mo3 + tap S          |
| Toggle zoom current pane  | Hold mo3 + tap T          |
| Kill current pane         | Hold mo3 + tap G          |
| Enter copy mode           | Hold mo3 + tap V          |
| Previous/next window      | Manual: Ctrl+B P / N      |

---

## Behavior Timing

| Behavior              | Parameter              | Value  |
|-----------------------|------------------------|--------|
| Home row mods         | tapping-term-ms        | 180ms  |
| Home row mods         | quick-tap-ms           | 150ms  |
| Home row mods         | require-prior-idle-ms  | 150ms  |
| Layer-tap (`lt`)      | tapping-term-ms        | 140ms  |
| Layer-tap (`lt`)      | require-prior-idle-ms  | 150ms  |
| Combos (low conflict) | timeout-ms             | 40ms   |
| Combos (med conflict) | timeout-ms             | 30ms   |
| Combos (high conflict)| timeout-ms             | 25ms   |
| Combos (low conflict) | require-prior-idle-ms  | 150ms  |
| Combos (med conflict) | require-prior-idle-ms  | 175ms  |
| Combos (high conflict)| require-prior-idle-ms  | 200ms  |
| Macros                | wait-ms / tap-ms       | 10ms   |

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
