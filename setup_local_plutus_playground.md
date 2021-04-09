## Setup local plutus playground

This guide cotains 2 guides:

- local plutus playground on fedora 32
- local plutus playground on ubuntu 20 (noted by [https://twitter.com/DangQuanNguyen](https://twitter.com/DangQuanNguyen))

### Local plutus playground on Fedora 32

Need to install nodejs, npm first

We may got this error with eaccess permissions errors when installing packages globally - [link](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally), and need to install *purescript* and *spago*

```
npm install -g purescript
npm install -g spago
```

#### Follow steps below

1. Clone plutus repo

`git clone https://github.com/input-output-hk/plutus`

2. from plutus root dir
```
# stack clean --full # optional setp incase we might need to clean up stack local cache
stack build plutus-playground-server
stack exec -- plutus-playground-server psgenerator ./plutus-playground-client/generated
stack exec -- plutus-playground-server webserver 
```
3. cd to plutus root dir
```
nix build -f default.nix web-ghc
./result/bin/web-ghc-server webserver
```
4. start local playground

cd to plutus root dir
```
nix-shell
cd plutus-playground-client/
npm run start
```

in case error like this
```
Error 35 of 36:

  at src/plutus-playground-client/generated/Wallet/Rollup/Types.purs:2:1 - 25:15 (line 2, column 1 - line 25, column 15)

    Module Wallet.Rollup.Types has been defined multiple times


  See https://github.com/purescript/documentation/blob/master/errors/DuplicateModule.md for more information,
  or to contribute content related to this error.

Error 36 of 36:
...
```

Run
```
rm -rf src/plutus-playground-client/generated/
```
then `npm run start` again


Then, there you go 🚀


### Setup dev environment on Ubuntu 20.04 LTS

0. Prerequisites:

Install nix, npm, cabal.
Make sure that your nix profile is sourced every time you open a new terminal, by adding this line to your ~/.bashrc file:
source ~/.nix-profile/etc/profile.d/nix.sh

1. Clone repo & checkout correct revision

```
git clone https://github.com/input-output-hk/plutus.git
cd plutus
git checkout -b pioneer 3746610e53654a1167aeb4c6294c6096d16b0502
```

2. Setup IOHK binary cache

see README.adoc at root of plutus repo:

. On non-NixOS, edit `/etc/nix/nix.conf` and add the following lines:

```
substituters        = https://hydra.iohk.io https://iohk.cachix.org https://cache.nixos.org/
trusted-public-keys = hydra.iohk.io:f/Ea+s+dFdN+3Y/G+FDgSq+a5NEWhJGzdjvKNGv0/EQ= iohk.cachix.org-1:DpRUyj7h7V830dp/i6Nti+NEO2/nhblbov/8MW7Rqoo= cache.nixos.org-1:6NCHdD59X431o0gWypbMrAURkbJ16ZPMQFGspcDShjY=
```

3. Build plutus and plutus-playground

```
cd plutus
nix-shell
nix-build -A plutus
nix-build -A plutus-playground
```

4. Start plutus-playground-server
```
cd plutus-playground-client
plutus-playground-generate-purs
plutus-playground-server
```

5. Start plutus-playground frontend

Open another terminal
```
cd plutus
nix-shell
cd plutus-playground-client
npm run start
```

Wait until you see 'wdm: Compile successfully.'

6. Enjoy the plutus & playground:

Open a web browser at
https://localhost:8009/

You should see the demo files: Hello world, Starter, Game, etc.
You should be able to compile and simulate them.
