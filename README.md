# Python bindings for wc(s)width

`cwcwidth` provides Python bindings for `wcwidth` and `wcswidth` functions defined in POSIX.1-2001
and POSIX.1-2008 based on [Cython](https://cython.org/). These functions compute the printable
length of a unicode character/string on a terminal. The module provides the same functions as
[wcwidth](https://pypi.org/project/wcwidth/) and its behavior is compatible.

On systems not conforming to POSIX.1-2001 and POSIX.1-2008, Markus Kuhn's
[implementation](https://www.cl.cam.ac.uk/~mgk25/ucs/wcwidth.c) is used to provide the
functionality.

## Dependencies

* `Cython >= 0.28` (optional, only for building). If Cython is not available, the C files are not
  regenerated from their source.

## Quick installation guide

`cwcwidth` can be installed via `pip`:
```sh
pip install cwcwidth
```
or by running:
```sh
python3 setup.py install
```

## Usage

```python3
import cwcwidth
cwcwidth.wcwidth("a") # 1
cwcwidth.wcswidth("コ") # 2
cwcwidth.wcswidth("コンニチハ, セカイ!") # 19
```

## Comparison with `wcwidth`

```python3
>>> import wcwidth, cwcwidth, timeit
>>> timeit.timeit(lambda: wcwidth.wcswidth("コンニチハ, セカイ!"))
19.14463168097427
>>> timeit.timeit(lambda: cwcwidth.wcswidth("コンニチハ, セカイ!"))
0.16294104099506512
```

## License

The code is licensed under the MIT license.

## Security contact informaton

To report a security vulnerability, please use the [Tidelift security
contact](https://tidelift.com/security). Tidelift will coorindate the fix and disclosure.
