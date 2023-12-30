XLTree output plugin for pyang
============================================================

Overview
------------------------------------------------------------

XLTree is a plugin for [pyang](https://github.com/mbj4668/pyang)
to output various aspects of YANG models to an Excel(xlsx) file.

- tree representation of data, rpc and notification
- list of enums for enum-like enumeration and identityref typedefs
- inheritance tree of identities
- relationship of modules


Requirements
------------------------------------------------------------

Aside form pyang this plugin depends on following libraries.

- [openpyxl](https://foss.heptapod.net/openpyxl/openpyxl)


How to use
------------------------------------------------------------

### 1) clone repository

```
> git clone https://github.com/nabium/pyang-xltree-plugin.git
> cd pyang-xltree-plugin
```

### 2) (optional) create venv

```
> python -m venv --prompt xltree venv
> venv\Scripts\activate
(xltree) > python --version
Python 3.12.1
(xltree) > python -m pip install --upgrade pip
```

### 3) install pyang and openpyxl

```
(xltree) > python -m pip install pyang setuptools openpyxl
(xltree) > pip list
Package    Version
---------- -------
et-xmlfile 1.1.0
lxml       5.0.0
openpyxl   3.1.2
pip        23.3.2
pyang      2.6.0
setuptools 69.0.3
```

### 4) run pyang with xltree output

```
(xltree) > python -m pyang --plugindir=. -f xltree --xltree-out=xltree.xlsx YANG_FILES...
```

Run `python -m pyang --plugindir=. --help` for other options.


Options
------------------------------------------------------------

- --plugindir=DIR

  Directory where plugin file `xltree.py` is located.

- -f xltree

  Use xltree output plugin.

- --xltree-out=FILE

  Excel file for output.
  Default is `xltree.xlsx`.
  This plugin cannot output contents to `stdout` or to the file specified by `-o`
  as they are opend in text mode.

- --xltree-font=FONT

  Name of the font to use.
  ex.) Calibri, "Yu Gothic Medium"
