```
neutral(charges, tol) # true or false. default tol = 1e-5
neutral(crystal, tol) # true or false. default tol = 1e-5
```

determine if a set of `charges::Charges` (`charges.q`) sum to an absolute value less than `tol::Float64`. if `crystal::Crystal` is passed, the function looks at the `crystal.charges`. i.e. determine the absolute value of the net charge is less than `tol`.
