# How to resync testnet node

1. To get the latest docker-compose.yml file, clone the repository if you do not have it yet
```
git clone https://github.com/DEIPworld/deip-testnet
cd deip-testnet
```
or pull latest changes
```
cd deip-testnet
git pull
```

2. Pull the latest docker image
```
docker-compose pull
```

3. In node config (`config/node.env` for witness node, `config/fullnode.env` for full node) uncomment the line:
```
# RESYNC_BLOCKCHAIN=1
```
It will force node to resync on startup. It means that your database will be purged and all blocks will be resynced.
