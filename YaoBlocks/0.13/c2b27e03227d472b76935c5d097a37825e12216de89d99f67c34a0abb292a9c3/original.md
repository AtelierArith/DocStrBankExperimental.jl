```
AbstractAdd{D} <: CompositeBlock{D}
```

The abstract add interface, aimed to support Hamiltonian types.

### Required Interfaces

  * `chsubblocks`
  * `subblocks`

### Provides

  * `unsafe_apply!` and its backward
  * `mat` and its backward
  * `adjoint`
  * `occupied_locs`
  * `getindex` over dit strings
  * `ishermitian`
