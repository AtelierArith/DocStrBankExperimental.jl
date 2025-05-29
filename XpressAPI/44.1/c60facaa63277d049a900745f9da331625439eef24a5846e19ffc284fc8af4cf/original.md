```
XPRS_BARHGOPS
```

Control options for the hybrid gradient algorithm. (integer)

Bits 1, 2 and 3 control which norms of the coefficient matrix are used for solution normalization. The normalization factor is the maximum of the selected norms. By default, or if all three bits are set to 0, the infinity norm is used. The omega parameter referenced in bits 4, 5 and 6 is a measure of the relative magnitudes of the objective and the right-hand side.

Default value: `8`, only the infinity norm is used for normalization, the other options are all off.

Values are a bitset: bit 0 : Use an asymmetric average for the primal averaging. bit 1 : Use the 1-norm of the coefficient matrix in normalizing the initial solution. bit 2 : Use the 2-norm of the coefficient matrix in normalizing the initial solution. bit 3 : Use the infinity norm of the coefficient matrix in normalizing the initial solution. bit 4 : Take the square root of omega. bit 5 : Contract omega towards 1 if the infeasibility is small enough. bit 6 : Omega is based on the infeasibility.
