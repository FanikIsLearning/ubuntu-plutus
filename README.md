# ubuntu-plutus-app (Ubuntu 20.04 LTS + https://www.virtualbox.org/)

ubuntu setup for plutus playground

some useful infos:
https://docs.plutus-community.com/docs/setup/Ubuntu.html

https://nixos.org/manual/nix/stable/installation/installing-binary.html

## VirtualBox setting for macOS Monterey Version 12.1

If VirtualBox is running slow on Mac, you can try the following config on your Macbook

https://askubuntu.com/questions/883955/ubuntu-software-center-is-very-slow

https://mkyong.com/mac/virtualbox-running-slow-and-lag-on-macos-macbook-pro/

```console
sudo nano /Applications/VirtualBox.app/Contents/Resources/VirtualBoxVM.app/Contents/Info.plist
```

Change High Resolution Capable to NO

## Step by step

Plutus Playground Setup and Run Instructions

## 1. prerequisite software

```console
sudo apt update
```
```console
sudo apt-get install build-essential
```
```console
sudo apt install nodejs
```
```console
sudo apt install curl git
```

## 2. nix install

```console
sh <(curl -L https://nixos.org/nix/install) --no-daemon
```

```console
. ~/.nix-profile/etc/profile.d/nix.sh
```

## 3. binary cache

```console
mkdir ~/.config/nix
```

```console
echo "substituters        = https://hydra.iohk.io https://iohk.cachix.org https://cache.nixos.org/
trusted-public-keys = hydra.iohk.io:f/Ea+s+dFdN+3Y/G+FDgSq+a5NEWhJGzdjvKNGv0/EQ= iohk.cachix.org-1:DpRUyj7h7V830dp/i6Nti+NEO2/nhblbov/8MW7Rqoo= cache.nixos.org-1:6NCHdD59X431o0gWypbMrAURkbJ16ZPMQFGspcDShjY=
experimental-features = nix-command" > ~/.config/nix/nix.conf
```

restart

## 4. plutus-repo preparation
```console
git clone https://github.com/input-output-hk/plutus-apps
```

```console
cd plutus-apps
```

```console
git checkout 41149926c108c71831cfe8d244c83b0ee4bf5c8a
```

## 5. building the playground

```console
nix-build -A plutus-playground.server
```

## 6. running the playground at https://localhost:8009/
# server

```console
cd plutus-apps
```

```console
nix-shell
```

```console
plutus-playground-server
```

```console 
plutus-playground-server
```

## 7. new terminal window
# client

```console
cd plutus-apps
```

```console
nix-shell
```

```console
cd plutus-playground-client
```

```console
npm install
```

```console
npm start
```

This should get the playground running
and then

### Haddock documentation for the various plutus libraries

```console
cd plutus-apps/
nix-shell
build-and-serve-docs
```
and then it will soft set port 8002

http://0.0.0.0:8002/haddock

### Notes
Uninstall nix
https://discussions.apple.com/docs/DOC-7942


