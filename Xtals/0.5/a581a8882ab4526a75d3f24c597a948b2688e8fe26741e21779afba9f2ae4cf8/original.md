```
strip_numbers_from_atom_labels!(crystal)
```

Strip numbers from labels for `crystal.atoms`. Precisely, for `atom` in `crystal.atoms`, find the first number that appears in `atom`. Remove this number and all following characters from `atom`. e.g. C12 –> C Ba12A_3 –> Ba

# Arguments

  * `crystal::Crystal`: The crystal containing the crystal structure information
