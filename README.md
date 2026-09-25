# volt-gui Nix

Unofficial Nix flake for [volt-gui](https://github.com/pythonlover02/volt-gui).

The flake builds:

- 64-bit and 32-bit Vulkan layers
- `volt`
- `volt-probe`
- the volt-gui interface
- the Vulkan manifest, desktop entry, and icon

## Installation

### Nix profile

Install into your user profile:

```sh
nix profile install github:keygenesis/volt-gui-nix
```

Run the GUI with:

```sh
volt-gui
```

### NixOS / Home Manager

Add the flake as an input:

```nix
inputs.volt-src = {
  url = "github:pythonlover02/volt-gui";
  flake = false;
};

inputs.volt-gui = {
  url = "github:keygenesis/volt-gui-nix";
  inputs.volt-src.follows = "volt-src";
};
```

Then add the package through NixOS or Home Manager:

```nix
inputs.volt-gui.packages.${pkgs.system}.default
```

### Run without installing

```sh
nix run github:keygenesis/volt-gui-nix
```

## Updating

This flake tracks the upstream volt-gui repository as an input.

To update the locked upstream version:

```sh
nix flake update volt-gui volt-src
```

Then rebuild your NixOS or Home Manager configuration.

## Upstream

volt-gui is developed by [pythonlover02](https://github.com/pythonlover02/volt-gui).

This repository only provides Nix packaging.
