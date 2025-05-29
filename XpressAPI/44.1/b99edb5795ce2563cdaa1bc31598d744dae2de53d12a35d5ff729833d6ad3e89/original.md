```
XPRSgetcheckedmode()::checkedmode
```

You can use this function to interrogate whether checking and validation of all Optimizer function calls is enabled for the current process.

Checking and validation is enabled by default but can be disabled by XPRSsetcheckedmode.

# Return value

  * `checkedmode::Int32`: Variable that is set to 0 if checking and validation of Optimizer function calls is disabled for the current process, non-zero otherwise.

See also the documentation of the correponding function [XPRSgetcheckedmode](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcheckedmode.html) in the C API.
