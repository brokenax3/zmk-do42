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
  the tmux prefix on the left and brackets on the right. This enables hand
  alternation: hold a thumb on one side, operate keys on the other.
- **Cross-layer coherence:** Layer 2 carries non-shifted symbols and operators;
  shifted symbols (`! @ # $ % ^ & * ( )`) live on Layer 3's number row.
- **Hand balance:** Symbol placement distributes load evenly between hands.
- **Navigation on Layer 2 right:** Vim-style arrow keys on the home row with
  page/document navigation directly below in matching directional
  correspondence (LEFT→HOME, DOWN→PGDN, UP→PGUP, RIGHT→END). Accessed
  via LEFT thumb hold (mo 2) + RIGHT hand keys.
- **Tmux on Layer 3 left:** Tmux prefix macro accessible via RIGHT thumb hold
  (mo 3) + LEFT hand key (T). After sending the prefix, you can use any
  standard tmux command.
- **Minimal combos:** Currently only one combo (S+E for ESC) to avoid
  accidental triggers during normal typing. Additional combos can be added
  based on actual usage patterns.

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
Includes SOCD (Simultaneous Opposite Cardinal Direction) cleaning for WASD to
prevent invalid diagonal inputs in games.

```
┌───────┬───────┬───────┬───────┬───────┬───────┐    ┌───────┬───────┬───────┬───────┬───────┬───────┐
│  ESC  │   Q   │ W/SOCD│   E   │   R   │   T   │    │   Y   │   U   │   I   │   O   │   P   │ BSPC  │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│  TAB  │A/SOCD │ S/SOCD│D/SOCD │   F   │   G   │    │   H   │   J   │   K   │   L   │   ;   │   '   │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│ LSHFT │   Z   │   X   │   C   │   V   │   B   │    │   N   │   M   │   ,   │   .   │   /   │  ESC  │
├───────┼───────┼───────┴───────┼───────┼───────┤    ├───────┼───────┼───────┴───────┼───────┼───────┤
│ LCTRL │ LGUI  │               │ SPACE │  mo2  │    │  mo3  │lt4/RET│               │ LALT  │ SLCK  │
└───────┴───────┘               └───────┴───────┘    └───────┴───────┘               └───────┴───────┘
                      D-PAD: Left / Down / (none) / Up / Right
```

**SOCD Cleaning:** WASD keys use SOCD resolution to handle simultaneous opposite
inputs (W+S or A+D). This prevents invalid diagonal movement in games that don't
handle such inputs properly.

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
│  TAB  │       │   ~   │   _   │   -   │   |   │    │  LEFT │ DOWN  │  UP   │ RIGHT │   :   │   '   │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│ LSHFT │       │   `   │   =   │   +   │   "   │    │ HOME  │ PGDN  │ PGUP  │  END  │       │  RET  │
├───────┼───────┼───────┴───────┼───────┼───────┤    ├───────┼───────┼───────┴───────┼───────┼───────┤
│ LGUI  │ LALT  │               │ SPACE │ ▓▓▓▓▓ │    │  mo5  │ SPACE │               │ RALT  │ LCTRL │
└───────┴───────┘               └───────┴───────┘    └───────┴───────┘               └───────┴───────┘
                      D-PAD: C_PREV / C_VOL_DN / C_PP / C_VOL_UP / C_NEXT
```

### Symbol Placement Rationale (Left Split)

**Home row** (strongest → weakest finger):
- `|` (ring) - Unix pipes, logical OR
- `_` (middle) - snake_case, Markdown italics
- `~` (ring) - Home directory, bitwise NOT
- (empty pinky position)

**Bottom row:**
- `"` (index) - String literals
- `+` (index) - Addition
- `=` (middle) - Assignment, comparison — highest frequency operator
- `` ` `` (ring) - Backticks, code blocks, command substitution
- (empty pinky position)

### Navigation Cluster (Right Split)

Arrow keys on home row right (Vim-style HJKL positions):

```
HOME ROW:    LEFT   DOWN   UP     RIGHT  :     '
BOTTOM ROW:  HOME   PGDN   PGUP   END
```

Each navigation key sits **directly below** its directional counterpart:
LEFT→HOME, DOWN→PGDN, UP→PGUP, RIGHT→END.

### Media Controls (D-Pad)

The d-pad provides media controls while on Layer 2:

```
D-PAD Layout:  C_PREV / C_VOL_DN / C_PP / C_VOL_UP / C_NEXT
               (Prev) / (Vol-)   / (Play)/ (Vol+)   / (Next)
