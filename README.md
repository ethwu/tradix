# tradix #

[![MIT License](https://img.shields.io/badge/license-MIT-informational)](https://opensource.org/licenses/MIT)

Convert between radices. Supports input radices from 2–16 and output radices of
any size greater than or equal to 2. Also supports arbitrary input and output
alphabets, with built-in support for:

- Hindu-Arabic numerals
  - With support for hexadecimal-style extension with lowercase and uppercase
    Latin letters
- Pitman dozenal numerals
- Delta-epsilon dozenal numerals
- Tau-epsilon dozenal numerals
- Base64

If you’d like to have an output alphabet that uses two or more characters to
represent a particular digit, use a placeholder character and text replacement
on the output.

## Help Text ##

```text
usage: tradix.rkt [ <option> ... ] [<number>]
  Convert between radices. Flags beginning with capital letters correspond to
  input, and flags beginning with lowercase letters correspond to output. Both
  input and output default to decimal. The default alphabet extends the Hindu–
  Arabic numeral system with the lowercase Latin letters for 10 through 35 and
  the uppercase Latin letters for 36 through 61. If no number is given for
  conversion, input will be taken from STDIN.

<option> is one of

 =============================== Radix Options =================================
 Specify the input and output radices. Both default to decimal (base 10). While
 shortcuts are provided for several common radices, you can also specify a radix
 in decimal using the --input-radix and --output-radix flags.
 
/ -i <input_radix>, -I <input_radix>, --input-radix <input_radix>
|    Specify the input radix. Must be between 2 and 16.
| -B, --Binary
|    Interpret as binary.      (Base 2)
| -S, --Senary
|    Interpret as senary.      (Base 6)
| --Octal
|    Interpret as octal.       (Base 8)
| -D, --Dozenal, --Duodecimal, --Uncial
|    Interpret as dozenal.     (Base 12)
| -X, --Hexadecimal
\    Interpret as hexadecimal. (Base 16)
 
/ -o <output_radix>, --output-radix <output_radix>
|    Specify the output radix. Must be at least 2.
| -b, --binary
|    Print in binary.          (Base 2)
| -s, --senary
|    Print in senary.          (Base 6)
| --octal
|    Print in octal.           (Base 8)
| -d, --dozenal, --duodecimal, --uncial
|    Print in dozenal.         (Base 12)
| -x, --hexadecimal
|    Print in hexadecimal.     (Base 16)
| --vigesimal
|    Print in vigesimal.       (Base 20)
| --sexagesimal, --sexagenary
\    Print in sexagesimal.     (Base 60)
 
 ============================== Alphabet Options ===============================
 Specify the alphabets used for interpreting and printing. The --input-alphabet
 and --output-alphabet flags may take either a string of one-character digits
 that form an alphabet (i.e., '0123456789abcdef') or one of the following
 specifiers:
 
   * default       An alphabet that extends the Hindu–Arabic numeral system with
                   lowercase Latin letters for 10 through 35 and uppercase Latin
                   letters for 36 through 61. Supports any radix up to 62.
   * pitman        An alphabet that uses Isaac Pitman’s dozenal numerals for ten
                   and eleven, '↊' and '↋'. Supports any radix up to 12.
   * delta-epsilon An alphabet that uses lowercase delta 'δ' and epsilon 'ε' for
                   ten and eleven. Supports any radix up to 12.
   * tau-epsilon   An alphabet that uses lowercase tau 'τ' and epsilon 'ε' for
                   ten and eleven. Supports any radix up to 12.
   * base64        The alphabet used by the Base64 encoding scheme. Does not
                   pad. Supports any radix up to 64.
 
/ -A <alphabet>, --input-alphabet <alphabet>
|    Specify the input alphabet.
| --Pitman
|    Interpret Isaac Pitman’s dozenal numerals.        Implies --Dozenal.
| --Delta-Epsilon
|    Interpret delta–epsilon-style dozenal numerals.   Implies --Dozenal.
| --Tau-Epsilon
|    Interpret tau–epsilon-style dozenal numerals.     Implies --Dozenal.
| --Base64
\    Interpret using Base64.                           Implies --input-radix 64.
 
/ -a <alphabet>, --output-alphabet <alphabet>
|    Specify the output alphabet. 
| --pitman
|    Print using Isaac Pitman’s dozenal numerals.      Implies --dozenal.
| --delta-epsilon
|    Print using delta–epsilon-style dozenal numerals. Implies --dozenal.
| --tau-epsilon
|    Print using tau–epsilon-style dozenal numerals.   Implies --dozenal.
| --base64
\    Print using using Base64.                         Implies --output-radix 64.
 
  -l, --list
     Print the converted number as a list of place values.
 
  --help, -h
     Show this help
  --
     Do not treat any remaining argument as a switch (at this level)

 /|\ Brackets indicate mutually exclusive options.

 Multiple single-letter switches can be combined after
 one `-`. For example, `-h-` is the same as `-h --`.
 
All numerals in this help text are in decimal (base 10).
```
