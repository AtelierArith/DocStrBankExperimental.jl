```
XPRS_MAXMCOEFFBUFFERELEMS
```

The maximum number of matrix coefficients to buffer before flushing into the internal representation of the problem. (integer)

Buffering coefficients can offer a significant performance gain when you are building a matrix using XPRSchgcoef or XPRSchgmcoef, but can lead to a significant memory overhead for large matrices, which this control allows you to influence.

Default value: `2147483647`

Domain: 0~+INF
