# Quick start

1. Install Docker and Docker Compose
Instructions for ubuntu 16-04 [here](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04) and [here](https://docs.docker.com/compose/install/#prerequisites), don't skip optional step 2 to run docker without sudo

2. To get the latest docker-compose.yml file, clone the repository
```
git clone https://github.com/DEIPworld/deip-testnet
cd deip-testnet
```

3. Pull the latest docker image
```
docker-compose pull
```

4. Configure node parameters in `deip-config.env`

5. Launch the node
```
docker-compose up
```

### More documentation
[How to run testnet node with docker](https://github.com/DEIPworld/deip-testnet/docs/blob/master/how-to-run-testnet-node-with-docker.md)

[How to create account using wallet](https://github.com/DEIPworld/deip-testnet/docs/blob/master/create-account-using-wallet.md)

[How to become a witness](https://github.com/DEIPworld/deip-testnet/docs/blob/master/how-to-become-a-witness.md)

[Wallet](https://github.com/DEIPworld/deip-testnet/docs/blob/master/wallet.md)