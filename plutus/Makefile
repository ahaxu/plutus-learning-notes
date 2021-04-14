#!/bin/bash 
SHELL := /bin/bash

begin:
	rm -rf plutus
	git clone https://github.com/input-output-hk/plutus.git
# edit file plutus-playground-client/webpack.config.js host: '0.0.0.0',
	sed -i "s/port: 8009,/host: '0.0.0.0',\n        port: 8009,/g" /home/installer/src/plutus/plutus-playground-client/webpack.config.js

	sudo rm -rf /etc/nix
	sudo mkdir /etc/nix
	sudo touch /etc/nix/nix.conf
	sudo cp nix.conf /etc/nix/nix.conf
	nix-store --gc
	cd /home/installer/src/plutus && nix build -f default.nix plutus.haskell.packages.plutus-core.components.library
	cd /home/installer/src/plutus && nix-build -A plutus-playground.client
	cd /home/installer/src/plutus && nix-build -A plutus-playground.server
	cd /home/installer/src/plutus && nix-build -A plutus-playground.generate-purescript
	cd /home/installer/src/plutus && nix-build -A plutus-playground.start-backend
	cd /home/installer/src/plutus && nix-build -A plutus-pab

start-server:
	cd /home/installer/src/plutus && nix-shell
# run in nix-shell command line
# cd /home/installer/src/plutus/plutus-pab && plutus-pab-generate-purs
# cd /home/installer/src/plutus/plutus-playground-server && plutus-playground-generate-purs
# cd /home/installer/src/plutus/plutus-playground-server && plutus-playground-server
start-client:
	cd /home/installer/src/plutus && nix-shell
# run in nix-shell command line
# cd /home/installer/src/plutus/plutus-playground-client && npm run start
nix-v:
	nix --version
nix-unreachable:
	nix-collect-garbage -d