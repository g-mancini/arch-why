# arch-why

A simple CLI tool for Arch Linux that explains **why a package is installed** on your system.

---

## What it does

`arch-why` analyzes a package using `pacman` and tells you:

* if it was installed manually or as a dependency
* which packages require it
* what dependencies it has

---

## Example

```bash
./arch-why.sh firefox
```

Output:

```
Firefox: Installato manualmente

Richiesto da: firefox-i18n-it

Dipendenze: alsa-lib at-spi2-core bash cairo dbus ...
```

---

## Requirements

* Arch Linux
* `pacman`

---

## Installation

Clone the repository:

```bash
git clone https://github.com/g-mancini/arch-why.git
cd arch-why
```

Make the script executable:

```bash
chmod +x arch-why.sh
```

(Optional) Move it to your PATH:

```bash
sudo mv arch-why.sh /usr/local/bin/arch-why
```

---

## Usage
```bash
arch-why <package>
```

Examples:
```bash
arch-why vim
arch-why firefox
```

Options:
```bash
arch-why --help    # show help message
arch-why -h        # short form
```

---

## How it works

The tool uses:

```bash
pacman -Qi <package>
```

To ensure consistent parsing across different system languages, it forces:

```bash
LANG=C
```

This guarantees stable output regardless of localization.

---

## Notes

* The script is **read-only**: it does NOT modify your system
* It only reads package information from `pacman`
* Works only on Arch-based systems

---

## Why this project?

On Arch Linux, it's common to forget why a package is installed.

`arch-why` helps you:

* understand your system
* identify unused packages
* keep your setup clean

---

## Future improvements

* dependency tree visualization (`--tree`)
* colored output
* JSON export
* support for AUR packages
* safer script execution (`set -euo pipefail`)

---

## License

MIT License

---

## Author

g-mancini

---

## Contributing

Pull requests are welcome!
Feel free to open issues for suggestions or bugs.

