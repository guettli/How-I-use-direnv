# How I use Direnv

## What is Direnv?

[Direnv](https://direnv.net/) has become one very important part of my development environments.

This tool reads `.envrc` files and sets up the environment accordingly.

## Example

```sh
# shellcheck shell=bash

# .envrc file of direnv.
# If you use vsode, pleaes use the `direnv` extension.

# Use nix-direnv
# https://github.com/nix-community/nix-direnv
# Ensures that flake.nix gets evaluated.
use flake

export PATH="$PWD/scripts:$PWD/node_modules/.bin:$PATH/bin:$PATH"

# Load variables from .env
dotenv
```

When you have direnv installed, and you enter the directory containing the `.envrc` file, the above
lines get executed.

I recommend [VSCode Direnv Extension](https://marketplace.visualstudio.com/items?itemName=mkhl.direnv), if you use vscode. It enables
your custom environment for tasks started by vscode (for example AI coding agents).

Above examples uses Nix Flakes `use flake`, but that is just and example. Ignore that, if you do not use Nix yet.

Then I update the PATH to read executables from the environment.

At the last line (`dotenv`) I load secrets from a `.env` file. If you keep secrets out of `.envrc`, you can add it to Git, and all team members get 
the same environment.

## Nix

Direnv works well together with Nix. I describe that here: [guettli/switching-to-nix: Switching to Nix](https://github.com/guettli/switching-to-nix)

