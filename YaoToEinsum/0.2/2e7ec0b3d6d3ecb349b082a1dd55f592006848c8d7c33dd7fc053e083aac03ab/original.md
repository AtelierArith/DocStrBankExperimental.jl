```
yao2einsum(circuit; initial_state=Dict(), final_state=Dict(), optimizer=TreeSA())
yao2einsum(circuit, initial_state::Dict, final_state::Dict, optimizer)
```

Transform a Yao `circuit` to a generalized tensor network (einsum) notation. The return value is a [`TensorNetwork`](@ref) instance.

### Arguments

  * `circuit` is a Yao block as the input.
  * `initial_state` and `final_state` are dictionaries to specify the initial states and final states (taking conjugate).

      * In the first interface, a state is specified as an integer, e.g. `Dict(1=>1, 2=>1, 3=>0, 4=>1)` specifies a product state `|1⟩⊗|1⟩⊗|0⟩⊗|1⟩`.
      * In the second interface, a state is specified as an `ArrayReg`, e.g. `Dict(1=>rand_state(1), 2=>rand_state(1))`.

If any qubit in initial state or final state is not specified, it will be treated as a free leg in the tensor network.

  * `optimizer` is the optimizer used to optimize the tensor network. The default is `TreeSA()`.

Please check [OMEinsumContractors.jl](https://github.com/TensorBFS/OMEinsumContractionOrders.jl) for more information.

```jldoctest
julia> using Yao

julia> c = chain(3, put(3, 2=>X), put(3, 1=>Y), control(3, 1, 3=>Y))
nqubits: 3
chain
├─ put on (2)
│  └─ X
├─ put on (1)
│  └─ Y
└─ control(1)
   └─ (3,) Y


julia> yao2einsum(c; initial_state=Dict(1=>0, 2=>1), final_state=Dict(1=>ArrayReg([0.6, 0.8im]), 2=>1))
TensorNetwork
Time complexity: 2^4.700439718141093
Space complexity: 2^2.0
Read-write complexity: 2^6.0
```
