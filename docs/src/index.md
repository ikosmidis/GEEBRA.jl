# GEEBRA.jl

## Authors

[Ioannis Kosmidis](http://www.ikosmidis.com) (author, maintainer) 

[Nicola Lunardon](https://www.unimib.it/nicola-lunardon)

## Licence

[MIT License](https://github.com/ikosmidis/GEEBRA.jl/blob/master/LICENSE.md)

## Package description

**GEEBRA** is a Julia package that provides infrastructure to estimate
statistical models by solving estimating equations or by maximizing
inference objectives, like
[likelihood](https://en.wikipedia.org/wiki/Likelihood_function) and
composite likelihood functions (see, Varin et al, 2011, for a review),
using user-specified templates.

A key feature is the option to adjust the estimating equation or
penalize the objectives in order to reduce the bias of the resulting
estimators.

## M-estimation and bias reduction

**GEEBRA** has been designed so that the only requirements from the
user are to:
1. implement a [Julia composite type](https://docs.julialang.org/en/v1/manual/types/index.html) for
   the data;
2. implement a function for computing the number of observations from
   the data object;
3. implement a function for calculating the contribution to the
   estimating function or to the objective function from a single
   observation that has arguments the parameter vector, the data
   object, and the observation index;
4. specify a GEEBRA template (using
   [`estimating_function_template`](@ref) for estimating functions and
   [`objective_function_template`](@ref) for objective function) that
   has fields the functions for computing the contributions to the
   estimating functions or to the objective, and the number of
   observations.

**GEEBRA**, then, can estimate the unknown parameters by solving the
estimating equations or maximizing the inference objectives.

There is also the option to compute bias-reducing adjustments to the estimating functions or bias-reducing penalties to the objective to compute estimators with improved bias properties.  The bias-reducing adjustments and penalties are formed internally from the supplied templates and data object, using forward mode automatic differentiation, as implemented in [**ForwardDiff**](https://github.com/JuliaDiff/ForwardDiff.jl). No further work or input is required by the user.

## Examples

```@contents
Pages = [
    "man/examples.md",
    ]
```

## Documentation

```@contents
Pages = [
    "lib/public.md",
    "lib/internal.md",
    ]
```

## [Index](@id main-index)

```@index
Pages = [
    "lib/public.md",
    "lib/internal.md",
    ]
```

## References

+ Varin, C., N. Reid, and D. Firth (2011). An overview of composite likelihood methods. Statistica Sinica 21(1), 5–42.
