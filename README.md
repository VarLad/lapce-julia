# Lapce Julia (LanguageServer)

Lapce plugin for the Julia language powered by LanguageServer.jl

## Pre-requisites

- Make sure you have the `julia` binary on PATH. This might not be the case if you installed julia using `juliaup`. 

- Make sure you have LanguageServer.jl installed in the main environment. You can install LanguageServer.jl using:
```julia
]add LanguageServer
```

in a Julia REPL.

## Passing custom julia executable path

In case you don't have julia on PATH, or your binary is named differently, as in the case of when its installed by `juliaup` (where its called `julialauncher`), you can still point to it in: Settings > Plugins > Julia (LanguageServer.jl)
