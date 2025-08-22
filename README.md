# codemetric_secure-pasword-generator

🔑 Features

Customizable Passwords – You can choose:

Length of the password

Whether to include uppercase letters

Whether to include lowercase letters

Whether to include digits

Whether to include special characters

Security Check – Ensures that the generated password always includes at least one character from each chosen type (upper/lower/digits/special).

Clipboard Support – If the pyperclip module is installed, the password is automatically copied to your clipboard for convenience.

Error Handling – If you don’t select any character types, it raises a clear error.
If you enter something invalid for length, it warns you.

📂 Code Explanation

Imports

import random
import string


random → for generating random characters.

string → provides sets like ascii_uppercase, ascii_lowercase, digits, punctuation.

try:
    import pyperclip
    CLIPBOARD_AVAILABLE = True
except ImportError:
    CLIPBOARD_AVAILABLE = False


pyperclip (optional) → copies the password directly to clipboard.

If not installed, it just skips that feature.

Password Generation Function

def generate_password(length=12, use_upper=True, use_lower=True, use_digits=True, use_special=True, copy_to_clipboard=False):


Parameters:

length → password length (default: 12).

use_upper, use_lower, use_digits, use_special → toggles for what character sets to use.

copy_to_clipboard → if True, and pyperclip is available, password gets auto-copied.

Inside:

Builds the pool of allowed characters.

Generates a random password.

Re-generates until it satisfies all enabled rules (at least one uppercase/lowercase/digit/special).

Clipboard Handling

if copy_to_clipboard and CLIPBOARD_AVAILABLE:
    pyperclip.copy(password)


If the feature is enabled and supported, the password is placed in the system clipboard.

Main Program

if __name__ == "__main__":
    length = int(input("Enter password length (number only): "))
    pwd = generate_password(length=length, copy_to_clipboard=True)


Asks user for password length.

Generates password.

Prints it.

Optionally copies to clipboard.

🖥️ Sample Run
Enter password length (number only): 14

✅ Generated Password: h3%F9!AbT2&Q1m
(Password has also been copied to clipboard!)


👉 In short:
This script is a safe and flexible password generator with clipboard integration, useful for quickly creating strong passwords.
