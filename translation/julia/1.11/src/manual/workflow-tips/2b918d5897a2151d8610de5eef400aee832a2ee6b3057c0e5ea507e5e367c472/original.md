# [Workflow Tips](@id man-workflow-tips)

Here are some tips for working with Julia efficiently.

## REPL-based workflow

As already elaborated in [The Julia REPL](@ref), Julia's REPL provides rich functionality that facilitates an efficient interactive workflow. Here are some tips that might further enhance your experience at the command line.

### A basic editor/REPL workflow

The most basic Julia workflows involve using a text editor in conjunction with the `julia` command line.

Create a file, say `Tmp.jl`, and include within it

```julia
module Tmp

say_hello() = println("Hello!")

# Your other definitions here

end # module

using .Tmp
```

Then, in the same directory, start the Julia REPL (using the `julia` command). Run the new file as follows:

```
julia> include("Tmp.jl")

julia> Tmp.say_hello()
Hello!
```

Explore ideas in the REPL. Save good ideas in `Tmp.jl`. To reload the file after it has been changed, just `include` it again.

The key in the above is that your code is encapsulated in a module. That allows you to edit `struct` definitions and remove methods, without restarting Julia.

(Explanation: `struct`s cannot be edited after definition, nor can methods be deleted. But you *can* overwrite the definition of a module, which is what we do when we re-`include("Tmp.jl")`).

In addition, the encapsulation of code in a module protects it from being influenced by previous state in the REPL, protecting you from hard-to-detect errors.

## Browser-based workflow

There are a few ways to interact with Julia in a browser:

  * Using Pluto notebooks through [Pluto.jl](https://github.com/fonsp/Pluto.jl)
  * Using Jupyter notebooks through [IJulia.jl](https://github.com/JuliaLang/IJulia.jl)

## Revise-based workflows

Whether you're at the REPL or in IJulia, you can typically improve your development experience with [Revise](https://github.com/timholy/Revise.jl). It is common to configure Revise to start whenever julia is started, as per the instructions in the [Revise documentation](https://timholy.github.io/Revise.jl/stable/). Once configured, Revise will track changes to files in any loaded modules, and to any files loaded in to the REPL with `includet` (but not with plain `include`); you can then edit the files and the changes take effect without restarting your julia session. A standard workflow is similar to the REPL-based workflow above, with the following modifications:

1. Put your code in a module somewhere on your load path. There are several options for achieving this, of which two recommended choices are:

      * For long-term projects, use [PkgTemplates](https://github.com/invenia/PkgTemplates.jl):

        ```julia
        using PkgTemplates
        t = Template()
        t("MyPkg")
        ```

        This will create a blank package, `"MyPkg"`, in your `.julia/dev` directory. Note that PkgTemplates allows you to control many different options through its `Template` constructor.

        In step 2 below, edit `MyPkg/src/MyPkg.jl` to change the source code, and `MyPkg/test/runtests.jl` for the tests.
      * For "throw-away" projects, you can avoid any need for cleanup by doing your work in your temporary directory (e.g., `/tmp`).

        Navigate to your temporary directory and launch Julia, then do the following:

        ```julia-repl
        pkg> generate MyPkg            # type ] to enter pkg mode
        julia> push!(LOAD_PATH, pwd())   # hit backspace to exit pkg mode
        ```

        If you restart your Julia session you'll have to re-issue that command modifying `LOAD_PATH`.

        In step 2 below, edit `MyPkg/src/MyPkg.jl` to change the source code, and create any test file of your choosing.
2. Develop your package

    *Before* loading any code, make sure you're running Revise: say `using Revise` or follow its documentation on configuring it to run automatically.

    Then navigate to the directory containing your test file (here assumed to be `"runtests.jl"`) and do the following:

    ```julia-repl
    julia> using MyPkg

    julia> include("runtests.jl")
    ```

    You can iteratively modify the code in MyPkg in your editor and re-run the tests with `include("runtests.jl")`.  You generally should not need to restart your Julia session to see the changes take effect (subject to a few [limitations](https://timholy.github.io/Revise.jl/stable/limitations/)).
