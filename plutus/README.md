The Plutus Playground

## Getting started

### Starting Docker

```bash
$ cd project_path
$ docker-compose up -d
```

### Setup

```bash
$ cd project_path
$ docker-compose exec plutus-origin bash
installer@396ff5e9de23:~/src$ make begin
```

### Starting the backend server

```bash
installer@396ff5e9de23:~/src$ make start-server
[nix-shell:~/src/plutus]$ cd /home/installer/src/plutus/plutus-pab && plutus-pab-generate-purs
[nix-shell:~/src/plutus]$ cd /home/installer/src/plutus/plutus-playground-server && plutus-playground-generate-purs
[nix-shell:~/src/plutus]$ cd /home/installer/src/plutus/plutus-playground-server && plutus-playground-server
```

### Starting the frontend server

With the backend server running you can get started using the `npm start` script (open new terminal):

```bash
$ cd project_path
$ docker-compose exec plutus-origin bash
installer@396ff5e9de23:~/src$ make start-client
[nix-shell:~/src/plutus]$ cd /home/installer/src/plutus/plutus-playground-client && npm run start
```

## Note: access url https://localhost:8089/