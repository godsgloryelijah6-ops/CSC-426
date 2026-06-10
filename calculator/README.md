# myCalculator (Python, Tkinter)

A desktop GUI calculator built with Python and Tkinter for the CSC426 weekly dev exercise.

## What it does

The whole expression you type is shown in the display, and the answer is added
after you press `=`. For example, typing `2 + 4 - 93` and pressing `=` shows:

```
2+4-93=-87
```

Supported keys:

| Button  | Operation                  |
|---------|----------------------------|
| `+`     | Addition                   |
| `-`     | Subtraction                |
| `*`     | Multiplication             |
| `/`     | Division                   |
| `\`     | Integer (floor) division   |
| `^`     | Exponentiation (power)     |
| `%`     | Modulo (remainder)         |
| `Clear` | Clear everything           |
| `<-`    | Backspace (delete a digit) |
| `.`     | Decimal point              |
| `=`     | Evaluate the expression    |

Notes:

* Expressions follow normal operator precedence, so `2 + 3 * 4` gives 14, and
  `^` is evaluated right to left, so `2 ^ 3 ^ 2` gives 512.
* Division and modulo by zero show `Error` instead of crashing.
* Whole number answers are shown without a trailing `.0`.
* The keyboard works too: type the digits and operators, press Enter to evaluate,
  Backspace to delete, and Esc to clear.

## Requirements

Python 3.8 or newer. Tkinter comes with Python on Windows and macOS. On most Linux
setups it ships separately, so if you see a Tkinter error, install it with
`sudo apt install python3-tk` on Debian or Ubuntu, or `sudo pacman -S tk` on Arch.

## Run

```bash
python3 myCalculator.py
```

The calculator window will open.

## How it works

Key presses build up an expression string that is shown in the display. When you
press `=`, a small recursive descent parser reads that string and evaluates it
with the correct precedence: `+` and `-` at the lowest level, then `*`, `/`, `\`
and `%`, then `^` at the highest level. The input is parsed by hand rather than
passed to `eval`, so only valid maths runs.
