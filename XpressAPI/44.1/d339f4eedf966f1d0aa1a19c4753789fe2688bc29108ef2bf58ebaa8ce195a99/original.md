```
XPRS_BARGAPSTOP
```

Newton barrier and hybrid gradient: This is a convergence parameter, representing the tolerance for the relative duality gap. (double)

When the difference between the primal and dual objective function values falls below this tolerance, the Optimizer determines that the optimal solution has been found.

Default value: `0`

Values: 0 : The default value is determined automatically based on the problem size, structure and algorithm choice.

> =0


: The tolerance for the relative duality gap.
