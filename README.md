# ubuntu-plutus-app
ubuntu setup for plutus playground

some useful infos:
https://docs.plutus-community.com/docs/setup/Ubuntu.html

https://nixos.org/manual/nix/stable/installation/installing-binary.html

## VirtualBox setting for macOS Monterey Version 12.1
```sudo nano /Applications/VirtualBox.app/Contents/Resources/VirtualBoxVM.app/Contents/Info.plist```
Change High Resolution Capable to NO

## Step by step

Plutus Playground Setup and Run Instructions

## 1. prerequisite software
```sudo apt install curl git```

## 2. nix install
```sh <(curl -L https://nixos.org/nix/install) --no-daemon```
```. ~/.nix-profile/etc/profile.d/nix.sh```

## 3. binary cache
```mkdir ~/.config/nix```
```echo "substituters = https://hydra.iohk.io/ https://iohk.cachix.org/ https://cache.nixos.org/```
```trusted-public-keys = hydra.iohk.io:f/Ea+s+dFdN+3Y/G+FDgSq+a5NEWhJGzdjvKNGv0/EQ= iohk.cachix.org-1:DpRUyj7h7V830dp/i6Nti+NEO2/nhblbov/8MW7Rqoo= cache.nixos.org-1:6NCHdD59X431o0gWypbMrAURkbJ16ZPMQFGspcDShjY=```
```experimental-features = nix-command" > ~/.config/nix/nix.conf```

## 4. plutus-repo preparation
```git clone https://github.com/input-output-hk/plutus-apps```
```cd plutus-apps```
```git checkout 41149926c108c71831cfe8d244c83b0ee4bf5c8a```

## 5. building the playground
```nix-build -A plutus-playground.server```

## 6. running the playground at https://localhost:8009/
# server
```cd plutus-apps```
```nix-shell```
```plutus-playground-server```
```plutus-playground-server```

## 7. new terminal window
# client
```cd plutus-apps```
```nix-shell```
```cd plutus-playground-client```
```npm install```
```npm start```

This should get the playground running
and then

## Lesson
## Building the week01 English Auction Contract

```cd plutus-apps```
```nix-shell```
```cd plutus-pioneer-program/code/week01/```
```cabal update```
```cabal build```

This worked for me @gluspier @PlanetStake

### Useful Tools in plutus-apps

### Haddock documentation for the various plutus libraries

```console
cd plutus-apps/
nix-shell
build-and-serve-docs
```
and then it will soft set port 8002

http://0.0.0.0:8002/haddock


or to uninstall nix if you prefere solidity :D (god sees everything):
https://gist.github.com/kintsugi/47e5e9f9d7c3a3a2f6004b6271365f8c 

