```
XPRS_BARORDERTHREADS
```

If set to a positive integer it determines the number of concurrent threads for the sparse matrix ordering algorithm in the Newton-barrier method. (integer)

Default value: `0`

Values: 0 : The default value is determined automatically based on the problem size, structure and algorithm choice.

> =0


: The number of concurrent threads for the sparse matrix ordering algorithm in the Newton-barrier method.
