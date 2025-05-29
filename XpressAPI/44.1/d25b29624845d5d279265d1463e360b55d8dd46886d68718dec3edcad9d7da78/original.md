```
XPRSrepairinfeas(prob, penalty, phase2, flags, lepref, gepref, lbpref, ubpref, delta)::status
```

Provides a simplified interface for XPRSrepairweightedinfeas.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `penalty::Integer`: The type of penalties created from the preferences: ceach penalty is the reciprocal of the preference (default); sthe penalties are placed in the scaled problem.
  * `phase2::Integer`: Controls the second phase of optimization: ouse the objective sense of the original problem (default); xmaximize the relaxed problem using the original objective; fskip optimization regarding the original objective; nminimize the relaxed problem using the original objective; iif the relaxation is infeasible, generate an irreducible infeasible subset for the analys of the problem; aif the relaxation is infeasible, generate all irreducible infeasible subsets for the analys of the problem.
  * `flags::Integer`: Specifies what type of solve should be done: gsolve as MIP (default); lsolve as a linear model ignoring the discreteness of variables; xcall the global solver.
  * `lepref::Float64`: Preference for relaxing the less or equal side of row.
  * `gepref::Float64`: Preference for relaxing the greater or equal side of a row.
  * `lbpref::Float64`: Preferences for relaxing lower bounds.
  * `ubpref::Float64`: Preferences for relaxing upper bounds.
  * `delta::Float64`: The relaxation multiplier in the second phase -1.

# Return value

  * `status::Int32`: The status after the relaxation: 0relaxed optimum found; 1relaxed problem is infeasible; 2relaxed problem is unbounded; 3solution of the relaxed problem regarding the original objective is nonoptimal; 4error (when return code is nonzero); 5numerical instability; 6analysis of an infeasible relaxation was performed, but the relaxation is feasible.

See also the documentation of the correponding function [XPRSrepairinfeas](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSrepairinfeas.html) in the C API.
