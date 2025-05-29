```
XPRS_AUTOSCALING
```

Whether the Optimizer should automatically select between different scaling algorithms. (integer)

If the `SCALING` control is set, no automatic scaling will be applied.

Default value: -1

Values: -1 : Automatic. 0 : Disabled. 1 : Cautious strategy. Non-standard scaling will only be selected if it appears to be clearly superior. 2 : Moderate strategy. 3 : Aggressive strategy. Standard scaling will only be selected if it appears to be clearly superior.
