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


## Finding julia in case of flatpak

In case you have installed Lapce via Flathub, which you can check from the distro's Store itself or by running `flatpak info dev.lapce.lapce`, there could be a few issues running running julia. Depending on how you've installed julia, here's a few ways to make it work.

- If you've installed it in some folder in your home directory, you can just paste the path to Lapce using the method discussed in the previous section
- If you've installed julia using your package manager, or using juliaup, follow the below procedure

Make and edit a file with the following contents:

```sh
#!/usr/bin/env sh

flatpak-spawn --host $JULIA_PATH "$@"
EOF
chmod +x $HOME/.local/bin/flatpak/julia
```

Then make it executable by running

`chmod +x /path/to/file`

Then in Lapce, in plugin's setting, point to the file in the custom julia executable path (discussed in the above section)
