# Caesar Cipher GUI

A simple Python desktop application that demonstrates a Caesar cipher-style encryption and decryption with a GUI built using `tkinter`. It allows the user to enter a message and a shift key to encrypt or decrypt the text, displaying the transformed message and the underlying shifted alphabet sequence.

## Table of Contents

- [Features](#features)  
- [Requirements](#requirements)  
- [Installation](#installation)  
- [Usage](#usage)  
- [How It Works](#how-it-works)  
- [Examples](#examples)  
- [Known Issues & Limitations](#known-issues--limitations)  
- [Future Improvements](#future-improvements)  
- [License](#license)

## Features

- Encrypts and decrypts text using a Caesar-like shift cipher.  
- Supports lowercase, uppercase, and punctuation in the transformation.  
- Displays the shifted alphabet sequence used for the transformation.  
- Simple and polished GUI with custom fonts and layout.  
- About and Credits dialog boxes.

## Requirements

- Python 3.8+ (should work with any modern Python 3.x)
- Standard library only: uses `tkinter`, `string`, and `tkinter.messagebox` (no external dependencies)

> Note: `tkinter` is included with most Python installations on Windows and macOS. On some Linux distributions you may need to install it separately (e.g., `sudo apt install python3-tk`).

## Installation

1. Clone or download this repository.
2. Ensure you have Python installed:
   ```bash
   python --version
   ```

3. Run the application:

   ```bash
   python main.py
   ```

## Usage

1. Launch the application.
2. In the **"Enter a message"** field, type the text you want to encrypt or decrypt.
3. In the **key** field, enter a numerical shift value (e.g., `5` or `13`).
4. Click **Encrypt** to apply the shift cipher, or **Decrypt** to reverse it.
5. The output appears in the labeled areas:

   * Shifted alphabet sequence
   * Resulting encrypted/decrypted text
6. Use the menu to view **About**, **Credits**, or **clear\_screen** to reset input/output.

## How It Works

This application uses a variant of the Caesar cipher:

* It constructs three alphabets:

  1. `string.ascii_lowercase`
  2. `string.ascii_uppercase`
  3. `string.punctuation`

* For encryption, each of these is rotated forward by the user-provided shift value.

* For decryption, the rotation is reversed (effectively shifting by `26 - key` for alphabetic parts).

* All three sequences are concatenated to form the source and target alphabets, and `str.translate` is used to map characters.

## Examples

* Message: `Hello, World!`
  Shift: `1`
  Encrypted: `Ifmmp-!Xpsme"` (punctuation also shifts)

* Message: `Ifmmp-!Xpsme"`
  Shift: `1`
  Decrypted: `Hello, World!`

## Known Issues & Limitations

* The shift is applied uniformly to punctuation and letters; this can produce non-standard or confusing characters for punctuation.
* No validation on the key input: non-numeric input will cause a crash.
* Shift wrapping for uppercase/lowercase is treated separately, but punctuation uses its own rotation—which may not be intuitive.
* The decryption logic currently assumes a fixed alphabet length of 26 for reversing alphabetic shifts; if the scheme is extended, adjustments are needed.
* No persistence or clipboard copy functionality.

## Future Improvements

* **Input validation**: Reject or sanitize non-integer keys and empty messages with user-friendly errors.
* **Separate toggles**: Let the user choose whether punctuation is shifted or left untouched.
* **Custom alphabet**: Allow users to define their own character sets (e.g., include digits).
* **Clipboard support**: One-click copy of output.
* **Save/load**: Export encrypted messages or keys.
* **Command-line mode**: Support headless encryption/decryption via CLI arguments.
* **Better key UX**: Show effective rotation for decryption explicitly.
* **Unit tests**: Add test suite for verifying correctness of encrypt/decrypt functions.
* **Packaging**: Build as a standalone executable (e.g., with `pyinstaller`).

## License

Licensed under the [MIT License](LICENSE).