# Local finschia single node development network

### Requirements

- Required: docker, docker-compose

## Starting the blockchain

### Run with local binary
```shell
./start_local.sh
```

### Run with docker
```shell
# Start the Finschia node
./start.sh

# Stop the Finschia node
./stop.sh
```

## Starting the faucet

### Run with local faucet
```shell
# Start faucet
./faucet.sh
```

### Checking the faucets status
```shell
curl http://localhost:8000/status
```

### Using the faucet
```shell
curl --header "Content-Type: application/json" \
--request POST \
--data '{"denom":"cony", "address":"link1pheah96n54rwnuu4xej9egwwggn3h8uvv7pjdu"}' \
http://localhost:8000/credit
```


## Run Test All Finschia Environment Set with docker-compose
To test Finschia locally, you need not only a node, but also an explorer and faucet. All of these development environments can be run with docker-compose as follows.  
```shell
# Start the finschia node and explorer and faucet and dashboard in background mode
docker-compose up -d

# Stop 
docker-compose down
```
* localnet dashboard: http://localhost:8000
* faucet: http://localhost:8081
* swagger: http://localhost:1317/swagger/#/
* explorer: http://localhost:8080

## How to change and generate default genesis and configurations

1. change the docker image you want in the `./single/env` file.
2. cd `./single/template`.
3. execute `./setup.sh docker`.
4. check the difference of `app.toml`, `client.toml`, `config.toml` and
   `genesis.json` in the `./single/template/.finschia/config` directory
   and select the code you want.

## Accounts

Through setup.sh, 11 accounts added to genesis. Every account is derived from the same mnemonic (`mind flame tobacco sense move hammer drift crime ring globe art gaze cinnamon helmet cruise special produce notable negative wait path scrap recall have`) and every account has the same amount of balances (`100000000000cony`).

- 1 validator account : hdpath(44/438/1/0/0)
- 1 faucet account: hdpath(44/438/2/0/0)
- 9 ordinary account: hdpath(44/438/0/0/0~8)
- 1 multisig account: multisig of account0,account1,account2,account3,account4 and threshold is 2.
