# How I Use Direnv

## What Is Direnv?

[Direnv](https://direnv.net/) has become a very important part of my development environments.

Direnv reads `.envrc` files and sets up your environment accordingly.

## Example

```sh
# shellcheck shell=bash

# .envrc file for direnv.
# If you use VS Code, please use the `direnv` extension.

# Use nix-direnv
# https://github.com/nix-community/nix-direnv
# Ensures that flake.nix gets evaluated.
use flake

export PATH="$PWD/scripts:$PWD/node_modules/.bin:$PATH"

# Load variables from .env
dotenv
```

When you have direnv installed and you enter the directory containing the `.envrc` file, the lines above get executed.

I recommend the [VS Code Direnv Extension](https://marketplace.visualstudio.com/items?itemName=mkhl.direnv) if you use VS Code. It enables your custom environment for tasks started by VS Code (for example, AI coding agents).

The example above uses Nix Flakes via `use flake`, but that’s just an example. Ignore it if you don’t use Nix (yet).

Next, I update `PATH` so executables from the environment are found first.

In the last line (`dotenv`), I load secrets from a `.env` file. If you keep secrets out of `.envrc`, you can commit `.envrc` to Git so all team members get the same environment.

## Config

My ~/.config/direnv/direnv.toml:

```toml
[global]
hide_env_diff = true
log_filter = "^$"

[whitelist]
   prefix = [ "/home/guettli/projects", "/home/guettli/syself" ]
```

There are two directories I trust, because they contain trusted git repos. Changes to `.envrc` files in that directories need no manual approval.

## Nix

Direnv works well together with Nix. I describe that here: [guettli/switching-to-nix: Switching to Nix](https://github.com/guettli/switching-to-nix)
