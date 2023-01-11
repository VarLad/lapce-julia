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

Paste these commands in a terminal (this assumes bash as the shell):

```sh
mkdir -p $HOME/.local/bin/flatpak
JULIA_PATH=`which julia || which julialauncher || echo 1`
if [ $JULIA_PATH != 1 ]
then
  cat >> $HOME/.local/bin/flatpak/julia <<EOF
  #!/usr/bin/env sh

  flatpak-spawn --host $JULIA_PATH "$@"
  EOF
  chmod +x $HOME/.local/bin/flatpak/julia
else
  echo "Julia not installed on PATH"
fi
```

Then in Lapce, point the custom julia executable path to (YOUR_HOME_FOLDER/.local/bin/flatpak/julia (for reference, look at the above section).

You can find YOUR_HOME_FOLDER with the following command `echo $HOME`(usually `/home/yourusername`).
Typically, the full path looks like `/home/username/.local/bin/flatpak/julia`.
