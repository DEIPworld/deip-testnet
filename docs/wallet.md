# Wallet

## How to start a wallet

1. Install Docker and Docker Compose
Instructions for ubuntu 16-04 [here](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04) and [here](https://docs.docker.com/compose/install/#prerequisites), don't skip optional step 2 to run docker without sudo

2. To get the latest docker-compose.yml file, clone the repository
```
git clone https://github.com/DEIPworld/deip-testnet
cd deip-testnet
```

3. Pull the latest docker images
```
docker-compose pull
```

4. Execute command
```
docker-compose run wallet -w /var/lib/wallet/wallet.json -s ws://82.196.2.5:8090
```
After this wallet will start and connect to node at 82.196.2.5 (Full-Node supported by DEIP). You can specify different address if you want to connect to different node.
Wallet file is saved to `data` folder.

To stop the wallet, press `Ctrl + P`, `Ctrl + Q`.

To get list of all available arguments execute:
```
docker-compose run wallet --help
```

## Further actions

[How to create account using wallet](https://github.com/DEIPworld/deip-testnet/blob/master/docs/create-account-using-wallet.md)

[How to become a witness](https://github.com/DEIPworld/deip-testnet/blob/master/docs/how-to-become-a-witness.md)

## Available commands
To get full list of all commands supported by wallet, execute `help` command while running wallet.

To get detailed information about command and all parameters, execute `gethelp command_name`, i.e. `gethelp create_account`