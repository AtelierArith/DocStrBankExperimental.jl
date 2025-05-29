```
@const_gate <gate name> = <expr>
@const_gate <gate name>::<type> = <expr>
@const_gate <gate>::<type>
```

This macro simplify the definition of a constant gate. It will automatically bind the matrix form to a constant which will reduce memory allocation in the runtime.

### Examples

```julia
@const_gate X = ComplexF64[0 1;1 0]
```

or

```julia
@const_gate X::ComplexF64 = [0 1;1 0]
```

You can bind new element types by simply re-declare with a type annotation.

```julia
@const_gate X::ComplexF32
```
