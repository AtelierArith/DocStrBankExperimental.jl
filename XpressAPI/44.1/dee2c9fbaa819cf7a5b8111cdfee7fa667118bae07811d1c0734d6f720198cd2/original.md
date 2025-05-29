```
XPRSnlpadduserfunctionmapdelta(prob, funcname, options, func)::type
```

Add user function definitions to an SLP problem.

`func` is invoked with this signature

```
function(value::Cdouble, delta::Cdouble)::Tuple{error::Cint,evaluation::Cdouble,partial::Cdouble}
```

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `funcname::Union{Nothing,AbstractString}`: The name of the function as it appears in text formula expressions.
  * `options::Integer`: options as a bitmap to the user function XSLP_INSTANCEFUNCTIONalways instantiate the function.
  * `func::Function`: Pointer of the user function to call.

# Return value

  * `type::Int32`: The token id of the user function added, to be used in the Value array when defining formulas and using with `XSLP_FUN`.

See also the documentation of the correponding function [XPRSnlpadduserfunction](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpadduserfunction.html) in the C API.