```

- **Left (44):** Previous track
- **Down (45):** Volume down
- **Center (46):** Play/Pause
- **Up (47):** Volume up
- **Right (48):** Next track

---

## Layer 3: Upper (Shifted Symbols + Tmux + Brackets)

Accessed by holding `mo 3` (position 40, RIGHT thumb). This is the
**mixed-mode layer**: tmux prefix on the left, brackets/delimiters on
the right, shifted number symbols on the top row.

Shifted number symbols on the top row double as `Super+Shift+Number` for
moving windows between workspaces.

```
┌───────┬───────┬───────┬───────┬───────┬───────┐    ┌───────┬───────┬───────┬───────┬───────┬───────┐
│   ~   │   !   │   @   │   #   │   $   │   %   │    │   ^   │   &   │   *   │   (   │   )   │  DEL  │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│  TAB  │       │       │       │ C-b   │       │    │       │   (   │   )   │   [   │   ]   │       │
├───────┼───────┼───────┼───────┼───────┼───────┤    ├───────┼───────┼───────┼───────┼───────┼───────┤
│ LSHFT │       │       │   \   │   /   │       │    │       │   {   │   }   │   <   │   >   │       │
├───────┼───────┼───────┴───────┼───────┼───────┤    ├───────┼───────┼───────┴───────┼───────┼───────┤
│ LGUI  │ LALT  │               │ SPACE │  mo5  │    │ ▓▓▓▓▓ │ SPACE │               │ RALT  │ LCTRL │
└───────┴───────┘               └───────┴───────┘    └───────┴───────┘               └───────┴───────┘
                      D-PAD: (none) / BRI_DN / (none) / BRI_UP / (none)
```

### Tmux Prefix (Left Split)

The keymap provides a single tmux prefix macro (`Ctrl+B`) rather than full
tmux command sequences. This gives you maximum flexibility to follow with
any tmux command.

| Position | Key | Macro       | Output     | Use                          |
|----------|-----|-------------|------------|------------------------------|
| 16       | T   | tmux_macro  | `Ctrl+B`   | Tmux prefix for all commands |

**Workflow:** 
1. Hold RIGHT thumb (mo 3)
2. Tap T to send `Ctrl+B` prefix
3. Release mo 3
4. Press your desired tmux command key

**Common tmux commands after prefix:**
- `C` - Create new window
- `%` - Split pane horizontal
- `"` - Split pane vertical
- `Z` - Toggle pane zoom
- `X` - Kill current pane
- `←` `↓` `↑` `→` - Navigate panes
- `[` - Enter copy mode
- `P` - Previous window
- `N` - Next window

### Bracket Pairs (Right Split)

**Home row right:**
- `( )` (index pair, positions 19-20) - Function calls, tuples, precedence
- `[ ]` (ring pair, positions 21-22) - Arrays, indexing, slices

**Bottom row right:**
- `{ }` (index pair, positions 31-32) - Code blocks, dicts, structs
- `< >` (ring pair, positions 33-34) - Comparisons, generics, HTML

**Bracket pairs** are always adjacent on the same hand for fast inward rolls.

### Additional Symbols (Left Split)

