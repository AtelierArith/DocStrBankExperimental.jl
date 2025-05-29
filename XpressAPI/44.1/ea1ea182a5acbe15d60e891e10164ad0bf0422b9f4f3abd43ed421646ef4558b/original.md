```
XPRS_TUNERMETHOD
```

Tuner: Selects a factory tuner method. (integer)

A tuner method consists of a list of controls with different settings that the tuner will evaluate and try to combine.

Default value: `-1`

Values: -1 : Automatically determined. The tuner will select the default method based on the problem type. 0 : Select the default LP tuner method. 1 : Select the default MIP tuner method. 2 : Select a more comprehensive MIP tuner method. 3 : Select a root-focus MIP tuner method. 4 : Select a tree-focus MIP tuner method. 5 : Select a simple MIP tuner method. 6 : Select the default SLP tuner method. 7 : Select the default MISLP tuner method. 8 : Select a MIP tuner method focussed on primal heuristics. 9 : Select the default Xpress Global tuner method.
