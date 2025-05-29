```
optimize_code(c::TensorNetwork, optimizer=TreeSA())
```

Optimize the code of the tensor network.

### Arguments

  * `c::TensorNetwork`: The tensor network.
  * `optimizer::Optimizer`: The optimizer to use, default is `TreeSA()`. Please check [OMEinsumContractors.jl](https://github.com/TensorBFS/OMEinsumContractionOrders.jl) for more information.