**Bottom row:**
- `\` (position 27) - Backslash for escaping, paths
- `/` (position 28) - Forward slash for division, paths, regex

### Additional Tmux Macros (Unbound)

The keymap currently only defines the tmux prefix macro (`Ctrl+B`). Additional
tmux command macros can be defined as needed. For complex tmux workflows, 
consider using the prefix macro followed by manual key presses.

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

Combos are Colemak-only (disabled on QWERTY gaming layer). Currently, only
one combo is defined:

**Timing:** `timeout-ms=40`, `require-prior-idle-ms=150`

### Active Combos

| Combo     | Keys (Colemak) | Positions | Output | Mnemonic     | Use Case              |
|-----------|----------------|-----------|--------|--------------|-----------------------|
| Escape    | S + E          | 15 + 20   | `ESC`  | Cross-split  | Vim normal mode, exit |

This minimal combo set prioritizes avoiding accidental triggers during normal
typing. Additional combos can be added as needed based on usage patterns.

---

## Symbol Access Matrix

Quick reference for finding any symbol across layers.

| Symbol | Layer 0 | Layer 2     | Layer 3     | Best Access        |
|--------|---------|-------------|-------------|--------------------|
| `~`    | -       | pos 14      | pos 0       | Layer 2 (pos 14)   |
| `_`    | -       | pos 15      | -           | Layer 2 (pos 15)   |
| `-`    | -       | pos 16      | -           | Layer 2 (pos 16)   |
| `\|`   | -       | pos 17      | -           | Layer 2 (pos 17)   |
| `` ` `` | -      | pos 26      | -           | Layer 2 (pos 26)   |
| `=`    | -       | pos 27      | -           | Layer 2 (pos 27)   |
| `+`    | -       | pos 28      | -           | Layer 2 (pos 28)   |
| `"`    | -       | pos 29      | -           | Layer 2 (pos 29)   |
| `:` | -       | pos 22      | -           | Layer 2 (pos 22)   |
| `'`    | pos 23  | pos 23      | -           | Layer 0 (pos 23)   |
| `!`    | -       | -           | Shift+1     | Layer 3 (Shift+1)  |
| `@`    | -       | -           | Shift+2     | Layer 3 (Shift+2)  |
| `#`    | -       | -           | Shift+3     | Layer 3 (Shift+3)  |
| `$`    | -       | -           | Shift+4     | Layer 3 (Shift+4)  |
| `%`    | -       | -           | Shift+5     | Layer 3 (Shift+5)  |
| `^`    | -       | -           | Shift+6     | Layer 3 (Shift+6)  |
| `&`    | -       | -           | Shift+7     | Layer 3 (Shift+7)  |
| `*`    | -       | -           | Shift+8     | Layer 3 (Shift+8)  |
| `( )`  | -       | -           | pos 19-20   | Layer 3            |
| `[ ]`  | -       | -           | pos 21-22   | Layer 3            |
| `{ }`  | -       | -           | pos 31-32   | Layer 3            |
| `< >`  | -       | -           | pos 33-34   | Layer 3            |
| `\`    | -       | -           | pos 27      | Layer 3 (pos 27)   |
| `/`    | -       | -           | pos 28      | Layer 3 (pos 28)   |
| `;`    | pos 10  | -           | -           | Layer 0 (pos 10)   |

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

The keymap provides a tmux prefix macro that sends `Ctrl+B`. This gives you
maximum flexibility to follow with any tmux command.

### Using the Tmux Prefix

Hold `mo 3` (RIGHT thumb, position 40) + tap `T` (position 16) to send `Ctrl+B`.
Then release and press your desired tmux command key.

### Common Tmux Commands

After sending the prefix (`mo 3` + `T`), use these common commands:

| Task                      | Keys after prefix         |
|---------------------------|---------------------------|
| Navigate to left pane     | `←` or `H`                |
| Navigate to right pane    | `→` or `L`                |
| Navigate to up pane       | `↑` or `K`                |
| Navigate to down pane     | `↓` or `J`                |
| Create new window         | `C`                       |
| Split pane horizontally   | `%`                       |
| Split pane vertically     | `"`                       |
| Toggle zoom current pane  | `Z`                       |
| Kill current pane         | `X`                       |
| Enter copy mode           | `[`                       |
| Previous window           | `P`                       |
| Next window               | `N`                       |

---

## Behavior Timing

| Behavior              | Parameter              | Value  |
|-----------------------|------------------------|--------|
| Home row mods         | tapping-term-ms        | 180ms  |
| Home row mods         | quick-tap-ms           | 150ms  |
| Home row mods         | require-prior-idle-ms  | 150ms  |
| Layer-tap (`lt`)      | tapping-term-ms        | 140ms  |
| Layer-tap (`lt`)      | require-prior-idle-ms  | 150ms  |
| Combos                | timeout-ms             | 40ms   |
| Combos                | require-prior-idle-ms  | 150ms  |
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
