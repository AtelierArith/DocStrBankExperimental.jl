```
Z = ZippedArray(A,B,C,...)
```

builds a zipped array `Z` based on arrays `A`, `B`, `C`, etc. such that the syntax `Z[i]` yields a tuple of values `(A[i],B[i],C[i],...)` while the syntax `Z[i] = (a,b,c,...)` is equivalent to `(A[i],B[i],C[i],...) = (a,b,c,...)`.

Any number of arrays can be zipped together, they must however have the same indices (as given by calling the `axes` method).

Use the syntax `Z.args` to retrieve the arrays `A`, `B`, `C`, etc.
