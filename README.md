[![Build Status](https://travis-ci.org/10sr/with-venv-el.svg?branch=master)](https://travis-ci.org/10sr/with-venv-el)
[![MELPA](https://melpa.org/packages/with-venv-badge.svg)](https://melpa.org/#/with-venv)
[![MELPA Stable](https://stable.melpa.org/packages/with-venv-badge.svg)](https://stable.melpa.org/#/with-venv)


with-venv.el
============

Execute with Python virtual environment activated


Usage
-----


Execute BODY with Python virtual environment activated with `with-venv-dir` macro:

``` emacs-lisp
(with-venv-dir (expand-file-name ".venv" default-directory)
  (executable-find "python"))
```


Alternatively, make this package try to find venv directory automatically
with `with-venv`:

``` emacs-lisp
(with-venv
  (executable-find "python"))
```


This macro uses `with-venv-find-venv-dir-functions` to find suitable venv
directory: this function currently support `pipenv`, `poetry`, and can find
directories named `.venv`.
Or, you can set buffer-local vairable `with-venv-venv-dir` to explicitly
specify path venv directory.


If you want to always enable `with-venv` for certain functions,
`with-venv-advice-add` can be used for this purpose:

``` emacs-lisp
(with-venv-advice-add 'blacken-buffer)
```

Adviced functions are always wrapped with `with-venv` macro when called.

Call `with-venv-advice-remove` to remove these advices.


License
-------

This software is licensed under Apache License 2.0 . See `LICENSE` for details.

