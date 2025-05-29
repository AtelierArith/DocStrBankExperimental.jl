```
script(str; roundhand=false)
```

Return a version of string `str` with mathematical script letters from the Unicode table.

There are two basic styles of mathematical script lettering: the “regular” calligraphic or Chancery alphabet, and the “fancy script” or round hand alphabet.

By default, the script style will be “script”. If `roundhand` is true, the style will be “roundhand”.

For more details, see [this Unicode document](https://www.unicode.org/L2/L2020/20275r-math-calligraphic.pdf).
