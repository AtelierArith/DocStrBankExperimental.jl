```
write_cssr(xtal, "myxtal.cssr")
write_cssr(xtal) # uses xtal.name to guess desired filename.
```

write crystal structure to `.cssr` format.

# arguments

  * `xtal::Crystal`: crystal to write to file
  * `filename::AbstractString`: filename to write to. default is to write `.cssr` file to `pwd()`.  will append `.cssr` if absent from `filename`.
  * `quiet::Bool` : (optional) set `true` to suppress console output
