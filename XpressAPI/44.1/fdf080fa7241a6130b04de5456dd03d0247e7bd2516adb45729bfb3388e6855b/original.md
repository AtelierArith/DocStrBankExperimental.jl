```
XPRS_PRESORT
```

This bit vector control specifies whether to sort rows, columns and MIP entities by their names when starting the presolve. (integer)

With the default value `0`, no sorting will take place.

Default value: `0`

Values are a bitset: bit 0 : Sort rows. bit 1 : Sort columns. bit 2 : Sort MIP entities. This bit only affects MIP problems.
