```
tracedist(register1, register2)
```

Return the trace distance of `register1` and `register2`.

# Definition

Trace distance is defined as following:

$$
\frac{1}{2} || A - B ||_{\rm tr}
$$

It takes values between 0 and 1.

### Examples

```jldoctest; setup=:(using Yao)
julia> reg1 = uniform_state(3);

julia> reg2 = zero_state(3);

julia> tracedist(reg1, reg2)
0.9354143466934852
```

### References

  * https://en.wikipedia.org/wiki/Trace_distance
