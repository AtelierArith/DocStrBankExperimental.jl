```
XPRS_MIPCONCURRENTSOLVES
```

Selects the number of concurrent solves to start for a MIP. (integer)

Each solve will use a unique random seed for its random number generator, but will otherwise apply the same user controls. The first concurrent solve to complete will have solved the MIP and all the concurrent solves will be terminated at this point. Using concurrent solves can be advantageous when a MIP displays a high level of performance variability.

Default value: `0`

Values: -1 : Enabled. The number of concurrent solves depends on MIPTHREADS. 0, 1 : Disabled n>1 : Enabled. The number of concurrent solves to start is given by `n`.
