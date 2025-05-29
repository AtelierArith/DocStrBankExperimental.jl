```
XPRS_ATTENTIONLEVEL
```

A measure between 0 and 1 for how numerically unstable the problem is. (double)

The attention level is based on a weighted combination of the number of basis condition numbers exceeding certain thresholds. It considers all nodes sampled by MIPKAPPAFREQ, with a setting of 1 being the most frequent sampling rate. The higher the attention level, the worse conditioned is the problem.
