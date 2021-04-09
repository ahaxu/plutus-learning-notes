### Local plutus playground on Fedora 32

Need to install nodejs, npm first

We may got this error with eaccess permissions errors when installing packages globally - [link](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally), and need to install *purescript* and *spago*

```
npm install -g purescript
npm install -g spago
```

1. Clone plutus repo

`git clone https://github.com/input-output-hk/plutus`

2. from plutus root dir
```
cd plutus-playground-client
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

Then, there you go 🚀
