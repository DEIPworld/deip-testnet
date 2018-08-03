# Running testnet node with Docker

#### Basic node setup

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

4. Configure node parameters in `deip-config.env`.

To configure **witness node** set following parameters:\
`DEIPD_WITNESS_NAME` - name of your witness account who will run the node \
`DEIPD_PRIVATE_KEY` - your witness account private key

To configure **full node** set following parameters:\
`USE_WAY_TOO_MUCH_RAM = 1` - to start full node \
`USE_FULL_WEB_NODE = 1` - to start web node with full set of APIs and associated plugins

You can also set `DEIPD_SEED_NODES` parameter if you want your node to connect to already running nodes. Whitespace delimited list of seed nodes (with port).

5. Launch the node in detached mode
```
docker-compose up -d
```
You can always look at its latest logs
```
docker-compose logs --tail 100
```
And stop it, if needed
```
docker-compose stop
```
